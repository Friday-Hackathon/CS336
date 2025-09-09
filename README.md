# CS336

## Assignment 1:

 - (a) What Unicode character does chr(0) return?
   - '\x00'
 - (b) How does this character’s string representation (__repr__()) differ from its printed representation?
   - print(c) is empty vs repr(c) is \\x00
 - (c) What happens when this character occurs in text? It may be helpful to play around with the
following in your Python interpreter and see if it matches your expectations:
  - >>> chr(0) '\x00'
  - >>> print(chr(0)) empty
  - >>> "this is a test" + chr(0) + "string" 'this is a test\x00string'
  - >>> print("this is a test" + chr(0) + "string") this is a teststrin
