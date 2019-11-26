Administrator Interface
=======================

This package has no administrator interface. All data privacy protection rules must be added via the system configuration and executed by a console command.


System Configuration Settings
-----------------------------

For security reasons, this package does not come with any pre-configured rules. Therefore the functionality does not work out-of-the-box and the rules must be configured by an administrator first.

To add a rule configuration:

1. Go to the *System Configuration* screen of the administrator interface.
2. Select *OTRSDataPrivacyProtection* in the *Navigation* widget.
3. Navigate to *Core → OTRSDataPrivacyProtection* in the navigation tree.
4. Add a rule configuration in YAML format to setting ``OTRSDataPrivacyProtection::RuleConfiguration``.

The configuration of the individual rule sets are stored in YAML format and consists of the five options. The options marked with an asterisk are mandatory.

``RuleName`` \*
   This string option has to be unique for all rules. It is a string, that is used to identify every different rule. The rule name appears in all related outputs and history entries, but does not affect any functionality.

``RuleSource``
  This string option is just for informational usage. Different countries and regions have different types and kinds of data protection regulations, that might be part of laws and/or written papers. To identify the related original sources, the different configured rules are based on. ``RuleSource`` can be used to add names and/or descriptions, that will be added to related history entries (if available).

``RuleType`` \*
   This string option describes the action, that will be executed on all objects, that were found during a search. The following actions are supported (in short format or in long format):

   ``Anonymization`` or ``PrivacyByAnonymization``
      The anonymization rule type is used to anonymize data sets, as identified in the data classification fields. Anonymization means, that the different fields will be replaced by a string *Anonymized*.

      .. warning::

         During anonymizations, the original data sets are replaced by the mentioned string in the database. The original data is not saved and is therefore irretrievably lost!

   ``Pseudonymization`` or ``PrivacyByPseudonymization``
      Like the anonymization, the pseudonymization rule type is used to remove the related data from their original fields. There is a major difference to the ``Anonymization`` rule type, as the data will be stored in a separated database table, called ``data_pseudonymization``.

      This table is not used by any other sub-system, and it is not usable via the GUI. It acts as a backup table, that can be (manually) searched by any administrator, that has access to the database or using the *SQL Box* module of the administrator interface.

      During pseudonymizations, a universal unique identifier (UUID) will be created for the related data field, which is used to identify the original data later. The original data will then be copied to the backup table, using the UUID as the field identifier. Afterwards the original data will be replaced by just the UUID, which is effectively the same as an anonymization, but including a pointer to the stored original source data.

   ``Deletion`` or ``PrivacyByDeletion``
      The deletion rule type is used to delete data sets, as identified in the data classification fields. Deletion means, that the different fields will be replaced by a string *Deleted*. Technically the original data will be deleted, as it will be replaced with a non-sensitive string, it therefore works equal to the ``Anonymization`` rule type.

      .. warning::

         During deletions, the original data sets are replaced by the mentioned string in the database. The original data is not saved and is therefore irretrievably lost!

``DataClassification`` \*
   This list option is used to identify the data types for which the associated actions are to be applied. It contains the different fields of any data object as an array. Every object drivers provides a list of possible data classification fields, that might be used.

   .. seealso::

      The specific fields are described in the *Drivers* section below.

``ObjectFilter`` \*
   This list option implements the search and filter criteria for every used driver. Every driver provides a list of possible search and filter options, that are allowed to be used.

   .. seealso::

      Please see the *Drivers* section below for more detailed information.

The different types of information represented by objects (e.g. ticket, customer user, etc.) are called *object types* within this package. Therefore we are talking about *object types*.

The modules implemented for the specific data processing, search functions and verification of such specific object types are called *drivers* or *driver objects*.


Rule Execution
--------------

Once the rules have been defined, they can be applied to the existing data sets. There is a console command ``Maint::DataPrivacy::Execute`` for this.

