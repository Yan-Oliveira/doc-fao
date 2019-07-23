Administrator Interface
=======================

This package has no administrator interface.


Configuration
-------------

This package provides the responsible feature for queues and handles the ``TicketQueueUpdate`` and ``TicketCreate`` events to set the responsible based on the name of the queue.

To activate the queue responsible feature:

1. Go to *System Configuration* screen.
2. Make sure that ``Ticket::Responsible`` setting is enabled in order to be able to check it on *Ticket Zoom* screen.
3. Select *OTRSQueueResponsible* in the *Navigation* widget.
4. Navigate to *Core → Ticket → OTRSQueueResponsible* in the navigation tree.
5. Set values for ``Ticket::QueueResponsible`` setting. Key is the queue name as stored in database (e.g. *Junk*, *Misc* or *Raw*) and content is the login name of the user to be defined as responsible.
6. Modify ``Ticket::QueueResponsibleOnNewTicket`` setting if needed. If the value is set to *Yes* then also the responsible of new tickets is set per queue and the new tickets are processed like the change of queue event.
