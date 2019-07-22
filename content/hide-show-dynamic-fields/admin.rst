Administrator Interface
=======================

This package has no administrator interface, but the function can be used in agent and external interface. The following screens can be configured:

Agent interface:

- New Phone Ticket
- New Email Ticket
- Ticket Phone Inbound
- Ticket Phone Outbound
- Ticket Note
- Ticket Close
- Ticket Move
- Ticket Pending
- Ticket Free Fields
- Ticket Owner
- Ticket Responsible
- Ticket Priority

External interface:

- New Ticket
- Ticket Reply (within *Ticket Detail View*)

In the *Ticket Search* screen the functionality is limited to show or hide dynamic fields if non-ticket-specific ACLs are used (e.g. *Properties → User → UserID* or *Roles*).


Example Usage
-------------

Goals:

- If brand *VW* is selected, all dynamic fields should be hidden and just *VW Model* is displayed.
- If VW model *Up* is selected, all dynamic fields should be displayed except for the fields *Peugeot Model* and *Peugeot Production Facility*.

Create the following dynamic fields:

+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Object | Type        | Name                          | Label                       | Possible values                            |
+========+=============+===============================+=============================+============================================+
| Ticket | Dropdown    | ``Brand``                     | Brand                       | - ``VW`` → VW                              |
|        |             |                               |                             | - ``Peugeot`` → Peugeot                    |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Dropdown    | ``VWModel``                   | VW Model                    | - ``Up`` → Up                              |
|        |             |                               |                             | - ``Polo`` → Polo                          |
|        |             |                               |                             | - ``Golf`` → Golf                          |
|        |             |                               |                             | - ``T5`` → T5                              |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Dropdown    | ``VWProductionFacility``      | VW Production Facility      | - ``Barcelona`` → Barcelona                |
|        |             |                               |                             | - ``Berlin`` → Berlin                      |
|        |             |                               |                             | - ``Bratislava`` → Bratislava              |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Dropdown    | ``PeugeotModel``              | Peugeot Model               | - ``207`` → 207                            |
|        |             |                               |                             | - ``307`` → 307                            |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Dropdown    | ``PeugeotProductionFacility`` | Peugeot Production Facility | - ``Poissy`` → Poissy                      |
|        |             |                               |                             | - ``Madrid`` → Madrid                      |
|        |             |                               |                             | - ``Trnava`` → Trnava                      |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Dropdown    | ``Fuel``                      | Fuel                        | - ``Gasoline`` → Gasoline                  |
|        |             |                               |                             | - ``Diesel`` → Diesel                      |
|        |             |                               |                             | - ``Gas`` → Gas                            |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Multiselect | ``Accessories``               | Accessories                 | - ``CDRadio`` → CD Radio                   |
|        |             |                               |                             | - ``GPS`` → GPS                            |
|        |             |                               |                             | - ``ProximitySensors`` → Proximity Sensors |
|        |             |                               |                             | - ``RearCamera`` → Rear Camera             |
|        |             |                               |                             | - ``ClimateControl`` → Climate Control     |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | TextArea    | ``Remarks``                   | Remarks                     |                                            |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Date        | ``RegistrationDate``          | Registration Date           |                                            |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+
| Ticket | Date        | ``InvoiceDate``               | Invoice Date                |                                            |
+--------+-------------+-------------------------------+-----------------------------+--------------------------------------------+

Add the dynamic fields to the *New Phone Ticket* screen via setting ``Ticket::Frontend::AgentTicketPhone###DynamicField``:

.. code-block:: none

   Brand → 1 - Enabled
   VWModel → 1 - Enabled
   VWProductionFacility → 1 - Enabled
   PeugeotModel → 1 - Enabled
   PeugeotProductionFacility → 1 - Enabled
   Fuel → 1 - Enabled
   Accessories → 1 - Enabled
   Remarks → 1 - Enabled
   RegistrationDate → 1 - Enabled
   InvoiceDate → 1 - Enabled

Import this ACL:

.. code-block:: YAML

   ---
   - ChangeBy: root@localhost
     ChangeTime: 2019-07-22 11:44:25
     Comment: ''
     ConfigChange:
       PossibleNot:
         Form:
         - PeugeotModel
         - PeugeotProductionFacility
         - Accessories
         - Fuel
         - Remarks
         - RegistrationDate
         - InvoiceDate
     ConfigMatch:
       Properties:
         Ticket:
           DynamicField_Brand:
           - VW
     CreateBy: root@localhost
     CreateTime: 2019-07-22 11:40:43
     Description: ''
     ID: 1
     Name: ACL-VW
     StopAfterMatch: 0
     ValidID: 1