Execute the console command with the ``--help`` option for more information:

.. code-block:: bash

   otrs> /opt/otrs/bin/otrs.Console.pl Maint::DataPrivacy::Execute --help

This command essentially offers three different options:

- Checking the integrity and validity of the existing rules.
- Test execution of existing rules without changing data records.
- Execution of the existing rules, whereby the matching data sets are permanently changed.

The validation checks all available rules in the context of the affected drivers and object types. If certain options are missing or incorrect, the rule is declared invalid and execution is skipped for all drivers.

For security reasons, the validity of the corresponding rules is implicitly checked both before each dry run and before each execution and is either completely stopped or skipped in case of errors.

.. warning::

   We recommend, that new rules or significant changes should be executed on test systems first to ensure that no data is accidentally changed or deleted.

.. warning::

   We recommend that you back up the database first to ensure that untested data is not lost after rules or rule changes are executed.

.. warning::

   Since rules are designed to change or completely delete data, it is very important to carefully check all rules in advance and execute the test runs for each rule change.

The console output of rule executions can be redirected into files to preserve the modified objects. Please see the following example:

.. code-block:: bash

   otrs> /opt/otrs/bin/otrs.Console.pl Maint::DataPrivacy::Execute --execute-detail > rule-execution.txt


Drivers
-------

This section describe the configuration and usage of the various drivers. In addition, this section contains sample configurations that can be copied and customized to your personal needs.


Customer Company Driver
~~~~~~~~~~~~~~~~~~~~~~~

The customer company driver provides the functionality to search and modify the information for customer companies.

Possible data classifications:

.. code-block:: none

   - CustomerID
   - CustomerCompanyName
   - CustomerCompanyCountry
   - CustomerCompanyStreet
   - CustomerCompanyZIP
   - CustomerCompanyCity
   - CustomerCompanyURL
   - CustomerCompanyComment
   - DynamicField_NameX

The driver supports dynamic fields for data classification. Dynamic fields will be identified by the prefix ``DynamicField_`` and the related field name.

Possible object filters:

.. code-block:: none

   - ValidID
   - CustomerID
   - CustomerCompanyStreet
   - CustomerCompanyURL
   - CustomerCompanyComment
   - WildcardSearch
   - CustomerCompanyZIP
   - CustomerCompanyCountry
   - CustomerCompanyName
   - CustomerCompanyCity

Object filter descriptions:

- ``Limit``: Limits the number of search results.
- ``CreateTime``: Searches for dates *greater than or equal to* (>=) the given time.
- ``WildcardSearch``: Affects all object filters, except ``ValidID``.


Rule Configuration Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are some examples for rule configurations. These examples are valid YAML codes. You can copy these examples and modify them according to your needs.

Delete customer company name and customer company country by customer company name without wildcard search:

.. code-block:: yaml

   ---
   RuleName: Delete customer company name and customer company country by customer company name without wildcard search.
   RuleType: PrivacyByDeletion
   RuleSource: GDPR
   DataClassification:
     CustomerCompany:
       - CustomerCompanyName
       - CustomerCompanyCountry
   ObjectFilter:
     CustomerCompany:
       CustomerCompanyName: someCompanyName
       WildcardSearch: 0

Delete customer company name and customer company country by customer company name with wildcard search:

.. code-block:: yaml

   ---
   RuleName: Delete customer company name and customer company country by customer company name with wildcard search.
   RuleSource: someRuleSource
   RuleType: PrivacyByDeletion
   DataClassification:
     CustomerCompany:
       - CustomerCompanyName
       - CustomerCompanyCountry
   ObjectFilter:
     CustomerCompany:
       CustomerCompanyName: someCompanyName
       WildcardSearch: 1


Customer User Driver
~~~~~~~~~~~~~~~~~~~~

The customer user driver provides the functionality to search and modify the information for customer users.

Possible data classifications:

