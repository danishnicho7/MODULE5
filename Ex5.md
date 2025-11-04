# Ex.No:5
# Ex.Name: Write a C++ program to illustrate Student Based Multiple inheritance with protected access specifier, find the student total marks. 
## Date:04/09/25

## Aim:
To write a C++ program to illustrate Student Based Multiple Inheritance with protected access specifier and find the total marks of a student.

## Algorithm:
1. Start the program.
2. Create a base class Subject with protected data members for two subject marks and a function to read them.
3. Create another base class Cocurricular with protected data member for cocurricular points and a function to read it.
4. Derive a class Student from both Subject and Cocurricular.
5. In the derived class, define a function to calculate the total marks (sum of subject marks and cocurricular points).
6. Display the total marks.
7. Stop the program.

## Program:
```cpp
#include <iostream>
using namespace std;
class SubjectMarks {
protected:
    int mark1, mark2;
public:
    void getMarks(int m1, int m2) {
        mark1 = m1;
        mark2 = m2;
    }
};
class Cocurricular {
protected:
    int points;
public:
    void getPoints(int p) {
        points = p;
    }
};
class Student : public SubjectMarks, public Cocurricular {
public:
    void calculateTotal() {
        int total = mark1 + mark2 + points;
        cout << "The total marks of the students is " << total << endl;
    }
};

int main() {
    Student s;
    int m1, m2, p;

    cin >> m1 >> m2 >> p;

    s.getMarks(m1, m2);
    s.getPoints(p);
    s.calculateTotal();

    return 0;
}
```



## Output:
<img width="696" height="314" alt="image" src="https://github.com/user-attachments/assets/d4bb7809-b683-4ee7-ae99-42b5210de6a3" />



## Result:
The program successfully demonstrates multiple inheritance with protected access specifier by calculating and displaying the total marks of a student using subject marks and cocurricular points.
