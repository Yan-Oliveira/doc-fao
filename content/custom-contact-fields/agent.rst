Agent Interface
===============

This package has no agent interface.


New Features
------------

Storing/Changing customer in a *Customer* field
   After the dynamic field of the type *Customer* was configured in the :doc:`admin/processes-automation/dynamic-fields` screen and added to the different views, the functionality can get used. The contact fields will be displayed below the recipients for new tickets or otherwise in the dynamic fields block of the page. The exact position and label of the field depends of the field configuration.

   If a customer number filter was configured the dynamic field will be locked and unchangeable as long as no customer is added to the ticket.

   After inserting at least one character into the text field of the dynamic field a search over the configured customer databases starts. At this point the configured filter takes it place and removes unmatched customers from the result set. To start a search for all available customers for this field you can use the ``*`` wildcard.

Showing *Customer* dynamic field values for a ticket
   To allow display of the *Customer* dynamic field values after the data was stored to the ticket, the different views (*Ticket Zoom* and *Ticket Detail View*) have to be configured accordingly.

Using *Customer* dynamic field values for communication in a ticket
   If a field has been configured to use the contacts for communication and the *reply all* functionality is used in the *Ticket Zoom* screen, all customers stored in the respective field will be added to the configured recipient list (To/Cc/Bcc) unless they exist as a recipient already. If necessary, they can be removed from the recipients manually. This functionality is not available for the reply to action.

   .. note::

      The field must not be configured in the dynamic field section of ``AgentTicketCompose``.

Searching tickets for *Customer* dynamic field values
   To allow searching of the *Customer* dynamic field values after the data was stored to the ticket the search view has to be configured accordingly.

   .. seealso::

      Add the name of the dynamic field to setting ``Ticket::Frontend::AgentTicketSearch###DynamicField``.

   Depending on the system configuration it is possible that the field has to be selected from the attributes drop down box and added via clicking the *+* symbol.

   The search works equals to the search for regular customers. The login name of the customer has to be used as the search criteria.

   Additionally it is possible to use wildcards in the *Customer* dynamic field search. For example searching for all tickets that have an otrs.com user stored in the dynamic field would look like this: \*@otrs.com. To search all tickets with a *mr.smith* stored to it the criteria would look like this: *mr.smith@\**. If all tickets with a customer login containing *otrs* should get searched, the criteria would look like this: *\*otrs\**.
