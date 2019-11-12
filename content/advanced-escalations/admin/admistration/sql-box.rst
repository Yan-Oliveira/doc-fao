SQL Box
=======

Escalation history is available for SQL reporting. The following chapters explain the structure of the database tables.


``escalation_history`` Table
----------------------------

All escalation events will create new entries in the ``escalation_history`` table, which is the basis to calculate statistics about the completed escalation cycles.

To activate the additional reporting of the escalation events, you need to enable the following system configuration option:

- ``Ticket::EventModulePost###EscalationHistory`` (group: ``OTRSAdvancedEscalations``, navigation: *Core → Event → EscalationHistory*).

Make sure OTRS daemon is running.

.. code-block:: bash

   shell> /opt/otrs/bin/otrs.Daemon.pl status

This event module will track the following escalation events:

- ``EscalationStart``
- ``EscalationStop``
- ``EscalationSuspend``
- ``EscalationRestart``
- ``EscalationResumeSuspend``
- ``EscalationResumeStop``

The ``escalation_history`` table has the following columns:

``id``
   This column contains the ID of the escalation history (auto increment).

``event_trigger``
   This column contains the event of the escalation (e.g. ``EscalationStart``).

``object_id``
   This column contains object ID of the escalation (e.g. the ticket ID).

``object_type``
   This column contains object type of the escalation (e.g. ``Ticket``).

``object_history_id``
   This column contains the related ID of the ``ticket_history`` table to the escalation event.

``escalation_type_id``
   This column contains the escalation type ID of the escalation.

``escalation_reached``
   This column contains whether the escalation time is already reached (possible values: 0/1).

``escalation_datetime``
   This column contains the timestamp of the escalation date.

``escalation_time``
   This column contains the rest of time (seconds) until the ticket will escalate.

``escalation_wt``
   This column contains the rest of time (seconds) until the ticket will escalate (calculated with working calendars).

``notify_datetime``
   This column contains the date-time timestamp of the notify start.

``notify_time``
   This column contains the seconds until the notify start.

``escalation_remaining_time``
   This column contains the rest of time until the ticket will escalate after a suspend of an escalation type.

   .. note::

      This column is only filled on suspend state.

``escalation_remaining_wt``
   This column contains the rest of time until the ticket will escalate after a suspend of an escalation type (calculated with working calendars).

   .. note::

      This column is only filled on suspend state.

``notify_remaining_time``
   This column contains the seconds until the notify start after a suspend of an escalation type.

   .. note::

      This column is only filled on suspend state.

``notify_remaining_wt``
   This column contains the seconds until the notify start after a suspend of an escalation type (calculated with working calendars).

   .. note::

      This column is only filled on suspend state.

``running_total_time``
   This column contains the total amount of seconds the timer was running based on the ``Timer(Start|Restart|Suspend|Resume|Stop)`` events.

``running_total_wt``
   This column contains the total amount of seconds the timer was running based on the ``Timer(Start|Restart|Suspend|Resume|Stop)`` events (calculated with working calendars).

``running_total_virtual_time``
   This column contains the total amount of seconds the timer was running based history entries.

``running_total_virtual_wt``
   This column contains the total amount of seconds the timer was running based history entries (calculated with working calendars).

``suspend_total_time``
   This column contains the total amount of suspended seconds of the escalation type based on the ``Timer(Start|Restart|Suspend|Resume|Stop)`` events.

``suspend_total_wt``
   This column contains the total amount of suspended seconds of the escalation type based on the ``Timer(Start|Restart|Suspend|Resume|Stop)`` events (calculated with working calendars).

``running_last_time``
   This column contains the seconds between a start or resuming event and a stop or suspending event (e.g. ``EscalationStart`` to ``EscalationSuspend`` or ``EscalationResume`` to ``EscalationStop``).

``running_last_wt``
   This column contains the seconds between a start or resuming event and a stop or suspending event (e.g. ``EscalationStart`` to ``EscalationSuspend`` or ``EscalationResume`` to ``EscalationStop``) (calculated with working calendars).

``running_last_virtual_time``
   This column contains the seconds between a start or resuming event and a stop or suspending event (e.g. ``EscalationStart`` to ``EscalationSuspend`` or ``EscalationResume`` to ``EscalationStop``) based on the history entries of the ticket.

``running_last_virtual_wt``
   This column contains the seconds between a start or resuming event and a stop or suspending event (e.g. ``EscalationStart`` to ``EscalationSuspend`` or ``EscalationResume`` to ``EscalationStop``) based on the history entries of the ticket (calculated with working calendars).

``suspend_last_time``
   This column contains the amount of seconds the ticket escalation was suspended last time based on the history entries of the ticket.

``suspend_last_wt``
   This column contains the amount of seconds the ticket escalation was suspended last time based on the history entries of the ticket (calculated with working calendars).

``create_time``
   This column contains create time of the escalation history entry.

``create_by``
   This column contains ID of the user who triggered the history data set.

``change_time``
   This column contains date and time when the escalation history data set was changed.

``change_by``
   This column contains ID of the user who triggered the data set change.


``escalation_history_data`` Table
---------------------------------

All escalation events will create new entries in the ``escalation_history`` table. For each escalation event it is possible to save ticket and dynamic field data in a separate data table. Make sure that ``TriggerEscalationStartEvents`` is enabled. The attributes which will be saved can be configured in the following system configuration options:

- ``EscalationHistoryData###Ticket`` (group: ``OTRSAdvancedEscalations``, navigation: *Core → EscalationHistoryData*).

   Example configuration: *Queue → 1*

- ``EscalationHistoryData###DynamicField`` (group: ``OTRSAdvancedEscalations``, navigation: *Core → EscalationHistoryData*).

   Example configuration: *DynamicField_Test → 1*

To activate the additional reporting of the escalation events, you need to enable the following system configuration option:

- ``Ticket::EventModulePost###EscalationHistory`` (group: ``OTRSAdvancedEscalations``, navigation: *Core → Event → EscalationHistory*).

Make sure OTRS daemon is running.

.. code-block:: bash

   shell> /opt/otrs/bin/otrs.Daemon.pl status

The data of the ticket and dynamic fields will be saved in a separate table ``escalation_history_data`` with the following columns:

``id``
   This column contains the ID of the escalation history (auto increment).

``escalation_history_id``
   This column contains ID of the related ``escalation_history`` entry.

``field_key``
   This column contains key of the related data (e.g. *DynamicField_Test* or *Queue*).

``field_value``
   This column contains value of the related data (e.g. a dynamic field value or the values of ticket attributes).

``create_time``
   This column contains create time of the escalation history data entry.

``create_by``
   This column contains ID of the user who triggered the escalation history data set.

``change_time``
   This column contains date and time when the escalation history data set was changed.

``change_by``
   This column contains ID of the user who triggered the data set change.
