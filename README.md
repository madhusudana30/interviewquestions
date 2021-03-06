I have two sand clocks, one that measures 4 minutes and one that measures 7.  How can I measure 9 minutes?

  Turn them both over at the same time.  When the 4 minute one runs out, the 7 minute one has 3 left.

  Turn both over again.  When the 7 minute one runs out, the 4 minute one has 1 left.  Ignore the 7 minute one from now.

  Turn the 4 minute one over.  The 9 minutes start here.

  Turn the 4 minute one over again.  You've measured 1 minute so far.

  Turn the 4 minute one over again.  You've measured 5 minutes so far.

  Turn the 4 minute one over again.  You've measured 9 minutes.

Write the functional factorial, both for the recursive version and the iterative version.

  See [src/main/java/Factorial.java](src/main/java/Factorial.java)

Implement an algorithm that verifies if a binary tree is sorted.

  See [src/main/java/BinaryTreeOrdered.java](src/main/java/BinaryTreeOrdered.java)

I have a linked list and there may be a cycle.  How can I tell if there is a cycle?  What's the complexity?

  See [src/main/java/LinkedListCycle.java](src/main/java/LinkedListCycle.java) - O(1) time, O(n) space

I have two large numbers that won't fit in any of Java's numeric types (i.e., ignore BigDecimal and BigInteger) so they
are stored in LinkedLists.  Write a function that will sum them both, returning a new LinkedList.

  See [src/main/java/SumLinkedLists.java](src/main/java/SumLinkedLists.java)

Explain why the recursive implementation of quicksort will require O(log(n)) of additional space.

  Because it needs a new stack frame with a new pivot value etc.

Create an Iterator filtering framework: an IObjectTest interface with a single boolean
test(Object o) method. An Iterator sub-class which is initialized with another Iterator
and an IObjectTest instance. Your iterator will then allow iteration over the original,
but skipping any objects which don't pass the test. Create a simple unit test for this
framework.

  See [src/main/java/iterators](src/main/java/iterators)

Given

    class Node {
        object value;
        Node next;
    }

Implement method Node getFromEnd(node head, int i);

  See [src/main/java/list/List.java](src/main/java/list/List.java)

Given Account and Transfer classes:

    class Account {
      int amount;

      lock();
      unlock();
    }

    class Transfer {
      int amount;
      account a;
      account b;
    }

Implement method void TransferMoney(Transfer t); trying to prevent a deadlock.

  See [src/main/java/account/TransferMoney.java](src/main/java/account/TransferMoney.java)

Implement a method that returns whether a String is a palindrome.

  boolean isPalindrome(String s) {
    return new StringBuilder(s).reverse().toString().equals(s);
  }

  Imagining that efficiency matters more than readability, see src/main/java/Palindrome.java

Implement a function that receives the name of an Excel column and returns the index of it.
E.g.: f("A") -> 1, f("AB") -> 28, f("XWA") -> ?

  See [src/main/java/ExcelNumbers.java](src/main/java/ExcelNumbers.java) - XWA = 1223

Implement a function that inverts the digits of an int, e.g., f(123) == 321, without converting them to a String.

  See [src/main/java/InvertDigits.java](src/main/java/InvertDigits.java)

Implement a method that gives the nth Fibonacci number, e.g., f(0) -> 1, f(1) -> 1, f(5) -> 8

  See [src/main/java/Fibonacci.java](src/main/java/Fibonacci.java)

Describe the steps needed to find the largest element of an array.  What's the complexity?

  Set a variable, max, to the value of the first element.  Iterate over the rest, comparing against max and replacing
  the value of max with the value of the element if it is larger.  max is the result.  O(n) time, O(1) space.

What sorting algorithms do you know?  Which is the most optimal?  What complexity does it have?

