So these are like maps or array of user id. If a userid is in the room then we know that it exists in this room.

Well socket io rooms are temporary or will only exist until there is a user in the room.  If we want to persist we can store all the metadata of the room in database and when we need that room again socket io will create will create a room again with same roomid as before and we 