Agent Interface
===============

This package has no agent interface.


Mapped Values as Sender Address
-------------------------------

When a ticket reply or forward is created or when an event based notification is sent, the configured dynamic field of the ticket is checked. If the dynamic field contains a value, a mapping configuration is checked. If there is a mapped value in :doc:`admin/communication-notifications/sender-address-mapping`, this value will be used as sender address.

If the dynamic field is not set or no mapping value exists, the default queue-based sender address will be used.

This feature should be used if your tickets have dynamic fields that contain information which sender address should be used, but are not email addresses. For this purpose the dynamic field values can be mapped to email addresses.


Example Usage
~~~~~~~~~~~~~

A dynamic field *Customer location* is configured to be used as sender address base. The configured queue sender address is *support@company.com*.

In the mapping module the following is configured:

- England → support.uk@company.com
- France → support.fr@company.com
- Germany → support.de@company.com
- Scotland → support.uk@company.com

When an agent replies to a ticket, the *Customer location* field is looked up and depending on the location the sender address is determined.

- Dynamic field value: <empty field>, sender address: support@company.com (address from queue).
- Dynamic field value: England, sender address: support.uk@company.com (mapped value).
- Dynamic field value: Ireland, sender address: support@company.com (no mapping found, therefore address from queue).
- Dynamic field value: France, sender address: support.fr@company.com (mapped value).


Direct Values as Sender Address
-------------------------------

When a ticket reply or forward is created or when an event based notification is sent, the configured dynamic field of the ticket is checked. If the dynamic field contains a value, this value will be used as sender address.

If the dynamic field is not set, the default queue-based sender address will be used.

This feature should be used if your tickets have dynamic fields that contain email addresses which should be used as sender address.

.. note::

   With this feature dynamic field values are not checked in advance, therefore all values for the configured field need to be valid email addresses to prevent delivery errors.


Example Usage
~~~~~~~~~~~~~

A dynamic field *Customer location address* is configured to be used as sender address. The configured queue sender address is *support@company.com*. When an agent replies to a ticket, the *Customer location address* field is looked up and the sender address is determined.

- Dynamic field value: <empty field>, sender address: support@company.com (address from queue).
- Dynamic field value: France, sender address: France (dynamic field value is an invalid email address, the email will not send).
- Dynamic field value: support.uk@company.com, sender address: support.uk@company.com (dynamic field value).
