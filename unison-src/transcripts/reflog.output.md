First we make two changes to the codebase, so that there's more than one line
for the `reflog` command to display:

```unison
x = 1
```

```ucm

  I found and typechecked these definitions in scratch.u. If you
  do an `add` or `update`, here's how your codebase would
  change:
  
    ⍟ These new definitions are ok to `add`:
    
      x : Nat

```
```ucm
.> add

  ⍟ I've added these definitions:
  
    x : Nat

```
```unison
y = 2
```

```ucm

  I found and typechecked these definitions in scratch.u. If you
  do an `add` or `update`, here's how your codebase would
  change:
  
    ⍟ These new definitions are ok to `add`:
    
      y : Nat

```
```ucm
.> add

  ⍟ I've added these definitions:
  
    y : Nat

.> view y

  y : Nat
  y = 2

```
```ucm
.> reflog

  Here is a log of the root namespace hashes, starting with the
  most recent, along with the command that got us there. Try:
  
    `fork 2 .old`             
    `fork #j7ar890fgd .old`   to make an old namespace
                              accessible again,
                              
    `reset-root #j7ar890fgd`  to reset the root namespace and
                              its history to that of the
                              specified namespace.
  
  1. #396ap2v898 : add
  2. #j7ar890fgd : add
  3. #7eacs027uv : builtins.merge
  4. #sg60bvjo91 : (initial reflogged namespace)

```
If we `reset-root` to its previous value, `y` disappears.
```ucm
.> reset-root 2

  Done.

```
```ucm
.> view y

  ⚠️
  
  The following names were not found in the codebase. Check your spelling.
    y

```
