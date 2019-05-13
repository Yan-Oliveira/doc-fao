CI Assignment Attribute Dynamic Field Map
=========================================

This feature add-on makes it possible to link configuration items (CIs) from the OTRS CMDB with services and SLAs, thereby both providing service agents with a better overview and making it possible to offer purely CI-oriented services. This is especially helpful for companies that provide services for a wide range of different devices or products and that must conform to strict SLAs.

In addition, the feature add-on also makes it possible to map and link CI attributes to previously created dynamic fields. If the fields are merely text fields, it is possible to carry out simple mapping in the system configuration. In the event that the CI has multiple values that must be displayed in a ‘drop down’ dynamic field in the ticket, an extended mapping must be configured.

To do so it is first necessary to link the value to be assigned with the CI attribute key, e.g. ``NIC::IPoverDHCP``, in order to then assign the content of the values of the CI attribute to the values of the dynamic field. Because it is not possible for technical reasons to do this in the system configuration graphical frontend of OTRS, it is necessary to modify the file ``Kernel/Config/Files/OTRSCIAssignmentSLA.xml``. To do so, the values of the dynamic fields — e.g. desktop, laptop, cell phone, etc. — are simply inserted into the *Hash-Item-Hash* part of the code as in the following example:

.. code-block:: XML

   <Hash>
       <Item Key="NIC::IPoverDHCP">
           <Hash>
               <Item Key="Yes">1</Item>
               <Item Key="No">2</Item>
           </Hash>
       </Item>
       <Item Key="Type">
           <Hash>
               <Item Key="Desktop">1</Item>
               <Item Key="Laptop">2</Item>
               <Item Key="Other">3</Item>
               <Item Key="PDA">4</Item>
               <Item Key="Phone">5</Item>
               <Item Key="Server">6</Item>
           </Hash>
       </Item>
   </Hash>

The numbers define the order in which the values are shown in the dynamic drop-down field. The changes are incorporated into the system configuration by clicking on the refresh button and reloading the page. It is now possible to assign the values of the dynamic field to the newly added values. If a CI is then linked to a ticket, the CI attributes assigned in the mapping will be shown in the ticket information on the right and will be automatically updated when the CMDB is modified.

Benefits
   - Better overview for agents thanks to the assignment of CIs to services and SLAs.
   - Enables the provision of CI-oriented services with numerous CI attributes.
   - Greater flexibility and transparent linking of CI attributes to ticket dynamic fields.
   - Optimized visualization of CI attributes with multiple values in a drop-down in the ticket.
   - CI attributes are readable and searchable.

Available in Service Package
   GOLD

Target Groups
   - Companies that offer services for different devices/products (CIs)
   - Agents
   - Internal and external IT
   - Facility Management

.. note::

   - We recommend that you carry out a backup before changing the file.
   - If the link between a CI and a dynamic field is removed, the values of the dynamic fields are not automatically deleted.
   - When assigning CIs to services, the service function must be activated in the system configuration and the CI fields for services and SLAs must be configured.
   - If a CI that is already assigned to a service is assigned again, the service and the SLAs will be updated to correspond to the new link.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ci-assignment-attribute-dynamic-field-map/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ci-assignment-attribute-dynamic-field-map/admin
   ci-assignment-attribute-dynamic-field-map/agent
   ci-assignment-attribute-dynamic-field-map/external
