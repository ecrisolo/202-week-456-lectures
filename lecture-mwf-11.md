# finishing binary search trees (15 minutes)

Okay first, finish up whatever you need to for Binary search trees. In my case,
that's .. um ... search and insert and log-n behavior. Yikes.

# Iterators for traversals

Okay, iterators for traversals.

Well, there are actually a number of different pieces.

Let's talk about traversals, first.

A "traversal" is essentially an ordering on the nodes of a tree.

There are three basic traversals of binary trees;

- preorder: value, left-recursive-call, right-recursive-call
- inorder: left-recursive-call, value, right-recursive-call
- postorder: left-recursive-call, right-recursive-call, value

The other three implied by these? not so common.

If you have list append, writing these traversals (specifically, the traversal
that produces a list) is bog easy.

Follows the template perfectly, with one line taken from the text above.

## Iterators

Okay, so what's an iterator?

Basically, an iterator is an encapsulation of a *partially completed*
traversal.

Suppose you traverse part of a data structure, and then you want to
take a break for a little while. You're going to need to represent
the state of your traversal, so you can resume it later.

Let's start simple. What if you're iterating over a list? How
would you represent a partially completed traversal? (Q) Yep...
probably just using the rest of the list. That is, if you've
already visited the first six of nine elements, you can represent
the remainder of the traversal using the list containing the
remaining three.

What are the operations on an iterator? Basically, you'd like
to be able to resume the iteration. What that means is that you'd like to
get the next element from an iterator. ... aaaaand, here comes the
problem. I think this is the first time in the course I'm just
going to knuckle under and show you the standard mutable-value
representation of an iterator.

```python
# a ListIterator is ListIterator(NumList)
class ListIterator:
    def __init__(self, l):
    # ...

# ListIterator -> int
# return the next element of the iterator
# self-mutate to remove it
def next_element(i):
    if i.l == None:
        raise IndexError()
    else:
        f = i.l.first
        i.l = i.l.rest
        return f

# test case must test mutation:
i = ListIterator(Pair(3, Pair(5, None)))
self.assertEqual(next_element(i),3)
self.assertEqual(i,ListIterator(Pair(5, None)))
```

Things get more interesting with a binary list. Don't forget;
you can always pre-flatten it.

Want to do it on a binary tree directly? Use CPS or yield.




--

Copyright (C) 2017, John Clements (clements@racket-lang.org)
