# Calculator-in-assembly-language

1) Title:
Building a Calculator in assembly language.
2) Objective: 
The purpose of this project is to develop a calculator as it supports correct calculations. It 
is clear that a calculator should relieve the user of the need to do mental operations. 
Using a calculator can help save a whole lot of computational time on basic arithmetical 
calculations. This makes it easier for them to stress more on important math concepts 
rather than stressing more on basic arithmetical calculations.
Calculator use can promote the higher-order thinking and reasoning needed for problem 
solving in our information- and technology-based society.
3) Implementation:
Firstly select the operation you want to perform. Next enter the operands using the 
keyboard. Result will be computed and will be displayed on the screen. The user will be 
asked whether they want to continue, if yes, the loop will run again. Calculator will 
restart. Then choose the operator and enter the operands.
9 different operations will be performed on the calculator.
1. Addition (+)
To choose the addition operation, enter 1, then enter the first and second 
number and display the result of addition.
2. Subtraction (-)
To choose the subtraction operation, enter 2, then enter the first and second 
number and display the result of subtraction.
3. Multiplication (*)
To choose the multiplication operation, enter 3, then enter the first and second 
number and display the result of multiplication.
4. Division (/)
To choose the division operation, enter 4, then enter the first and second number 
and display the result of division.
5. Modulo (%)
To choose modulo operation, enter 5, then enter the first and second number and 
display the result of Mod.
6. Factorial (!)
To choose the Factorial operation, enter 6, then enter any number between 0-7. 
Display the result of Factorial.
7. Square (n^2)
To choose the Square operation, enter 7, then enter the number to find and 
display the result of its square.
8. Cube (n^3)
To choose the cube operation, enter 8, then enter the number to find and display 
the result of its cube.
9. Complex Number (a+bi)+(c+di)
To choose the Complex Number operation, enter 9, then enter the first, second, 
third and fourth number. Display the result of its Complex Number.
10.Exit
To exit the calculator, enter 0.
4) Code:
include emu8086.inc
org 100h
.data 
 op1 db 10,13, '1 -> Addition ',13,10,'$'
 op2 db '2 -> Subtracion ',13,10,'$' 
 op3 db '3 -> Multiplication',13,10,'$'
 op4 db '4 -> Division ',13,10,'$' 
 op5 db '5 -> MOD ',13,10,'$' 
 op6 db '6 -> Factorial ',13,10,'$'
 op7 db '7 -> Square',13,10,'$' 
 op8 db '8 -> Cube',13,10,'$' 
 op9 db '9 -> Complec Addition (a+bi)+(c+di)',13,10,'$'
 op10 db '0 -> Exit ',13,10,'$' 
 option DB 10,13, 'Which operation do you want to perform? $' 
 