Bubblesort O(n^2), quicksort (O(n log n) worst case O(n^2) when the pivot always ends up at the wrong end,
mergesort (O(n log n) - divide into two lists, mergesort those then merge the two into one.  Possible but tricky and
possibly worse performance if the merge is done in-place.
timsort (mergesort with some adaptation for presorted sequences) - O(n log(n))

  See [src/main/java/sorting/Bubblesort.java](src/main/java/sorting/Bubblesort.java)

  See [src/main/java/sorting/Quicksort.java](src/main/java/sorting/Quicksort.java)

  See [src/main/java/sorting/Mergesort.java](src/main/java/sorting/Mergesort.java)

  See [src/main/java/sorting/Sleepsort.java](src/main/java/sorting/Sleepsort.java)

How does binary search work?  What complexity does it have?  Why?

  Start in the middle, see whether that element is higher or lower than the searched-for value.  If it's higher,
  repeat with the higher half only.  If it's lower, repeat with the lower half only.  If it's the searched-for
  value then we've found the result.  It has complexity O(log(n)) because every step halves the search space.

  For an implementation, see [src/main/java/BinarySearch.java](src/main/java/BinarySearch.java)

Given a boolean n by n matrix that represents a labyrinth, where every element indicates whether it's possible to pass,
how would you implement an algorithm that allows you to find a path between the entrance and the exit?

  Recursively attempt, backtracking where the end of the path is reached.  If recursion is a problem, maintain a
  separate n by n matrix storing whether we've already attempted going down a particular path.

Given an n by n matrix of letters, implement an algorithm that returns how many times a word appears, moving
horizontally and vertically.  I think this question is based on Boggle, so it's not directly a wordsearch.

  for each letter in the matrix that matches the starting letter, recursively attempt to move from it in each direction
  returning the count of words that match.  One problem, it will match, e.g., BOB, twice, so maintain a separate
  Set<List<Coord>> and return its size at the end.

Overriding equals and hashCode: what is the rule you need to follow and what could happen if you do not?

  x.equals(x), x.equals(y) == y.equals(x), x.equals(y) && y.equals(z) == x.equals(z),
  x.equals(y) == x.equals(y) provided no modifications,
  x.equals(null) == false,
  x.hashCode() == x.hashCode() provided no modifications,
  if x.equals(y) then x.hashCode() == y.hashCode(),

  If you don't follow it, then any collections that use equals and/or hashCode will appear to be inconsistent.
  Without breaking those rules you can have inconsistent results if the hashCode changes.

How does a HashMap work (related to the previous question on equals and hashCode)?

  It has a number of buckets that it assigns each key to based on a function of the hashCode, storing the key-value
  pairs in a linked list within each bucket.  When retrieving values if the hashCode matches equals is checked.

Describe how CountDownLatch works including code.

  See [src/main/java/sorting/Sleepsort.java](src/main/java/sorting/Sleepsort.java)

Which are the base collection interfaces in Java?

  Collection, List, Set, Queue, Map

What does each one guarantee?

  Collection guarantees nothing.

  List guarantees insertion order unless overridden with add(int,K) or set.

  Set guarantees that each element is not null, and that there are no duplicates.

  Queue guarantees nothing.

  Map guarantees nothing.

How do the most common implementations work?

  ArrayList has a backing array that grows according to some implementation-defined function.

  LinkedList contains nodes that store the value and a next pointer (actually also a prev pointer).

  HashSet is based on a HashMap with a dummy value for each key.

  TreeSet is based on a TreeMap with a dummy value for each key.

  HashMap is an array of buckets where each bucket is a linked list of key-value pairs.

  TreeMap is based on a binary tree where each node has a reference to its parent and optional two children,
  always maintaining order based on a Comparator or the Comparables that are the elements.

  LinkedHashMap extends HashMap adding a doubly-linked list maintaining the order of insertion as the order of iteration.
    It can also be used via the int, float, boolean constructor to maintain the order in terms of most recent access.

  ArrayBlockingQueue is a Queue implementation that blocks when putting in a full queue, and blocks when taking from an
  empty queue, so it's handy for inter-thread messaging.

  DelayQueue is a Queue implementation that only 'releases' each element after its delay has been reached.

Garbage collection, different schemes, memory management

  Garbage collection is provided by the runtime to avoid that the programmer need to track when an object is no longer
  reachable and can be removed.  This helps the programmer because at least in the case of immutable objects there is
  no need for the concept of ownership of an object.

  Python's GC is reference-counting with cycle detection, very predictable immediate collection.
  Java has generational collectors, so that objects that survive the young generation make it to a longer-lived
  generation, etc.  Objects can be moved around in memory by the GC for better cache locality.
  There's the throughput collector (-XX:+UseParallelGC) which gives control over the number of threads that will perform
  garbage collection (-XX:ParallelGCThreads=..).
  There's the concurrent mark sweep collector, also called the concurrent low pause collector, which might give a hit to
  performance generally but with the advantage that there will be shorter pauses.
  There's the garbage first garbage collector (G1GC), mainly for larger heaps.
  Azul Zing offers 'pauseless' garbage collection, although it still has very short (3ms or lower) pauses.

  Memory management in general, you can use malloc/free in C, new/delete in C++, and if you need to manage memory
  manually in Java, you could allocate a big ByteBuffer and manage allocations within it.

Explain what 'path to root' means in the context of garbage collection.  What are roots?

  A root is an object or context from which it is known that referenced objects should not be garbage collected, e.g.,
  a running method, a static field, JNI references, an object synchronized upon.

  The path to root is the path of references between an object and a root that proves that the object should not be
  collected, e.g., if a static field x has a field y that in turn has a field z pointing to our object, that is the path.

Examples of design patterns in the Java APIs.

  Strategy - Comparator

  Visitor - java.nio.file.FileVisitor

  Factory - Basically all the DOM stuff, BorderFactory

  Singleton - Collections.EMPTY_LIST

  Builder - DOM's DocumentBuilder, ProcessBuilder, StringBuilder

  Flyweight - Integer.valueOf maintaining a cache of -128 to +127.

  Command - Runnable, Callable

Write code for a simple implementation of HashMap/Hashtable

  See [src/main/java/Hash.java](src/main/java/Hash.java)

Write a short program to illustrate the concept of deadlock

  See [src/main/java/Deadlock.java](src/main/java/Deadlock.java)

Exceptions

  Checked exceptions, runtime exceptions, errors, throws, try..catch..finally, try-with-resources, throw,
  cost is mainly in filling the stack trace, generally should set a serializationVersionUID

Logging

  java.util.logging, limited control

  log4j, good

  logback, better

  slf4j, interface over various

  generally can configure them via XML or programmatically.

  log.error("foo", e);

Determination of big-oh complexity

  Roughly, if the algorithm doesn't depend at all on the length, O(1), e.g., list.head

  If it's a divide and conquer without any extra iteration, O(log n), e.g., binary search

  If it has a loop over n, O(n), e.g., maximum value in a list.

  If it has a loop over n, plus some divide and conquer, O(n.log(n)), e.g., mergesort

  If it has two nested loops, O(n^2), e.g., bubblesort.

  If it's a brute force search, probably O(c^n), e.g., travelling salesman.

Deadlocks

  When two or more threads each hold a resource and are blocking waiting for a resource that another thread in the group owns.
  None can proceed.  Java's thread dumps have deadlock detection.

Monitors

  The part of an object that interacts with synchronized.  Only one thread at a time may hold a monitor, thus it can be used to protect regions from concurrent access.

Locks

  Same idea as monitor but with other options like reentrancy, allowing multiple read locks, allowing a time-constrained tryLock, etc.

Happens-before

  A condition where the JVM guarantees that an update made in one thread/location will be visible from another, i.e., if A happens-before B then A can correctly use B's results.

Monitor versus semaphore

  A monitor is basically boolean, a semaphore is an int that can go up and down with some semantics about whether 0 means free.

Atomic access

  Operations that can either complete 100% or not happen/be visible at all, e.g., int++ is atomic, double++ is not.  AtomicInteger.

Does a monitor work at the instance level, class-level, method-level?

  A monitor is always on an instance.  The synchronized construct when on an instance method applies to this, and on a static method it applies to the Class instance.

What does a Lock guarantee?

  That the lock cannot be obtained again until the lock is released.

What does volatile guarantee?

  It tells the JVM not to cache the value of the variable per-thread, so that updates are visible across all threads instantly.

Clustered index

  An index that forces the data to be accessible in a certain order.  Handy for sequential access or ranges.  E.g., telephone directory.

Join types

  Inner join, only those records from both that match.

  Full outer join, all records from both, regardless of matches.  The missing side will contain null.

  Left outer join, all records from the first, and if they match, records from the second, otherwise null.

  Right outer join, all records from the second, and if they match, records from the first, otherwise null.

  Cross join, all combinations of both:
    select * from foo cross join bar
    select * from foo, bar


