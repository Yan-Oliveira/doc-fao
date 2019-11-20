CIs in Customer Frontend
========================

This feature add-on uses the customer ID attribute of your CI classes and makes CIs visible in the external interface. The customer user has read-only access to the following attributes:

- ID of their CI
- Name of the CI
- Class of the CI
- Deployment state
- Current incident state
- Date and time of the last update

On mail-in this feature add-on automatically links affected CIs based on the given configuration item ID found in the body of the email. It is also helpful for your service desk as, on ticket creation, they only have access to the CIs of the requester’s organization or department. This eases the selection of affected CIs a lot, especially if you have many CIs in your CMDB.

Benefits
   - Automatic assignment of CIs saves time.
   - Customers can assign CIs to new tickets.

Target Groups
   - Customer service organizations
   - External IT service providers
   - Logistics
   - Technical field service

Available in Service Package
   - GOLD

Package Name in OTRS Package Manager
   - OTRSCIsInCustomerFrontend

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`hide-show-dynamic-fields`
   - :doc:`ticket-forms`

.. note::

   This feature add-on requires the *ITSM Configuration Management* feature.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-cis-in-customer-frontend/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   cis-in-customer-frontend/admin
   cis-in-customer-frontend/agent
   cis-in-customer-frontend/external
