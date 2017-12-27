# Preface

Because of this, too many people shy away from these concepts, feeling that they’re simply not “smart” enough to understand them.

The truth, however, is that everything about data structures and algorithms boils down to common sense.

Once you understand these concepts, you will be equipped to write code that is efficient, fast, and elegant. You will be able to weigh the pros and cons of various code alternatives, and be able to make educated decisions as to which code is best for the given situation.

# Why Data Structures Matter

Data is a broad term that refers to all types of information, down to the most basic numbers and strings.

Data structures refer to how data is organized.

And if you’re building a program that needs to deal with lots of data, or a web app used by thousands of people simultaneously, the data structures you select may affect whether or not your software runs at all, or simply conks out because it can’t handle the load.

# The Array: The Foundational Data Structure

We assume that you have worked with arrays before, so you are aware that an array is simply a list of data elements. The array is versatile, and can serve as a useful tool in many different situations.

`array = ["apples", "bannanas", "cucumbers", "dates", "elderberries"]`

The index of an array is the number that identifies where a piece of data lives inside the array.

--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------
    index 0         index 1         index 2         index 3     index 4

To understand the performance of a data structure—such as the array—we need to analyze the common ways that our code might interact with that data structure.

Most data structures are used in four basic ways, referred as **operations**.

- **Read**. Reading refers to looking something up from a particular spot within the data structure. With an array, this would mean looking up a value at a particular index.

- **Search**. Searching refers to looking for a particular value within a data structure. With an array, this would mean looking to see if a particular value exists within the array, and if so, which index it’s at.

- **Insert**. Insertion refers to adding another value to our data structure. With an array, this would mean adding a new value to an additional slot within the array.

- **Delete**. Deletion refers to removing a value from our data structure. With an array, this would mean removing one of the values from the array.

We’ll analyze **how fast** each of these operations are when applied to an array.

And this brings us to the first Earth-shattering concept of this book: when we measure how “fast” an operation takes, we do not refer to how fast the operation takes in terms of pure time, but instead in **how many steps it takes**.

We can never say with definitiveness that any operation takes, say, five seconds. Measuring the speed of an operation in terms of time is flaky, since it will always change depending on the hardware that it is run on.

However, we can measure the speed of an operation in terms of how many steps it takes. If Operation A takes five steps, and Operation B takes 500 steps, we can assume that Operation A will always be faster than Operation B on all pieces of hardware. Measuring the number of steps is therefore the key to analyzing the speed of an operation.

Measuring the speed of an operation is also known as measuring its **time complexity**. Throughout this book, we’ll use the terms speed, time complexity, efficiency, and performance interchangeably.

## Reading

Looking up what value is contained at a particular index inside the array.

Reading from an array actually takes just one step. This is because the computer has the ability to jump to any particular index in the array and peer inside. In our example of `["apples", "bananas", "cucumbers", "dates", "elderberries"]`, if we looked up index 2, the computer would jump right to index 2 and report that it contains the value "cucumbers".

**How is the computer able to look up an array’s index in just one step?**

A computer's memory can be viewed as a gian collection of cells. The following diagram is a good representation of this.

--------------------------------------------------------------------------------
|       |  12   |       |       |       |       |       |   42  |       |      |--------------------------------------------------------------------------------
|       |       |  100  |       |       |       |       |       |       |      |--------------------------------------------------------------------------------
|       |       |       |       |       |       |   13  |       |       |      |--------------------------------------------------------------------------------
|       |       |  90   |       |       |       |       |       |       |      |--------------------------------------------------------------------------------
|       |       |       |       |  "a"  |       |       |       |  "hi" |      |--------------------------------------------------------------------------------

When a program declares an array, it allocates a contiguous set of empty cells for use in the program.

So, if you were creating an array meant to hold five elements, your computer would find any group of five empty cells in a row and designate it to serve as your array.

Now, every cell in a computer’s memory has a specific address. It’s sort of like a street address (for example, 123 Main St.), except that it’s represented with a simple number. Each cell’s memory address is one number greater than the previous cell.

--------------------------------------------------------------------------------
| 1000  | 1001  | 1002  | 1003  | 1004  | 1005  | 1006  | 1007  | 1008  | 1009 |--------------------------------------------------------------------------------
| 1010  | 1011  | 1012  | 1013  | 1014  | 1015  | 1016  | 1017  | 1018  | 1019 |--------------------------------------------------------------------------------
| 1020  | 1021  | 1022  | 1023  | 1024  | 1025  | 1026  | 1027  | 1028  | 1029 |--------------------------------------------------------------------------------
| 1030  | 1031  | 1032  | 1033  | 1034  | 1035  | 1036  | 1037  | 1038  | 1039 |--------------------------------------------------------------------------------
| 1040  | 1041  | 1042  | 1043  | 1044  | 1045  | 1046  | 1047  | 1048  | 1049 |--------------------------------------------------------------------------------

So, there is a correspondence between memory address and index array:

--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------
    ma 1010         ma 1011         ma 1012         ma 1013     ma 1014
    index 0         index 1         index 2         index 3     index 4

When the computer reads a value at a particular index of an array, it can jump straight to that index in one step because of the combination of the following facts:

1. A computer can jump to any memory address in one step.
2. Recorded in each array is the memory address which it begins at. So the computer has this starting address readily.
3. Every array begins at index 0.

