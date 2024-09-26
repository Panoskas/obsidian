# Collections

## Tuples
my_tuple = (1,2 'boat', 'car')
- Immutable
- ordered
- iterable(constant time)
#### Useful commands
- my_tuple[0]
- len(my_tubple)
- .count()
	- use count() to count the number of occurrences of an element of the tuple
- .index()
	- use index() to find the index of 'boat'

## Lists
my_list = [1, 2, 'boat', 'car']
- Mutable
- Ordered
- Iterable (linear time)
#### Useful commands
.append() and .insert()
	insert() takes as first argument the index and as second the value
.pop() and .remove()
.reverse() and .sort()
	you can use sort if the elements of the list are the same type 

## Dictionaries
my_dict = {
"num_cupcakes": 5,
"my_name": "George"
}
- key value pairs
- mutable 
- iterable (constant time)
- ordered by time of insertion
#### Useful commands
my_dict['some_key']
.keys() , .values(), .items
my_dict.pop('some_key') , del my_dict['some_key']

## Sets
my_set = {5, 6, 'cupcakes', 'frosting'}
- Mutable
- Unordered (cant index)
- Iterable(constant time)
- Unique items not duplicates
#### Useful commands
1. add(): This method is used to add a single element to a set. If the element is already present in the set, it does not add it again.
```python
my_set = {1, 2, 3}
my_set.add(4)
print(my_set) # Output: {1, 2, 3, 4}
```

2. update(): This method is used to add multiple elements to a set. It can take multiple arguments, such as lists, tuples, or other sets.
```python
my_set = {1, 2, 3}
my_set.update([3, 4, 5])
print(my_set) # Output: {1, 2, 3, 4, 5}
```

3. remove(): This method is used to remove a specific element from the set. If the element is not present in the set, it raises a KeyError.
```python
my_set = {1, 2, 3}
my_set.remove(2)
print(my_set) # Output: {1, 3}
```

4. intersection(): This method returns a new set that contains only the common elements between two sets.
```python
set1 = {1, 2, 3, 4}
set2 = {2, 3, 5}
intersection_set = set1.intersection(set2)
print(intersection_set) # Output: {2, 3}
```

5. difference(): This method returns a new set that contains only the elements that are present in the first set but not in the second set.
```python
set1 = {1, 2, 3, 4}
set2 = {2, 3, 5}
difference_set = set1.difference(set2)
print(difference_set) # Output: {1, 4}
```


# Time Complexity
Describes the amount of time it takes to run an algorithm in worst-case scenario, compared to the length of the input
Sure, here's a list of time complexities in order from best to worst:

1.  O(1) - constant time complexity
2.  O(log n) - logarithmic time complexity
3.  O(n) - linear time complexity
4.  O(n log n) - linearithmic time complexity
5.  O(n^2) - quadratic time complexity
6.  O(n^c) - polynomial time complexity where c is a constant greater than 2
7.  O(c^n) - exponential time complexity where c is a constant greater than 1
8.  O(n!) - factorial time complexity

It's important to note that this is just a general order of time complexities from best to worst and that the actual running time of an algorithm will depend on a variety of factors, including the size of the input, the hardware being used, and the specific details of the algorithm itself. Additionally, there are many other factors to consider when choosing an algorithm, such as the ease of implementation and readability, not just its time complexity.

# Recursion
An elegant method of solving a problem when the solution depends on solutions to smaller occurences of the problem. Also means that a fucntion can call itself.
1. Divide a problem into subproblems.
	1. Must be the same type as the original
2. Solve these subproblems
3. Combine the results to sovle the original

**Parts of a Recursive Solution
1. Base case or degenerate case
	1. How i know when im done with recursing?
	2. Smallest slice of the problem is treated differenetly
2. Recursive case or progress
	1. Continue reducing the problem until reaching the base case

```sql
list[start:end:step]
```
# OOP
```python
class Dog:
	species = 'canie'

	def __init__(self,name):
		self.name = name
	def greed(self):
		print("hello there my name is ", self.name)
```

e.g.
```python
toby = dog('Toby')
toby.species --> class attribute
toby.name --> instance attribute
```

## Why objects are useful

- **Encapsulation**
The data and functions associated with an object are contained together within the project keeping the safe from outside iterference.

- **Inheritance**
Allows classes to be arranged in hierarhical order
e.g
Canine --> Dog --> Terrier
Canine --> Coyote
Canine --> Fox --> DesertFox

