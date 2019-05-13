Customer-specific Services
==========================

This feature add-on makes it possible to assign services to customer IDs or customer users so that only the assigned service is displayed when a ticket is created in the customer portal and only the appropriate SLAs are valid.

After the installation, two new options appear in the *User, Groups & Roles* group in the administrator interface: *Customer ID ↔ Service* and *Customer User ↔ Service*. Here you can define which services should be assigned to a customer ID (customer company) and/or customer user within the same customer company.

Furthermore, you can define in the system configuration which of these options should be the leading one.

Benefits
   - Efficient and well-structured administration of multiple services and SLAs for many clients.
   - Avoid the creation of unwarranted tickets that stress out your service team.
   - Optimal guidance for the customer regarding for which services he or she can open a ticket.
   - Speed-up of ticket handling process.

Available in Service Package
   SILVER

Target Groups
   - Internal IT departments
   - External IT service providers
   - Call centers
   - Agencies
   - Consulting businesses
   - Companies offering a wide range of services or products

.. note::

   Before your first use, please make sure that you activate the *Services* option in the administrator interface.

.. note::

   The ``CustomerUserSearchListLimit`` option should be configured in the ``CustomerUser`` section in the ``Config.pm``.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-customer-specific-services/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   customer-specific-services/admin
   customer-specific-services/agent
   customer-specific-services/external
