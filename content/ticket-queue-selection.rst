Ticket Queue Selection
======================

This feature add-on makes it possible to automatically move a ticket to preferred queues on the basis of ticket and customer data when it is created. In the standard version of **OTRS**, some similar selection can be done by using several email addresses or moving tickets manually.

After installing the feature add-on, you can define in the system configuration on which data the queue selection should be executed. For example, it would be possible to define certain customer names, which causes their tickets to move into a special queue where the appropriate customer consultant can work on it immediately.

It would also be possible to define keywords, like *problem* or *computer*, for the ticket title so that those tickets are automatically routed to the first-level-support queue.

Benefits
   - Immediate handling of the ticket.
   - Automatic assignment in the correct queue according to individually definable keywords.
   - Saves time compared to a manual assignment.

Target Groups
   - External IT service
   - Call centers
   - Sales
   - Customer service
   - And many more

Available in Service Package
   - GOLD

Package Name in OTRS Package Manager
   - OTRSTicketQueueSelection

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-queue-selection/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-queue-selection/admin
   ticket-queue-selection/agent
   ticket-queue-selection/external
