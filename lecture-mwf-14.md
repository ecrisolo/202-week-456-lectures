# Priority Queues

Okay, so we know what a queue is; it's like standing in line.

But... does everyone take their turn? No! We live in America, and
the fancy people get to go to the head of the line. In fact, the
fanciest people go straight to the front, and the medium-fancy
people are right behind them, and then there's the rest of us in
scum class.

A *priority* queue is a queue where every item has a fixed priority;
the next thing to come out of the queue is the thing with the highest
priority.

We assume that a queue has a mapping from elements to priority.

## The interface:

Functional:

```
add(q,elt) -> q
remove_highest_priority(q) -> (q,elt)
```

Imperative:

```
add(q,elt) -> None
remove_highest_priority(q) -> elt
```

## Implementing it

The goal is to come up with an implementation for this interface. 

How can we implement something like this? (Q)

- simple unordered list, always search for element with highest priority.

Is this a good implementation? Well, it works... what's wrong with it?

Yep, it's slow. Okay, let's talk more about this. What's the running time
of each of the operations? Well, inserting is constant time. What about
removing? Well, that takes O(n). How can we combine these measures
to see how we like the thing overall? Well, which are we likely to do
more often, insert or retrieve? (Q)

Interestingly, this question is not entirely dumb; if we use a functional
data structure, and pass it to eight different clients, each one might
remove the same element; there might be many removals for each insertion,
or there might be many insertions for each removal.

HOWEVER, this is rare. Typically (and *certainly*, for imperative
implementations), insertions and removals are matched 1-to-1. In this
case, we can consider the overall performance as a function of the number
of elements both-added-and-removed from the queue. So, what do we get
if we add O(1) and O(n) ?

That's right, it's O(n). (I think it might be worth reinforcing this intuition
with some explanation).

## Implementing it again

What about... a *sorted* list? This will be much better. Now, removal
can be constant time, assuming that we put the highest-priority elements
at the end of the list that we can remove from in constant time.

But... what about insertion? Oh dear. Insertion into a sorted list is
O(n). So in fact, the sorted list *isn't any better at all.*

--

Copyright (C) 2017, John Clements (clements@racket-lang.org)
