#Conversation-Driven Development (CDD)#
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

**Play 1: Self Assessment**


Give this templet to each of the member to review and fill their individual scores, then calculate the avg score  
![a](https://user-images.githubusercontent.com/69692410/129474864-8a1ceebe-ac15-41cf-9246-6a6e431ee824.JPG)
the avg score is where your projects is right now!

now discuss the given below points with teammates for better understanding and training of your Bot
![b](https://user-images.githubusercontent.com/69692410/129474874-d30a85a7-938f-410f-95d8-6dcb20a9cccb.JPG)

Bringing users into the development process—early and often—is one of the cornerstones of conversation-driven development as it helps you build a representative data set. User testing doesn’t just measure how effective your design is; the process also generates messages, which can be annotated and turned into training data, helping you build your assistant at the same time.

If possible, you should recruit testers who reflect the demographics of your end user. The most important thing is that testers should not have first-hand knowledge of the assistant’s development because then they tend to subconsciously stick to the messages and conversation flows they know the assistant can handle.

Rasa X provides a simple chat interface, where one can test before one connects a messaging channel, the tester’s conversations are automatically saved for developer to analyze. One can run this play as often as one need to, while the assistant is in development.



**Play 2: Conduct a User Test**

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


**Play 3: Filter Conversations and Annotate Messages**

Materials:
Rasa X instance, running locally or on a server
A few conversations, collected in Rasa X. You can collect this data by running Play 2, or, if you’re already in production, by connecting your live assistant to Rasa X


People:
1-3 team members
Step 1: Filter conversations

Open Rasa X and navigate to the Conversations screen. First, we’ll apply a filter to omit very short conversations. Open the filter menu, select Other as the filter type, and set the Message length filter to 5. This helps us weed out conversations where the user opened the chat session and immediately closed it. (filtering for very short conversations can also be useful to diagnose low engagement)

Read through few conversations. Ask yourself:

    Did the assistant make any mistakes? What type of mistakes?
    Did the user’s sentiment seem positive or negative?
    Was there anything surprising about the way the user phrased their requests?
    Was the user able to complete their goal?

Step 2: Use tags to apply labels

In the right hand panel, click the Tags gear and select the option to create a new tag. For each conversation you read, consider which labels might help you categorize and evaluate the conversation. Here are a few ideas:

    Positive or negative sentiment
    NLU error
    Out-of-scope request ( or feature request)
    Goal completed

Apply one or more tags to the conversation. If you find individual messages that require further discussion, use the message flag feature to mark and share them.

Step 3: Search for significant conversations

Return to the filters on the Conversation screen and note that you can now filter by the tags you’ve created. Use the filters to search your conversations and consider which produce an interesting sample set.

As you read conversations, use the Mark as reviewed button to indicate you’ve read them.

Step 4: Annotate user messages

Navigate to the NLU Inbox. The NLU Inbox displays user messages that don’t match any training examples you already have in your NLU data. 

Use the sort dropdown to filter messages with low confidence to the top of the inbox. Working your way from lowest to highest confidence, correct the intent and entity labels if needed and mark the message Correct to add it to your training data. If you find messages you don’t want to add to your training data, e.g. spam them.

After annotating data, retrain and test your new model.

Step 5: Document what needs to be fixed

![d](https://user-images.githubusercontent.com/69692410/129484875-d77cede5-b8ac-4c8b-95b2-5db601f9b65e.JPG)

**Fix and Test**

**Play 4: Establish a Development and Testing Workflow**

Materials:
Rasa X instance, running on a server
Git repository for your assistant (Bitbucket, GitLab, GitHub, etc.)
CI/CD tool (Circle CI, Jenkins, Bitbucket, GitHub Actions, etc.)

When you run on a CI/CD server, these tests can tell you whether the changes you’ve made have resulted in better performance or introduced a new problem—before you deploy the new model to production.

Step 1: Connect version control

Establish the connection between your deployment and version control by using Integrated Version Control to connect Rasa X to your Git repository.

Step 2: Create a conversation test set
Navigate to the Conversations screen in your Rasa X dashboard. Locate a conversation your assistant handled well—one where your assistant gave the correct responses to the user’s requests. You want your conversation test set to reflect the kinds of conversations users typically have with your assistant or a conversation you want to make sure your assistant continues to handle well. 

Once you’ve located a successful conversation, click the Save test conversation button to automatically add the conversation to your test set. When you run the rasa test CLI command, the conversation test function checks the model’s prediction at each step, so you can be sure a conversation that worked in the past hasn’t broken.

Step 3: Set up a CI/CD build pipeline

Using the CI/CD tool of your choice, configure your build pipeline. You can deploy a Rasa assistant by following these basic steps:

    Start with a base image that supports Python 3.6 or 3.7
    Install Rasa Open Source and any dependencies needed by your custom actions
    Run data validation, to check for mistakes in training data
    Train the new model
    Run conversation tests
    Test the NLU model
    Deploy the new model

Step 4: Test the deployment

Trigger the deployment pipeline by making an update, eg by annotating a few user messages in the NLU inbox. After annotating a message, you’ll see the Integrated Version Control indicator turn orange; click it and push the changes to Git. 

Trigger your CI/CD pipeline by opening a pull request! Review the pull request as a team. Look through the test results produced by the CI run, and merge the pull request if the results check out.

![e](https://user-images.githubusercontent.com/69692410/129485162-d383c57c-8b37-4f4d-adf9-3c964955cafe.JPG)

**Track**

It could be the most important question conversational AI teams ask: is the assistant really helping users?

Teams typically look at two types of metrics to answer that question: direct measures and proxy measures.

In direct measures, teams can track the number of users and conversations the assistant handled, or the session length, or the average number of messages sent in a conversation.

Proxy measures of whether an assistant helped a user are just as important, one might track whether or not a customer contacts support a second time within 24 hours, or clicks a link or CTA, or rates a positive NPS score from an exit survey. 

**Play 5:Identify the Metrics that Matter**

Materials:
Post-it notes and markers for each member of the group
Whiteboard or large sheet of paper
Timer

Step 1: Brainstorm questions

Ask participants to write down questions about the assistant’s success rate on individual. Eg- whether a user would choose getting help from the assistant over other methods, the number of contacts deflected, or how many users complete their goal within a session.

Step 2: Rank the important questions

Collect all of the Post-it notes. The facilitator reads each note and places it on the whiteboard. Similar questions should be grouped together to track duplicates.
Rank the top 5 questions according to the number of duplicate “votes” and group discussion.

Step 3: Establish measurable answers

Move all question except the top 5 to an out-of-the-way area of the board. Ask participants to brainstorm measurable ways to answer each of the top 5 questions and write down each idea on its own Post-it. 


Step 4: Balance direct metrics with proxies

On your whiteboard divide the space into two halves: Direct Metrics (measured inside the assistant) and Proxy Metrics (measured outside the assistant). The facilitator collects all of the Post-its from Step 4 and reads the ideas out loud. They sort each idea into the appropriate section of the board.

When all ideas have been sorted, consider the balance of proxy to direct metrics. 

Step 5: Summarize your findings

Document the session by taking pictures of the board and summarizing the brainstorming session in a place where it can be accessed across the organization. 

![f](https://user-images.githubusercontent.com/69692410/129485668-bc12a8db-d998-480d-8c0b-49e924685a8a.JPG)

**SUMMARY**
**CDD Checklist**

*Share

    Conduct a user test with internal testers
    Conduct a user test with a focus group of real users

*Review

    Read conversations
    In Rasa X, use filters to surface important conversations
    Identify issues that need to be addressed
    Identify successful conversation that can be turned into training stories and tests

*Annotate

    Label user messages and add them to training data
    Convert successful conversations into training stories

*Fix

    Connect your assistant to version control
    Make updates to address issues uncovered during review 

*Test

    Establish a CI/CD pipeline
    Make automated tests part of your CI/CD process
    Institute a code review process

*Track

    Identify proxy metrics as well as top-level statistics to measure success
    Use tags to label when events occur in conversations

