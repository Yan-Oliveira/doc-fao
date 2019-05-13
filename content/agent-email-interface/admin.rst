Administrator Interface
=======================

This package has no administrator interface.


System Configuration
--------------------

The agent interface address should be set to the same as in setting *Core → Email → NotificationSenderEmail*.

To check if the addresses are the same:

1. Go to *System Configuration* screen.
2. Select *OTRS* in the *Navigation* widget.
3. Navigate to *Core → Email* in the navigation tree and search for setting ``NotificationSenderEmail``.
4. Change the email address if needed, and remember it.
5. Select *OTRSAgentEmailInterface* in the *Navigation* widget.
6. Navigate to *Core → Email → PostMaster* in the navigation tree.
7. Change the value of key ``AgentInterfaceAddress`` to the same as set in step 3.
