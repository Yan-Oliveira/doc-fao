Administrator Interface
=======================

This package provides new features to the OTRS ticket screens, using the bundled packages :doc:`../hide-show-dynamic-fields`, *Dynamic Ticket Templates* and :doc:`../restore-pending-information`, as well as other functionalities provided by this package itself.

:doc:`../hide-show-dynamic-fields` package allows the definition of ACL based visibility of dynamic fields. For more information see the documentation of the package.

*Dynamic Ticket Templates* package uses the extension to the ACLs mechanism to create ticket templates based on the selected ticket type and service. This templates include a predefined ticket body, title, attachments and full dynamic fields visibility configuration.

:doc:`../restore-pending-information` package provides the functionality to pre-select the target time for pending reminder with the last target time (including time, status, title and text) set by the agent. For more information see the documentation of the package.

*Ticket Forms* itself, enables to set a custom maximum length for services and SLA names in ticket creation screens.

This feature can work cooperatively with :doc:`../ticket-workflow` package by integrating defined ticket workflows into a template and trigger them automatically when the ticket is created.

.. toctree::
   :maxdepth: 3
   :caption: Contents

   admin/ticket-settings
   admin/communication-notifications
   admin/users-groups-roles


Example Usage
-------------

For this example we will use the same fields as in the example of :doc:`../hide-show-dynamic-fields`, but is necessary to comment or remove the ACLs.

.. note::

   While the dynamic ticket templates can work in conjunction with other ACL rules, it is recommended to test the templates without other affecting ACLs, and after the templates work as needed, incorporate other ACLs one by one.


Preparation
~~~~~~~~~~~

To show the full functionalities of the dynamic ticket templates we can simply remove all dynamic fields for *New Phone Ticket* in the system configuration setting ``Ticket::Frontend::AgentTicketPhone###DynamicField`` or disable the dynamic fields:

.. code-block:: none

   Brand → 0 - Disabled
   VWModel → 0 - Disabled
   VWProductionFacility → 0 - Disabled
   PeugeotModel → 0 - Disabled
   PeugeotProductionFacility → 0 - Disabled
   Fuel → 0 - Disabled
   Accessories → 0 - Disabled
   Remarks → 0 - Disabled
   RegistrationDate → 0 - Disabled
   InvoiceDate → 0 - Disabled

To define a dynamic ticket template it is necessary to specify a ticket type and a service. If these features are not activated by default, please follow the next steps before start using this feature.

To activate ticket type and service features:

1. Go to *System Configuration* screen.
2. Select *OTRS* in the *Navigation* widget.
3. Navigate to *Core → Ticket* in the navigation tree.
4. Scroll down to the setting ``Ticket::Service`` and enable it.
5. Scroll down to the setting ``Ticket::Type`` and enable it.

   .. note::

      Notice that if you already have ITSM packages this options are already active.

To activate ticket type and service features for the external interface:

1. Go to *System Configuration* screen.
2. Select *All settings* in the *Navigation* widget.
3. Navigate to *Frontend → External → View → TicketCreate* in the navigation tree.
4. Scroll down to the setting ``ExternalFrontend::TicketCreate###Service`` and enable it.
5. Scroll down to the setting ``ExternalFrontend::TicketCreate###TicketType`` and enable it.

Create the following services:

- *Peugeot Service*
- *VW Service*

All services should be available for the customer user who will use this feature, or marked as default services.


Goals of This Example
~~~~~~~~~~~~~~~~~~~~~

The goals of this example are the follows:

- If the selected service is *VW Service* and the selected dynamic ticket template is *VWTemplate1*, the ticket form should look like:

   +---------------+-----------------------------------------------+
   | Subject       | VW Service Request 1                          |
   +---------------+-----------------------------------------------+
   | Body          | - Oil Change                                  |
   |               | - Oil Filter Change                           |
   |               | - Air Filter Change                           |
   |               | - Fluids Check                                |
   +---------------+-----------------------------------------------+
   |Dynamic Fields | - ``VWModel``: visible and required           |
   |               | - ``VWProductionFacility``: visible           |
   +---------------+-----------------------------------------------+

