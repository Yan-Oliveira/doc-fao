Administrator Interface
=======================

This feature implements a generic dynamic field type *Web Service* that gathers its selectable options from an external system using a web service.

The response from the external system defines the possible options to be displayed, and they could vary depending on the data that is sent in the request. Normally when a field is changed in a screen (e. g. the ticket priority in the *New Phone Ticket* screen) the values of other fields could be updated. That is the case with this type of dynamic fields, as they could also include all screen field values in the request and the remote server could potentially return completely different values depending on input.

Additionally if the dynamic field source object already exists (e. g. a ticket, and the field is set in the *Ticket Free Fields* screen), the details of the already created ticket are also included in the request.

.. toctree::
   :maxdepth: 3
   :caption: Contents

   admin/processes-automation
