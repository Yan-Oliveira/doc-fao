Agent Email Interface
=====================

This feature add-on makes it possible for an agent to work with tickets via emails without having to use the web agent interface of **OTRS**.

In order to work with this module an agent could just reply to any ticket notification email by including one or many commands between two special command tags, like this:

.. code-block:: none

   <OTRS_CMD> send </OTRS_CMD>

or

.. code-block:: none

   <OTRS_CMD> send, nocc </OTRS_CMD>

Commands can be combined (comma separated) if it makes sense to combine them.

The following commands exist:

- ``send`` – Sends an email to the customer, including the cc and bcc recipients (``send`` also locks the ticket).
- ``nocc`` – If used together with ``send``, the cc and bcc recipients will be excluded.
- ``lock`` – Locks the ticket.
- ``unlock`` – Unlocks the ticket.
- ``get`` – Gets the last customer article and sends it to the agent.
- ``note`` – Adds an internal note to the ticket.
- ``close`` – Closes the ticket (also unlocks the ticket).

.. note::

   The package restricts the functionality of this feature to agents known to the system, but it does not use advanced security mechanisms such as digital signatures and the like.

Benefits
   - Saves time because frequent logging in and out is not necessary.
   - Increase flexibility because you do not have to log in to the system.

Available in Service Package
   GOLD

Target Groups
   - Can be used in all areas where agents are not logged in permanently to the OTRS agent interface.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-agent-email-interface/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   agent-email-interface/admin
   agent-email-interface/agent
   agent-email-interface/external
