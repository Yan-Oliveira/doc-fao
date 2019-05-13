Agent Interface
===============

For assigning an advanced escalation to a ticket, this one should contain a valid customer ID and valid SLA, so the advanced escalation for the ticket will be assigned based on previous configuration, advanced escalations currently does not work for unknown customers.

It is possible to show advanced escalations columns in ticket overviews, ticket dashboard widgets and statistics. The advanced escalations data is calculated on-the-fly and could have a huge negative performance impact on the whole system.

.. note::

   Escalation automatism is not supported. Use the generic agent or generic interface to trigger escalation events.

.. toctree::
   :maxdepth: 3
   :caption: Contents

   agent/tickets
   agent/reports


