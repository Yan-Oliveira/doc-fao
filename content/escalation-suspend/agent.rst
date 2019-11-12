Agent Interface
===============

This package has no dedicated agent interface.

.. note::

   For this example escalations should be configured for at least one queue.

Example usage:

1. Go to one of the new ticket screens, and create a new ticket for one of the queues configured with escalation (for this example *Escalation - first response time* is OK).
2. Open the *Ticket Zoom* screen for the newly created ticket. Notice that the escalation is running.
3. Once the escalation is running, change the ticket state to one that has been configured in ``EscalationSuspendStates`` setting.
4. Go back to the *Ticket Zoom* screen for the suspended escalation ticket and verify that the escalation is not running.
5. Change the ticket state to one different from those configured on ``EscalationSuspendStates`` setting. The escalation continues.

On ticket menu will be located a new option for *Escalation view - Without Suspend State*. Open this view and check the ticket without a suspend state.
