### Model Configurations
The configuration file defines the components and policies that our model will use to make predictions based on user input.  
The language and pipeline keys specify the components used by the model to make NLU predictions. The policies key defines the policies used by the model to predict the next action. 
 Components make up your NLU pipeline and work sequentially to process user input into structured output. There are components for entity extraction, for intent classification, response selection, pre-processing, and more.

#### Pipeline: 
To enable our model to understand the intents and extract entities,  we have to build a model, It is done by defining a pipeline.    
Pipeline:  A sequence of processing steps, which are used to extract specific text features and train certain components which allow the model to learn the underlying patterns from the provided examples.
Pre-configured pipelines exsist, custom pipelines can be built too.   
They have pre trained data, which helps when we have lesser training data.  
As long as we leave the configuration commented out and don't specify any configuration for a key ourself, a default configuration will be suggested whenever you train a new model.
Examples of preconfigured pipelines:  RegexFeaturizer, DIETClassifier etc.   
❗Note: order matters!

#### Components: 
Components make up your NLU pipeline and work sequentially to process user input into structured output.  
Language Models: The following components load pre-trained models that are needed if we want to use pre-trained word vectors in our pipeline:  
(word vectors:  vectors of numbers that represent the meaning of a word)  
MitieNLP (outputs: nothing, requires nothing):  Initializes MITIE structures. Every MITIE component relies on this, hence this should be put at the beginning of every pipeline that uses any MITIE components. The MITIE library needs a language model file, that must be specified in the configuration.
SpacyNLP(outputs: nothing, requires nothing): Initializes spaCy structures. Every spaCy component relies on this, hence this should be put at the beginning of every pipeline that uses any spaCy components. You need to specify the language model to use. The name will be passed to spacy.load(name) . SpaCy’s trained pipelines can be installed as Python packages.  
(Neither used)

#### Tokenizers
Tokenizers split text into tokens.  
Tokenization allows us to use methods built for words such as: Named entity recognition, word vectors.  
WhitespaceTokenizer:   A Tokenizer using whitespaces as a separator. No requirements.  
Creates a token for every whitespace separated character sequence.  

Any character not in:  a-zA-Z0-9_#@&   will be substituted with whitespace before splitting on whitespace, if it’s in the beginning or end of the word. In addition, any character not in: a-zA-Z0-9_#@&.~:\/?[]()!$*+,;=- will be substituted with whitespace before splitting on whitespace if the character is not between numbers. Consider the following examples:  

"twenty{one" → "twenty", "one" ("{"` is not between numbers)  
"20{1" → "20{1" ("{"` is between numbers)     
"name@example.com" → "name@example.com"  
"10,000.1" → "10,000.1"  
"1 - 2" → "1","2"  

#### Featurizer
Part of NLP Pipeline that converts input into features.
Feature:  machine readable/ numerical representation , used as an input for ML model. 
Common types of features: 
Labels(entity): short text descriptions, represented numerically usually by a list of possible labels mapped with a no.
Word embedding/vectors :  Numeric vector(matrix) , that represents a word.
They can also approximate meaning (for example, words used frequently together are more similar to each other)

All featurizers can return two different kind of features: sequence features and sentence features. The sequence features are a matrix of size (number-of-tokens x feature-dimension) . The sentence features are represented by a matrix of size (1 x feature-dimension) 

These Features are often used as input to ML model.  

Note: check the documentations for using different featurizers, to know its output specifications. Using wrong pipeline components can lead to errors!


![image](https://user-images.githubusercontent.com/64036955/127670502-288a362c-cdba-4b70-a905-d4256d2a0c2c.png)


#### Intetnt Classifiers
Intent classifiers assign one of the intents defined in the domain file to incoming user messages.
DIETClassifier:  Dual Intent Entity Transformer (DIET) used for intent classification and entity extraction.  It outputs: entities, intent and intent_ranking .

#### Fallback Classifier: 
Classifies a message with the intent nlu_fallback if the NLU intent classification scores are ambiguous.  
               
 It outputs: entities, intent and intent_ranking . 
It requires intent and intent_ranking output from a previous intent classifier 

The FallbackClassifier classifies a user message with the intent nlu_fallback in case the previous intent classifier wasn’t able to classify an intent with a confidence greater or equal than the threshold of the FallbackClassifier.






### Policies
Assistant uses policies to decide which action to take at each step in a conversation.
There are machine-learning and rule-based policies that your assistant can use.
There are different policies to choose from, and you can include multiple policies in a single configuration.
Note:  If you don't know which policies to choose, leave out the policies key from your config.yml completely. If you do, the Suggested Config feature will provide default policies for you .
At every turn, each policy defined in your configuration will predict a next action with a certain confidence level.  The policy that predicts with the highest confidence decides the assistant's next action.
Policy priority:  In the case that two policies predict with equal confidence, the priority of the policies is considered. Rasa Open Source policies have default priorities that are set to ensure the expected outcome in the case of a tie.    
                
![image](https://user-images.githubusercontent.com/64036955/127669323-8408fc89-163a-426d-88bd-a55ed63a1a78.png)
If we have 2 policies with the same priority and they predict with the same confidence, the resulting action will be chosen randomly.
### Few policies used:  

**TED Policy**: The Transformer Embedding Dialogue (TED) Policy is a multi-task architecture for next action prediction and entity recognition.  
**Memoization Policy**:  The MemoizationPolicy remembers the stories from your training data. It checks if the current conversation matches the stories in your stories.yml file. If so, it will predict the next action from the matching stories of your training data with a confidence of 1.0. If no matching conversation is found, the policy predicts None with confidence 0.0.   
**Rule Policy**: The RulePolicy is a policy that handles conversation parts that follow a fixed behavior . It makes predictions based on any rules you have in your training data. 


