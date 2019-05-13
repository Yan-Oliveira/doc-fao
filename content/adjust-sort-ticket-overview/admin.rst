Administrator Interface
=======================

This package has no administrator interface.


System Configuration
--------------------

Width of columns
   The width of the columns in the small ticket overviews are configurable.

   To configure the width of columns:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Agent → TicketOverview* in the navigation tree.
   4. Add new entries to setting ``Frontend::Agent::TicketOverview::OTRSAdjustSortTicketOverviewFixedWidth``. Examples:

      - ``Queue`` → *10%*
      - ``State`` → *8%*
      - ``Age`` → *40px*
      - ``DynamicField_DateofReceipt`` → *3cm*

      Configurable fields are: ``TicketNumber``, ``Age``, ``EscalationTime``, ``Title``, ``State``, ``Queue``, ``Lock``, ``Owner``, ``CustomerID``, ``DynamicField_*``.

   This feature is activated by default after installation of the package.

Word length of title column
   The word length of the title column in the ticket overview widgets is configurable.

   To configure the word length:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Agent → TicketOverview* in the navigation tree.
   4. Set the word length in setting ``Frontend::Agent::TicketOverview::OTRSAdjustSortTicketOverviewTitleLength``.

Drag and drop table column widths
   The width of the columns in the ticket overview widgets and the dashboards are configurable via drag and drop on a per-user-base.

   To activate this feature:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Agent → TicketOverview* in the navigation tree.
   4. Enable setting ``Frontend::Agent::TicketOverview::OTRSAdjustSortTicketOverviewUseDragAndDrop``.

   After activation it is possible to drag and drop the different table columns with the mouse to set the widths of every single column. Those settings are saved and restored for every single user in the user preferences.

Queue and service display names
   Depending on a system configuration setting, queue and service names can be displayed with complete paths, only with first letter of parents followed by ``::`` and their names, or just by their names in the ticket overview widgets.

   To modify the display names:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Agent → TicketOverview* in the navigation tree.
   4. Set the display names in setting ``Frontend::Agent::TicketOverview::ProcessQueueServiceFields``.

   .. warning::

      There is a potential risk that if ticket title (if double colons are contained) is also displayed in shortened manner because internally the double colons are used for creating the correct shortened path for queue and service name.

Ticket number always visible
   This setting prevents the users to hide the ticket number column by drag and drop.

   To activate this feature:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Agent → TicketOverview* in the navigation tree.
   4. Enable setting ``Frontend::Agent::TicketOverview::TicketNumberAlwaysVisible``.

Affected screens
   The features can be enabled or disabled in each ticket overview screens.

   To modify the affected screens:

   1. Go to *System Configuration* screen.
   2. Select *OTRSAdjustSortTicketOverview* in the *Navigation* widget.
   3. Navigate to *Frontend → Base → OutputFilter* in the navigation tree.
   4. Add or remove screen names in the ``Template`` key of each setting.
