# Big O notation.

- Transfering 1TB can be quicker by plane then over the net.

- Electronic Transfer: 0(s) , where s is the size of the file. This means that the time to transfer the file
  increases linearly with the size of the file. (Yes, this is a bit of a simplification, but that's okay for these
  purposes.)
- Airplane Transfer: 0(1 ) with respect to the size of the file. As the size of the file increases, it won't take
  any longer to get the file to your friend. The time is constant.

- Informally, the term asymptotic means approaching a value or curve arbitrarily closely (i.e., as some sort of limit is take

Big O describes an upper bound on the time.

- Q (big omega): In academia, 0 is the equivalent concept but for lower bound. Printing the values in
  an array is fl(N) as well as fi(log M) and Q(l) . After all, you know that it won't be faster than those
  runtimes.
- 0 (big theta): In academia, 0 means both 0 and fi. That is, an algorithm is 0 (N) if it is both 0( N) and
  0(N). 0 gives a tight bound on runtime.

pg52...
