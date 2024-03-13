# tz_atcoder_fish

# ><>

.fish

Ponnosuke

https://esolangs.org/wiki/Fish


Movement and execution
 > < ^ v	Change the direction of the instruction pointer (right, left, up, down respectively)
 / \ | _ #	Mirrors; the IP will change direction depending on what direction it already has.
 x	Random direction.
 !	Trampoline - skip the following instruction.
 ?	Conditional trampoline - pop one value off the stack. The next instruction is only executed if the popped value is non-zero.
.	Jump - pop y and x off the stack, and move the IP to (x,y) in the codebox. The current direction is retained. Note that you have to jump to the cell before the instructions you want to execute, as the IP will move one position next tick before executing.
Literals and operators
 0-9 a-f	Push the corresponding value onto the stack. a = 10, ..., f = 15
 + - * , %	Addition, subtraction, multiplication, division and modulo, respectively. Pop x and y off the stack, and push y operator x. Division is float division (meaning 94,n; outputs 2.25 and not 2). Division by 0 raises an error.
 =	Equals. Pop x and y off the stack, and push 1 if y = x, and 0 otherwise.
 ) (	Greater than and less than, respectively. Pop x and y off the stack, and push 1 if y operator x, and 0 otherwise.
 ' "	Single and double quote - enable string parsing. String parsing pushes every character found to the stack until it finds a closing quote.
Stack manipulation
 :	Duplicate the top value on the stack.
 ~	Remove the top value from the stack.
 $	Swap the top two values on the stack
 @	Swap the top three values on the stack, shifting them rightwards (e.g. if your stack is 1,2,3,4, calling @ results in 1,4,2,3)
 } {	Shift the entire stack to the right and left, respectively. (e.g. when having 1,2,3,4, calling } results in 4,1,2,3 while { results in 2,3,4,1)
 r	Reverse the stack.
 l	Push the length of the stack onto the stack.
 [	Pop x off the stack and create a new stack, moving x values from the old stack onto the new one. See Stacks.
 ]	Remove the current stack, moving its values to the top of the underlying stack.
Input/output
See Input/output.

 o n	Pop and output as a character and a number, respectively. Output is written to stdout.
 i	Read one character from stdin and push it to the stack. The character should not be shown when read from console. When no more input is available, -1 is pushed.
Reflection/miscellaneous
 &	Pop the top value off the stack and put it in the register. Calling & again will take the value in the register and put it back on the stack. See The register.
 g	Pop y and x off the stack, and push the value at x,y in the codebox. Empty cells are equal to 0.
 p	Pop y, x, and v off the stack, and change the value at x,y to v. E.g. 123p puts 1 at 2,3 in the codebox.
 ;	End execution
