# Simple XOR

## Algorithm

### Formula

$P \oplus K = C$

### Truth Table and Logical Gate

^cbf7ed

[[XOR Logical Gate.canvas|XOR Logical Gate]]

| _Plaintext (P)_ | _Key_ | _Ciphertext (C)_ |
|---------------|-----|----------------|
|      0        |  0  |      0         |
|      0        |  1  |      1         |
|      1        |  0  |      1         |
|      1        |  1  |      0         |

### Compute

To demonstrate how it works. Let's define the variables first. _**Plaintext (P)**_ is 5 and _**Key (K)**_ is 10.

$$
\begin{flalign}
P = 5 &&
\newline
K = 10 &&
\end{flalign}
$$

Convert the numbers from decimal base 10 to binary base 2.

$$
\begin{flalign}
5 \oplus 10 = C &&
\end{flalign}
$$

Make a table to simplify the conversion. Just to confirm from the binary placeholders of 1's to get the sum total.

<html>
	<body>
		<table>
            <th align="center" colspan="4">
                <em>Plaintext (P) = 5</em>
            </th>
			<th align="center" colspan="4">
                <em>Key (K) = 10</em>
            </th>
            <tr>
                <td>8</td>
                <td>4</td>
                <td>2</td>
                <td>1</td>
                <td>8</td>
                <td>4</td>
                <td>2</td>
                <td>1</td>
            </tr>
            <tr>
                <td>0</td>
                <td>1</td>
                <td>0</td>
                <td>1</td>
				<td>1</td>
                <td>0</td>
                <td>1</td>
                <td>0</td>
            </tr>
			<tr>
                <td>0</td>
                <td><b>4</b></td>
                <td>0</td>
                <td><b>1</b></td>
                <td><b>8</b></td>
                <td>0</td>
                <td><b>2</b></td>
                <td>0</td>
            </tr>
			<tr>
                <td align="center" colspan="4"><b>4 + 1 = 5</b></td>
				<td align="center" colspan="4"><b>8 + 2 = 10</b></td>
				<td align="center"><b>Total</b></td>
            </tr>
		</table>
	</body>
</html>

$$
\begin{flalign}
Plaintext: 4 + 1 = 5 &&
\newline
Key: 8 + 2 = 10 &&
\end{flalign}
$$

Decimal base 10 to binary base 2 has been converted.

$$
\begin{flalign}
0101 \oplus 1010 = C &&
\end{flalign}
$$

XOR the binaries based on the [[Simple XOR#^cbf7ed|truth table]].

$$
\begin{flalign}
\begin{split}
0101 \\ \oplus 1010 \\
\hline
1111
\end{split} &&
\end{flalign}
$$

The _**Ciphertext (C)**_ is 1111

$$
\begin{flalign}
C = 1111 &&
\end{flalign}
$$

Then _**Ciphertext (C)**_ from binary base 2 to decimal base 10. To get the outcome.

<html>
	<body>
		<table>
            <th align="center" colspan="4">
                <em>Ciphertext (C)</em>
            </th>
            <tr>
                <td>1</td>
                <td>1</td>
                <td>1</td>
                <td>1</td>
            </tr>
            <tr>
                <td><b>8</b></td>
                <td><b>4</b></td>
                <td><b>2</b></td>
                <td><b>1</b></td>
            </tr>
			<tr>
                <td align="center" colspan="4"><b>8 + 4 + 2 + 1 = 15</b></td>
				<td align="center"><b>Total</b></td>
            </tr>
		</table>
	</body>
</html>

$$
\begin{flalign}
Ciphertext: 8 + 4 + 2 + 1 = 15 &&
\end{flalign}
$$

### Flowchart

TODO: Translate from pseudo code to a flowchart

### Pseudo Code

TODO: Provide Pseudo code

#### Simple XOR Ciphered Message

```c
function XOR()
Plaintext = "Attack at Dawn!"

Key = 0x0A

Ciphertext = Plaintext XOR Key
```

#### Simple XOR Ciphered Bytes

```c
Plaintext = {0x00, 0x11}

Key = 0x0A

Ciphertext = Plaintext XOR Key
```

---
## References

- [Wikipedia: XOR Cipher](https://en.wikipedia.org/wiki/XOR_cipher)