.. code-block:: none

   - UserTitle
   - UserFirstname
   - UserLastname
   - UserEmail
   - UserLogin
   - UserComment
   - UserCountry
   - UserFax
   - UserMobile
   - UserCity
   - UserPhone
   - UserTitle
   - UserStreet
   - UserZip
   - DynamicField_NameX

The driver supports dynamic fields for data classification. Dynamic fields will be identified by the prefix ``DynamicField_`` and the related field name.

Possible object filters:

.. code-block:: none

   - UserCity
   - UserTitle
   - UserFirstname
   - UserPhone
   - ValidID
   - UserCountry
   - UserLogin
   - UserCustomerID
   - UserLastname
   - UserZip
   - UserMobile
   - UserEmail
   - UserFax
   - WildcardSearch
   - UserStreet
   - UserComment

Object filter descriptions:

- ``Limit``: Limits the number of search results.
- ``CreateTime``: Searches for dates *greater than or equal to* (>=) the given time.
- ``Valid``: Searches for valid or invalid users. Possible values are 0 or 1.
- ``WildcardSearch``: Affects all object filters, except ``ValidID``.


Rule Configuration Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are some examples for rule configurations. These examples are valid YAML codes. You can copy these examples and modify them according to your needs.

Delete user first names and user last names by user first name with wildcard search:

.. code-block:: yaml

   ---
   RuleName: Delete user first names and user last names by user first name with wildcard search.
   RuleType: PrivacyByDeletion
   RuleSource: GDPR
   DataClassification:
     CustomerUser:
       - UserFirstname
       - UserLastname
   ObjectFilter:
     CustomerUser:
       UserFirstname: someFirstname
       WildcardSearch: 1

Anonymize user first names and user last names by user first name and without wildcard search:

.. code-block:: yaml

   ---
   RuleName: Anonymize user first names and user last names by user first name and without wildcard search.
   RuleSource: someRuleSource
   RuleType: PrivacyByAnonymization
   DataClassification:
     CustomerUser:
       - UserFirstname
       - UserLastname
   ObjectFilter:
     CustomerUser:
       UserFirstname: someFirstname
       WildcardSearch: 0

Delete user first names and user last names by user first name and user last name with wildcard search:

.. code-block:: yaml

   ---
   RuleName: Delete user first names and user last names by user first name and user last name with wildcard search.
   RuleSource: someRuleSource
   RuleType: PrivacyByDeletion
   DataClassification:
     CustomerUser:
       - UserFirstname
       - UserLastname
   ObjectFilter:
     CustomerUser:
       UserFirstname: someFirstname
       UserLastname: someLastname
       WildcardSearch: 1


Ticket Driver
~~~~~~~~~~~~~

The ticket driver provides the functionality to search and modify the information for tickets and related articles.

Possible data classifications for tickets:

.. code-block:: none

   - Title
   - CustomerUserID
   - CustomerID
   - DynamicField_NameX

Possible data classifications for articles:

.. code-block:: none

   - From
   - To
   - Cc
   - Subject
   - Body
   - Attachments
   - DynamicField_NameX

The driver supports dynamic fields for data classification. Dynamic fields will be identified by the prefix ``DynamicField_`` and the related field name.

The data classification supports history types. Since history types may vary (framework versions, framework updates, installed packages etc.), the driver will dynamically determine those types by name.

History types have to be prefixed with the term ``History``. Please see the examples in the following listing:

