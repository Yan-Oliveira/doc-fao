Ticket Time Unit Dropdown
=========================

For service organizations that must meet strict service level agreements (SLAs), the documentation of time units is fundamental. For this purpose, the standard version of **OTRS** provides a field without any unit that can be filled in however you wish. However, the correct documentation of the working time with this field requires a company-wide understanding and knowledge of time and billing intervals. Unfortunately, and especially in global companies with several locations, this is not always the case. This can cause working times to be documented incorrectly and be a source of confusion for customers.

The problem can be solved by using this feature add-on. It makes it possible to set time units in a dropdown as e.g. minutes or hours.

It is possible to define the following values:

- Selectable values
- Displayed name of value (e.g. *hour* or *minute*)
- Set default value

These definitions allow you to take into account the individual time and billing charge needs of your company. For example, when a quarter of an hour has already started, it could be calculated as a 15-minute interval automatically.

Benefits
   - Reduction of error ratio when entering time units.
   - Unmistakable definition of intervals and default values reduces documentation time.

Available in Service Package
   SILVER

Target Groups
   - IT service management
   - Internal IT service
   - Customer service/support
   - Globally active companies

.. note::

   For using this feature add-on, it is necessary to activate the dropdown option via system configuration (e.g. ``Ticket::Frontend::UnitsAccountedTime###1-TimeUnit``).

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-time-unit-dropdown/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-time-unit-dropdown/admin
   ticket-time-unit-dropdown/agent
   ticket-time-unit-dropdown/external
