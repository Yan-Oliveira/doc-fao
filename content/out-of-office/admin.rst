Administrator Interface
=======================

This package has no administrator interface.


Configuration
-------------

This package includes the functionality to create articles for a ticket with the ``X-OTRS-Header`` out of office without changing the status of the ticket. The module also prevents the locking of the ticket if mentioned header is present.

To configure this feature:

1. Go to *System Configuration* screen.
2. Select *OTRSOutOfOffice* in the *Navigation* widget.
3. Navigate to *Core → Email → PostMaster* in the navigation tree.
4. Activate the setting ``OTRSOutOfOffice-Header``.
5. Select *OTRS* in the *Navigation* widget.
6. Navigate to *Core → Email → PostMaster* in the navigation tree.
7. Add the ``X-OTRS-OutOfOffice`` header to the end of the list in setting ``PostmasterX-Header``.
8. Deploy the settings.
9. Go to the *PostMaster Filters* screen of the administrator interface and add a new postmaster filter.
10. Set email header ``X-OTRS-Header`` with value *1* of an incoming email based on whatever regular expression or text you want to use (e.g. Subject: *[Out of Office]*).
11. Click on the *Save* button.