.. code-block:: none

   - HistoryAddNote
   - HistoryAddSMS
   - HistoryArchiveFlagUpdate
   - HistoryBounce
   - HistoryCustomerUpdate
   - HistoryEmailAgent
   - HistoryEmailCustomer
   - HistoryEmailResend
   - HistoryEscalationResponseTimeNotifyBefore
   - HistoryEscalationResponseTimeStart
   - HistoryEscalationResponseTimeStop
   - HistoryEscalationSolutionTimeNotifyBefore
   - HistoryEscalationSolutionTimeStart
   - HistoryEscalationSolutionTimeStop
   - HistoryEscalationUpdateTimeNotifyBefore
   - HistoryEscalationUpdateTimeStart
   - HistoryEscalationUpdateTimeStop
   - HistoryFollowUp
   - HistoryForward
   - HistoryLock
   - HistoryLoopProtection
   - HistoryMerged
   - HistoryMisc
   - HistoryMove
   - HistoryNewTicket
   - HistoryOwnerUpdate
   - HistoryPhoneCallAgent
   - HistoryPhoneCallCustomer
   - HistoryPriorityUpdate
   - HistoryRemove
   - HistoryResponsibleUpdate
   - HistorySendAgentNotification
   - HistorySendAnswer
   - HistorySendAutoFollowUp
   - HistorySendAutoReject
   - HistorySendAutoReply
   - HistorySendCustomerNotification
   - HistoryServiceUpdate
   - HistorySetPendingTime
   - HistorySLAUpdate
   - HistoryStateUpdate
   - HistorySubscribe
   - HistorySystemRequest
   - HistoryTicketDynamicFieldUpdate
   - HistoryTicketLinkAdd
   - HistoryTicketLinkDelete
   - HistoryTimeAccounting
   - HistoryTitleUpdate
   - HistoryTypeUpdate
   - HistoryUnlock
   - HistoryUnsubscribe
   - HistoryWebRequestCustomer

All contents of the classified history types will be affected during executions.

If attachments are classified, every attachment of all matching articles or tickets will be affected during executions.

.. warning::

   The ticket driver is used to search for tickets, even if the rule contains filters for article fields. If article fields are part of the data classification, all articles of the related, matching ticket will be processed!

The following fields can be used as search terms or filters for tickets and articles. Possible object filters:

.. code-block:: none

   - Limit
   - TicketID
   - TicketNumber
   - Title
   - Queues
   - QueueIDs
   - UseSubQueues
   - Types
   - TypeIDs
   - States
   - StateIDs
   - StateType
   - StateTypeIDs
   - Priorities
   - PriorityIDs
   - Services
   - ServiceIDs
   - SLAs
   - SLAIDs
   - Locks
   - LockIDs
   - OwnerIDs
   - ResponsibleIDs
   - WatchUserIDs
   - CustomerID
   - CustomerUserLogin
   - CreatedUserIDs
   - CreatedTypes
   - CreatedTypeIDs
   - CreatedPriorities
   - CreatedPriorityIDs
   - CreatedStates
   - CreatedStateIDs
   - CreatedQueues
   - CreatedQueueIDs
   - TicketFlag
   - ArticleFlag
   - MIMEBase_From
   - MIMEBase_To
   - MIMEBase_Cc
   - MIMEBase_Subject
   - MIMEBase_Body
   - AttachmentName
   - FullTextIndex
   - ContentSearch
   - ContentSearchPrefix
   - ContentSearchSuffix
   - ConditionInline
   - ArticleCreateTimeOlderMinutes
   - ArticleCreateTimeNewerMinutes
   - ArticleCreateTimeNewerDate
   - ArticleCreateTimeOlderDate
   - TicketCreateTimeOlderMinutes
   - TicketCreateTimeNewerMinutes
   - TicketCreateTimeNewerDate
   - TicketCreateTimeOlderDate
   - TicketChangeTimeOlderMinutes
   - TicketChangeTimeNewerMinutes
   - TicketLastChangeTimeOlderMinutes
   - TicketLastChangeTimeNewerMinutes
   - TicketLastChangeTimeNewerDate
   - TicketLastChangeTimeOlderDate
   - TicketChangeTimeNewerDate
   - TicketChangeTimeOlderDate
   - TicketCloseTimeOlderMinutes
   - TicketCloseTimeNewerMinutes
   - TicketCloseTimeNewerDate
   - TicketCloseTimeOlderDate
   - TicketPendingTimeOlderMinutes
   - TicketPendingTimeNewerMinutes
   - TicketPendingTimeNewerDate
   - TicketPendingTimeOlderDate
   - TicketEscalationTimeOlderMinutes
   - TicketEscalationTimeNewerMinutes
   - TicketEscalationTimeNewerDate
   - TicketEscalationTimeOlderDate
   - TicketEscalationUpdateTimeOlderMinutes
   - TicketEscalationUpdateTimeNewerMinutes
   - TicketEscalationUpdateTimeNewerDate
   - TicketEscalationUpdateTimeOlderDate
   - TicketEscalationResponseTimeOlderMinutes
   - TicketEscalationResponseTimeNewerMinutes
   - TicketEscalationResponseTimeNewerDate
   - TicketEscalationResponseTimeOlderDate
   - TicketEscalationSolutionTimeOlderMinutes
   - TicketEscalationSolutionTimeNewerMinutes
   - TicketEscalationSolutionTimeNewerDate
   - TicketEscalationSolutionTimeOlderDate
   - ArchiveFlags

