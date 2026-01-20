In prefix sum we create or update our data as such that whenever we need result in certain range we can find it in one operation O(n). It is kind of similar to [[Sliding Window]] where we store result of a entire window.

For example if i wanted to find sum of certain range in a array like from 2th index to 5th index i need to do it one by one but with prefix i can just keep the range 2 to 5 and remove the rest of part.

### Things to know

- we store result of 