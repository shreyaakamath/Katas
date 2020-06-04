Source: https://stepik.org/users/245386548/courses


# Introduction
## Time Complexity
There are three main notations to describe time complexity: Big-O ("Big-Oh"), Big-Ω ("Big-Omega"), and Big-ϴ ("Big-Theta"). Big-O notation provides an upper-bound on the number of operations performed, Big-Ω provides a lower-bound, and Big-ϴ provides both an upper-bound and a lower-bound. In other words, Big-ϴ implies both Big-O and Big-Ω. For our purposes, we will only consider Big-O notation because, in general, we only care about upper-bounds on our algorithms.

Note that, although this algorithm is O(n), it is also technically O(n²) and any other larger function of n, because technically, these are all functions that are upper-bounds on the function f(n) = 3n. However, when we describe algorithms, we always want to describe them using the tightest possible upper-bound.

### Infinite geometric series
As n tends to infinity, Sn will tend to 1. See proof here https://en.wikipedia.org/wiki/1/2_%2B_1/4_%2B_1/8_%2B_1/16_%2B_%E2%8B%AF -> it is  quite simple and you learnt this in high school

*<img src="https://lh6.googleusercontent.com/gsZhGXmvuUV4CB9L0dGjMHcy2ZnibAE8UU0Nqbw3bkYpAMub3jDWqvNniytq0kIbrR_SanXTmFK9n1e20tIPkQmXt6zuwNbUyVXdIYnHNLvAxLFyOnYabMIdkue2VGEQvnzotQkz" alt="img" style="zoom:50%;" />*

### Good vs Bad complexity

* "Constant Time" = O(1)
* "Logarithmic Time" = "Scales/Increases Logarithmically" = O(log n)
* "Polynomial Time" = "Scales/Increases Polynomially" = O(nk) (for any constant k)
* "Exponential Time" = "Scales/Increases Exponentially" = O(kⁿ) (for any constant k)
* "Factorial Time" = O(n!)

<img src="https://lh4.googleusercontent.com/XRsX8CxeukYOx_Ucj_52SKEeDWMbz78vkkTrileqNqDeqEGFNU2Uda4h5AxsWl5gqa2rXuG-oFXSGIcYnVmFYHiJ7fRDKLmeQWpuWKNkF0IuWMkFqpzwFcH4j4BM-OLeZ4Bq5ixM" alt="img" />

## Classification of Computational Problems 
### P 

Any computational problem that can be solved in polynomial time (or better, of course) is considered a member of P. In other words, given a computational problem, if there exists a polynomial time algorithm that solves the problem—where we would need to formally prove that the algorithm does indeed always provide an optimal solution to the problem—we would classify the problem as class P.

### NP 
* (Nondeterministic Polynomial time)  NP

* Any computational problem where, given a proposed answer to the problem, one can verify the answer for correctness in polynomial time is considered a member of NP.
* P is a subset of NP: if we can solve a problem in polynomial time, then we can certainly verify a proposed answer to the problem in polynomial time (we can just solve it in polynomial time and then compare the proposed answer to our answer).

### NP-Hard
* NP-Hard (Nondeterministic Polynomial-time hard)
* a problem can be considered NP-Hard if it is at least as hard as the hardest problems in NP. More precisely, a problem H is NP-Hard when every problem L in NP can be "reduced," or transformed, to problem H in polynomial time. 
* As a result, if someone were to find a polynomial-time algorithm to solve any NP-Hard problem, this would give polynomial-time algorithms for all problems in NP.

### NP-Complete
* simply the intersection between NP and NP-Hard. In other words, an NP-Hard problem is considered NP-Complete if it can be verified in polynomial time (i.e., it is also in NP).
* Example : boolean satisfiability problem 
* The "Boolean Satisfiability Problem" is the basis of modern encryption, and it asks the following question: "Given some arbitrary Boolean formula, does there exist a set of values for the variables in the formula such that the formula is satisfied?" For example, if we were given the Boolean formula x AND NOT y, does there exist a set of values for x and y that satisfies the formula? In this small example, we can see there does indeed a solution that satisfies this formula (x = TRUE and y = FALSE), but is there way of algorithmically determining if a solution exists for some arbitrary Boolean formula?

### P vs NP Problem

