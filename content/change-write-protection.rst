Change Write Protection
=======================

This feature add-on makes it possible to hide specific changes or work orders in a particular status, thus preventing further changes.

The feature add-on is ideal for use in IT service management. For example, the authorization for a change normally comes after its description. After authorization is given, the description of the change can no longer be changed retroactively in the change builder. In addition, the change is then no longer shown in the *Change Zoom* view.

With system configuration you can define:

- The status of a change/work order: enables the creation of a list of statuses that must take place for write protection to be activated.
- Actions: enables the creation of a list of actions that are no longer shown/no longer possible once a predefined status is activated.

This feature add-on will take you to the next level of transparent work and careful change management.

Benefits
   - Increases transparency and leads to more care and diligence in the change process.
   - Optimizes the general transparency of your system.

Available in Service Package
   GOLD

Target Groups
   - IT service management
   - All clients that use the OTRS::ITSM feature

.. note::

   The feature add-on must be activated/deactivated in the system configuration.

.. note::

   If a change is write-protected, this will affect all contained work orders.

.. Original content: https://otrs.com/otrs-feature/brute-force-attack-protection/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   change-write-protection/admin
   change-write-protection/agent
   change-write-protection/external
