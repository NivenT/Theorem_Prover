# Theorem_Prover
(Very) simple automated theorem prover using resolution

## Details
* All formulas used should be in CNF
* conjuctions are stored using the following format: (and a b c)
* disjuctions are stored using the following format: (or a b c)
* negatations are stored using the following format: (not a)

## Example
The main function in this project is prove. It accepts the conclusion you are trying to reach as its first argument and the premises as the rest of the arguments. If the statement has been proved, the output will end in 'QED'. If the statement cannot be proven, then it will end in '?'.
``` CommonLisp
; Deducing a from a \/ b and ~b
(prove 'a '(or a b) '(not b))
  => ((OR A B) (NOT B) (NOT A) B F QED)
; Deducing r from p \/ q, p -> r, and q -> r
(prove 'r '(or p q) '(or (not p) r) '(or (not q) r))
  => ((OR P Q) (OR (NOT P) R) (OR (NOT Q) R) (NOT R) (NOT P) Q R F QED)
; Attempting to deduce a from a \/ b, b \/ c, ~c
(prove 'a '(or a b) '(or b c) '(not c))
  => ((OR A B) (OR B C) (NOT C) (NOT A) B ?)
```

## TODO (in no particular order)
- [ ] Make the output of prove more neat/readable
- [ ] Automatically convert formulas to CNF
- [ ] Support claims made in FOL
