External Interface
==================

The login in the external interface counts the failed login attempts. If the configurable count of failed login attempts is reached, the customer user account is locked using the customer preferences within the OTRS database.

The login is not possible and the customer user will see the message: *Login failed! Your user name or password entered incorrectly.*

This mechanism works for customer users which are stored in the OTRS database itself or in a tethered LDAP server.
