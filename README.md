# Running FORTRAN II
Because the simulator simulates an IBM 1401, you will need to carry out the
standard workflow by mounting the tapes and inserting a deck of cards. For
example, here is the sequence of actions to run "hello.f"

```
$ i1401

IBM 1401 simulator V3.12-3
sim> at mt1 fortran.tap
sim> at cdr examples/hello.f
sim> at lpt listing
LPT: creating new file
sim> b mt1

HALT instruction, IS: 280 (H 280)
```

Now, open the "listing" file in another terminal/window and verify that the
program is listed and compiled successfully. If it worked, you will see the
following at the end of the listing:

```
END OF COMPILATION

PRESS START TO GO
```

If you see this, go ahead and type "g" in the simh window. The output of the
program will then appear in the listing.

```
sim> g

HALT instruction, IS: 4296 (B 4291)
```

Consult the listing file to see your output. You can also continuously monitor
your listing file by opening a second terminal window and running the command:

```
tail -f listing
```

Then you will see input as it comes off the line printer.

# Some Hints and Tips
- I recommend that you delete the listing file between runs of the simulator. If
  you exit the simulator, and then reattach the listing it sometimes has weird
  results!
- If you need to correct your program, you can do so by correcting the file.
- If you need to recompile/compile a different program, you need to reattach the
  card reader (cdr). You can then do the `b mt1` directive to invoke the compiler.
- FORTRAN II programs must be preceded by a parameter card. The parameter card
  can be found at the top of all the programs. Copy this line into your programs,
  and it should generally work. If you want to explore the parameters and play
  with different ones, consult the 1401 specifications manual.
- VS Code has many extensions which can do syntax highlighting/formatting for
  Fortran. Be careful with these! They understand *modern* Fortran. They may
  result in incompatible code with the venerable old version we are using here.
