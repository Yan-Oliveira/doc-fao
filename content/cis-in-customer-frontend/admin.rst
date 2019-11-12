Administrator Interface
=======================

This package has no administrator interface.


Extend Class Definition
-----------------------

The definition of a configuration item class has to be altered to make it able to be displayed in the external interface.

By default, the ``CustomerID`` field is configured in the system configuration to store the customer ID information in the configuration item definition.

You can use more than one ``CustomerID`` per configuration item, to make one configuration item accessible by more than just one customer. To do so, repeat the following steps for the maximum amount of customers one configuration item may grant access to (for example: ``PartnerA``, ``PartnerB``, ``PartnerC``, etc.).

.. seealso::

   To use more than one ``CustomerID`` or use another name than ``CustomerID``, it is necessary to change the setting ``ITSMConfigItem::CustomerIDField`` in system configuration or add additional entries for each entry field.

If your class definition does not contain the ``CustomerID`` attribute, then you have to add it manually.

To add the fields for configuration items:

1. Open the *Config Items* module of the *CMDB Settings* group in the administrator interface.
2. Select a configuration item class and click on the *Change class definition* button.
3. Add the new fields to the class definition. The input type could be either ``Text`` or ``CustomerCompany``.

   ``Text`` Field
      Text based field gives the flexibility to use any string as value to match the ``CustomerID`` for one or more customers. The value must be entered manually by editing each configuration item, but it needs to be done carefully, because any mismatch will prevent the configuration item to be displayed in the external interface.

      .. code-block:: yaml

         - Key: CustomerID
           Name: Customer Company
           Searchable: 1
           Input:
             Type: Text
             Size: 50
             MaxLength: 100


   ``CustomerCompany`` Field
      A customer company field needs to have correctly configured customer companies in the system, as it will be presented as a drop-down list in the configuration item add and edit screens. The source of the drop-down will be the list of companies. ``CustomerID`` field in all customer users must point to the correct customer ID in customer companies administration.

      .. code-block:: yaml

         - Key: CustomerID
           Name: Customer Company
           Searchable: 1
           Input:
             Type: CustomerCompany

4. Save the new definition.
5. Edit a configuration item from the modified class. Find the *Customer Company* field (or another field you have added) and fill it with the customer ID of an existing customer.
6. Login to the external interface with any customer user that has the customer ID described above.
7. Go to *Company Configuration Items*. The edited configuration item must be listed.


Define Strictness of Customer ID Restriction
--------------------------------------------

The setting ``ITSMConfigItem::CustomerCIPermissionByLink`` is set to 0 by default, so configuration items are only accessible in the external interface if the company (customer ID) of the customer user matches the value of a configured field. If this behavior is more strict than desired or not all configuration items can/should be configured in such a way, the configuration can be changed to consider links between configuration items (permission inheritance by links). When linking configuration items to new tickets in the external interface and in the agent interface (if enabled), only direct permission is considered though (i. e. ``CustomerID`` field in configuration item matches).

For example:

- There are multiple computer configuration items assigned to the customer company. All computer configuration items are linked to at least one network configuration item (switches). These devices do not belong to the customer and are therefore not visible. Also the network configuration items are linked to other network configuration items (router).
- By default, only the companies computers are visible under *Company Configuration Items*, are shown in linked tickets and (depending on the configuration) can be viewed in detail and used for new tickets.
- If the setting ``ITSMConfigItem::CustomerCIPermissionByLink`` is set to 1, all switches connected to a computer will be visible under *Company Configuration Items*, are shown in linked tickets and can be viewed in detail, but not used for to be linked to new tickets.
- If the setting ``ITSMConfigItem::CustomerCIPermissionByLink`` is set to 2, the routers will be included as well.

.. warning::

   The link type and direction is not relevant for determining the permission. Therefore please carefully consider which value to use for ``ITSMConfigItem::CustomerCIPermissionByLink`` in order to prevent unwanted disclosure of configuration items.


Hide Configuration Item Fields in External Interface
----------------------------------------------------

It could be possible that configuration items has fields that customer does not need to view, or that contains sensitive information that customers must not know. For these cases an administrator can restrict a field by placing a simple new attribute ``NotForCustomer`` to the field definition on a particular class.

To hide a field in external interface:

1. Open the *Config Items* module of the *CMDB Settings* group in the administrator interface.
2. Select a configuration item class and click on the *Change class definition* button.
3. Add the attribute ``NotForCustomer: 1`` to the field definition.

   For example:

   .. code-block:: yaml

      - Key: Vendor
        Name: Vendor
        Searchable: 1
        Input:
          Type: Text
          Size: 50
          MaxLength: 50
        NotForCustomer: 1

4. Edit the configuration items of this class in order to create a new version, so the new version will take the new definition.

To avoid the need to create new versions for configuration items if the definition of a class is updated to hide a field from external interface, it will be applied to all configuration items of that class. On the other hand, if the class definition is updated to show a field that was previously hidden and the configuration item was already updated to the class definition where the field was hidden, the field will not be shown until the configuration item is updated to last class definition where the field is set to be shown again.

The intention of this behavior is to enforce the privacy of the data that should not be displayed in the external interface.
