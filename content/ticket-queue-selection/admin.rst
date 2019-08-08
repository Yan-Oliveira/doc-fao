Administrator Interface
=======================

This package has no administrator interface, but makes it possible to move tickets with specific ticket or customer user data into queues.

The package can be configured with the setting ``OTRSTicketQueueSelection::Configuration``. Key is the queue name and value is a semicolon-separated list of ticket and/or customer user settings and their expected value as regular expression. The fields available for tickets and customer users have to match those available in OTRS.


Example Usage
-------------

This example shows how to configure a set of rules to move a ticket from any selected queue to a defined destination queue based on a ticket attribute, on ticket creation time.

To configure rules for newly created tickets with title ``Test`` to be moved to queue *Junk*:

1. Go to *System Configuration* screen.
2. Select *OTRSTicketQueueSelection* in the *Navigation* widget.
3. Navigate to *Core → Ticket* in the navigation tree.
4. Select ``OTRSTicketQueueSelection::Configuration`` setting for editing.
5. Enter *Junk* for key and ``Ticket::Title='^Test$'`` for content.
6. Create a ticket with title *Test* and check that tickets are moved according to your configuration.

As seen in this example there is only one rule to that the ticket must match to be moved to the queue *Junk*. If more rules are needed, they can be added to the same content field with a ``;`` character as a separator, like:

.. code-block:: none

   Ticket::Title='^Test$';CustomerUser::UserFirstname='^John$';CustomerUser::UserLastname='^Doe$'

Each rule is taken by the system as an AND condition, so for these new rules the ticket will need to match the title condition **and** the customer condition in order to be moved to the *Junk* queue.

The rules can be based on ticket attributes ``Ticket::<Attribute>`` or on customer user attributes ``CustomerUser::<Attribute>``.
