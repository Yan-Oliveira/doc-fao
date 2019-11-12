Overview
========

This feature makes it possible to *write protect* a change or a work order, which means that certain actions which are normally visible in the *Change Zoom* or the *Work Order Zoom* screens, are no longer visible and usable, once a change or a work order is in a defined state.

.. seealso::

   The list of states and forbidden actions can be individually configured for changes and work orders in the following system configuration settings:

   - ``ITSMChange::WriteProtection###Actions``
   - ``ITSMChange::WriteProtection###ChangeStates``
   - ``ITSMWorkOrder::WriteProtection###Actions``
   - ``ITSMWorkOrder::WriteProtection###WorkOrderStates``

If a change is write protected, all included work orders will be write protected as well. This feature can be disabled in the system configuration.

If you want to hide some work order or change actions from the zoom screen if the work order or change has reached a certain state, you need to define the states and actions in the system configurations.

Then look at the the zoom screen of a work order or a change which has not yet reached one of the defined states and notice that still all actions are visible in the zoom screen.

Now change the state of the work order or change to a state that was defined in the write protection settings, and notice that the actions listed in the system configuration settings are no longer visible. These actions can also not be called directly, if you would have bookmarked the link to that action.
