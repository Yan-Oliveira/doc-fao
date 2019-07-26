Agent Interface
===============

This package has no agent interface, but it extends the standard behavior of the queue selection method. The service based queue routing affects the ticket creation screens and the *Ticket Move* screen. For this, the given service of the selected ticket will be used.

After selecting a service, there is a lookup for configured queues for this service. If there are configured queues for the selected service, only those will be available in the queue selection. If there are no queues configured for the selected service, all queues will be displayed.

It is possible to add a *Get All* button next to the queue selection in the agent and/or external interface. After clicking this button all available queues get restored to the queue selection field and can be selected.

Configured ACLs affect the displayed queues as usual.
