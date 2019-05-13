Ticket Forms
============

For service organizations that use the OTRS Help Desk software in different departments or that have to respond to many different types of customer requests, this Feature Add-on is a definite must-have. With it you can display different ticket masks and forms in the agent and customer interfaces, depending on which dynamic fields are relevant to the customer request. Moreover, the ticket creation process is faster as headlines and message body fields are pre-filled with the necessary information. You can define required fields for forms as well as display pre-filled fields, such as ticket types and services, in the customer interface based on the Customer Group settings. Since version 1.2.1, you can also pre-fill ticket masks by adding attachments, using rich text format, or using the OTRS Smart Tags ``<OTRS_CONFIG_*>`` and ``<OTRS_CURRENT_*>`` in the template body.

With this feature add-on the following screens can be configured:

- Agent Interface

   - New phone ticket
   - New email ticket

- Customer Interface

   - New ticket

In addition, the included feature add-on :doc:`hide-show-dynamic-fields`, which is also available as a separate feature add-on, enables you to define which dynamic fields you want to display in your ticket forms and which ones you want to hide. This gives you more freedom to configure all OTRS ticket masks to your specific needs.

Another included feature add-on is :doc:`restore-pending-information`, which makes it possible to restore the pending reminder information of the last reminder when you open a new reminder in the ticket pending pop-up screen.

The following information can be restored:

- Pending Date
- State
- Title
- Text (only pre-filled if the text comes from a note article; for example, one created by the AgentTicketPending pop-up screen)

This feature add-on works when the target time of the reminder has not expired; otherwise, the standard functionality sets the usual default values.

Benefits
   - Flexible reaction to a variety of customer requests.
   - Acceleration of processes by using forms.
   - Increases the completeness of forms by defining mandatory fields.

Available in Service Package
   GOLD

Target Groups
   - Customer service/support
   - IT service management
   - Sales
   - Public authorities

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`advanced-editor`
   - :doc:`categories-for-text-modules` (when deployed in OTRS 3.2)
   - :doc:`cis-in-customer-frontend`
   - :doc:`dynamic-field-ci`
   - :doc:`hide-show-dynamic-fields`
   - :doc:`restore-pending-information`
   - :doc:`service-based-queue-routing` (when deployed in OTRS 3.3)

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-forms/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-forms/admin
   ticket-forms/agent
   ticket-forms/external