All possible object filter parameters can be used to filter tickets and articles. Most of the attributes can be single strings or array references, like:

.. code-block:: yaml

   TicketNumber: 123546
   TicketNumber:
     - 123546
     - 123666

.. code-block:: yaml

   Title: SomeText
   Title:
     - SomeTest1
     - SomeTest2

.. code-block:: yaml

   States:
     - new
     - open
   StateIDs:
     - 3
     - 4

The corresponding YAML code could look as follows:

.. code-block:: yaml

   RuleName: My Explanation Rule
   RuleType: PrivacyByDeletion
   RuleSource: GDPR
   DataClassification:
     Ticket:
       - CustomerUserID
       - CustomerID
   ObjectFilter:
     Ticket:
       Queue:
         - Junk
         - Raw
       Services:
         - Service A
         - Service B

This rule would find all tickets, that are located in the queue *Junk* or *Raw* and which have the service *Service A* or *Service B* assigned. The fields ``CustomerUserID`` and ``CustomerID`` would be deleted.

There are several possible filter parameters, regarding relative times and dates, like:

.. code-block:: none

   - ArticleCreateTimeOlderMinutes
   - ArticleCreateTimeNewerMinutes
   - ArticleCreateTimeNewerDate
   - ArticleCreateTimeOlderDate

A filter like ``*\*TimeOlderMinutes*`` means *older than X minutes*.

The following statement would mean: all tickets, that have a ``CreateTime`` older than one day (1440 minutes).

.. code-block:: yaml

   TicketCreateTimeOlderMinutes: 1440

The following statement would mean: all tickets, that have a ``CreateTime`` newer than one day (1440 minutes).

.. code-block:: yaml

   TicketCreateTimeNewerMinutes: 1440

This is principal valid for all filter parameters with this syntax.

For more descriptions about the single search parameters, check the `TicketSearch() in API reference <https://doc.otrs.com/doc/api/otrs/7.0/Perl/Kernel/System/Ticket/TicketSearch.pm.html>`__.


Rule Configuration Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are some examples for rule configurations. These examples are valid YAML codes. You can copy these examples and modify them according to your needs.

Delete ticket titles by state names, that are older than one month:

.. code-block:: yaml

   ---
   RuleName: Delete ticket titles by state names, that are older than one month.
   RuleSource: GDPR
   RuleType: deletion
   DataClassification:
     Ticket:
       - Title
   ObjectFilter:
     Ticket:
       State:
         - new
         - open
       TicketCreateTimeOlderMinutes: 43200

Delete article subject and body by state names, that are located in specific queues:

.. code-block:: yaml

   ---
   RuleName: Delete article subject and body by state names, that are located in specific queues.
   RuleSource: GDPR
   RuleType: deletion
   DataClassification:
     Ticket:
       - Subject
       - Body
   ObjectFilter:
     Ticket:
       State:
         - new
         - open
       Queues:
         - Postmaster
         - Misc