Reading from an array is, therefore, a very efficient operation, since it takes just one step. An operation with just one step is naturally the fastest type of operation. One of the reasons that the array is such a powerful data structure is that we can look up the value at any index with such speed.

## Searching

As we stated previously, searching an array is looking to see whether a particular value exists within an array and if so, which index it’s located at.

When you and I look at the shopping list, our eyes immediately spot the "dates" and we can quickly count in our heads that it’s at index 3. However, a computer doesn’t have eyes, and needs to make its way through the array step by step.

To search for a value within an array, the computer starts at index 0, checks the value, and if it doesn’t find what it’s looking for, moves on to the next index. It does this until it finds the value it’s seeking.

With our example if the computer is searching for "dates" the operations would be as follows.


1. Checks index 0

        ˅
--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------

Since the value at index 0 is "apples" and not the "dates", the computer moves on the next index.

2. Checks index 1

                        ˅
--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------

Since the value at index 1 is "bannanas" and not the "dates", the computer moves on the next index.

3. Checks index 2

                                        ˅
--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------

Since the value at index 2 is "cucumbers" and not the "dates", the computer moves on the next index.

3. Checks index 3

                                                       ˅
--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elderberries" |
--------------------------------------------------------------------------------

Since the value at index 3 is "dates", the computer does not need to move on the next cell.

In this example, since we had to check four different cells until we found the value we were searching for, we’d say that this particular operation took a total of four steps.

This kind of search is called **linear search**.

**Now, what is the maximum number of steps a computer would need to conduct a linear search on an array?**

So it turns out that for an array of five cells, the maximum number of steps that linear search would take is five. For an array of 500 cells, the maximum number of steps that linear search would take is 500.

Another way of saying this is that for N cells in an array, linear search will take a maximum of N steps. In this context, N is just a variable that can be replaced by any number.

In any case, it’s clear that searching is less efficient than reading.


## Inserting

The efficiency of inserting a new piece of data inside an array depends on where inside the array you’d like to insert it.

Let’s say we wanted to add "figs" to the very end of our shopping list. Such an insertion takes just one step. As we’ve seen earlier, the computer knows which memory address the array begins at. Now, the computer also knows how many elements the array currently contains, so it can calculate which memory address it needs to add the new element to, and can do so in one step.

Inserting a new piece of data at the beginning or the middle of an array, however, is a different story. We need to create a next cell in memory and use it for placing the last element in there, repeating the operation until the right cell is free for the new element.

--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |   "elder" |      |
--------------------------------------------------------------------------------
                                                                ↓           ↑
                                                                →→→→→→→→→→→→→


--------------------------------------------------------------------------------
|   "apples"    |   "bannanas"  |   "cucumbers" |   "dates" |       | "elder"  |
--------------------------------------------------------------------------------
                                                    ↓           ↑
                                                    →→→→→→→→→→→→→

... N + 1


For example, let’s say we wanted to add "figs" to index 2 within the array. To do this, we need to move "cucumbers", "dates", and "elderberries" to the right to make room for the "figs". But even this takes multiple steps, since we need to first move "elderberries" one cell to the right to make room to move "dates". We then need to move "dates" to make room for the "cucumbers".

The worst-case scenario for insertion into an array—that is, the scenario in which insertion takes the most steps—is where we insert data at the beginning of the array.

So we can say that insertion in a **worst-case scenario can take up to N + 1 steps for an array containing N elements**. This is because the worst-case scenario is inserting a value into the beginning of the array in which there are N shifts (every data element of the array) and one insertion.


## Deleting

The final operation we’ll explore—deletion—is like insertion, but in reverse.

Deletion from an array is the process of eliminating the value at a particular index.

Like insertion, the worst-case scenario of deleting an element is deleting the very first element of the array. This is because index 0 would be empty, which is not allowed for arrays, and we’d have to shift all the remaining elements to the left to fill the gap.

Now that we’ve learned how to analyze the time complexity of a data structure, we can discover how different data structures have different efficiencies. This is extremely important, since choosing the correct data structure for your program can have serious ramifications as to how performant your code will be.

The next data structure—the set—is so similar to the array that at first glance it seems that they’re basically the same thing. However, we’ll see that the operations performed on arrays and sets have different efficiencies.


# Sets: How a Single Rule Can Affect Efficiency

A set is a data structure that does not allow duplicate values to be contained within it.

There are actually different types of sets, but for this discussion, we’ll talk about an array-based set. This set is just like an array—it is a simple list of values. The only difference between this set and a classic array is that the set never allows duplicate values to be inserted into it.

Sets are useful when you need to ensure that you don’t have duplicate data.

In any case, a set is an array with one simple constraint of not allowing duplicates. Yet, this constraint actually causes the set to have a different efficiency for one of the four primary operations.

- Reading from a set is exactly the same as reading from an array.

- Searching a set also turns out to be no different than searching an array—it takes up to N steps to search to see if a value exists within a set.

- Insertion, however, is where arrays and sets diverge. With a set, however, the computer first needs to determine that this value doesn’t already exist in this set—because that’s what sets do: they prevent duplicate data. So every insert first requires a search. 2N + 1

# Wrapping up

Analyzing the number of steps that an operation takes is the heart of understanding the performance of data structures.

Now that we’ve begun to learn how to think about the time complexity of data structures, we can also use the same analysis to compare competing algorithms (even within the same data structure) to ensure the ultimate speed and performance of our code.









