# XOR

## Simple XOR

### Algorithm

#### Formula

$P \oplus K = C$

#### Truth Table

| Plaintext (P) | Key | Ciphertext (C) |
|---------------|-----|----------------|
|      0        |  0  |      0         |
|      0        |  1  |      1         |
|      1        |  0  |      1         |
|      1        |  1  |      0         |

#### Example

TODO: Write it down step by step

$$
\begin{flalign}
P = 5 &&
\newline
C = 10 &&
\newline
5 \oplus 10 = C &&
\newline
1000 \oplus 1111 = C &&
\newline\newline
\begin{split}
\oplus1000 \\
1111 \\
\hline
2222
\end{split}
\end{flalign}
$$

#### Pseudo Code

TODO: Provide Pseudo code

```
Ciphertext = Plaintext XOR Key
```

## XOR Repeater

---
## References

- [Wikipedia: XOR Cipher](https://en.wikipedia.org/wiki/XOR_cipher)