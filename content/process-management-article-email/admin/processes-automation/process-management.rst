Process Management
==================

This feature adds the ability to add email addresses to process management articles and sends the article to the inserted recipients.

To add an email communication channel to process management article:

1. Go to the *Process Management* screen.
2. Click on the *User Task Activity Dialogs* item in the *Available Process Elements* widget in the left sidebar.
3. Click on the pencil icon to edit the user task activity dialog.
4. Drag the *Article* field from the *Available Fields* pool and drop into the *Assigned Fields* pool or click on a pencil icon of an already added *Article* field.
5. Select *Email* in the *Communication Channel* field.

   .. figure:: images/edit-article-field-details.png
      :alt: Edit Field Details Window

      Edit Field Details Window

6. Save and deploy the process.
7. Go to the *Ticket Notifications* screen of the administrator interface.
8. Create a corresponding ticket notification for the event ``ArticleCreate`` so that the email is sent.

.. warning::

   In the same activity dialog, you can use either the above-mentioned article field with email or a regular article field. Using both fields together will cause a process error.

Now go to the :doc:`../../agent/tickets/new-process-ticket` and start a new process.
