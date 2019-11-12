Statistics
==========

Advanced Escalations Data in Statistics
---------------------------------------

By installing the advanced escalations package, you have the possibility to use the new statistics object modules:

``TicketAccountedTimeEscalation``
   A new matrix statistic which only contains tickets with accounted time. It is a copy of the ``TicketAccountedTime`` statistic out of the **OTRS** framework, but you are able to show advanced escalations data and to filter the data by ticket attributes as well as by advanced escalations.

``TicketEscalation``
   A new matrix statistic which shows configured columns on X- and Y-axis. It is a copy of the ticket matrix statistic out of the **OTRS** framework, but you are able to show advanced escalations data and to filter the data by ticket attributes as well as by advanced escalations.

``TicketListEscalation``
   A new statistic which shows configured columns (advanced escalations data, too) on X-axis. You can specify a column which is used in an order by clause on Y-axis. You are able to filter the data by ticket attributes as well as by advanced escalations columns.

``TicketSolutionResponseTimeEscalation``
   A new matrix statistic which only contains closed tickets. It is a copy of the default ``TicketSolutionResponseTimeEscalation`` statistic out of the **OTRS** framework, but you able to select advanced escalations columns in the *Elevation by* field. As already mentioned in the other new statistics, you can filter the data by advanced escalations columns.


Filtering
---------

In general, there are the following types of advanced escalations columns:

Yes/no columns
   For this type of columns (e.g. ``EscalationReached``), a drop-down field is displayed to select the wanted values. This type is used on X- and Y-axis and as filter.

Datetime columns
   For this type of columns (e.g. ``EscalationDatetime``), a complex field with the selection of an absolute or a relative time range is shown. This type is used on X- and Y-axis and as filter.

   .. note::

      Please note that in the ``TicketListEscalation`` statistic these columns are not available on the Y-axis.

Time columns (seconds)
   For this type of columns (e.g. ``RunningTotalTime``), a normal input field is shown. You can use these columns only as filter as *greater or equal* and/or *smaller or equal*.

   Entered values are treated as minutes. For example if you enter 30 it is converted to 30 × 60 = 1800 seconds automatically.
