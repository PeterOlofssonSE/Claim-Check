# Claim-Check
The code in this repo is showcasing a Claim-Check integration pattern using a Logic App workflow.

# Problem
In a messaging-based architecture, there are scenarios where messages contain large payloads (such as images, sound files, or other binary data). Sending such large messages directly to the message bus is not recommended because it consumes more resources and bandwidth, or may simply not be possible because of constraints of the bus.

# Solution
*  Store the entire message payload in an external service (e.g., a database or Azure Blob Storage).
*  Instead of sending the full payload, we send a message to the bus that contains a reference to the payload.
*  Clients interested in processing that specific message can use the obtained reference to retrieve the payload from the external service if needed.

# Benefits
*  Large messages can be processed without overwhelming the message bus or slowing down client applications.
*  Reduces costs, as storage is usually cheaper than the resource units used by the messaging platform.

# Trivia 
*  This pattern was originally described in the book “Enterprise Integration Patterns” by Gregor Hohpe and Bobby Woolf.

# Implementation
*  Store the message payload externally.
*  Send the reference (claim check) to the message bus.
*  When needed, retrieve the payload using the reference.

# Considerations
*  Delete message data after consumption if archiving isn’t necessary.
*  Implement logic to use this pattern only for messages exceeding the message bus’s data limit.
*  Use asynchronous deletion processes to minimize impact on throughput and performance.
