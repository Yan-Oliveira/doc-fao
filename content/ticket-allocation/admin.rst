Administrator Interface
=======================

The ticket allocation is the core feature of this package. It will automatically set an owner and a configurable lock for tickets. The events that trigger an allocation check can be defined in
the *Events* widget of the :doc:`admin/processes-automation/generic-agent` job management screen. Each event can be configured to allocate only the triggering ticket or all relevant tickets. Which tickets are relevant for ticket allocation can be defined by setting the ticket filters in the generic agent job.

The possible owners of a ticket have to be in the configured group of the ticket queue. Agents can be excluded from the allocation by being member in one of the configured blacklist groups. The allocation can be influenced by the competence feature (if enabled).

The competences will get summed for each agent. The group-competences will be mapped to the queue group of the ticket, and all other competences to its corresponding ticket attribute (queue,
priority etc.). If all/some agents have the same competence score or the competences feature is disabled, the agent with the least amount of tickets will be set as the new ticket owner. The competences can be set for each :doc:`admin/users-groups-roles/agents` individually.

It is possible to define a maximum number of tickets per agent via the system configuration to prevent flooding the agent with tickets. If the configured value is reached for an agent no
new ticket will get allocated to her/him. It is possible to loose this rule for tickets that get manually allocated to an agent via the system configuration, too.

By default only on-line agents will get tickets allocated. This behavior can also be changed by a system configuration setting.

.. toctree::
   :maxdepth: 3
   :caption: Contents

   admin/processes-automation
   admin/users-groups-roles
