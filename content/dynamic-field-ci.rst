Dynamic Field CI
================

This feature add-on makes it possible to show configuration items from the OTRS CMDB in dynamic fields in ticket masks in the agent and customer interface. This speeds up the ticket creation process for agents and clients by enabling the use of filters so that only those configuration items that are relevant for the client company are shown and can be selected in the ticket masks. In addition, the configuration item search function can also be used directly in the ticket. Filters can be defined, e.g. based on:

- Configuration item class
- Usage status
- Incident status
- Customer
- Customer user

In addition, the following configurations are possible:

- Automatic linking and type of linking between configuration item and ticket.
- How and in which ticket masks the configuration item should be shown (e.g. as a dropdown or a tree view).
- Visualization in the external or agent interface.

Benefits
   - Customer-based visualization and selection of configuration items when creating a ticket in the external interface.
   - Faster ticket creation thanks to the use of filters to choose which configuration items should be shown, e.g. according to class, usage status, incident status, etc.
   - Maximum flexibility through use in different ticket masks for customers and/or agents.
   - Rapid search for configuration items when creating a ticket.
   - Useful for statistics and automatic ticket notifications.

Available in Service Package
   GOLD

Target Groups
   - Customers of companies that offer services for different devices/products (CIs)
   - Customer service
   - Internal and external IT
   - Facility management
   - Sales

.. note::

   This feature add-on requires the *ITSM Configuration Management* feature.

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`ticket-forms`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-dynamic-field-ci/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   dynamic-field-ci/admin
   dynamic-field-ci/agent
   dynamic-field-ci/external
