# Claim-Check
The code in this repo is showcasing a Claim-Check integration pattern using a Logic App workflow.

# Problem
In a messaging-based architecture, there are scenarios where messages contain large payloads (such as images, sound files, or other binary data). Sending such large messages directly to the message bus is not recommended because it consumes more resources and bandwidth, or may simply not be possible because of constraints of the bus.

# Solution
*  Store the entire message payload in an external service (e.g., a database or Azure Blob Storage).
*  Instead of sending the full payload, we send a message to the bus that contains a reference to the payload.
*  Clients interested in processing that specific message can use the obtained reference to retrieve the payload from the external service if needed.
