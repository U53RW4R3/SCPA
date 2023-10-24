# RC4

## Algorithm

### Pseudo Code

```vb
function rc4(key, plaintext)
    initialize_s_box(key)
    initialize_state_array()
    
    i := 0
    j := 0
    ciphertext := ""
    
    for each character in plaintext
        i := (i + 1) mod 256
        j := (j + S[i]) mod 256
        swap_values(S[i], S[j])
        
        key_byte := S[(S[i] + S[j]) mod 256]
        char := character XOR key_byte
        ciphertext := ciphertext + char
    
    return ciphertext


function initialize_s_box(key)
    S := array[0 to 255]
    key_length := length(key)
    for i from 0 to 255
        S[i] := i
    j := 0
    for i from 0 to 255
        j := (j + S[i] + key[i mod key_length]) mod 256
        swap_values(S[i], S[j])


function initialize_state_array()
    i := 0
    j := 0
    state_array := array[0 to 255] // State array initialization
    
    for i from 0 to 255
        state_array[i] := i


function swap_values(a, b)
    temp := a
    a := b
    b := temp
```