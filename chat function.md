states of message - guess, normal, system

**structure of message**
- uuid
- name 
- uid
- message
- type
- time
**Structure of player data**
- Name
- uid
- isguessed
- isdraw
**Structure of scores**
- uid 
- scores

-  So first the user will send the message that will contain their name, message.
- now when we will recieve the message at the backend we will construct a full block of message according the structure given above.
- well the main thing to discuss is "type" so we are going to set this type before storing the message in store. well if the message is equal to word then we will change the type to guess, if not then normal and if something else like word is close then system.
- when a player