Agent Interface
===============

This package has no agent interface, but the dynamic field of type database can be added to many screens.


Searching and Saving Data Sets
------------------------------

After the created dynamic fields are activated in some screens (like *New Phone Ticket*, *New Email Ticket*) a new text field appears with the name, the dynamic field got in the configuration. In this field it is possible to input search terms and therefore execute a search over all configured database fields. Otherwise click on the *Detailed search* link and start a detailed search in which the fields to search in are selected explicitly. Wildcard character \* is allowed in every single field.

Independent of using the auto-completion or the detailed search, every single result can just selected ones. If an agent tries to select a value multiple times, a related warning message is displayed.


Auto-completion
~~~~~~~~~~~~~~~

Since search terms are typed in into the text field, a database search will be started over the configured columns and the result will displayed via an auto-completion below the text field. The more exact the search term is, the more exact will be the result (less result entries).

If the wished value will be displayed in the results, it can be selected via a mouse click or via the keyboard and therefore be added to the dynamic field results.

Via the link *Details* a popup screen can be accessed, which offers detailed information about the whole result row. This information includes the line headers and the data. This information can be used to get an overview about the rest (of the not configured) columns or to compare data. The added result entries can be removed via the minus button.


Detailed Search
~~~~~~~~~~~~~~~

The link *Detailed search* opens a new modal dialog to start a new database search. In this mask it is possible to select the fields to search on explicitly.

By default the first available field is activated, but it is also possible to remove available fields or add additional ones. Only activated and filled fields are considered for the search. Wildcard character \* is allowed in every single field.

The database search will be executed via the *Start search* button and the results will be tabular displayed. If the search was successful, the results will be listed and one of the entries can be selected via a mouse click. The value will be added to the list of saved values afterwards.
