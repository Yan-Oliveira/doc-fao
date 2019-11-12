Ticket Notifications
====================

This package adds some new features to the ticket notification methods.


Notification Smart Tags
-----------------------

The notification smart tags only work in notifications related to the escalation. It does not work for ``TicketCreate`` but it will work for *Escalation: First Response* (``NotifyBefore``). The following smart tags with information about each escalation are available:

``<OTRS_TICKET_CustomEscalation_EscalationTime>``
   If the escalation is running, then this tag will return the escalation date-time when the escalation type will escalate (e.g. *2019-01-01 10:00:00*).

``<OTRS_TICKET_CustomEscalation_NotifyTime>``
   If the escalation is running, then this tag will return the escalation notify date-time of the escalation type (e.g. *2019-01-01 10:00:00*).

``<OTRS_TICKET_CustomEscalation_EscalationTimeIn>``
   If the escalation is running, then this tag will return the difference the current time and escalation time in format *3h 30m*.

``<OTRS_TICKET_CustomEscalation_TypeName>``
   This tag will return the name of the escalation type (e.g. *solution time*).


Configure Event Based Notifications
-----------------------------------

Use this steps to configure event based notifications for users of escalated tickets:

1. Make sure OTRS daemon is running.

   .. code-block:: bash

      shell> /opt/otrs/bin/otrs.Daemon.pl status

2. Go to the system configuration and enable ``Daemon::SchedulerCronTaskManager::Task###TriggerEscalationStartEvents`` setting. It will allow the generic agent to run the module in charge to start the advanced escalations events.
3. Go to the administrator interface and open the *Ticket Notifications* module to configure the notifications.
4. Configure the notification and change text by using the new notification smart tags provided by this package and described above.


Escalation Events
-----------------

The following escalation events are available:

Escalation: [EscalationName] (Start) (EscalationStart_[EscalationTypeID])
   This event will be executed if the escalation has been started.

Escalation: [EscalationName] (NotifyBefore) (EscalationNotifyBefore_[EscalationTypeID])
   This event will be executed if the time reached where the agent gets notified for the escalation.

   This event will be only executed correctly if the escalation bundle configuration per escalation type is correctly configured, ``TriggerEscalationStartEvent`` is enabled and the daemon is running.

Escalation: [EscalationName] (Breached) (EscalationBreached_[EscalationTypeID])
   This event will be executed if the escalation time has been reached.

   This event will be only executed correctly if the escalation bundle configuration per escalation type is correctly configured, ``TriggerEscalationStartEvent`` is enabled and the daemon is running.

Escalation: [EscalationName] (Restart) (EscalationRestart_[EscalationTypeID])
   This event will be executed if the escalation has been restarted.

Escalation: [EscalationName] (Suspend) (EscalationSuspend_[EscalationTypeID])
   This event will be executed if the escalation has been suspended.

Escalation: [EscalationName] (ResumeSuspend) (EscalationResumeSuspend_[EscalationTypeID])
   This event will be executed if the escalation has been resumed from a suspend state.

Escalation: [EscalationName] (ResumeStop) (EscalationResumeStop_[EscalationTypeID])
   This event will be executed if the escalation has been resumed from a stop state.

Escalation: [EscalationName] (Stop) (EscalationStop_[EscalationTypeID])
   This event will be executed if the escalation has been stopped.
