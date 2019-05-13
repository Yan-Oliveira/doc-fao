Hide/Show Dynamic Fields
========================

A dynamic field enables the extension of the information stored in a ticket and the individual configuration of your OTRS. However, dynamic fields can also cause confusion when they appear in the wrong context.

A typical example of an internal IT-department process is the ordering of hardware or software in OTRS. Dynamic fields help structure this order process through dropdown lists.

After choosing the object to be ordered (e.g. hardware), the feature add-on ensures that only appropriate choices will appear in the next step, e.g. screen, keyboard and printer. The dynamic fields defined for software, e.g. word processing, image processing or spreadsheet software, will not be displayed. This feature add-on can be used in the agent and the customer interface of your OTRS.

With this feature add-on, the following screens can be configured:

Agent Interface:

- New Phone Ticket
- New Email Ticket
- Ticket Phone Inbound
- Ticket Phone Outbound
- Ticket Note
- Ticket Close
- Ticket Move
- Ticket Pending
- Ticket Free Fields
- Ticket Owner
- Ticket Responsible
- Ticket Priority

Customer Interface:

- New Ticket
- Ticket reply (within *Ticket Zoom*)

Benefits
   - Clarity and transparency for your users.
   - Flexible configuration of ticket information in the agent and customer interface.
   - Faster and more accurate entering of information, saving time for your employees and customers.

Available in Service Package
   GOLD

Target Groups
   - IT services
   - Complaint management
   - E-commerce
   - Supply-chain management
   - IT support
   - Sales
   - Marketing
   - Procurement

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`advanced-editor`
   - :doc:`categories-for-text-modules`
   - :doc:`cis-in-customer-frontend`
   - :doc:`restore-pending-information`
   - :doc:`ticket-forms`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-hide-show-dynamic-fields/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   hide-show-dynamic-fields/admin
   hide-show-dynamic-fields/agent
   hide-show-dynamic-fields/external
