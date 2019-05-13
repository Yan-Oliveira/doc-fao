OpenBook Connector
==================

This feature add-on makes it possible to set up authentication for OpenBook customer users and a read-only customer back end for accessing customer user data stored in Talligent’s billing and reporting solution OpenBook when using **OTRS**.

To set up the authentication module, you must add a piece of code to the ``Kernel/Config.pm`` file that enables the following configurations in order to access the OpenBook customer user data:

- Define the OpenBook API user.
- Define the OpenBook API password.
- Define the OpenBook API URL.
- Define the valid user roles in **OTRS** to access the OpenBook customer back end.

To set up the OpenBook customer back end module, you must add a piece of code to the ``Kernel/Config.pm`` file that enables the following configurations:

- ``Map``: defines all possible fields that are visible to the customer user.
- ``CustomerUserNameField``: comprises all fields that are assigned to the customer user.
- ``CacheTTL``: defines the cache time in seconds.
- ``CustomerValid``: defines the name of fields in OpenBook for valid columns.
- And many more.

Benefits
   - Seamless and easy integration of **OTRS** with Talligent’s OpenBook.
   - Authentication with an OpenBook account with restrictions for certain customer user roles in **OTRS**.
   - Display of and search for OpenBook customer user data in **OTRS**.
   - Better integration of service provision with billing and reporting processes.

Available in Service Package
   GOLD

Target Groups
   - External IT
   - Internal IT
   - Customer service
   - Finance
   - And many more

.. note::

   Right now this feature add-on is only usable with **OTRS 4**. If you wish for it to be ported to **OTRS 7**, please contact our sales team at sales@otrs.com.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-openbook-customer-backend/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   openbook-connector/admin
   openbook-connector/agent
   openbook-connector/external
