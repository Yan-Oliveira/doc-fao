Ticket Notifications
====================

After installation of the package a new ticket notification will be added to the system.


New Ticket Notification
-----------------------

Missing DTT assignment for CustomerGroup
   If no template is assigned to a group and the notification is enabled, such notification can be customized by adding different recipients or updating the notification body.

To configure the optional settings for the notification:

1. Go to *System Configuration* screen.
2. Select *OTRSTicketForms* in the *Navigation* widget.
3. Navigate to *Core → DynamicTicketTemplate* in the navigation tree.
4. Enable ``Ticket::DynamicTicketTemplate::CustomerGroup::Notify`` setting to send a notification if a customer does not use a template to create a ticket.
5. Add agent login names to ``Ticket::DynamicTicketTemplate::CustomerGroup::NotifyAgents`` setting. The agent list in this setting will receive the notification when a user creates a ticket without using a template.
