Ticket Forms
============

For service organizations that use the **OTRS** helpdesk software in different departments or that have to respond to many different types of customer requests, this feature add-on is a definite must-have. With it you can display different ticket masks and forms in the agent and external interfaces, depending on which dynamic fields are relevant to the customer request. Moreover, the ticket creation process is faster as headlines and message body fields are pre-filled with the necessary information. You can define required fields for forms as well as display pre-filled fields, such as ticket types and services, in the external interface based on the customer group settings. You can also pre-fill ticket masks by adding attachments, using Rich Text format, or using the OTRS smart tags ``<OTRS_CONFIG_*>`` and ``<OTRS_CURRENT_*>`` in the template body.

With this feature add-on the following screens can be configured:

- Agent interface

   - New phone ticket
   - New email ticket

- External interface

   - New ticket

In addition, the included feature add-on :doc:`hide-show-dynamic-fields`, which is also available as a separate feature add-on, enables you to define which dynamic fields you want to display in your ticket forms and which ones you want to hide. This gives you more freedom to configure all ticket screens to your specific needs.

Another included feature add-on is :doc:`restore-pending-information`, which makes it possible to restore the pending reminder information of the last reminder when you open a new reminder in the ticket pending pop-up screen.

The following information can be restored:

- Pending date
- State
- Title
- Text (if the text comes from a note article created by the *Ticket Pending* screen)

This feature add-on works when the target time of the reminder has not expired. Otherwise the standard functionality sets the usual default values.

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
   - :doc:`categories-for-text-modules`
   - :doc:`cis-in-customer-frontend`
   - :doc:`dynamic-field-ci`
   - :doc:`hide-show-dynamic-fields`
   - :doc:`restore-pending-information`
   - :doc:`service-based-queue-routing`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-forms/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-forms/admin
   ticket-forms/agent
   ticket-forms/external
