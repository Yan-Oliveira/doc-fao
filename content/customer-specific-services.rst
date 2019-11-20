Customer-specific Services
==========================

This feature add-on makes it possible to assign services to customers so that only the assigned service is displayed when a ticket is created and only the appropriate SLAs are valid.

After installation of the package, a new module *Customers ↔ Service* appears in the *Users, Groups & Roles* group in the administrator interface. Here you can define which services should be assigned to customers.

Furthermore, you can define in the system configuration which of these options should be the leading one.

Benefits
   - Efficient and well-structured administration of multiple services and SLAs for many customers.
   - Avoid the creation of unwarranted tickets that stress out your service team.
   - Optimal guidance for the customer regarding for which services he or she can open a ticket.
   - Speed-up of ticket handling process.

Target Groups
   - Internal IT departments
   - External IT service providers
   - Call centers
   - Agencies
   - Consulting businesses
   - Companies offering a wide range of services or products

Available in Service Package
   - SILVER

Package Name in OTRS Package Manager
   - OTRSCustomerSpecificServices

.. note::

   Before your first use, please make sure that you activate the *Services* option in the administrator interface.

.. note::

   The ``CustomerUserSearchListLimit`` setting should be configured in the ``CustomerUser`` section in the ``Kernel/Config.pm``.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-customer-specific-services/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   customer-specific-services/admin
   customer-specific-services/agent
   customer-specific-services/external
