Ticket Workflow
===============

The feature add-on allows one to easily define business workflow templates for common tasks. Workflow *task* tickets can be dependent on any other task in that workflow, giving a high level of control over the order in which tasks are completed. A task that is dependent on preceding tasks will not appear in the queue until the preceding tasks are closed.

Each task ticket within a workflow can be predefined using these fields:

- Queue
- Subject
- Body
- Owner
- Priority
- Attachments

Individual tasks can be made dependent on another corresponding task within a workflow. This dependence means that tickets will only be shown in a queue when the dependent preceding ticket has changed to the status *closed*.

An agent can start a workflow through an existing ticket. The content of the original ticket will then be copied to all task tickets. All agents will have a quick overview of their tasks in their personal dashboard widgets.

Distinctive criteria:

- No further workflows can be started within an existing workflow.
- A task can be dependent on another task within a workflow.
- Workflows can only be started in the agent interface.

Benefits
   - Enables the improvement of handling processes.
   - Relieves agents.
   - Simplifies data collection.
   - Reduces error sources.

Target Groups
   - IT service management
   - Human resources
   - Finance
   - Internal IT

Available in Service Package
   - SILVER

Package Name in OTRS Package Manager
   - OTRSTicketWorkflow

.. note::

   This feature add-on is also available for the OTRS::ITSM module.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-workflow/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-workflow/admin
   ticket-workflow/agent
   ticket-workflow/external
