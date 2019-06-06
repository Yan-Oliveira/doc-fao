Administrator Interface
=======================

This package has no administrator interface, but it allows to add additional input fields for configuration item classes.


Additional Configuration Item Fields
------------------------------------

It is possible to add additional reference fields to refer to different data in OTRS, like to other configuration items, services and users.

To add the fields for configuration items:

1. Open the *Config Item* module of the *CMDB Settings* group in the administrator interface.
2. Select a configuration item class and click on the *Change class definition* button.
3. Add the new fields to the class definition.

The following sections describe the possible input fields.


``ReferenceCI`` Field
~~~~~~~~~~~~~~~~~~~~~

This field adds an input field with auto-completion feature to search for other configuration items in the configuration item dialog. The following example configuration is needed to insert this kind of field:

.. code-block:: yaml

   - Key: testci
     Name: Test CI
     Searchable: 1
     Input:
       Type: ReferenceCI
       Required: 0
       Reference:
         Name: Computer
         LinkType: AlternativeTo
         LinkDirection: Source
         ImportExportKey: Name

The following settings are available when adding or editing this resource. The fields marked with an asterisk are mandatory.

``Key`` \*
   Must be unique and only accept alphabetic and numeric characters. If this is changed, data will not be readable from old definitions.

``Name`` \*
    The label of the field in the form. Any type of characters can be entered to this field including uppercase letters and spaces.

   .. note::

      It is recommended to always use English words for names.

   .. seealso::

      Names can be translated into other languages with custom translation files. See the `Custom Translation File <http://doc.otrs.com/doc/manual/developer/7.0/en/content/how-it-works/translations.html#custom-translation-file>`__ chapter in the developer manual.

``Searchable``
   Defines whether the field is searchable or not. Possible values are *0* or *1*.

``Input`` \*
   Initiates the definition of the input field.

   ``Type`` \*
      Defines the type of the element. Must be placed indented as a logical block. The value is ``ReferenceCI`` in this case.

   ``Required``
      Defines whether the field is mandatory or not. Possible values are *0* or *1*.

   ``Reference``
      Initiates the definition of the reference field.

      ``Name``
         Defines the class of the configuration item which should be possible to search for.

      ``LinkType``
         Defines the type of the link which will be created if the value will be saved. Possible values are:

         - ``Normal``
         - ``ParentChild``
         - ``DependsOn``
         - ``AlternativeTo``
         - ``RelevantTo``
         - ``Includes``
         - ``ConnectedTo``

      ``LinkDirection``
         Defines the direction of the link. Possible values are ``Source`` and ``Target``.

      ``ImportExportKey``
         Defines the value for the identification of the referenced configuration item. Possible values are ``Name``, ``Number`` or a configured field key.

After a value is set for the input field the value will be used to set a link to the given configuration item. If there is already a value, then the old value will be unlinked. If the reference field in the class definition has been extended with the setting ``CountDefault``, several configuration items can also be linked.

For the export and import of this field the name and the configuration item number are used. If a configuration item is not found for the import, then it will imported 2 times to verify that the linked configuration item which is needed for the link is already imported.

Example export value: ``ConfigItemName1``.


``ReferenceService`` Field
~~~~~~~~~~~~~~~~~~~~~~~~~~

This field adds an input field with auto-completion feature to search for services in the configuration item dialog. The following example configuration is needed to insert this kind of field:

.. code-block:: yaml

   - Key: testservice
     Name: Test Service
     Searchable: 1
     Input:
       Type: ReferenceService
       Required: 0
       Reference:
         LinkType: AlternativeTo
         LinkDirection: Source

The following settings are available when adding or editing this resource. The fields marked with an asterisk are mandatory.

``Key`` \*
   Must be unique and only accept alphabetic and numeric characters. If this is changed, data will not be readable from old definitions.

``Name`` \*
    The label of the field in the form. Any type of characters can be entered to this field including uppercase letters and spaces.

   .. note::

      It is recommended to always use English words for names.

   .. seealso::

      Names can be translated into other languages with custom translation files. See the `Custom Translation File <http://doc.otrs.com/doc/manual/developer/7.0/en/content/how-it-works/translations.html#custom-translation-file>`__ chapter in the developer manual.

``Searchable``
   Defines whether the field is searchable or not. Possible values are *0* or *1*.

``Input`` \*
   Initiates the definition of the input field.

   ``Type`` \*
      Defines the type of the element. Must be placed indented as a logical block. The value is ``ReferenceService`` in this case.

   ``Required``
      Defines whether the field is mandatory or not. Possible values are *0* or *1*.

   ``Reference``
      Initiates the definition of the reference field.

      ``LinkType``
         Defines the type of the link which will be created if the value will be saved. Possible values are:

         - ``DependsOn``
         - ``AlternativeTo``
         - ``RelevantTo``
         - ``Includes``
         - ``ConnectedTo``

         Additional link types can be defined in the OTRS configuration.

      ``LinkDirection``
         Defines the direction of the link. Possible values are ``Source`` and ``Target``.

After a value is set for the input field the value will be used to set a link to the given configuration item. If there is already a value, then the old value will be unlinked. If the reference field in the class definition has been extended with the setting ``CountDefault``, several configuration items can also be linked.

For the export and import of this field the name of the service is used.

Example export value: *Service 1*.


``ReferenceUser`` Field
~~~~~~~~~~~~~~~~~~~~~~~

This field adds an input field with auto-completion feature to search for users in the configuration item dialog. The following example configuration is needed to insert this kind of field:

.. code-block:: yaml

   - Key: testuser
     Name: Test User
     Searchable: 1
     Input:
       Type: ReferenceUser
       Required: 0

The following settings are available when adding or editing this resource. The fields marked with an asterisk are mandatory.

``Key`` \*
   Must be unique and only accept alphabetic and numeric characters. If this is changed, data will not be readable from old definitions.

``Name`` \*
    The label of the field in the form. Any type of characters can be entered to this field including uppercase letters and spaces.

   .. note::

      It is recommended to always use English words for names.

   .. seealso::

      Names can be translated into other languages with custom translation files. See the `Custom Translation File <http://doc.otrs.com/doc/manual/developer/7.0/en/content/how-it-works/translations.html#custom-translation-file>`__ chapter in the developer manual.

``Searchable``
   Defines whether the field is searchable or not. Possible values are *0* or *1*.

``Input`` \*
   Initiates the definition of the input field.

   ``Type`` \*
      Defines the type of the element. Must be placed indented as a logical block. The value is ``ReferenceUser`` in this case.

   ``Required``
      Defines whether the field is mandatory or not. Possible values are *0* or *1*.

For the export and import of this field the login of the user is used.

Example export value: *root@localhost*.
