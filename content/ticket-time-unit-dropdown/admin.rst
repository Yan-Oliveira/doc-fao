Administrator Interface
=======================

This package has no administrator interface.

.. note::

   For using this feature add-on, it is necessary to activate the drop-down lists via system configuration.

To activate the drop-down lists:

1. Go to *System Configuration* screen.
2. Select *OTRSTicketTimeUnitDropdown* in the *Navigation* widget.
3. Navigate to *Frontend → Agent* in the navigation tree.
4. Activate the settings for the first, second and third drop-down lists, if needed.

To use a custom time unit:

1. Change the value of the ``Name`` key to the custom time unit name.
2. Add possible values to ``Settings`` key, where the first entry is the time in seconds and the second entry is the label to be displayed in the drop-down list.

It is possible to set default value for each setting using the ``Default`` key and any valid value from the **second** entry of the ``Settings`` key. This default value will be pre-selected in the drop-down list on the ticket screens.

Now open the *New Phone Ticket* screen or any other screen using time units on the :doc:`agent` and use the drop-down lists for hours and minutes to set the time units instead of an input field.
