# Stacks

## Basic ideas of stacks.

Stacks? Really? Stacks are simple. Basically, a stack is a linked list,
viewed slightly differently.

First, let's see the standard interface of a linked list:

- None : the empty list
- Pair(Any, List) : create a new list with Any on the front. That is,
  add an element.
- l.first : return the first element of a non-empty list
- l.rest : return the rest of a non-empty list
- (l == None) : is this list empty?

Now: here's the idea behind a stack: a stack represents a list of things
to be remembered. You can add elements to the list ('push'), and take
them back off again ('pop'). This metaphor is perhaps most familiar in
our interrupt-driven society in situations where you stop doing one
thing in order to to another, with the intent of returning to the first
thing. Then you interrupt the second thing to do a third thing, and
so forth.

When you get about six levels deep, you call this "yak shaving."

Seriously. Look it up.

Are you ready to see the stack interface? Are you sure?

- First, we have creation. Create an empty list.
- Second, we can add an element to a list. we call this 'push'.
- Next, we can get the top element of the list: we call this 'pop'.
- Finally, we can ask whether the stack is empty. We call this 'is_empty'

Gosh, this looks familiar! What are the *differences* between this and
the linked list interface?

At it turns out, it depends.

It depends on whether you use the version of stacks with value mutation,
or whether you use the purely functional version.

If you use the purely functional version, the difference is almost nonexistent;
push returns a new stack, and pop returns two things: the first and the rest.
Basically, pop returns the values of both the first and the rest.

If you use the one with mutation, then things look slightly different; you need
a wrapper class to keep track of the value of the stack.

Basically, this is the same idea that we used for our iterator.

Why would you choose the one with mutation? Well, there's less code.
Value mutation creates hidden tangling links between different parts of
our code. This means that the value keeps track of itself, and we don't
need to keep track of it.

Why would you choose the one without value mutation? Well, you don't
have hidden tangling connecting the different parts of your code. Your
code is easier to debug.

So, it mostly comes down to this: pay early, with purely functional, or
pay later, with mutation. Up to you.

And that's stacks!

# write some code? draw some pictures?

--

Copyright (C) 2017, John Clements (clements@racket-lang.org)