* What if, however, P wasn't just a subset of NP? What if P and NP were actually equal sets? This question of whether or not P equals NP is known as the "P vs. NP Problem," which is a major unsolved problem in the field of computer science.
* Informally, it asks whether every problem whose solution can be quickly verified by a computer can also be quickly solved by a computer.
  Thus, if there is no known algorithmic solution to a problem that can be verified in polynomial time, we can conclude that a solution must exist, and humans just have not found the solution yet.

<img src="https://lh4.googleusercontent.com/HJONXIMjUHm5lr3tTm7zseJPd-iyUgY0InET4pElJrOGwOmogxIvTgT6qYIY0FgdhwH-LNPA89eMePbRJxKg2zhx-ONOK3jxG2fMS6sD-zLFb_8d8C3RjUPdmhrWanIaG-0rKnp2" alt="img" />

## Randomness

* The method by which we generate true random numbers is by measuring some physical phenomenon that is expected to be random and then compensating for possible biases in the measurement process.
* Example sources of physical randomness include measuring atmospheric noise, thermal noise
  true random number generation is typically very slow.
  generator is said to be pseudo-random because it seems to be random for all intents and purposes, but given the seed, it's fully deterministic
* Merge both! We can take a pseudo-random number generator and seed it with a true random number! The result is a sequence of random numbers that can be generated quickly, but that changes upon each execution of our program.

## Bits Bytes
* A bit is the basic unit of information in computing and can have only one of two values. We typically represent these two values as either a 0 or a 1,
* A byte is a unit of digital information, and it is just a sequence of some number of bits. you can assume that a byte is specifically a sequence of 8 bits.  a byte is the smallest unit that can be stored. 1,2,3 not 1.5 
* ASCII, abbreviated from American Standard Code for Information Interchange, is a character-encoding scheme where each possible byte is mapped to a specific "symbol" (I say "symbol" in quotes because not all ASCII characters are meaningful to humans).
* with an unsigned datatype, all of the bits are used to represent magnitude of the number.In a signed datatype, one bit is reserved to represent the sign of the number (typically, 0 = positive and 1 = negative), and the remaining bits represent the magnitude of the number.
* Eg:  if a given signed datatype has a size of n bits, the smallest value it can hold is -2ⁿ⁻¹ (why is it not -(2ⁿ⁻¹ -1)) and the largest value it can hold is 2ⁿ⁻¹–1 

There are three main types of version control systems (VCSs): local, centralized, and distributed. 

# Basic Data Structures
## Arrays

* Because of this phenomenon of being able to find the memory address of any i-th element in constant time (and thus being able to access any i-th element in constant time), we say that arrays have random access. In other words, we can access any specific element we want very quickly: in O(1) time.
* Complexity: As can be seen, even though the best-case time complexity for insertion into an array is O(1) (which we saw in the previous step), the worst-case time complexity for insertion into an Array List is O(n) because we could potentially have to move all ﻿n element in the array (or as in the case of the previous step, we may have to allocate an entirely new array and copy all n elements into this new array).
* We will introduce an algorithm called Binary Search, which allows us to exploit random access in order to obtain a worst-case time complexity of O(log n) for searching in a sorted Array List. 

<img src="https://lh4.googleusercontent.com/XRsX8CxeukYOx_Ucj_52SKEeDWMbz78vkkTrileqNqDeqEGFNU2Uda4h5AxsWl5gqa2rXuG-oFXSGIcYnVmFYHiJ7fRDKLmeQWpuWKNkF0IuWMkFqpzwFcH4j4BM-OLeZ4Bq5ixM" alt="img" style="zoom:50%;" />

## LinkedList 

* if we are looking for the i-th element of a Linked List, this is a O(i) operation, whereas in an array, accessing the i-th element was a O(1) operation (because of "random access"). 
* This is one main drawback of a Linked List: even if we know exactly what index we want to access, because the data is not stored contiguously in memory, we need to slowly iterate through the elements one-by-one until we reach the node we want.
* Insert into double LL simple
* <img src="https://lh5.googleusercontent.com/nuGGvaJHZQOjnOM0Z2oyRtICoL-zE9N38K76eYI1X5PT_sa1Qc1Qaf0hcW8TKgS9r1n942mXZDpRxhOOmo-J-YPOxIy3mtViPZdMcmZRxRg3IK-e8IXuVbvOfjpQUx46gASIUOZS" alt="img" style="zoom:50%;" />

## SkipList 

