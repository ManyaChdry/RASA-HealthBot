CDD is a set of activities and design principles that help conversational AI teams build AI assistants that really help users.

We can use conversation data to understand the user based on past interactions and even feed conversations back into the assistant as training data, allowing the assistant to learn and better recognize what users are saying over time.

This principle is one key idea behind conversation-driven development (CDD): that we can build better AI assistants when we listen to users and use what they say to guide our development.

We see exactly how each interaction went in the conversation data, these conversations can become training data that helps our model become better over the time.

The core idea of CDD is making full use of conversation data: conversations provide training data for your model and guide your development decisions by showing you what is and isn’t working about your assistant’s design. The other piece of CDD is rooted in engineering best practices.

These ideas can be incorporated into six steps that make up CDD:

*Share* - Test your prototype early in the development process with users from outside your development team.

*Review* - Read the conversations that users have with your assistant, instead of focusing entirely on top-level metrics.

*Annotate* - Convert the messages that users send to your assistant into training examples.

*Test* - Make testing an automated step, every time you deploy new changes.

*Track* - Measure meaningful metrics, so you can understand what’s working and not working.

*Fix* - Reduce failures over time by making adjustments based on analyzing your assistant’s interactions.

Rasa X was a tool developed that would make it simple to sift through conversation data and make it actionable. Rasa X layers on top of Rasa Open Source and provides a UI for reviewing conversation data and annotating user messages. It also includes features for testing your assistant and sharing it with other users before you go live.

As one practice CDD over time, one’ll reach a point where most of the messages users send will already be in the training data—and DIET (our NLU architecture) typically fits to training data messages with 100% accuracy. 
