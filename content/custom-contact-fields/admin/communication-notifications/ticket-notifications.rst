Ticket Notifications
====================

Use this screen to activate sending emails to custom contact field customers. The ticket notification management screen is available in the *Ticket Notifications* module of the *Communication & Notifications* group.


Sending Articles Created in the External Interface as Emails
------------------------------------------------------------

To activate sending emails to custom contact field customer users:

1. Click on the *Add Notification* button in the left sidebar.
2. Fill in the required fields.
3. In the *Add Notification* section, choose a name and set it in the *Name* field.
4. In the *Events* section, select *ArticleCreate*.
5. In the *Article Filter* section:

   - Set agent and customer in the *Article Sender Type* field.
   - Set *Visible to customer* in the *Customer visibility* field.
   - Select *Email* in the *Communication channel* field.
   - Switch *Include attachments to notification* to *Yes*.

6. In the *Recipients* section set a dynamic contact field in the *Send to* field.
7. In the *Notification Methods* section:

   - Make sure, that the *Email* method is enabled.

     .. note::

        Joined notifications are only sent by *Email*.

   - Select the checkbox in the *Article visible for customer* field.

8. In the *Notification Text* section:

   - If you want the contacts of the custom contact field to get the title of the article as mail subject add ``<OTRS_CUSTOMER_SUBJECT>`` into the *Subject* field.
   - If you want to send the article body as mail body add ``<OTRS_CUSTOMER_BODY>`` into the *Text* field.

9. Click on the *Save* button.
