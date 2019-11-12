Web Services
============

To create a new dynamic field of type *Web Service* it is necessary to have an already working web service. It requires to have at least one invoker of the type ``Generic::PassThrough``. This invoker will be called to fetch the data from the remote server. The original data that it is sent in a request is similar to the following example.

.. code-block:: Perl

   {
       DynamicFieldID    => 123,
       DynamicFieldLabel => 'NameX',
       DynamicFieldName  => 'NameX',
       DynamicFieldValue => 'Value',
       Form => {
           # Form fields
           # ...
       },
       Ticket => {
           # Ticket attributes
           # ...
       },
       DynamicField => {
           NameX => 'Value'
           NameY => [ 'Value' ],
       },
       UserID => 123,
   },

``Form``
   This section contains the fields in the current form in the web browser. This information changes as the screen is filled in.

``Ticket``
   This section (or another source object, e. g. ``CustomerUser``) contains the attributes of the object where the dynamic field belongs.

   For example in the *New Phone Ticket* screen the section is empty as the ticket is not created yet, but in the *Ticket Free Fields* screen it contains the information of the current ticket.

``DynamicField``
   This section contains all non empty values of all configured dynamic fields for the current object.

In most cases the data that the remote server requires will be very different from the data provided, so it is highly recommended to use a mapping module for the outgoing data to format it specifically for the remote server call.

The following outgoing mapping example shows an XSLT mapping that discards any data and sets a fixed ``UserLogin``, ``Password`` and ``TicketID`` (as needed for a ``TicketGet`` operation).

.. code-block:: XML

   <?xml version="1.0" encoding="UTF-8"?>
   <xsl:transform
       xmlns:xsl="https://www.w3.org/1999/XSL/Transform"
       xmlns:date="https://exsalt.org/dates-and-times"
       version="1.0"
       extension-element-prefixes="date">

       <xsl:output method="xml" encoding="utf-8" indent="yes" />

       <!-- Don't return unmached tags -->
       <xsl:template match="text()" />

       <!-- Remove empty elements -->
       <xsl:template match="*[not(node())]" />

       <!-- Root template -->
       <xsl:template match="/">
           <RootElement>
               <UserLogin>someuser</UserLogin>
               <Password>somepassword</Password>
               <TicketID>1</TicketID>
           </RootElement>
       </xsl:template>

   </xsl:transform>

The response from the server can also be very different, so in this case is also very recommended to use a mapping module for the incoming data in order to be able to process the information. The response must be a list of key and value elements.

The following incoming mapping example shows an XSLT mapping that converts the results from a ``TicketGet`` operation response form the remote server, extracting and formatting the state and queue as needed to be used as options for the dynamic field.

.. code-block:: XML

   <?xml version="1.0" encoding="UTF-8"?>
   <xsl:transform
       xmlns:xsl="https://www.w3.org/1999/XSL/Transform"
       xmlns:date="https://exsalt.org/dates-and-times"
       version="1.0"
       extension-element-prefixes="date">

       <xsl:output method="xml" encoding="utf-8" indent="yes" />

       <!-- Don't return unmached tags -->
       <xsl:template match="text()" />

       <!-- Remove empty elements -->
       <xsl:template match="*[not(node())]" />

       <!-- Root template -->
       <xsl:template match="/">
           <RootElement>
               <xsl:apply-templates />
           </RootElement>
       </xsl:template>

       <xsl:template match="/*/Ticket">
           <PossibleValue>
               <Key>State</Key>
               <Value>
                   <xsl:value-of select="/*/Ticket/State" />
               </Value>
           </PossibleValue>
           <PossibleValue>
               <Key>Queue</Key>
               <Value>
                   <xsl:value-of select="/*/Ticket/Queue" />
               </Value>
           </PossibleValue>
       </xsl:template>

   </xsl:transform>

The following web service definition (importable YAML file) can be used for testing the field, but the endpoint must be adapted to match current system. This web service acts as requester and provider and it always returns the state and queue from ``TicketID`` 1, as possible values to the field.

.. note::

   This example should not be used in conjunction with the development web server.

