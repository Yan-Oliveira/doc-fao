Process Management Article Email
================================

This feature add-on makes it possible to add email addresses to process management articles, as well as send them via email. This guarantees a more direct communication straight from the process and therefore increases the transparency of the process communication.

To use a process management article with this functionality, you must click on the pencil sign in the field *Add Article* of a previously created process with at least one activity dialog. In the form that appears you must select *Email external* or *Email internal* in the dropdown field *Article Type* and click *Save*.

After the process has been activated, you can open a new process ticket by clicking on the option of the same name displayed after clicking on the menu option *Ticket*. In the form that appears next, you can add an email address to the field *customer user* — just like when you are using the regular email ticket form. The article will be sent to the chosen customer user or agent.

Benefits
   - More flexible usage of the OTRS process management.
   - Direct communication with customers or other agents straight from the process.
   - Greater transparency for customers or other agents regarding the process step their request is in.
   - More interactivity with the customer or other agents during the process.
   - More efficient design of your business processes.

Available in Service Package
   GOLD

Target Groups
   - Process managers
   - External IT
   - Internal IT
   - Customer service
   - Facility management
   - And many more

.. note::

   In the same activity dialog, you can use either the above-mentioned article field with email or a regular article field. Using both fields together will cause a process error.

.. note::

   Do not forget to also create a corresponding ticket notification for the event ``ArticleCreate`` so that the email is sent.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-process-management-article-email/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   process-management-article-email/admin
   process-management-article-email/agent
   process-management-article-email/external
