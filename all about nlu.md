Rasa Open Source uses YAML as a unified and extendable way to manage all training data, including NLU data, stories and rules.  
You can split the training data over any number of YAML files, and each file can contain any combination of NLU data, stories, and rules.  
Each file can contain one or more keys with corresponding training data. One file can contain multiple keys, but each key can only appear once in a single file. The available keys are:
  
    version  
    nlu    
    stories  
    rules  
    
 We should specify the version key in all YAML training data files,  or by default, latest training data format specification supported by the version of Rasa Open Source we have installed.  
 __*Currently, the latest training data format specification for Rasa 2.x is 2.0.*__  
 
 ## NLU training data:
  NLU training data consists of example user utterances categorized by intent. Training examples can also include entities.  
  NLU training data is defined under the nlu key. Items that can be added under this key are:  
  
      - Training Examples
      - Synonyms
      - Regular expressions
      - Lookup Tables
      
      
  ### Training Examples:
  Training examples are grouped by **intent** and listed under the **examples** key.
  Example:  
            
            nlu: 
            - intent:  |
              exeamples: 
              - Hi there!
              - Hello
              - What's up
              
Note :  | is  (pipe) symbol.
In YAML, | identifies multi-line strings with preserved indentation. This helps to keep special symbols like ", ' and others still available in the training examples.   

Note : Retrieval intent: A special type of intent that can be divided into smaller sub-intents. the / symbol is reserved as a delimiter to separate retrieval intents from their associated response keys. Make sure not to use it in the name of your intents.  
For Example:  

          nlu:
          - intent: chitchat/ask_name
            examples: |
              - What is your name?
              - May I know your name?
              - What do people call you?
              - Do you have a name for yourself?

          - intent: chitchat/ask_weather
            examples: |
              - What's the weather like today?
              - Does it look sunny outside today?
              - Oh, do you mind checking the weather for me please?
              - I like sunny days in Berlin.

### Entities:  
Entities are structured pieces of information that can be extracted from a user's message.
Entities are annotated in training examples with the entity's name. In addition to the entity name, you can annotate an entity with synonyms, roles, or groups.  
**_Full syntax_**:   [<entity-text>]{"entity": "<entity name>", "role": "<role name>", "group": "<group name>", "value": "<entity synonym>"}  
  
  
### Synonyms:  
  Synonyms normalize your training data by mapping an extracted entity to a value other than the literal text extracted. 
  **_Format: _** 
    
           nlu:
          - synonym: credit
            examples: |
              - credit card account
              - credit account
Another way to specify synonyms:  
  
      nlu:
      - intent: check_balance
        examples: |
          - how much do I have on my [credit card account]{"entity": "account", "value": "credit"}
          - how much do I owe on my [credit account]{"entity": "account", "value": "credit"}  
  
  ### Regular Expressions:  
  We  can use regular expressions to improve intent classification and entity extraction using the **RegexFeaturizer** and **RegexEntityExtractor** components.
  (to be added)  
  
  
  ### Lookup Tables:  
  Lookup tables are lists of words used to generate **case-insensitive regular expression patterns**.  
  **Format:**  
  
       nlu:
       - lookup: banks
         examples: |
          - JPMC
          - Bank of America
  
  When we supply a lookup table in your training data, the contents of that table are combined into one large regular expression. This regex is used to check each training example to see if it contains matches for entries in the lookup table.   
  Note:   
  
  ![image](https://user-images.githubusercontent.com/64036955/122665266-d9553500-d1c3-11eb-8ebe-1d3c6d367796.png)