.. code-block:: YAML

   ---
   Debugger:
     DebugThreshold: debug
     TestMode: '0'
   Description: Dynamic Field Web Service Test
   FrameworkVersion: 7.0.x git
   Provider:
     ErrorHandling: {}
     ErrorHandlingPriority: []
     Operation:
       TicketGet:
         Description: ''
         IncludeTicketData: ''
         MappingInbound: {}
         MappingOutbound: {}
         Type: Ticket::TicketGet
     Transport:
       Config:
         AdditionalHeaders: ~
         MaxLength: '100000000'
         NameSpace: https://www.otrs.org/TicketConnector/
         RequestNameFreeText: ''
         RequestNameScheme: Plain
         ResponseNameFreeText: ''
         ResponseNameScheme: Response
       Type: HTTP::SOAP
   RemoteSystem: ''
   Requester:
     ErrorHandling: {}
     ErrorHandlingPriority: []
     Invoker:
       TicketGet:
         Description: Get possible values from the other side.
         Events: []
         MappingInbound:
           Config:
             Template: |-
                 <?xml version="1.0" encoding="UTF-8"?>
                 <!--
                 Copyright (C) 2001-2019 OTRS AG, https://otrs.com/
                 This software comes with ABSOLUTELY NO WARRANTY. For details, see
                 the enclosed file COPYING for license information (GPL). If you
                 did not receive this file, see https://www.gnu.org/licenses/gpl.txt.
                 -->

                 <!-- DOCUMENTATION

                 * Example XML Input *
                 <RootElement>
                     ...
                 </RootElement>


                 * Example XML Output *
                 <RootElement>
                     <PossibleValues>
                         <Key>???</Key>
                         <Value>???</Value>
                     </PossibleValues>
                     <PossibleValues>
                         <Key>???</Key>
                         <Value>???</Value>
                     </PossibleValues>
                     ...
                 </RootElement>

                 -->


                 <xsl:transform
                     xmlns:xsl="https://www.w3.org/1999/XSL/Transform"
                     xmlns:date="https://exslt.org/dates-and-times"
                     version="1.0"
                     extension-element-prefixes="date">

                     <xsl:output method="xml" encoding="utf-8" indent="yes" />

                     <!-- Don't return unmatched tags -->
                     <xsl:template match="text()" />

                     <!-- Remove empty elements -->
                     <xsl:template match="*[not(node())]" />

                     <!-- Root template -->
                     <xsl:template match="/">
                         <RootElement>
                             <xsl:apply-templates />
                         </RootElement>
                     </xsl:template>

                     <xsl:template match="/*/Ticket">
                         <PossibleValue>
                             <Key>State</Key>
                             <Value><xsl:value-of select="/*/Ticket/State" /></Value>
                         </PossibleValue>
                         <PossibleValue>
                             <Key>Queue</Key>
                             <Value><xsl:value-of select="/*/Ticket/Queue" /></Value>
                         </PossibleValue>
                     </xsl:template>

                 </xsl:transform>
           Type: XSLT
         MappingOutbound:
           Config:
             Template: |-
                 <?xml version="1.0" encoding="UTF-8"?>
                 <!--
                 Copyright (C) 2001-2019 OTRS AG, https://otrs.com/

                 This software comes with ABSOLUTELY NO WARRANTY. For details, see
                 the enclosed file COPYING for license information (GPL). If you
                 did not receive this file, see https://www.gnu.org/licenses/gpl.txt.
                 -->

                 <!-- DOCUMENTATION

                 * Example XML Input *
                 <RootElement>
                    ...
                 </RootElement>


                 * Example XML Output *
                 <RootElement>
                     <PossibleValues>
                         <Key>???</Key>
                         <Value>???</Value>
                     </PossibleValues>
                     <PossibleValues>
                         <Key>???</Key>
                         <Value>???</Value>
                     </PossibleValues>
                     ...
                 </RootElement>

                 -->

                 <xsl:transform
                     xmlns:xsl="https://www.w3.org/1999/XSL/Transform"
                     xmlns:date="https://exslt.org/dates-and-times"
                     version="1.0"
                     extension-element-prefixes="date">
                     <xsl:output method="xml" encoding="utf-8" indent="yes" />

                     <!-- Don't return unmatched tags -->
                     <xsl:template match="text()" />

                     <!-- Remove empty elements -->
                     <xsl:template match="*[not(node())]" />

                     <!-- Root template -->
                     <xsl:template match="/">
                         <RootElement>
                             <UserLogin>someuser</UserLogin>
                             <Password>somepassword</Password>
                             <TicketID>1</TicketID>
                         </RootElement>
                     </xsl:template>

                 </xsl:transform>
           Type: XSLT
         Type: Generic::PassThrough
     Transport:
       Config:
         Encoding: ''
         Endpoint: https://localhost/otrs/nph-genericinterface.pl/Webservice/GenericConfigItemConnectorSOAP
         NameSpace: https://www.otrs.org/TicketConnector/
         RequestNameFreeText: ''
         RequestNameScheme: Plain
         ResponseNameFreeText: ''
         ResponseNameScheme: Response
         SOAPAction: Yes
         SOAPActionSeparator: '#'
         SSL:
           SSLProxy: ''
           SSLProxyPassword: ''
           SSLProxyUser: ''
       Type: HTTP::SOAP
     UseMappedData: '1'
