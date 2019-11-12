Agent Interface
===============

This package has no agent interface.


Usage
-----

Reply any ticket notification and insert for example the following tag anywhere in the body of the mail:

.. code-block:: none

   <OTRS_CMD> close </OTRS_CMD>

Switch to the ticket from the ticket notification and compare the ticket state. The ticket should have the state *closed*.

.. note::

   The package restricts the functionality of this feature to agents known to the system, but it does not use advanced security mechanisms such as digital signatures and the like.
