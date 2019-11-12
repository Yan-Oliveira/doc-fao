Ticket Zoom
===========

Use this screen to add tickets to a watch list or to remove tickets from a watch list. The *Ticket Zoom* screen is available, if you click on a ticket in any other screens.


Ticket Menu
-----------

After installation of the package, two new menu items will be added to the ticket menu.

Watchlists
   The ticket can be assigned to a watch list via this menu item. Additionally, the ticket can be removed from a watch list.

   .. figure:: images/ticket-zoom-watchlist.png
      :alt: Ticket Watchlists Screen

      Ticket Watchlists Screen

   Click on the *Add* link in the *Action* column to add the ticket to the selected watch list. The *Add* link will be changed to *Delete* and the ticket will be added in the background.

   Click on the *Delete* link in the *Action* column to remove the ticket from the selected watch list. The *Delete* link will be changed to *Add* and the ticket will be removed in the background.

   When you finish to edit the watch lists just close this window.

Watchlist Reminder
   Use this menu item to set a reminder for the ticket in the watch list. For this, the agent has to be subscribed to the ticket or it has to be assigned to one of his watch lists.

   .. note::

      This menu item is visible only, if the ticket is already added to a watch list.

   .. figure:: images/ticket-zoom-watchlist-reminder.png
      :alt: Ticket Watchlist Reminder Screen

      Ticket Watchlist Reminder Screen

   Reminder active
      Controls, whether the reminder is active or not.

   Reminder Time
      Set the date and time when the reminder should be displayed.

   Reminder for
      Select a watch list from the drop-down list.

   Note
      Add additional information to the reminder text.

   This information will also be shown within the watch list overview.

A watch list belongs to the agent who created it. The list can be moved to another agent in the :doc:`watchlist-management` screen. When moving a watch list to another agent, reminders will also be moved.

In this case, where the owner of the watch list is changed, the notification that is sent is different that the others. It can only be sent by the email notification method and it should not contain any ticket related OTRS smart tag (if so they will be removed before sending) as there is no ticket involved in the process that triggers the event.

The default *Watchlist move notification* is attached to the event ``WatchlistMoveNotification``. This and any other ticket notification attached to the same event should prevent the use of these ticket related OTRS smart tags.

Reminders will only be sent if the assigned agent at this time still has access to the watch list containing the ticket and/or still is subscribed to the ticket.

There can only be one active reminder per agent and ticket. Notifications are only being sent every ten minutes.