Pseudonymize customer user IDs for tickets, that are closed and archived:

.. code-block:: yaml

   ---
   RuleName: Pseudonymize customer user IDs for tickets, that are closed and archived.
   RuleSource: GDPR
   RuleType: PrivacyByPseudonymization
   DataClassification:
     Ticket:
       - CustomerUserID
   ObjectFilter:
     Ticket:
       StateType:
         - Closed
       ArchiveFlags:
         - y

Anonymize customer IDs and some dynamic fields, that are closed, have certain services and are located in specific queues:

.. code-block:: yaml

   ---
   RuleName: Anonymize Customer IDs and some dynamic fields, that are closed, have certain services and are located in specific queues.
   RuleSource: GDPR
   RuleType: PrivacyByAnonymization
   DataClassification:
     Ticket:
       - CustomerID
       - DynamicField_SensitiveNames
       - DynamicField_SensitiveLocations
   ObjectFilter:
     Ticket:
       StateType:
         - Closed
       Queue:
         - Special Queue A
         - Junk
       Services:
         - Sensitive Customer Service
         - VIP Customer Service


User Driver
~~~~~~~~~~~

The user driver provides the functionality to search and modify the information for users.

Possible data classifications:

.. code-block:: none

   - UserTitle
   - UserFirstname
   - UserLastname
   - UserEmail
   - UserMobile

Possible object filters:

.. code-block:: none

   - UserFirstname
   - UserLastname
   - UserLogin
   - UserTitle
   - CreateTime
   - Valid
   - Limit
   - UserPreferences
   - WildcardSearch

Object filter descriptions:

- ``Limit``: Limits the number of search results.
- ``CreateTime``: Searches for dates *greater than or equal to* (>=) the given time.
- ``Valid``: Searches for valid or invalid users. Possible values are 0 or 1.
- ``WildcardSearch``: Affects the object filters ``UserFirstname``, ``UserLastname``, ``UserLogin`` and ``UserTitle``.
- ``UserPreferences``: Array containing the user preferences like user email address as keys with certain search criteria as values (see YAML configuration examples).


Rule Configuration Examples
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are some examples for rule configurations. These examples are valid YAML codes. You can copy these examples and modify them according to your needs.

Delete user first names by user first name:

.. code-block:: yaml

   ---
   RuleName: Delete user first names by user first name.
   RuleSource: GDPR
   RuleType: PrivacyByDeletion
   DataClassification:
     User:
     - UserFirstname
   ObjectFilter:
     User:
       UserFirstname: someFirstname

Delete user first names and user last names by user email:

.. code-block:: yaml

   ---
   RuleName: Delete user first names and user last names by user email.
   RuleSource: GDPR
   RuleType: PrivacyByDeletion
   DataClassification:
     User:
     - UserFirstname
     - UserLastname
   ObjectFilter:
     User:
       UserPreferences:
         UserEmail: someMail@example.com

Delete user first names and user last names with wildcard search:

.. code-block:: yaml

   ---
   RuleName: Delete user first names and user last names with wildcard search.
   RuleSource: GDPR
   RuleType: PrivacyByDeletion
   DataClassification:
     User:
       - UserFirstname
       - UserLastname
   ObjectFilter:
     User:
       UserFirstname: someFirstname
       WildcardSearch: 1

Delete user first names by user first name and create time, which are greater than or equal with the specified date:

.. code-block:: yaml

   ---
   RuleName: Delete user first names by user first name and create time, which are greater than or equal with the specified date.
   RuleSource: GDPR
   RuleType: PrivacyByDeletion
   DataClassification:
     User:
       - UserFirstname
   ObjectFilter:
     User:
       CreateTime: 2019-01-01
       UserFirstname: someFirstname