<img src="https://lh5.googleusercontent.com/ZtDDgJlfGLsKEH4SUSFMVkQ9xdO4aCyqAtJJWei9BOUtnjl-xvxuR40mMKw8hC5XS9AqwfY9BEMQzb9OZQdzesl8z7hYt2pX_FPJ2eUczzLUFF0hB6vtxGBEwqi2LmGyy6uo4k-m" alt="img" style="zoom:50%;" />

* In the "Step 1: Find" figure, red arrows denote pointers that we could have traversed, but that would have taken us to a node that was too big (so we instead chose to go down 1 level), and green arrows denote pointers we actually took.
* Clearly, the distribution of heights has a significant impact on the performance of a Skip List. With the best distribution of heights, the Skip List "find" algorithm effectively performs binary search, resulting in a O(log n) time complexity.
* How to insert ? How to figure out the optimum height of a new node? By definition, the new node must have a height of at least 0 (i.e., the 0-th layer). So how many layers higher should we build the new node? To answer this question, we will play a simple coin-flip game (we will explain in the next step what this game formally represents): starting at our base height of 0, we flip a coin, where the coin's probability of heads is p. If we flip heads, we increase our height by 1. If we flip tails, we stop playing the game and keep our current height.
* average-case time complexity of a Skip List is O(log n) when the height is chosen correctly (see text for proof)

### Bernoulli distribution and geometric distribution 

* A coin-flip is a Bernoulli distribution (or a binary distribution), which is just the formal name for a probability distribution in which we only have two possible outcomes: success and failure
* What we described above, where we perform multiple coin-flips until we get our first tails, is synonymous to saying "Sample from a Bernoulli distribution until you see the first failure." It turns out that this statement is actually a probability distribution in itself: the Geometric distribution
* The Geometric distribution tells us, given a Bernoulli distribution with probability p of success, what is the probability that our k-th trial (i.e., our k-th coin-flip) results in the last failure in a row before the first success?
* Since  we want the number of flips until the first failure -> We swap two probabilities <img src="https://lh4.googleusercontent.com/2gmCID8IEHFZ_RqnCMohgXy_jPML8iK9NDbSRj4d4O_FCA07m8Vm8N3YQp-GTpsgyEOzBxuUWvdYIRKQG9Xf3ZGQamf1PxPtzdrMqyQEY2VyNPJEce4PRB2FXhZ5Nkm2ICpTDXC_" alt="img" style="zoom:33%;" />

## Tree Structures 
* Definition: A tree is defined as a graph without any undirected cycles 
* In a rooted tree, a given node can have a single parent node above it and can have any number of children nodes below it. 
* In an unrooted tree, there is no notion of parents or children. Instead, a given node has neighbors. Any nodes with just a single neighbor is considered a leaf and any node with more than one neighbor is considered an internal node. For example, in Bioinformatics, if we want to construct an evolutionary tree from different organisms, if we don't know what the true ancestor was, we have no way of picking a node to be the root. However, the unrooted tree still provides us relational information: leaves closer together on the tree are more similar biologically, and leaves farther apart on the tree are more different biologically. 

**<img src="https://lh6.googleusercontent.com/obVSPEByh0VPrfnvtFFaY9q-2GaCTtzQs4tjk1DMs3a1DDbEdFVVfNOqr4bmvxv9emFdSsRvSxg6UCUmX5DSu_SIfEAqSSAUnpy4M9-vVmBRQann33D_Eu9jSbfpJIGsc_lGqfIe" alt="img" style="zoom:33%;" />****<img src="https://lh6.googleusercontent.com/CFJjnvV11-Z3CrIrMcl24gnh6g-9kGt9vlMxwgANKUOR5TufXtP_GUFuyG5CVgX8Ukzv14kOor6O1lyEA_e3RZkOGWRlGrRkdXwBYEPOHrhaFrGWTzqHyuOejSWOzu52BhqOOEf1" alt="img" style="zoom: 33%;" />****<img src="https://lh3.googleusercontent.com/i5YM95HAUYa6Yg07EwkY52FCMTmz-KoSLQu1LqhjaAgRtnHyLkUrU-zB--7BsmRdv1EbodYlx49U-8RfEupjdbH0YzvCgYrl4n68hiZLeVQFp569VKMTSrIkVsEDpNcMUNA-N3h9" alt="img" style="zoom: 25%;" />**


