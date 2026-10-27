
#include <iostream>
#include <string>
using namespace std;

class Student { 
private:
    int rollNo;
    string name;
    float marks;
    static int count;

public:
    Student(int r, string n, float m) {
        this->rollNo = r;
        this->name = n;
        this->marks = m;
        count++;
    }

    inline void display() {
        cout << "Roll Number: " << this->rollNo << endl;
        cout << "Name: " << this->name << endl;
        cout << "Marks: " << this->marks << endl;
    }

    static void showCount() {
        cout << "Total Students: " << count << endl;
    }

    friend class StudentInfo;
};

int Student::count = 0;

class StudentInfo {
public:
    void showDetails(Student s) {
        cout << "Accessing Private Data Using Friend Class:" << endl;
        cout << "Student Name: " << s.name << endl;
        cout << "Student Marks: " << s.marks << endl;
    }
};

int main() {
    Student s1(101, "Amit", 85.5);
    Student s2(102, "Neha", 92.0);

    cout << "Student Record Management System" << endl;
    cout << "--------------------------------" << endl;

    cout << "\nStudent 1 Details:" << endl;
    s1.display();

    cout << "\nStudent 2 Details:" << endl;
    s2.display();

    cout << endl;
    Student::showCount();

    cout << endl;
    StudentInfo info;
    info.showDetails(s1);

    return 0;
}
