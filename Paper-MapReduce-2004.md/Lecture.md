*This file is fully copied from course [lecture](https://pdos.csail.mit.edu/6.824/notes/l01.txt)*

Infrastructure hides distribution from applications. Three big kinds of abstraction:
- **Storage.**
- **Communication.**
- **Computation.**

A couple of topics come up repeatedly.

- implementation
- performance
- fault tolerance
- consistency

CASE STUDY: MapReduce

MapReduce single-handedly made big cluster computation popular.
- Not the most efficient or flexible.
+ Scales well.
+ Easy to program -- failures and data movement are hidden.


These were good trade-offs in practice.

We'll see some more advanced successors later in the course.

Have fun with the lab!
