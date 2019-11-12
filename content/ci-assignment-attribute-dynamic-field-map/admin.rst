Administrator Interface
=======================

This package has no administrator interface, but it allows to set dynamic field values as well as service and SLA of tickets based on linked configuration items.


Assign Service and SLA
----------------------

It is possible to add definition of two configurable fields in configuration items which contain service and SLA information.

Whenever a configuration item is linked to a ticket or unlinked from a ticket, these fields are used to update or remove service and SLA of the linked ticket.

To add the fields for configuration items:

1. Open the *Config Items* module of the *CMDB Settings* group in the administrator interface.
2. Select a configuration item class and click on the *Change class definition* button.
3. Add the new fields to the class definition.

   .. code-block:: yaml

      - Key: TicketServiceName
        Name: Service
        Searchable: 1
        Input:
          Type: Text
          Size: 50
          MaxLength: 50

      - Key: TicketSLAName
        Name: SLA
        Searchable: 1
        Input:
          Type: Text
          Size: 50
          MaxLength: 50

   .. note::

      The ``Key`` values must be the same as set in ``ITSMConfigItem::ServiceField`` and ``ITSMConfigItem::SLAField`` settings.

After this is configured correctly, just create a configuration item with both fields filled out. If you are going to link this newly created configuration item to a ticket, service and SLA from configuration item attributes are taken into the linked ticket.

Requirements and limitations for service and SLA linking:

- Service functionality must be enabled.
- Configuration item fields for service and SLA must be configured.
- Linked configuration item must contain valid service and SLA names.
- Service and SLA names of configuration item must be allowed for the linked tickets (e.g. not restricted via ACL).
- Linking a configuration item when another configuration item is already linked will update service and SLA again.

Requirements and limitations for service and SLA unlinking:

- Service functionality must be enabled.
- Configuration item fields for service and SLA must be configured.
- Service and SLA of ticket and configuration item must match.
- After unlinking, service and SLA of ticket will be removed, not changed to values before linking.


Assign Dynamic Field Values
---------------------------

It is possible to add definition of a configuration item attribute to dynamic field mapping.

Whenever a configuration item is linked to a ticket, it is checked if the configuration item has attributes defined in this mapping and if so, assigns these values to the dynamic fields of the corresponding ticket. Whenever a configuration item is unlinked from a ticket, the dynamic field value remains unchanged.

To configure the mapping:

1. Go to *System Configuration* screen.
2. Select *OTRSCIAssignmentAttributeDynamicFieldMap* in the *Navigation* widget.
3. Navigate to *Core → OTRSCIAssignmentAttributeDynamicFieldMap* in the navigation tree.
4. Search for setting ``ITSMConfigItem::TicketDynamicFieldMapping`` and set the mapping between configuration item attributes and ticket dynamic fields.

   For example:

   .. code-block:: none

      NIC::IPAddress         → IPAddress
      NIC::IPoverDHCP        → IPoverDHCP
      SerialNumber           → SerialNumber
      WarrantyExpirationDate → WarrantyExpirationDate

   .. note::

      If you want to use configuration item attributes nested into a deeper structure, add the chain of attribute keys separated by ``::``.

5. Search for setting ``ITSMConfigItem::TicketDynamicFieldValueMapping`` and set the mapping between configuration item attributes and the values of ticket dynamic fields. We have to specify mappings for this to solve a mismatch between possible values of configuration item attributes and possible values of ticket dynamic fields.

   For example:

   .. code-block:: none

      NIC::IPoverDHCP → No  → 2
                        Yes → 1

   The numbers define the order in which the values are shown in the drop-down dynamic field. If you would store the values *Yes* and *No* into a dynamic field with the configuration shown above, the system would try to store the value *Yes* or *No* whereas the dynamic field would expect key ``1`` for *Yes* or key ``2`` for *No*.

.. note::

   This mapping can also be used for other fields, if the configuration item attribute value does not match a dynamic field key. In this case write the configuration item attribute value into the key part of the hash and the dynamic field key inside the item tag.

After this is configured correctly, just create a configuration item with the mapped fields filled out. If you are going to link this newly created configuration item to a ticket, the ticket dynamic fields are populated with configuration item attributes. The configuration item attributes will be shown in the ticket information in the right sidebar of the *Ticket Zoom* screen and will be automatically updated when the CMDB is modified.

Limitations of the dynamic field assignment functionality:

- Dynamic fields are just filled if they do not have content yet.
- If a configuration item is unlinked from a ticket, the dynamic field values do not get deleted.
- If a configuration item attribute contains a list of values (for example multiple IP addresses of a computer configuration item) only the first value of this list is assigned to a dynamic field.
