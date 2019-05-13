Example Usage
=============

This chapter describes how to add a first response time escalation.


Creating the Escalation Type
----------------------------

Go to the administration interface and choose *Escalation Type*. Click on the *Create New Escalation Type* button.

Fill in the needed fields. After submitting the form, you will be redirected to the edit screen for the new escalation type. You will see the *Start* tab for the new escalation type. Choose from the available conditions which one you want to be needed in order to start the escalation. Switch to another tab to set up more conditions.

In this example, we would enable the *The ticket has been created by a customer* setting and the *An agent message is not present*. Use the drop-down menu in order to choose whether or not an agent message has to be present.

Switch to the *Stop* tab in order to set up the escalation stop conditions. In this case, the escalation should be stopped if an agent sends a message, so we enable the *An agent sent a message* setting.


Creating the Escalation Type Bundle
-----------------------------------

Go to the administration interface and choose *Escalation Type Bundle*. Click on the *Create new escalation type bundle* button.

Fill in the needed fields. See the description on the previous pages in order to fill in *Execution order* correctly. After submitting the form, you will be redirected to the edit screen for the new bundle. You will now be able to add your previously created escalation type by choosing it from the *Add escalation type* drop-down menu. After you have added the escalation type, you can set up its parameters. Set up a time span (like *1*) and a time unit (like *Hour(s)*). Save the screen.

Assigning the New Bundle to an SLA
----------------------------------

In order to get the new escalation type to work, you need to assign it to an existing SLA. Call the SLA administration screen for an existing SLA and mark your bundle from the list of available bundles. Save the screen.


Conclusion
----------

The new escalation type in connection with the bundle and SLA assignment will cause new tickets which are being created by customers to escalate after one hour if no agent has responded.
