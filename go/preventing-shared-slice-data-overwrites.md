# Preventing shared slice data confusion

Slices are small constructs that point to the first element in a slice, indicate the slices length, and indicate the capacity of the underlying array; it's 24bytes long so very cheap to copy-by-value. 

If we create 2 slices with an overlap to an underlying array instance and attempt to append datausing the `append` built-in function, we find that data in 1 slice creates a change in the second slice. 

```go
slice := []string{"Tomato", "Squash", "Lettuce", "Spinach"}

newSlice := slice[0:1] // Length 1, capacity 4
append(newSlice, "Hello world") // Overwrites "Squash"
```

We can prevent this using the special slice syntax `newSlice := slice[0:1:1]`. The second `1` sets the capacity of the slice to the same as it's length. When we append to a slice the Go runtime checks if there is room by ensuring the `len < cap`. If it isn't, up to `len = 1000` the Go runtime doubles the capacity and copies everything over. Therefore, when specify capacity equals length a subsequent `append` call results in a new array being created and the slice elements copied to the new array avoiding any overwriting of the original underlying array.
