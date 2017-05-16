# Queues

## big idea: Queues are basically just values standing in line.

## LIFO vs. FIFO

## enqueue / dequeue

Basic constant-time linked list implementation:

* A queue is Queue(AnyList, AnyList)
* ... where the first list represents the elements at the head of the tree,
* and the second list represents the reversed elements at the tail of the
* tree.

```python
class Queue:
    def __init__(self, early, late):
    # ...
```

Using this implementation gives you constant-time enqueue (just add to the
head of the second list), and amortized constant-time dequeue:

```python
# Queue -> (Element, Queue)
# return the first element from the queue, and the remainder of the queue
def dequeue(q):
    if (q.early == None):
        if (q.late == None):
            raise NoSuchElementException() # yeah okay that's java
        else:
            new_early = reverse(late)
            return (new_early.first, Queue(new_early.rest, None))
    else:
        return (q.early.first, Queue(q.early.rest, q.late))
```

That is: if the earlies are empty, just reverse the lates and use
them as the new earlies. 


--

Copyright (C) 2017, John Clements (clements@racket-lang.org)
