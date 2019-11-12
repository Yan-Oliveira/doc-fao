Advanced Escalations
====================

This feature add-on makes your escalation management more flexible and adjusts it according to your customers or to different service level agreements. Escalation types defined in **OTRS**, such as *First Response Time*, *Update Time*, and *Solution Time*, can be enhanced by creating new types and defining your own names and properties.

The *Ticket Escalation Types* option in the administrator interface enables you to define when escalations should:

- start,
- stop,
- be suspended,
- be resumed
- and be restarted.

Ticket attributes, like its status or certain events like creating or answering a ticket, can be used as a trigger. For example, an escalation can start when a ticket is created, but the escalation can stop when the ticket is answered by the agent. If the status of a ticket is changed to *Pending Reminder*, the escalation is suspended, but if the status is changed back to *Open*, the escalation resumes. An up-to-date display of the escalation time left makes accurate service time management possible.

In the ticket view, the new widget *Escalation Information* appears. This shows through the use of different colors and numerical values whether or not:

- the escalation time is still within the original timeframe (green),
- the escalation time will run out soon (yellow),
- the escalation is paused (brown),
- the escalation time has been reached, i.e. the ticket has escalated (red) or
- escalation has been suspended or the ticket has been worked on during escalation (the window is no longer visible).

The *Ticket Escalation Type Bundle* option enables you to assign newly created escalation types to different customers or service level agreements.

The following scenarios can now be handled more flexibly with *Advanced Escalations*:

- A customer requests a rework of a solution – the escalation must be adjusted.
- To present a solution, more information is required from the customer – the escalation must be suspended.
- A service technician can’t get into the building or has no free access to the machine that needs to be fixed – the escalation must be suspended
- and many more!

Benefits
   - Even more flexible escalation management – individually adoptable to customer or SLA.
   - More precise service time management by detailed indication of remaining time.

Available in Service Package
   PLATINUM

Target Groups
   - Customer service organizations having many partners or suppliers
   - External IT service providers
   - Call centers
   - Sales departments and sales companies
   - Advertising or communications agencies

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`escalation-suspend`
   - :doc:`ticket-watchlist`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-advanced-escalations/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   advanced-escalations/admin
   advanced-escalations/agent
   advanced-escalations/external
