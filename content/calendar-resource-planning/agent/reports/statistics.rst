Statistics
==========

After installation of the package you can set up new statistics using the ``AppointmentList`` statistic back end to create statistics about the stored appointments in your **OTRS** system. It is a regular statistic (e.g. like the ``TicketList`` statistic), which means you can configure the X-axis and Y-axis to your needs. A lot of the appointment attributes are even available as restrictions.

Some of the selectable attributes are calculated on-the-fly:

- Age
- Days
- Hours

The filter *Period* could be used to combine start and end time of an appointment with the OR operator instead of AND operator. For example the filter *Start Time* with a relative time period for the current one month will not show appointments starting one month before but ends in the current month. To see such appointments, you have to use the *Period* filter. Appointments which are overlapping are split.

For each linked ticket one row is added to the statistic output. For example an appointment is linked with two tickets, the appointment is shown twice.

.. note::

   Please be careful if you are using teams and resources to filter the appointments. Unfortunately it is not possible to filter for teams and resources on database level, meaning the time which is needed to create a statistic could be higher than usual.
