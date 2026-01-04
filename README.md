# basic-maths

### INDEX
- [checklist](#checklist)
- [number place value and face value](#number-place-value-and-face-value)

######  Checklist

# 📝 Aptitude Learning Checklist

## 🧮 Level 0: Number Foundations
- [x] **Number System – Basics**
  - [x] Counting numbers
  - [x] Reading & writing numbers
  - [x] Place value (ones, tens, hundreds, thousands)
  - [x] Face value vs place value
  - [x] Number names
- [x] **Types of Numbers**
  - [x] Natural numbers
  - [x] Whole numbers
  - [x] Even & odd numbers
  - [x] Zero concept
- [x] **Comparison of Numbers**
  - [x] Greater than, less than, equal to
  - [x] Number line
  - [x] Ascending & descending order

## ➕ Level 1: Basic Operations
- [x] **Addition**
  - [x] Single digit
  - [x] Multi-digit
  - [x] Word problems
- [x] **Subtraction**
  - [x] Borrow method
  - [x] Difference between numbers
  - [x] Word problems
- [x] **Multiplication**
  - [x] Tables (1–20)
  - [x] Single × multi digit
  - [x] Properties of multiplication
- [ ] **Division**
  - [x] Simple division
  - [x] Remainder & quotient
  - [x] Division checks

## 🔢 Level 2: Core Number Skills
- [x] **Factors & Multiples**
  - [x] Factors
  - [x] Multiples
  - [x] Prime numbers
  - [x] Composite numbers
- [x] **HCF & LCM**
  - [x] Prime factorization
  - [x] Division method
  - [x] Real-life problems
- [ ] **Fractions**
  - [ ] Proper & improper fractions
  - [ ] Mixed fractions
  - [ ] Addition & subtraction of fractions
- [ ] **Decimals**
  - [ ] Decimal place value
  - [ ] Operations on decimals
  - [ ] Conversion: fraction ↔ decimal

## 📊 Level 3: Commercial Math
- [ ] **Percentages**
  - [ ] Basics
  - [ ] Increase & decrease
  - [ ] Percentage comparison
- [ ] **Ratio & Proportion**
  - [ ] Ratios
  - [ ] Proportions
  - [ ] Direct & inverse proportion
- [ ] **Profit, Loss & Discount**
  - [ ] Cost price, selling price
  - [ ] Profit % & loss %
  - [ ] Successive discount
- [ ] **Simple Interest**
  - [ ] Formula
  - [ ] Time, rate, principal problems
- [ ] **Compound Interest**
  - [ ] Annual & half-yearly
  - [ ] Difference between SI & CI

## ⏱️ Level 4: Time & Work
- [ ] **Time & Work**
  - [ ] Work efficiency
  - [ ] Combined work
  - [ ] Pipes & cisterns
- [ ] **Time, Speed & Distance**
  - [ ] Speed formula
  - [ ] Relative speed
  - [ ] Trains, boats & streams

## 📐 Level 5: Basic Algebra & Geometry
- [ ] **Algebra Basics**
  - [ ] Variables
  - [ ] Simple equations
  - [ ] Linear equations
- [ ] **Geometry Basics**
  - [ ] Lines & angles
  - [ ] Triangles
  - [ ] Quadrilaterals
  - [ ] Circles
- [ ] **Mensuration**
  - [ ] Perimeter
  - [ ] Area
  - [ ] Volume (cube, cuboid, cylinder)

## 📈 Level 6: Data & Logical Thinking
- [ ] **Data Interpretation (DI)**
  - [ ] Tables
  - [ ] Bar graphs
  - [ ] Pie charts
  - [ ] Line graphs
- [ ] **Averages**
  - [ ] Simple average
  - [ ] Weighted average
- [ ] **Permutation & Combination (Basics)**
  - [ ] Arrangements
  - [ ] Selections
- [ ] **Probability (Basic)**
  - [ ] Simple probability
  - [ ] Real-life examples

## 🧠 Level 7: Logical Aptitude
- [ ] Number series
- [ ] Coding–decoding
- [ ] Blood relations
- [ ] Directions
- [ ] Syllogism
- [ ] Puzzles

### number place value and face value
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "enter the number : ";
    cin >> n;

    cout << "find place value of : ";
    int pn;
    cin >> pn;

    int place = 1;
    int temp = n;   

    while (temp != 0) {

        int p = temp % 10;

        if (p == pn) {

            if (place == 1) {
                cout << "place value of " << pn << " in " << n << " is : ones.";
            }

            if (place == 10) {
                cout << "place value of " << pn << " in " << n << " is : tens.";
            }

            if (place == 100) {
                cout << "place value of " << pn << " in " << n << " is : hundreds.";
            }

            if (place == 1000) {
                cout << "place value of " << pn << " in " << n << " is : thousands.";
            }

            if (place == 1) {
                cout << "place value of " << pn << " in " << n << " is : ten thousands.";
            }

            if (place == 1) {
                cout << "place value of " << pn << " in " << n << " is : hundread thousands.";
            }

            if (place == 1) {
                cout << "place value of " << pn << " in " << n << " is : milions.";
            }

            break;
        }

        temp = temp / 10;
        place = place * 10;
    }

    return 0;
}

```




#### factors of a number
```cpp
#include <bits/stdc++.h>
using namespace std;


        
int main() 
{
   
    int n;
    cin >> n;

    for(int i = 1; i <= sqrt(n);i++) {
    if (n%i == 0){ 
        cout << (i);
        if(n%i != 0){ 
           cout << (n/i);
        }   
    }
    }  

    
    return 0;
}
```
