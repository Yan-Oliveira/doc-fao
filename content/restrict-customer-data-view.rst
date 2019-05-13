Restrict Customer Data View
===========================

Service organizations that go global or have a wide range of products have to outsource their customer service to distribution partners or call centers. When that happens, the security of customer data is very important and only the appropriate third party providing the service should have access to customer information.

This feature add-on makes this defined access possible with the assignment of customer IDs to partner IDs. It enhances and specifies the customer information center of the standard version and whose customer data can be accessed by all agents. When customer data is retrieved from an LDAP server, the Feature Add-on checks for a partner ID and which customer IDs are assigned to it. Therefore, agents of a partner ID can only see customer data of the assigned customer ID. If there is no customer ID assigned to a partner ID, the agents are not allowed to see any customer data. If no partner ID has been created, all agents can see all customer data.

The first configuration steps after the installation are the configuration of the LDAP server connection and the mapping of partner IDs to customer IDs with the help of a graphical interface. The administration of those connections can also be managed in a separate dashboard.

Benefits
   - Specific allocation of access permissions allows protection of your customer data.
   - Simplifies the collaboration with subsidiaries, subcontractors and partners.

Available in Service Package
   GOLD

Target Groups
   - International companies.
   - Call centers.
   - Companies offering a wide range of products.

.. note::

   Not compatible with the following feature add-ons:

   - :doc:`vip-customer` (when deployed with OTRS 3.2 and later versions)

.. Original content: https://otrs.com/otrs-feature/brute-force-attack-protection/

.. toctree::
   :maxdepth: 1
   :caption: Contents

   restrict-customer-data-view/admin
   restrict-customer-data-view/agent
   restrict-customer-data-view/external
