Well i have to create rounds like 3 for now each round will run like 60 secs for now

when ever someone joins a room it will be created 

- for each round there will be a word
- a person who will draw 
- a state of a person when they will guess the word

Well the rounds will have two kind of data one is "game session scope" and other is "round scope" meaning a data will change after like a round and one will stay persistent for the span of game . now i am thinking actually three kind of data one is "game span " second is "round space" and the last is "room span". well the room span data is like "chat", "users in room".

for people in room
- socket io does keep track of who is in the room
- so we can know who joined who left.

for game 
- so a game will run infinitely until only one player is left in the room.
- So we can create condition that will check if there are atleast two players in the room or else disconnect everyone in the room.
- this condition will only run when a game is created not when players are just at the inviting phase or creating phase.
- we wil

for rounds
- So we can use a timeout for each round where

for chat
- divide people in two pools one is where not guess are and other where guessed are.
- we can just simply send a object where guessed value is true or false cause the one who hasn't guessed will still get the data even though they can't see it.
- So we should create a different end point for the different pools