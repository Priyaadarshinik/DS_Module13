# Ex2 Conversion of the infix expression into postfix expression
## DATE:
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Start the program.
2. Initialize a stack and set the top index to -1.
3. Define the push() and pop() functions to add and remove elements from the stack.
4. Define the priority() function to assign priorities to operators.
5. Traverse the expression in the IntoPost() function, handling operands, parentheses, and operators.
7. After processing the expression, pop and print any remaining operators from the stack.
8. End..   

## Program:
```
/*
Program to convert the infix expression into postfix expression
Developed by: PRIYAADARSHINI K
RegisterNumber:  212223240126
*/
#include<stdio.h>
#include<ctype.h>

char stack[100];
int top = -1;

void push(char x)
{
   stack[++top] = x;
}

char pop()
{
    if(top==-1){
        return -1;
    }
    return stack[top--];
}
int priority(char x)
{
    if(x== '(') return 0;
    if(x == '&' || x == '|') return 1;
    if(x== '+' || x== '-') return 2;
    if(x=='*' || x == '/') return 3;
    if(x == '^') return 4;
    return 0;
}
char IntoPost(char *exp)
{
    char *e,temp;
    e = exp;
    while(*e != '\0'){
        if(isalnum(*e)){
            printf("%c ",*e);
        }
        else if(*e == '('){
            push(*e);
        }
        else if(*e == ')'){
            while(temp = pop()) != '(' ){
                printf("%c ",temp);
            }
        }
        else{
            while(priority(stack[top])>=priority(*e)){
                printf("%c ",pop(*e));
            }
            push(*e);
        }
        e++;
    }
    
    while(top != -1)
    {
       printf("%c ",pop());
    }return 0;
}


int main()
{
    char str[100] = "a+(b|c-(d/e^f)*g)&h";
    IntoPost(str);
    return 1;
}

```

## Output:
![image-1](https://github.com/user-attachments/assets/781b8e1d-51b3-474c-af62-d759e5f781db)


## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
