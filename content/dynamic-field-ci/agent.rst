Agent Interface
===============

This package has no agent interface, but the dynamic field of type configuration item can be added to many screens.


Automatic Linking and Unlinking
-------------------------------

When configuration items are added to or removed from tickets via the new dynamic field back end, links for the respective configuration items can be added or removed automatically. If this is configured, links will be compared and links will be added and/or removed, if necessary.

.. warning::

   In order to prevent inconsistencies between the dynamic field content and links please do not add or remove links of the configured type and direction manually via the link mechanism in the *Ticket Zoom* screen. Those changes are not synchronized back to the dynamic field content.

.. seealso::

   The dynamic field configuration decides if linking happens and what link type and direction will be used. See the :doc:`admin/processes-automation/dynamic-fields` in the administrator interface.
