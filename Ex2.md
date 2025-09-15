# Ex.No:2
# Ex.Name: Write a CPP program for Infix To Postfix Conversion using Stack STL
## Aim:
To write a C++ program to convert an infix expression into a postfix expression using the Stack STL.

## Algorithm:
1. Start the program.
2. Define a function precedence(op) to return precedence of operators (+,- = 1, *,/ = 2, ^ = 3).
3. Traverse the infix expression character by character:
4. If the character is an operand → append to postfix string.
5. If the character is ( → push onto stack.
6. If the character is ) → pop from stack until ( is found.
7. If the character is an operator → pop from stack while top of stack has greater or equal precedence, then push current operator.
8. After traversing, pop all remaining operators from stack and append to postfix expression.
9. Print the final postfix expression.
10. Stop the program.

## Program:
```cpp
#include <iostream>
#include <stack>
#include <string>
#include <cctype>

using namespace std;
int precedence(char op) {
    switch (op) {
        case '+':
        case '-':
            return 1;
        case '*':
        case '/':
            return 2;
        case '^':
            return 3;
        default:
            return 0;
    }
}
bool isOperator(char c) {
    return (c == '+' || c == '-' || c == '*' || c == '/' || c == '^');
}
string infixToPostfix(const string &infix) {
    stack<char> s;
    string postfix = "";

    for (char c : infix) {
        if (isspace(c)) {
            continue; // Skip spaces
        } else if (isdigit(c) || isalpha(c)) {
            postfix += c; // Add operands to postfix expression
        } else if (c == '(') {
            s.push(c); // Push '(' onto stack
        } else if (c == ')') {
            // Pop and output from the stack until '(' is encountered
            while (!s.empty() && s.top() != '(') {
                postfix += s.top();
                s.pop();
            }
            s.pop(); 
        } else if (isOperator(c)) {
            while (!s.empty() && precedence(s.top()) >= precedence(c)) {
                postfix += s.top();
                s.pop();
            }
            s.push(c); 
        }
    }
    while (!s.empty()) {
        postfix += s.top();
        s.pop();
    }

    return postfix;
}

int main() {
    string infix;
    getline(cin, infix);

    string postfix = infixToPostfix(infix);
    cout << "Postfix is : " << postfix << endl;

    return 0;
}
```


## Output:
<img width="460" height="224" alt="image" src="https://github.com/user-attachments/assets/7b7de62d-55cb-4e96-88f3-404e803accc4" />

## Result:
The program successfully converts an infix expression into its equivalent postfix expression using a stack with the help of operator precedence and parentheses handling.
