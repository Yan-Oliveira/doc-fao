Agent Interface
===============

This package has no agent interface.


Restriction for Linking
-----------------------

This feature restricts the link interface for the agent when linking a ticket with a configuration item. Only configuration items and the tickets which belong to the same company of the customer user can be selected. The feature can be disabled in the system configuration via the setting ``ITSMConfigItem::RestrictAgentLinking``.


Postmaster Filter
-----------------

There is a postmaster filter added to search incoming emails for a configuration item identifier (usually the configuration item number) and links all found configuration items with the new ticket that was created from this email. The email body and the subject are searched, all found configuration item numbers will be linked with the ticket. This feature is deactivated by default and needs to be enabled in the system configuration via the setting ``PostMaster::PostFilterModule###100-ITSMConfigItemLink``.
