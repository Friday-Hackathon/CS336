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

(a) What are some reasons to prefer training our tokenizer on UTF-8 encoded bytes, rather than
UTF-16 or UTF-32? It may be helpful to compare the output of these encodings for various
input strings.

Tokenizers like Byte-Pair Encoding (BPE) or SentencePiece often work on bytes.This allows tokenizers to learn subword units efficiently while keeping vocabulary small.UTF-16 and UTF-32 produce fixed-width sequences, which are: Larger in size Less flexible for learning subword patterns


(b) Consider the following (incorrect) function, which is intended to decode a UTF-8 byte string into
a Unicode string. Why is this function incorrect? Provide an example of an input byte string
that yields incorrect results.
```
def decode_utf8_bytes_to_str_wrong(bytestring: bytes):
return "".join([bytes([b]).decode("utf-8") for b in bytestring])
>>> decode_utf8_bytes_to_str_wrong("hello".encode("utf-8"))
'hello'
```

```
## It should not loop as utf-8 is variable length
def decode_utf8_bytes_to_str_correct(bytestring: bytes) -> str:
    return bytestring.decode('utf-8')
```

Deliverable: An example input byte string for which decode_utf8_bytes_to_str_wrong produces incorrect output, with a one-sentence explanation of why the function is incorrect.
(c) Give a two byte sequence that does not decode to any Unicode character(s).
Deliverable: An example, with a one-sentence explanation.

```
UTF-8 uses 1 to 4 bytes per character.

1 byte (ASCII): 0xxxxxxx → 0–127 (normal letters, numbers, punctuation)

2 bytes: 110xxxxx 10xxxxxx

First byte starts with 110 → tells UTF-8 “this is a 2-byte character”

Second byte must start with 10 → continuation byte

3 and 4 bytes follow similar rules with more 10xxxxxx continuation bytes.

So any multi-byte character must follow this pattern exactly.
```
