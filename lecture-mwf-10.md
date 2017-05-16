# Finishing List ADTs (15 minutes)

operations, running time on linked list / array

* create empty list : O(1) / O(1)
* add to beginning : O(1) / O(n)
* add to end : O(n)* / O(n)*
* insert at location :  O(n) / O(n)
* remove : O(n) / O(n)
* append (catenate) : O(m) / O(n)

# Binary Search Trees (35 minutes)

(First look at binary trees, and log-n times.)

Efficient search. Can we do better than linear?

Library metaphor.

We want a structure that reflects this. Let's try
to formulate it.

```python
# A StrBST is one of
# - None
# - BSTNode(str, StrBST, StrBST) where strings in left are < value, strings in
#    right are not.
class BSTNode:
    def __init__(value, left, right):
    ## BPH
```



Draw self-reference arrows.

Write examples. Highlight the fact that many values are constrained by a
pair of constraints. That is, this is *not* legal:

BSTNode ("mmm", None, BSTNode("ppp",BSTNode("ccc",None,None),None))



All-important method: search. Follows the template!

Step 2:

```python
# StrBST str -> bool
# return true if the given string is in the tree
def search(tree, sought):
    pass
```

3: Write tests, be sure to include empty.

4: Write template. All pieces will be used.

5: refine template to finish function. In fact... ask
them to finish the function.

```python
# StrBST str -> bool
# return true if the given string is in the tree
def search(tree, sought):
    if (tree == None):
        return False
    else:
        if (sought < tree.value):
            return search(tree.left, sought)
        elif (sought > tree.value):
            return search(tree.right, sought)
        else:
            return True
```

Okay, here's the interesting part. What's the running
time of this? Well, what's the independent variable?
Depth of tree? Okay, can we express the running time
as a function of the depth of the tree? Sure. It's
linear.

What if the tree has different branches of different
sizes? Ooh, good one. In this case, we can think about
doing a bunch of searches, and computing the expected
value.

Ooh, this gets really fun, really fast; in order to
talk about expected value, we need a distribution
of search strings. I think we probably don't want to
go too far down this road.

I think we should probably just agree that the
expected search time is linear in the average
depth of the tree.

But... how deep *is* the tree?

It's going to depend on the number of elements in
the tree. It'll be faster on the names of the people
in this class than it will be on the titles of the
books in the library of congress.

So, suppose a tree contains a million elements.
How deep will the tree be?

Well, it depends. You can imagine trees like this:

(nice balanced tree)

or trees like this

(totally one-sided tree)

Which one do we like better? (Q) Balanced tree.

For now, let's assume that trees are nice and
balanced. We'll probably have to revisit this later.

So, if the tree is balanced, what will its depth be?

Examples of full trees with 1, 3, 7, 15... how big are
these trees? 2^n - 1. Can you prove it? Sure, by induction.

Skimming here: First, how many nodes are at each level?
2^n. By near-trivial induction.

Next, how many nodes are in the full tree? (2^(n+1) - 1).
By somewhat less trivial induction: T_1, check.
If T_n has has (2^(n+1) - 1) nodes, and 2^n nodes in the
bottom layer (by previous lemma), then T_(n+1)
= (2^(n+1) - 1) + 2^(n+1) = 2^(n+2) - 1, check.

Okay, so let's go the other way: how many layers does
a tree with m nodes have? Take log of both sides, get
log n. Wave hands about fractional values. 


Insertion: works just the same. Follow the template to
obtain (I'm just showing the final):

```python
# StrBST str -> StrBST
# insert the given string into the tree
def insert(t, newstr):
    if (t == None)
        return BSTNode(newstr, None, None)
    else:
        if (newstr < t.value):
            return BSTNode(t.value, insert(t.left, newstr), t.right)
        else:
            return BSTNode(t.value, t.left, insert(t.right, newstr))
```

Follows design recipe.

With mutation: very similar; each return becomes a mutate/return pair.

How much time does this take? Turns out to be the same: O(log(n))




--

Copyright (C) 2017, John Clements (clements@racket-lang.org)
