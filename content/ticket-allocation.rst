Ticket Allocation
=================

Service organizations that need to handle a high number of tickets in a short time span and call centers that want to assign tickets automatically to staff members will both be excited about this feature add-on. New tickets are automatically assigned to agents with the smallest number of tickets to work on or to agents with suitable skills. Your service team will efficiently operate at full capacity and will be able to answer more tickets without feeling overburdened. This feature add-on turns **OTRS** into a call center software.

In the generic agent job configuration you can define the event that will trigger the ticket allocation. For example, the trigger could be the creation of a ticket, the reaching of a reminder time, or the closing of a ticket. Moreover, you can decide if only the ticket that triggered the event is allocated or if all relevant tickets are allocated to a specific agent.

You can also define which tickets are relevant. To avoid flooding your agents with tickets, you can restrict the number of allocated tickets per agent. Ticket ordering can also be configured with an additional *order module*. By default, it is the ticket creation time, but you can also choose queue priority or service times. Additionally, a maximum number of allocated tickets per queue can be defined.

Last but not least, you can also create competence groups in order to react more quickly to emergency tickets or to assign tickets to a team with special knowledge of tricky issues right from the start. By default the queue, priority, type, and group competences are active; however, you can also add SLA and service in the system configuration.

Benefits
   - Optimal capacity utilization of your service team by automatic allocation of tickets.
   - Simple handling of an increased number of tickets.

Target Groups
   - IT service
   - Sales
   - Facility management
   - Internal IT
   - And many more

Available in Service Package
   - GOLD

Package Name in OTRS Package Manager
   - OTRSTicketAllocation

.. note::

   Not compatible with the following feature add-on:

   - :doc:`advanced-generic-agent`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-allocation/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-allocation/admin
   ticket-allocation/agent
   ticket-allocation/external
