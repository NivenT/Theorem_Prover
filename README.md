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
1. A || B            given
2. ~B                given
3. ~A                negation of conclusion
4. B                 resolve 3 1
5. F                 resolve 4 2
QED

; Deducing r from p \/ q, p -> r, and q -> r
(prove 'r '(or p q) '(or (not p) r) '(or (not q) r))
1. P || Q            given
2. ~P || R           given
3. ~Q || R           given
4. ~R                negation of conclusion
5. ~P                resolve 4 2
6. Q                 resolve 5 1
7. R                 resolve 6 3
8. F                 resolve 7 4
QED
  
; Attempting to deduce a from a \/ b, b \/ c, ~c
(prove 'a '(or a b) '(or b c) '(not c))
Conclusion unable to be proven from premises
?
```

## TODO (in no particular order)
- [X] Make the output of prove more neat/readable
- [ ] Automatically convert formulas to CNF
- [ ] Support claims made in FOL
