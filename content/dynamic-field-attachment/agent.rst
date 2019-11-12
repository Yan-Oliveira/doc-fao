Agent Interface
===============

This package has no agent interface, but the dynamic field of type attachment can be added to many screens.


Upload Files
------------

To upload files to dynamic field of type attachment:

1. Make sure that the dynamic field of type attachment is added to the desired screen.
2. Click on the uploading area or just dropping the files there. The file gets uploaded immediately to the server and a new upload field will be displayed as long as the configured maximum amount of attachments has not been reached.
3. Click on the *Submit* button. If a file has exceeded the maximum attachment size, a message will appear warning the agent that the file exceeds the maximum attachment size. In this case the file will not be uploaded and the ticket will be created without problem.

Uploading multiple files with identical names to one dynamic field of type attachment will result in an error notifying the agent that this is not permitted.


Download Files
--------------

The dynamic field of type attachment is displayed in *Ticket Zoom* screen, if it is added to the screen and a file has been uploaded.

To download a file from a ticket dynamic field of type attachment:

1. Find the *Attachments* link in the *Ticket Information* widget in the right sidebar.
2. Click on the *Attachments* link. A small *Attachments* dialog appears showing all filenames as well as their size.
3. Click on a filename to download the file.

To download a file from an article dynamic field of type attachment:

1. Select an article, that has a dynamic field of type attachment with at least one uploaded file.
2. Expand the article header with the *i* icon in the top right corner of the article widget.
3. Find the *Attachments* link in the article header.
4. Click on the *Attachments* link. A small *Attachments* dialog appears showing all filenames as well as their size.
5. Click on a filename to download the file.


Delete Files
------------

If a ticket dynamic field of type attachment has been configured to be displayed in the *Ticket Free Fields* screen, it is possible to delete the uploaded files and add new files.

To delete a file from a ticket dynamic field of type attachment:

1. Make sure that the dynamic field of type attachment is added to the *Ticket Free Fields* screen.
2. Click on the *Miscellaneous → Free Fields* menu item in the ticket menu.
3. Click on the trash icon in the last column of an attachment. The attachment will be deleted without confirmation!

.. note::

   It is not possible to delete files from dynamic field of type attachment created for article object.


Search for Files
----------------

Dynamic field of type attachment supports searching for the file names.

To search for a dynamic field of type attachment:

1. Make sure that the dynamic field of type attachment is added to the *Ticket Search* screen.
2. Click on the *Tickets → Search* menu item in the main menu.
3. Add the dynamic field to the search criteria. The \* character as wildcard is supported.
