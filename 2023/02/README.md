# Day 02: Cube Conundrum

# Part 1

## Problem

Find full description [here](task.md).

Find source code [here](solution.cpp).

### Example

Provide an example input and the expected output to give users a clear understanding of the problem.

## Approach

Here I tried to make the compiler solve the task. I used [compile time constants](https://en.cppreference.com/w/cpp/language/constexpr) and wrote the code to force the compiler generate the asm code that looks like:

    printf("answer")

Check the golbolt link: https://godbolt.org/z/35h8nhx54

The generated code is literally just printing the answer:

```asm
main:                                   # @main
        pushq   %rax
        leaq    .L.str(%rip), %rdi
        // 2913 is an actual answer for the problem
        movl    $2913, %esi                     # imm = 0xB61
        xorl    %eax, %eax
        callq   printf@PLT
        xorl    %eax, %eax
        popq    %rcx
        retq
.L.str:
        .asciz  "%lu\n"

```



### How to Run

Since all constants must be known to the compiler at compile time, in order to reuse the code for your own task, you need to change following constants:

```
INPUT_SIZE - number of lines in your input.
MAX_RED_CUBES - maximum number of red cubes from the task description.
MAX_GREEN_CUBES - maximum number of green cubes from the task description.
MAX_BLUE_CUBES - maximum number of blue cubes from the task description.
MAX_NUMBER_OF_SETS - number of ; in input. Value should be greater than the actual number of set in the input. If you don't want to count use some large number, 100 would be enough.
games - input of the puzzle. See the format in the solution.cpp file
```

Compile for c++17 standard.

Example compilation string: `clang++ -std=c++17 -O3 solution.cpp -o solution`

Run with: `./solution`

If you want to examine generated asm code use: `clang++ -std=c++17 -O3 -S solution.cpp` and navigate to `solution.s` file.

### Notes

Take into account that different participants have different tasks.

# Part 2

Nothing interesting happened here
