Administrator Interface
=======================

This package has no administrator interface.


Add Search Attribute
--------------------

It is possible to add additional search attribute to the search dialog.

To add a search attribute:

1. Go to *System Configuration* screen.
2. Select *OTRSCICustomSearch* in the *Navigation* widget.
3. Navigate to *Frontend → Agent → View → ConfigItemSearch* in the navigation tree.
4. Search for setting ``ITSMConfigItem::CustomSearchXMLFields`` and add new search attribute. The key is the value from the ``Key`` entry of the configuration item.

If the field is set to *0 - Disabled*, the search attribute will not be displayed in the search dialog.