num1 dw ?
num2 dw ?
num3 dw ?
num4 dw ? 
RESULT dw ? 
.code
MAIN PROC 
 
 print ' ******************************' 
 printn 
 print ' SCIENTIFIC CALCULATER' 
 printn
 print ' ******************************'
 printn 
 printn 
 
 Menu: 
 MOV AX,@DATA
 MOV DS,AX
 
 LEA DX,op1
 MOV AH,9
 INT 21H
 
 LEA DX,op2
 MOV AH,9
 INT 21H
 
 LEA DX,op3
 MOV AH,9
 INT 21H
 
 LEA DX,op4
 MOV AH,9
 INT 21H 
 
 LEA DX,op5
 MOV AH,9
 INT 21H 
 
 LEA DX,op6
 MOV AH,9
 INT 21H 
 LEA DX,op7
 MOV AH,9
 INT 21H 
 
 LEA DX,op8
 MOV AH,9
 INT 21H 
 LEA DX,op9
 MOV AH,9
 INT 21H
 LEA DX,op10
 MOV AH,9
 INT 21H 
 LEA DX,option
 MOV AH,9
 INT 21H 
 printn 
 
 MOV AH,1
 INT 21H
 MOV BH,AL
 SUB BH,48
 
 CMP BH,1
 JE ADD
 
 CMP BH,2
 JE SUB
 
 CMP BH,3
 JE MUL
 
 CMP BH,4
 JE DIV 
 
 CMP BH,5
 JE MOD 
 
 CMP BH,6
 JE factorial
 
 CMP BH,7
 JE Square 
 
 CMP BH,8
 JE Cube
 
 CMP BH,9
 JE Complex
 
 CMP BH, 0
 printn
 
 JMP Return 
 
 ret 
 
 ADD:
 
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter 1st number = '
 call scan_num
 mov num1,cx 
 
 printn
 print 'Enter 2nd number = '
 call scan_num
 mov num2,cx
 
 mov ax,num1
 mov bx,num2
 ADD ax,bx 
 printn 
 printn 
 print 'Result of Addition = '
 call print_num
 
 JMP EXIT_P 
 
 SUB:
 
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter 1st number = '
 call scan_num
 mov num1,cx
 printn 
 print 'Enter 2nd number = '
 call scan_num
 mov num2,cx
 
 mov ax,num1
 mov bx,num2
 SUB ax,bx 
 
 mov RESULT,ax
 printn 
 printn 
 print 'Result of Subtraction = '
 call print_num
 
 JMP EXIT_P 
 
 MUL: 
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter 1st number = '
 call scan_num
 mov num1,cx
 printn 
 print 'Enter 2nd number = '
 call scan_num
 mov num2,cx
 
 mov ax,num1
 
 Mul num2 
 
 mov RESULT,ax
 printn 
 printn 
 print 'Result of Multiplication = ' 
 call print_num
 
 JMP EXIT_P 
 
 DIV:
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter 1st number = '
 call scan_num
 mov num1,cx
 printn 
 print 'Enter 2nd number = '
 call scan_num
 mov num2,cx
 
 mov dx,0
 mov ax,num1
 
 DIV num2 
 printn
 printn
 print 'Result of Division = '
 
 mov RESULT,ax
 call print_num 
 printn
 JMP EXIT_P 
 
 MOD: 
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter 1st number = '
 call scan_num
 mov num1,cx
 printn 
 print 'Enter 2nd number = '
 call scan_num
 mov num2,cx
 
 mov dx,0
 mov ax,num1
 
 DIV num2 
 printn
 printn 
 print 'Result of MOD = ' 
 mov ax,dx
 call print_num 
 
 JMP EXIT_P 
 
 factorial:
 
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter number between 0 to 7' 
 printn 
 
 print 'Enter number = '
 call scan_num
 mov num1,cx
 mov ax, num1
 mov bx,ax 
 L:
 dec bx
 mul bx
 cmp bx,1
 jne L
 mov cx,ax 
 printn
 printn
 print 'Result of Factorial = ' 
 call print_num 
 printn
 
 JMP EXIT_P
 
 Square:
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter number = '
 call scan_num
 mov num1,cx
 printn 
 mov bx,num1
 mul num1
 mov ax,bx
 Mul bx 
 printn 
 printn
 print 'Result of the Square of given number = ' 
 
 call print_num
 
 JMP EXIT_P 
 Cube:
 printn 
 print ' _______________________ '
 printn 
 printn
 
 print 'Enter number = '
 call scan_num
 mov num1,cx
 printn 
 mov bx,num1
 mul num1
 mov ax,bx
 Mul bx 
 Mul bx
 
 printn
 printn 
 print 'Result of the cube of given number = ' 
 call print_num
 
 JMP EXIT_P 
 
 Complex: 
 
 printn 
 print ' _______________________ '
 printn 
 printn 
 
 print 'Enter 1st number = '
 call scan_num
 mov num1 , cx 
 printn 
 print 'Enter 2nd number = '
 call scan_num 
 mov num2 , cx 
 printn
 print 'Enter 3rd number = ' 
 call scan_num
 mov num3 ,cx
 
 printn 
 print 'Enter 4th number = '
 call scan_num 
 mov num4 ,cx 
 mov ax,num1
 mov bx,num3
 add ax,bx
 printn 
 call print_num
 print '+'
 mov ax,num2
 mov bx,num4
 add ax,bx
 
 call print_num
 print 'i' 
 
 JMP EXIT_P 
 printn
 
 ret
 
 EXIT_P:
 printn
 printn 
 print ' _______________________ ' 
 
 printn
 print "Enter 0 to continue: " 
 MOV AH,1
 INT 21H
 MOV BH,AL
 SUB BH,48
 
 CMP BH,0
 JE menu 
 call Return
 
 Return:
 printn
 print ' *** Thank You ***'
 EXIT:
define_print_num
define_print_num_uns
define_scan_num 
 MOV AH,4CH
 INT 21H
 
END MAIN 


Output:

![image](https://user-images.githubusercontent.com/92652883/193628735-36087d61-b8ee-4ecd-8807-82bac054e789.png)


![image](https://user-images.githubusercontent.com/92652883/193628781-b3ba331c-e824-4cb1-9cbe-a03fa4c57c5f.png)



