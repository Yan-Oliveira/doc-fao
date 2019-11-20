Dynamic Field Value Import
==========================

This feature add-on offers additional options for uploading values from CSV files for dynamic fields. The data from individual columns of the CSV file are assigned to a specific dynamic field that you can flexibly select. These files can additionally contain headers into which you can insert the desired name of the target fields. Before the value can be imported, the target fields have to be created manually.

After a successful upload, the *Change Overview* widget shows all new or deleted values for the dynamic fields affected. These values are marked in colors.

In addition, the feature add-on enables the automatic creation of ACLs based on the dynamic fields chosen and their imported values. This significantly reduces the manual workload for ACL creation.

Dependencies between the dynamic fields are created from left to right. If values for more than two dynamic fields are imported, the allocation of the ACL relations starts in the column furthest to the left. Multi-level dependencies are therefore possible.

Benefits
   - Fast import of modified product portfolios.
   - Customer service and sales are more quickly up-to-date.
   - Easier integration of partners from outsourced corporate areas.

Target Groups
   - Call centers
   - Customer service
   - Wholesalers
   - Sales
   - Order management

Available in Service Package
   - GOLD

Package Name in OTRS Package Manager
   - OTRSDynamicFieldValueImport

.. Original content: https://otrs.com/otrs-feature/feature-add-on-dynamic-field-value-import/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   dynamic-field-value-import/admin
   dynamic-field-value-import/agent
   dynamic-field-value-import/external
