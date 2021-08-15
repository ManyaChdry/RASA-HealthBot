CDD is a set of activities and design principles that help conversational AI teams build AI assistants that really help users.

We can use conversation data to understand the user based on past interactions and even feed conversations back into the assistant as training data, allowing the assistant to learn and better recognize what users are saying over time.

This principle is one key idea behind *conversation-driven development* (CDD): that we can build better AI assistants when we listen to users and use what they say to guide our development.

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

Give this templet to each of the member to review and fill their individual scores, then calculate the avg score  
![a](https://user-images.githubusercontent.com/69692410/129474864-8a1ceebe-ac15-41cf-9246-6a6e431ee824.JPG)
the avg score is where your projects is right now!

now discuss the given below points with teammates for better understanding and training of your Bot
![b](https://user-images.githubusercontent.com/69692410/129474874-d30a85a7-938f-410f-95d8-6dcb20a9cccb.JPG)

Bringing users into the development process—early and often—is one of the cornerstones of conversation-driven development as it helps you build a representative data set. User testing doesn’t just measure how effective your design is; the process also generates messages, which can be annotated and turned into training data, helping you build your assistant at the same time.

If possible, you should recruit testers who reflect the demographics of your end user. The most important thing is that testers should not have first-hand knowledge of the assistant’s development because then they tend to subconsciously stick to the messages and conversation flows they know the assistant can handle.

Rasa X provides a simple chat interface, where one can test before one connects a messaging channel, the tester’s conversations are automatically saved for developer to analyze. One can run this play as often as one need to, while the assistant is in development.



2: Conduct a User Test

Materials:
Rasa X instance, running locally or on a server
Laptop or mobile phone for each tester

People:
3-10 testers
1 note taker
1 facilitator

Decide on a list of tasks you want the tester to complete. Provide enough contextual information for the tester to complete the tasks without leading the tester or influencing their behavior. Prepare a list of 10-15 questions you’d like to ask the user during the session.

Designate a note taker from your team to record observations during the session. 


Information your testers by providing background about your project and outlining what you’ll be doing during the test session - it’s important to convey that you’re testing the assistant, not them.

*Share a test link

If you’re running Rasa X locally, you’ll need to run ngrok to make your assistant available to your testers on their own computers.

Ask your testers to complete the tasks you’ve outlined and encourage them to describe their thought process out loud, especially if they find something frustrating or surprising.

*Interview your testers using the questions you prepared. 

Let your testers do most of the talking—you can follow up with statements such as, “and then what happened?” to encourage testers to keep going and open up.

As soon as the session has ended, reflect on what you’ve learned as a team while the session is still top of mind.
![c](https://user-images.githubusercontent.com/69692410/129477137-fcd1d7de-96b2-4c2c-9fd2-bd7fb03ef162.JPG)

With AI assistants, what users say is actually what they do. Software teams often have to infer and guess at user interactions by looking at heat maps or telemetry, but an assistant keeps a detailed record of every user interaction automatically, in its conversation data —you can see exactly how every user interaction went. 

Rasa X collects the conversations users have with your assistant and makes them accessible through a user interface. You can filter your conversations to surface interactions where a fallback action occurred, the channel the conversation came through, the length of the conversation, and more.


Play 3: Filter Conversations and Annotate Messages

Materials:
Rasa X instance, running locally or on a server
A few conversations, collected in Rasa X. You can collect this data by running Play 2, or, if you’re already in production, by connecting your live assistant to Rasa X


People:
1-3 team members
Step 1: Filter conversations

Open Rasa X and navigate to the Conversations screen. First, we’ll apply a filter to omit very short conversations. Open the filter menu, select Other as the filter type, and set the Message length filter to 5. This helps us weed out conversations where the user opened the chat session and immediately closed it. (filtering for very short conversations can also be useful to diagnose low engagement)
