
## NTable Testbench

A simple stimulus pattern generator, with checking, to test a scheme
implementation of a table data structure where values are stored under
a varying number of keys.

> Exercise 3.25 SICP[^1] 1st & 2nd Ed
>
> Generalizing one- and two-dimensional tables, show how to implement a table
> in which values are stored under an arbitrary number of keys and different val-
> ues may be stored under different numbers of keys.  The lookup and insert!
> procedures should take as input a list of keys used to access the table.

### How to generate the self-checking stimulus

At the shell prompt ```./nttest >stim```

### Restrictions and Caveats
Peruse the generated stimulus to see what, if any, changes need to be made
to the exported procedures of the implementation under test (IUT) to align
with what the stimulus uses.  Small shim procedures may be required.

The IUT must return #f upon an unsuccessful lookup.  FYI, SICP 1st
Edition returned nil.

The object #f is never used as an element in the keylist, but there
is no reason why not.

### Methodology
Randomize the objects to be inserted into the table, the number
and objects of the key(s), and the insertion order.  Insert these
(key(s),value) tuples into two distinct tables.  Finally, check in
random order against a reference model that all table entries retain
the correct value previously inserted.  Augment with many additional
unsuccessful lookups sprinkled throughout.

### Verification
The testbench was verified on Linux using these scheme implementations
1. s9 Scheme 9 from Empty Space by Nils M Holm, 2018-12-05
2. mit-scheme  Release 10.1.11 || Microcode 15.3 || Runtime 15.7
3. racket v7.9 [bc]

### See Also
* http://community.schemewiki.org/?sicp-ex-3.25
* [archived 24 Feb 2023](https://web.archive.org/web/20230224171808/http://community.schemewiki.org/?sicp-ex-3.25)

[^1]: *Structure and Interpretation of Computer Programs* by Harold Abelson et al. 1985, 1996
