Ticket Watchlist
================

This feature add-on allows you to manage several watchlists. A ticket agent defines watchlists and assigns tickets to a watchlist. Within the watchlist view, the agent gets an overview of all of his watchlists and can administer them.

The feature add-on has the following features:

Define notification events for each watchlist
   The agent is able to administer the following events which trigger an email notification to himself:

      - new article
      - change of customer
      - change of owner
      - change of queue
      - change of ticket status to a defined status

   This email notification is independent of the notification preferences of the current owner of the ticket – unlike the standard subscribe/watchlist feature add-on of **OTRS**.

Assign a watchlist to another agent
   A watchlist can be handed over to another agent. The list will disappear in the overview of the former owner and appear in the overview of the new owner. This feature is typically used to hand the list over to another agent when the original agent goes on vacation.

Assign a deputy
   One or more deputy agents can be assigned to a watchlist. A deputy then sees the new watchlist in his overview, and he is allowed to add or remove tickets to or from this watchlist. This feature is typically used to share a watchlist with colleagues to work on a ticket in a team.

Export to CSV
   The list can be exported to a CSV file, e. g. to process it in Excel.

Benefits
   - Get a quick and easy overview about all relevant tickets.
   - Administration of several watchlists saves time.
   - Export function enables the processing in Excel sheets.

Target Groups
   - IT service management
   - Service providers
   - Call centers
   - Service manager

Available in Service Package
   - SILVER

Package Name in OTRS Package Manager
   - OTRSTicketWatchlist

.. note::

   Not compatible with the following feature add-on:

   - :doc:`advanced-escalations`

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ticket-watchlist/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ticket-watchlist/admin
   ticket-watchlist/agent
   ticket-watchlist/external
