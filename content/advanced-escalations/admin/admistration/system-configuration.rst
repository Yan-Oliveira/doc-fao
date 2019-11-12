System Configuration
====================


Visualization of Escalation Times in Ticket Overviews
-----------------------------------------------------

In the ticket overviews and also on ticket dashboard widgets, information regarding the escalation data is displayed in one column for each escalation type.

In addition to this, you have the possibility to specify which advanced escalations columns you want to use in ticket overviews and ticket dashboard widgets.

In the system configuration options the possible advanced escalations columns are predefined, but they are not active. If you want to use them, you have to change the value to 1 in setting ``AgentDashboard###AdvancedEscalationsDefaultColumns``.

Due to a technical reason there is only one system configuration option for the ticket dashboard widgets. So you are not able to define the advanced escalations columns for each ticket dashboard widget.

Advanced escalations columns are shown like this: Escalation type (Column), e.g. *First Response Time* (Escalation reached, yes/no). They are translatable.

For the user based settings the modal dialog for the configuration of views has been extended to offer a selection of available escalation types.

The traffic light colors for the escalation states:

- Green: No escalation times are reached or exceeds the limit.
- Yellow/Orange: The warning time was reached or exceeds the limit, but no escalation time is reached or exceed the limit yet.
- Red: Escalation time is reached or exceeds the limit.
- Brown: Escalation time is currently paused.


Possible Advanced Escalations Columns
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For each configured escalation type the following 22 advanced escalations columns are calculated and available. It is not necessary to activate the columns like you have to do e.g. for the agent dashboard. You will find a complete list with explanations below.

``EscalationDatetime``
   Timestamp of the escalation date.

``EscalationReached``
   Yes/no value whether escalation time is reached.

``EscalationTime``
   Seconds until the escalation type is breached.

``EscalationWorkingTime``
   Seconds until the escalation type is breached with working calendar (only if calendar is defined).

``EscalationRemainingTime``
   Seconds until the escalation type is breached if suspended/stopped (only set if given).

``EscalationRemainingWorkingTime``
   Seconds until the escalation type is breached if suspended/stopped with working calendar (only if calendar is defined and if given).

``NotifyDatetime``
   Timestamp of notify start (only set if given).

``NotifyTime``
   Seconds until the notify start (only if given).

``NotifyRemainingTime``
   Seconds remaining until notify start if suspended/stopped (only set if given).

``NotifyRemainingWorkingTime``
   Seconds remaining until notify start if suspended/stopped with working calendar (only if calendar is defined).

``SuspendLastTime``
   Total amount of seconds that the timer was suspended last time.

``SuspendLastWorkingTime``
   Total amount of seconds that the timer was suspended last time with working calendars (only if calendar is defined).

``SuspendTotalTime``
   Total amount of seconds that the timer was suspended.

``SuspendTotalWorkingTime``
   Total amount of seconds that the timer was suspended with working calendars (only if calendar is defined).

``RunningTotalTime``
   Total amount of seconds that the timer was running (excluding suspend times).

``RunningTotalWorkingTime``
   Total amount of seconds that the timer was running (excluding suspend times) with working calendars.

``RunningTotalVirtualTime``
   Total amount of seconds that the timer was running with ``BaseTime`` as start date (excluding suspend times).

``RunningTotalVirtualWorkingTime``
   Total amount of seconds that the timer was running with ``BaseTime`` as start date (excluding suspend times) with working calendars (only if calendar is defined).

``RunningLastTime``
   Total amount of seconds that the timer was running last time (excluding suspend times).

``RunningLastWorkingTime``
   Total amount of seconds that the timer was running last time (excluding suspend times) with working calendars.

``RunningLastVirtualTime``
   Total amount of seconds that the timer was running last time with ``BaseTime`` as start date (excluding suspend times).

``RunningLastVirtualWorkingTime``
   Total amount of seconds that the timer was running last time with ``BaseTime`` as start date (excluding suspend times) with working calendars (only if calendar is defined).
