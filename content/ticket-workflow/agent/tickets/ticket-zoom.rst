Ticket Zoom
===========

Use this screen to add workflows to tickets. The *Ticket Zoom* screen is available, if you click on a ticket in any other screens.


Ticket Menu
-----------

After installation of the package, a new menu item will be added to the ticket menu.

Workflow
   When the ticket is neither a master nor a task, then a selection of workflow templates is shown. When a template is selected and submitted, then the appropriate task tickets are generated. The generated task tickets are linked to the master ticket.

   .. figure:: images/ticket-zoom-workflow.png
      :alt: Ticket Workflow Screen

      Ticket Workflow Screen

   The task tickets are linked with *Task* link to their master ticket. The dependent task tickets are linked with *Depends On* link to the required ticket.

The deadline notice in the ticket workflow task is the solution time for the ticket. It is necessary to set an SLA escalation for this. If a defined service level agreement (SLA) is in danger of being breached, the system sends out an automatic warning message via email.
