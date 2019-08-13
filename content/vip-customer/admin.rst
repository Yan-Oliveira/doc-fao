Administrator Interface
=======================

This package has no administrator interface.


System Configuration
--------------------

The package has no default configuration for customer users and SLAs available only for VIP customer users. Customer users and SLAs have to be added in the system configuration.

To set VIP status for a customer user:

1. Go to *System Configuration* screen.
2. Select *OTRSVIPCustomer* in the *Navigation* widget.
3. Navigate to *Core → OTRSVIPCustomer* in the navigation tree.
4. Add the customer user IDs (login names) to setting ``VIP::UIDs``.

To set an existing SLA only available for VIP customer users:

1. Go to *System Configuration* screen.
2. Select *OTRSVIPCustomer* in the *Navigation* widget.
3. Navigate to *Core → OTRSVIPCustomer* in the navigation tree.
4. Add the SLAs to setting ``VIP::SLAs``.

.. note::

   If a customer user is configured as a VIP, the internal customer record will have the attribute ``UserVIP`` set to ``TRUE``. This allows to access the customer user’s VIP status through other technical facilities, such as ACL definitions.
