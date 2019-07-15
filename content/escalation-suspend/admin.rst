Administrator Interface
=======================

This package has no administrator interface, but includes the functionality to stop or suspend escalations. If a ticket is assigned to one of several configurable states, the escalation is stopped (disabled).


Configuration
-------------

To configure the states where the escalation is stopped:

1. Go to *System Configuration* screen.
2. Select *OTRSEscalationSuspend* in the *Navigation* widget.
3. Navigate to *Core → Ticket* in the navigation tree.
4. Add new entries to setting ``EscalationSuspendStates``.
5. If suspend escalation is needed for already escalated tickets, enable the ``SuspendEscalatedTickets`` setting.

.. note::

   Invalid states will not be considered as suspend states for the calculation.

When changing the state of the ticket to normal, the escalation will continue. In this case, it starts with the date when the status was changed, displaying the remaining time.

Therefore, the entire period when the ticket was not on a normal state is not counted for solution time. However, only periods when the ticket was in suspended states before first response is not counted for first response time.


Console Command
---------------

This package contains a console command ``Maint::Ticket::RebuildEscalationIndexOnline`` handled by the OTRS daemon used for resetting the escalation times to the point it was suspended. This script is the one in charge to reset the escalation time to the point it was suspended.

To check if the script is running, execute the following command and find the ``RebuildEscalationIndexOnline`` task in the *Recurrent cron tasks* section.

.. code-block:: bash

   otrs> /opt/otrs/bin/otrs.Console.pl Maint::Daemon::Summary