Detailed explanation:

.. code-block:: YAML

   DynamicField_Brand:
   - VW

The condition for this ACL rule. If brand *VW* is selected, the rule will come into action. The array contains the used possible values keys found in your database inside the ``dynamic_field`` table in column ``config``. In this example it is a dynamic field of type *Dropdown*.

.. code-block:: YAML

   Form:

This package introduces the ``Form`` key as new option in the *Possible*, *PossibleAdd* and *PossibleNot* ACL change sections. ``Form`` holds the configuration for the visibility of dynamic fields.


.. code-block:: YAML

   PossibleNot:
     Form:
     - PeugeotModel
     - PeugeotProductionFacility
     - Accessories
     - Fuel
     - Remarks
     - RegistrationDate
     - InvoiceDate

This section lists the dynamic fields that should not be visible. In this example the dynamic fields *VW Model* and *VW Production Facility* are visible. All other dynamic fields will be hidden.

Import this second ACL:

.. code-block:: YAML

   ---
   - ChangeBy: root@localhost
     ChangeTime: 2019-07-22 12:06:24
     Comment: ''
     ConfigChange:
       Possible:
         Ticket:
           DynamicField_Accessories:
           - CD Radio
           - Climate Control
           DynamicField_Fuel:
           - Gasoline
           DynamicField_VWProductionFacility:
           - Bratislava
       PossibleAdd:
         Form:
         - Accessories
         - Fuel
         - Remarks
         - RegistrationDate
         - InvoiceDate
       PossibleNot:
         Form:
         - PeugeotModel
         - PeugeotProductionFacility
     ConfigMatch:
       Properties:
         Ticket:
           DynamicField_Brand:
           - VW
           DynamicField_VWModel:
           - Up
     CreateBy: root@localhost
     CreateTime: 2019-07-22 11:47:02
     Description: ''
     ID: 2
     Name: ACL-VW-Up
     StopAfterMatch: 0
     ValidID: 1

Detailed explanation:

.. code-block:: YAML

   DynamicField_Brand:
   - VW
   DynamicField_VWModel:
   - Up

In this example two conditions should be met. Brand has to be *VW* and VW model has to be *Up* for this rule to come into action. It will be triggered only if an agent selects brand *VW* **and** VW model *Up*.

.. code-block:: YAML

   PossibleAdd:
     Form:
     - Accessories
     - Fuel
     - Remarks
     - RegistrationDate
     - InvoiceDate

Here the dynamic fields *VW Model*, *VW Production Facility* were already visible and they remain, but *Accessories*, *Fuel*, *Remarks*, *Registration Date*, and *Invoice Date* has to be re-added to the fields that are visible. This is done in the *PossibleAdd* section as the first ACL sets this fields as not shown and both ACLs works together. If this was done in the *Possible* section for example, the result will be that only this fields explicitly will be shown and *VW Model* and *VW Production Facility* will be hidden as they are not longer part of the (new) *Possible* section.

.. code-block:: YAML

   PossibleNot:
     Form:
     - PeugeotModel
     - PeugeotProductionFacility

Just *Peugeot Model* and *Peugeot Production Facility* are invisible (in our example it does not make much sense to configure a Peugeot model if the user has a VW Up).

In addition to the visibility of dynamic fields there is the possibility to show just some of the possible values of a dynamic field. Combined into ACL rules like in here, makes it easier to handle big multi-selects.

.. code-block:: YAML

   Possible:
     Ticket:
       DynamicField_Accessories:
       - CD Radio
       - Climate Control
       DynamicField_Fuel:
       - Gasoline
       DynamicField_VWProductionFacility:
       - Bratislava

In our example a VW Up can have just CD radio and climate control as extra accessories, just gasoline as fuel and can be produced just in Bratislava.

If we would have an ACL rule for Peugeot 207 for example, there may be other extras, fuel options and production locations selectable.

.. note::

   If you are showing dynamic fields using the *Possible* option based on a ``DynamicField_NameX`` value, is normally desirable to include the dynamic field that triggers the ACL to be part of the fields to be displayed in the *Possible* or *PossibleAdd* sections (if apply). Otherwise if *Possible* or *PossibleAdd* contains other fields and not the trigger, the latest will not be shown after the value is selected.

.. note::

   The mandatory status of the fields can not be changed using this method.
