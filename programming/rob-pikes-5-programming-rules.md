## Rob Pike's 5 Rules of Programming

I came across the 5 rules of programming by Rob Pike and loved them and co-related them with myself. Here they are for
my own reference:

- You can't tell where a program is going to spend its time. Bottlenecks occur in surprising places, so don't try to
second guess and put in a speed hack until you've proven that's where the bottleneck is.
- Measure. Don't tune for speed until you've measured, and even then don't unless one part of the code overwhelms the rest.
- Fancy algorithms are slow when n is small, and n is usually small. Fancy algorithms have big constants. Until you know that n is frequently going to be big, don't get fancy. (Even if n does get big, use Rule 2 first.)
- Fancy algorithms are buggier than simple ones, and they're much harder to implement. Use simple algorithms as well as simple data structures.
- Data dominates. If you've chosen the right data structures and organized things well, the algorithms will almost always be self-evident. Data structures, not algorithms, are central to programming.
