Administrator Interface
=======================

This package has no administrator interface. It provides performance optimizations for the ticket search for some heavily used systems.

When using the ticket search in agent or external interface, historical values will be gathered from the database for select-type dynamic fields (e.g. drop-down and multiselect). On systems with a large number of tickets and/or dynamic fields, looking through potentially millions of entries can take more time than desirable which leads to a noticeable delay until the form has opened.

The result is cached but as dynamic fields change constantly on heavily used systems, caches are outdated quite frequently and the database has to be queried again. This package keeps track of used values and their number of occurrence for all relevant dynamic fields and uses this data to present a quick response when historical values are requested.

On package installation the current state for all dynamic fields will be retrieved and afterwards it is automatically being updated. However, synchronization can be force triggered by
a new console command ``Maint::Ticket::DynamicFieldSearchBoosterSync``.

The search booster is initialized on package installation (via a daemon task). It might take a while for this task to complete. Until that time historical values retrieved in the search form may be incorrect.

The search booster is in effect automatically when the ticket search form is opened and should deliver the same results as before.
