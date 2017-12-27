# Why Algorithms Matter
 
There is another major factor that can affect the efficiency of our code: the proper selection of which algorithm to use.

An algorithm is simply a particular process for solving a problem.

# Ordered Arrays

It emerges that when inserting into an ordered array, we need to always conduct a search before the actual insertion to determine the correct spot for the insertion. That is one key difference (in terms of efficiency) between a standard array and an ordered array.

While insertion is less efficient by an ordered array than in a regular array, the ordered array has a secret superpower when it comes to the search operation.

## Searching an Ordered Array

Let’s see how linear search differs between a regular and ordered array.

Say that we have a regular array of [17, 3, 75, 202, 80]. If we were to search for the value 22—which happens to be nonexistent in our example—we would need to search each and every element because the 22 could potentially be anywhere in the array. The only time we could stop our search before we reach the array’s end is if we happen to find the value we’re looking for before we reach the end.

With an ordered array, however, we can stop a search early even if the value isn’t contained within the array. Let’s say we’re searching for a 22 within an ordered array of [3, 17, 75, 80, 202]. We can stop the search as soon as we reach the 75, since it’s impossible that the 22 is anywhere to the right of it.

**We’ve been assuming until now that the only way to search for a value within an ordered array is linear search. The truth, however, is that linear search is only one possible algorithm **—that is, it is one particular process for going about searching for a value. It is the process of searching each and every cell until we find the desired value. But it is not the only algorithm we can use to search for a value.