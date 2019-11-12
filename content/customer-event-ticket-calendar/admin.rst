Administrator Interface
=======================

After installation of the package the available configuration settings can be found in the system configuration. This package has no administrator interface.


System Configuration Settings
-----------------------------

The *Customer Event Ticket Calendar* widget displays tickets in a calendar, but this widget does not work out-of-the-box.

To display the tickets in this calendar, the following settings need to be set by an **admin user**:

1. Create the following dynamic fields:

   +--------+-------------+-------------------------------------+---------------------+
   | Object | Type        | Name                                | Label               |
   +========+=============+=====================================+=====================+
   | Ticket | Date / Time | ``CustomerTicketCalendarStartTime`` | Calendar Start Time |
   +--------+-------------+-------------------------------------+---------------------+
   | Ticket | Date / Time | ``CustomerTicketCalendarEndTime``   | Calendar End Time   |
   +--------+-------------+-------------------------------------+---------------------+

2. Navigate to *Frontend → Agent → View* and select a view to add the dynamic field to.

   For example add these dynamic fields to *New Phone Ticket* screen and *New Email Ticket* screen to set the dates at ticket creation time, or to *Ticket Free Fields* screen to set the dates for existing ticket in the *Miscellaneous → Free Fields* menu item of the *Ticket Zoom* screen.

   - ``Ticket::Frontend::AgentTicketPhone###DynamicField``

      - ``CustomerTicketCreateStartTime`` → *1 – Enabled*
      - ``CustomerTicketCreateEndTime`` → *1 – Enabled*

   - ``Ticket::Frontend::AgentTicketEmail###DynamicField``

      - ``CustomerTicketCreateStartTime`` → *1 – Enabled*
      - ``CustomerTicketCreateEndTime`` → *1 – Enabled*

   - ``Ticket::Frontend::AgentTicketFreeText###DynamicField``

      - ``CustomerTicketCreateStartTime`` → *1 – Enabled*
      - ``CustomerTicketCreateEndTime`` → *1 – Enabled*

3. Add more queues to ``CustomerTicketCalendar###Queues`` setting (default is *Raw* queue only).

If the dynamic fields contain values for the tickets, the tickets are displayed in the widget.