- **Polymorphism**
Several classes or subclasses having the same method names, but different implementations for  those methods 

- **Modularity**
OOP promotes a modular approach to software design, allowing developers to break down complex systems into smaller, more manageable pieces. This makes it easier to develop, maintain, and debug code.

- **Abstraction**
OOP allows developers to create abstract classes and interfaces that define a set of properties and methods that can be used by multiple classes. This promotes code reuse and helps to ensure that different parts of the system are compatible with each other.

# Linear Data Structures

- **Stacks**
1. LIFO
2. Add or remove items in constant time
3. Maintain items in the order they were added
**When to use Stack**
Use stack when u want to quick access to the most recent item and need to keep items in order

**Queues**
1. FIFO
2. Add items in constant time, remove items in linear time
3. Maintain items in the order they're added
**When to use Queue**
Use Queue when you want to process the items in the order in which they were aded

**Singly Linked List**
1. Made of series of connected nodes
2. Can only move forward though connected nodes
3. Adds and removes nodes before or after any key in the linked list
4. Maintains items in order, based on when or where you add nodes
**When to use Singly Linked List**
1. Unknown number of items to store
2. One-directional movement is OK
3. Need to insert items in between other items
4. Sequential access is ok

**Doubly Linked List**
1. Made of a series of connected nodes
2. Can only move forward and backward through the connected nodes 
3. Adds and removes nodes before or after any key in the linked list
4. Maintains items in order, based on when or where you add nodes
**When to use Doubly Linked List**
1. Unknown number of items to store
2. Need to insert items in between other items
3. Sequential access is ok (via ehter end
4. )

# NonLinear Data Structures

**Trees**
1. Simulates a hierarchical tree structure with a root node and zero or more subtrees
2. Parent, child and sibling nodes
**When to use tree**
Use tree when you need to store data hierarchically. Classic examples are a family tree and predator or prey diagram

**Binary search trees**
1. root node is roughly the midpoint
2. smalled nodes go to the left and larger nodes on the right
3. Tkes O(logn) comparisons to find a specific node
4. Worst case search is O(n)
**When to use binary search tree**
Use a binary search tree when you need to store hierarchical data in a way that is easily and quickly serachable

**Graph**
1. A finite set of nodes(points) connected by lines (edges)
2. The edges can optionally have values
**when to use a graph**
Use a graph when you need to store data in a wa that captures relationships between nodes. A classic graph example is social networks

**Hash maps**
1. Maps keys to values
2. A hash function converts the key to an index
3. This index is used to find they key's value
4. Search add delete O(1)
**when to use hash maps**
Use a hash map when you need to store data based on a key that can be used to retrieve the data later like python dictionaries
# Common sorting algorithms
**Insertion Sort**
1. Best used on shorter or almost-sorted lists
2. looks at one list element per iteration and grows a sorted output list by placing the element in its correct position 
3. Sorts in place so memory usage is low
4. Average runtime O(n^2)
![[Pasted image 20230316123947.png]]

**Mergesort**

1. Breaks a list down into individual elements; continually puts elements into sorted pairs until the list is reassembled in order
2. Memory usage is O(n)
3. Average runtime is O(nlogn)
![[Pasted image 20230316124136.png]]

**Quick Sort**
1. Comparison based, divide and conquer
2. Chooses a pivot in the list
3. Moves all elements that are smalled than the pivot to the left of the pivot and the elemets that are larger of the pivot to the right of the pivot
4. memory usage is low
5. average run time O(nlogn)
![[Pasted image 20230316124509.png]]

**
# Common searching algorithms

**Binary search**
1. Compares the target value to the middle element in *sorted list*
2. if they are not equal the half in whioch the target value cannot exist is eliminated
3. The midpoint search is performed recursively on the remaining half until the target value is found or not
4. Worst case O(logn)
![[Pasted image 20230316124904.png]]

**Breadth-First Search**
1. An algorithm for traversing trees and graphs
2. Starts at the root node and explores all sibling nodes before moving on to the next level of siblings
3. Worst case scenario O(|V| + |E|),  V= Vertices and E=Edges

![[Pasted image 20230316125208.png]]

**Depth-First Search**
1. Starts at the root node and explores as far down the path as possible until hitting the end, then backtracks to the node that was the most recent root node and explores back again
2. Worst case scenario O(|V| + |E|),  V= Vertices and E=Edges

![[Pasted image 20230316125601.png]]
