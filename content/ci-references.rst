CI References
=============

With this feature add-on it is possible to enhance the CIs in the configuration management database (CMDB) through additional fields and to create links and references between these or other data in **OTRS**. This can be useful for linking CIs with each other when there is a dependency relationship between them or to store information regarding linked services and users directly in the CI, as well as find this information with a quicker autocomplete search.

The following input fields with autocomplete search can be added:

- ``ReferenceCI`` field: a further configuration item.
- ``ReferenceService`` field: a further service.
- ``ReferenceUser`` field: a further user.

In the administrator interface, it is possible to create new reference fields under *Config Item*. Then, it is necessary to add the visualization configuration as code for the desired CI class. If, for example, a new CI is being created in the said class, then the newly added reference field will appear in the form to be filled out. A search for the referenced CIs using autocomplete can then be carried out, and these can be added. If the new CI is updated, an automatic linking to the referenced CI is carried out.

Benefits
   - Enhancement of CIs through additional input fields and additional, system-referenced data.
   - Linking of CIs with each other and with other data in **OTRS**.
   - Quicker autocomplete search for values referenced in CI fields.
   - Clear visualization of complex dependencies between CIs and other CIs, services, and users.

Target Groups
   - Configuration item managers
   - Internal and external IT
   - Facility management
   - Sales

Available in Service Package
   - GOLD

Package Name in OTRS Package Manager
   - OTRSCIReferences

.. note::

   This feature add-on requires the *ITSM Configuration Management* and *Import/Export* features.

.. Original content: https://otrs.com/otrs-feature/feature-add-on-ci-references/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   ci-references/admin
   ci-references/agent
   ci-references/external