- If the selected service is *VW Service* and the selected dynamic ticket template is *VWTemplate2*, the ticket form should look like:

   +---------------+-----------------------------------------------+
   | Subject       | VW Service Request 2                          |
   +---------------+-----------------------------------------------+
   | Body          | The selected accessory reports the            |
   |               | following issues:                             |
   +---------------+-----------------------------------------------+
   |Dynamic Fields | - ``VWModel``: visible                        |
   |               | - ``Accessories``: visible and required       |
   |               | - ``Remarks``: visible                        |
   |               | - ``RegistationDate``: visible                |
   |               | - ``InvoiceDate``: visible                    |
   +---------------+-----------------------------------------------+

- If the selected service is *Peugeot Service*, the ticket form should look like:

   +---------------+-----------------------------------------------+
   | Subject       | Peugeot Service Request                       |
   +---------------+-----------------------------------------------+
   | Body          | The car computer report the following issues: |
   +---------------+-----------------------------------------------+
   |Dynamic Fields | - ``PeugeotModel``: visible                   |
   |               | - ``PeugeotProductionFacility``: visible      |
   |               | - ``Fuel``: visible                           |
   +---------------+-----------------------------------------------+


Create Dynamic Ticket Templates
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To create the dynamic ticket templates:

1. Open the :doc:`admin/ticket-settings/dynamic-ticket-templates` module of the *Ticket Settings* group in the administrator interface.
2. Click on the *Add template* in the left sidebar.
3. Fill in the required fields.
4. Click on the *Save* button.

If you have added other dynamic fields by your own, the template form will show more fields than the ones explained in this examples. There is nothing to worry about, just leave all other dynamic fields as *Hide* while you create the new templates.

There are special dynamic fields from ITSM packages that are not displayed in the template form. This special fields has a determined behavior and they should be always hidden, always shown or their visibility depends on other configurations, so they can not be part of the template definition. Also any dynamic field marked as *Internal* will not be displayed in the template form.

.. seealso::

   A quick way to know if a dynamic field is *Internal* is to look at dynamic fields in the overview table of the *Dynamic Field Management* screen. *Internal* dynamic fields can not be deleted, and they does not have a icon in the *Delete* column.

Create the *VWTemplate1* dynamic ticket template with the following data:

+-------------------------------+------------------------------+
| Field name                    | Value                        |
+===============================+==============================+
| Name                          | VWTemplate1                  |
+-------------------------------+------------------------------+
| Comments                      | VW Template 1                |
+-------------------------------+------------------------------+
| Valid                         | Valid                        |
+-------------------------------+------------------------------+
| Frontend                      | Agent and External Interface |
+-------------------------------+------------------------------+
| Type                          | Unclassified                 |
+-------------------------------+------------------------------+
| Service                       | VW Service                   |
+-------------------------------+------------------------------+
| Subject                       | VW Service Request 1         |
+-------------------------------+------------------------------+
| Body                          | - Oil Change                 |
|                               | - Oil Filter Change          |
|                               | - Air Filter Change          |
|                               | - Fluids Check               |
+-------------------------------+------------------------------+
| Attachments                   |                              |
+-------------------------------+------------------------------+
| ``Brand``                     | Hide                         |
+-------------------------------+------------------------------+
| ``VWModel``                   | Show as mandatory            |
+-------------------------------+------------------------------+
| ``VWProductionFacility``      | Show                         |
+-------------------------------+------------------------------+
| ``PeugeotModel``              | Hide                         |
+-------------------------------+------------------------------+
| ``PeugeotProductionFacility`` | Hide                         |
+-------------------------------+------------------------------+
| ``Fuel``                      | Hide                         |
+-------------------------------+------------------------------+
| ``Accessories``               | Hide                         |
+-------------------------------+------------------------------+
| ``Remarks``                   | Hide                         |
+-------------------------------+------------------------------+
| ``RegistationDate``           | Hide                         |
+-------------------------------+------------------------------+
| ``InvoiceDate``               | Hide                         |
+-------------------------------+------------------------------+

Create the *VWTemplate2* dynamic ticket template with the following data:

+-------------------------------+------------------------------+
| Field name                    | Value                        |
+===============================+==============================+
| Name                          | VWTemplate2                  |
+-------------------------------+------------------------------+
| Comments                      | VW Template 2                |
+-------------------------------+------------------------------+
| Valid                         | Valid                        |
+-------------------------------+------------------------------+
| Frontend                      | Agent and External Interface |
+-------------------------------+------------------------------+
| Type                          | Unclassified                 |
+-------------------------------+------------------------------+
| Service                       | VW Service                   |
+-------------------------------+------------------------------+
| Subject                       | VW Service Request 2         |
+-------------------------------+------------------------------+
| Body                          | The selected accessory       |
|                               | reports the following        |
|                               | issues:                      |
+-------------------------------+------------------------------+
| Attachments                   |                              |
+-------------------------------+------------------------------+
| ``Brand``                     | Hide                         |
+-------------------------------+------------------------------+
| ``VWModel``                   | Show                         |
+-------------------------------+------------------------------+
| ``VWProductionFacility``      | Hide                         |
+-------------------------------+------------------------------+
| ``PeugeotModel``              | Hide                         |
+-------------------------------+------------------------------+
| ``PeugeotProductionFacility`` | Hide                         |
+-------------------------------+------------------------------+
| ``Fuel``                      | Hide                         |
+-------------------------------+------------------------------+
| ``Accessories``               | Show as mandatory            |
+-------------------------------+------------------------------+
| ``Remarks``                   | Show                         |
+-------------------------------+------------------------------+
| ``RegistationDate``           | Show                         |
+-------------------------------+------------------------------+
| ``InvoiceDate``               | Show                         |
+-------------------------------+------------------------------+

Create the *PeugeotTemplate* dynamic ticket template with the following data:

+-------------------------------+------------------------------+
| Field name                    | Value                        |
+===============================+==============================+
| Name                          | PeugeotTemplate              |
+-------------------------------+------------------------------+
| Comments                      | Peugeot Template             |
+-------------------------------+------------------------------+
| Valid                         | Valid                        |
+-------------------------------+------------------------------+
| Frontend                      | Agent and External Interface |
+-------------------------------+------------------------------+
| Type                          | Unclassified                 |
+-------------------------------+------------------------------+
| Service                       | Peugeot Service              |
+-------------------------------+------------------------------+
| Subject                       | Peugeot Service Request      |
+-------------------------------+------------------------------+
| Body                          | The car computer report the  |
|                               | following issues:            |
+-------------------------------+------------------------------+
| Attachments                   |                              |
+-------------------------------+------------------------------+
| ``Brand``                     | Hide                         |
+-------------------------------+------------------------------+
| ``VWModel``                   | Hide                         |
+-------------------------------+------------------------------+
| ``VWProductionFacility``      | Hide                         |
+-------------------------------+------------------------------+
| ``PeugeotModel``              | Show                         |
+-------------------------------+------------------------------+
| ``PeugeotProductionFacility`` | Show                         |
+-------------------------------+------------------------------+
| ``Fuel``                      | Show                         |
+-------------------------------+------------------------------+
| ``Accessories``               | Hide                         |
+-------------------------------+------------------------------+
| ``Remarks``                   | Show                         |
+-------------------------------+------------------------------+
| ``RegistationDate``           | Show                         |
+-------------------------------+------------------------------+
| ``InvoiceDate``               | Show                         |
+-------------------------------+------------------------------+


Activate Dynamic Ticket Templates
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once there are one or more templates activated in the system, you can use them.

.. note::

   ACL restrictions will be ignored for the superuser account (UserID 1).

To activate the dynamic ticket templates:

1. Click on the *New phone ticket* menu item of the *Ticket* menu in the navigation bar.

   There is new field called *Dynamic Ticket Template*. By default it is empty and it will be filled automatically when you select the appropriate combination of ticket type and service.

2. Fill the form with the following data:

   - Type: Unclassified
   - Customer user: Customer1
   - To queue: Misc
   - Service: VW Service

3. The *Dynamic Ticket Template* field will be automatically populated with *VWTemplate1* and *VWTemplate2*.
4. Select each template and match the resulting *New Phone Ticket* form with the expected results.
5. Now change the selected service to *PeugeotService*. As there is only one template defined for this combination of ticket type and service, the template will be automatically selected for you.
6. Compare the resulting *New Phone Ticket* form with the expected results.

This complete example can be tested also *New Email Ticket* or external *New Ticket* screen without changing anything.

The template definition is independent from the screen and once a template is defined, it can be used on any ticket creation screen, but please review the dynamic field configuration on each screen for the default fields configuration when a template is not selected.


Dynamic Ticket Templates Customer Groups
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this example we will use the *PeugeotTemplate* defined in the example above.

The goal to have a pre-filled form to create a new ticket in external interface.

To configure customer groups:

1. Go to *System Configuration* screen.
2. Select *OTRS* in the *Navigation* widget.
3. Navigate to *Core → Customer* in the navigation tree.
4. Scroll down to the setting ``CustomerGroupSupport`` and enable it.
5. Select *OTRSTicketForms* in the *Navigation* widget.
6. Navigate to *Core → DynamicTicketTemplate* in the navigation tree.
7. Scroll down to the setting ``Ticket::DynamicTicketTemplate::CustomerGroup`` and enable it.
8. Go to the *Group Management* screen of the administrator interface.
9. Create the group *PeugeotCustomer*.
10. Go to the *Customers ↔ Groups* screen of the administrator interface.
11. Assign *Customer1* customer to the *PeugeotCustomer* group.
12. Go to *Dynamic Ticket Templates ↔ Groups* screen of the administrator interface.
13. Assign the *PeugeotCustomer* group to the *PeugeotTemplate* template.
14. Login in the external interface as customer user of *Customer1* and create a new ticket.
15. Compare the pre-filed new ticket form with the expected results, also notice that the ticket type is pre-selected as default and service is also pre-selected as *PeugeotService*.

You can also set the optional setting, but for this example we will not use these optional settings, so you can leave it as default.

.. seealso::

   If no template is assigned to a group and the notification is enabled, such notification can be customized by adding different recipients or updating the notification body. To do this, edit the *Missing DTT assignment for CustomerGroup* notification in the :doc:`admin/communication-notifications/ticket-notifications` screen of the administrator interface.


Dynamic Ticket Templates and Ticket Workflows
---------------------------------------------

For this example we will use the *VWTemplate1* defined previously.

The goal to activate a predefined ticket workflow when create a new ticket using a particular dynamic ticket template.

.. seealso::

   Please follow the :doc:`../ticket-workflow` documentation for the steps to create a new ticket workflow.

Create a ticket workflow:

- Name: VWWorkflow1
- Comment: VW workflow 1
- Valid: valid
- Clone tasks from: -

Create a workflow task:

- Name: Oil Change Task
- To queue: Misc
- Owner: -
- Depends on: -
- Description: Change the oil
- Attachment: -
- Priority: 3 normal

Create an other workflow task:

- Name: Oil Filter Change Task
- To queue: Misc
- Owner: -
- Depends on: Oil Change Task
- Description: Change the oil filter
- Attachment: -
- Priority: 3 normal

Create an other workflow task:

- Name: Air Filter Change Task
- To queue: Misc
- Owner: -
- Depends on: -
- Description: Change the air Filter
- Attachment: -
- Priority: 3 normal

Create an other workflow task:

- Name: Fluids Check
- To queue: Misc
- Owner: -
- Depends on: Oil Change Task
- Description: Check all fluids
- Attachment: -
- Priority: 4 high

.. note::

   When dynamic ticket templates detects the installation of *OTRSTicketWorkflow* package, more options are revealed in the template edit screen.

To assign the ticket workflow to the dynamic ticket template:

1. Open the :doc:`admin/ticket-settings/dynamic-ticket-templates` module of the *Ticket Settings* group in the administrator interface.
2. Click on the *VWTemplate1* template name to edit it.
3. Set the workflow field to *VWWorkflow1*
4. Click on the *Save* button.

To activate the template and the workflow:

1. Click on the *New phone ticket* menu item of the *Ticket* menu in the navigation bar.
2. A new *Ticket Workflow* field has appeared. This field is just informative and can not be changed in ticket create screens, just in the dynamic ticket template definition. It shows the name of the ticket workflow to be applied automatically when the new ticket is created.
3. Fill the form with the following data:

   - Type: Unclassified
   - From customer: Customer1
   - Service: VWService
   - Dynamic Ticket Template: VWTemplate1

4. After selecting the *VWTemplate1*, the *Ticket Workflow* field will be filled with the *VWWorkflow1*.
5. Fill any other required field and submit the ticket.
6. After the ticket is created, click in the ticket number in the notification area at the top of the screen to zoom into the new ticket.
7. Look for the link table, either in the sidebar if configuration setting is set to *simple* or at the bottom of the page if is set to *complex*.
8. Verify that the list of liked tickets are the same as the tasks that where defined in the *VWWorkflow1* ticket workflow.
