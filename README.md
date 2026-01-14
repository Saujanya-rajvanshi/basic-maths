# basic-maths

## INDEX
- [checklist](#checklist)
- [number place value and face value](#number-place-value-and-face-value)
- [Types of Numbers](#types-of-numbers)
- [Even and odd numbers](#even-odd)
- [Greater than less than equal to](#Greater-than-less-than-equal-to)
- [Ascending & descending order](#Ascending-descending)
- [calculator](#calculator)
- [Factors](#factors-of-a-number)
- [multiples](#multiples)
- [prime numbers](#prime-number)
- [composite numbers](#composite-numbers)
- [HCF](#HCF)
- [LCM](#LCM)
- [prime factorisation](#prime-factorisation)
- [Division method]()
- [ ] **Fractions**
  - [ ] Proper & improper fractions
  - [ ] Mixed fractions
  - [ ] Addition & subtraction of fractions
- [ ] **Decimals**
  - [ ] Decimal place value
  - [ ] Operations on decimals
  - [ ] Conversion: fraction ↔ decimal
- [loss or profit by cp and sp](#loss-or-profit-by-cp-and-sp)
- [validation of triangle](#validation-of-triangle)
- [Arithmetic progression](#Arithmetic-progression)
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
    long long int n;
    cout << "enter the number : ";
    cin >> n;

    cout << "find place value of : ";
    int pn;
    cin >> pn;

    long long int place = 1;
    long long int temp = n;   

    while (temp != 0) {

        int p = temp % 10;

        if (p == pn) {
            cout << "place value of " << pn << " in " << n << " is :" << place << " place";
            break;
        }

        temp = temp / 10;
        place = place * 10;
    }

    return 0;
}

```
### types of numbers

### even odd 

### Greater than less than equal to

### Ascending descending

### calculator
```cpp
#include<iostream>
using namespace std;

void calculator(){
    cout << "hello its your calculator";
    cout << endl ;
    cout<< "select any operator" << endl << "+ - * / ";
    char opr ;
    cin >> opr ;
    int a, b;
    cout << "enter the first numbers";
    cin >> a;
    cout << "enter the second number";
    cin >> b;
    int answer;
    if ( opr == '+'){
        answer = a+b;
    }
    else if( opr == '-'){
        answer = a-b;
    }
    else if ( opr == '*'){
        answer = a*b;
    }
    else if ( opr == '/'){
        int rem ;
        rem = a % b ;
        cout << " remainer : " << rem ;
        answer = a/b ;
        cout << endl ;
        cout << " quotient : " ;
        
    }
    cout << "your answer  : " << answer;
    cout << endl << endl ;
}

int main(){
    int t;
    cin >> t;
    for(int i=0; i<t; i++){
        calculator();
    }
    return 0;
}
```

### factors of a number
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
### multiples 
```cpp
#include<iostream>
using namespace std;

int multiples(int n, int k){
    cout << "your multiples are :\n"; 
    for (int i=1;i<=k;i++){
        cout << i*n << " ";
    }
    return 0;
}

int main(){
    cout << "enter the number";
    int n;
    cin >> n;
    cout << "how may nultiples do you want";
    int k;
    cin >> k;

    multiples(n,k);

    return 0;
}
```


### prime number
```cpp
#include<iostream>
using namespace std;

int main(){
cout<< " hello world";
    // new line
cout << endl ;
cout << "\n";
int n; 
cin >> n;
int i;
for( i = 2;i < 10000000 ;i++ ){
    if(n%i == 0){
        break;
    }
}
if(i == n){
            cout << "prime number";
        }
else{
            cout << "not a prime number";
        }
return 0;
}
```

### composite numbers
```cpp
#include<iostream>
using namespace std;

int main(){
cout<< " hello world";
    // new line
cout << endl ;
cout << "\n";
int n; 
cin >> n;
int i;
for( i = 2;i < 10000000 ;i++ ){
    if(n%i == 0){
        break;
    }
}
if(i == n){
            cout << "not a composite number ";
        }
else{
            cout << "composite number";
        }
return 0;
}
```

### LCM

### HCF
```cpp
#include <iostream>
using namespace std;

int main() {
    int n,i;
    cout << "Enter number (n): ";
    cin >> n;
    int hcf;
    for(i=(n/2);i<n;i++){
        if(n%i==0){
            hcf=i;
        }
    }

    cout << "hcf: " << hcf;
    

    return 0;
}
```

### prime factorisation
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    for (int i = 2; i * i <= n; i++) { 
        while (n % i == 0) {
            cout << i << " ";
            n /= i;
        }
    }

    if (n > 1) {
        cout << n;
    }
}

//dont use i<= sqrt(n) it will result in double use i*i <= n
// dont check after half of number in factor question
// if n is prime number n%i  will not be equal to 0 and the thr no. itself will be printed

```



### loss or profit by cp and sp 
```cpp
    
#include <iostream>
using namespace std;
int main()
{
    int cp;
    cout<<"enter cost price :";
    cin>>cp;
    int sp;
    cout<<"enter selling price :";
    cin>>sp;
    
    if(cp<sp){
        cout<<"loss";
    }
    else{
        cout<<"profit";
    }

    return 0;
}
```

### validation of triangle 

```cpp
#include <iostream>
using namespace std;
int main()
{
    int a,b,c;
    cout<<"enter first side of the triangle ";
    cin>>a;
    cout<<"enter second side of the triangle ";
    cin>>b;
    cout<<"enter third side of the triangle ";
    cin>>c;
    if((a+b)>c &&(b+c)>a && (c+a)>b){
        cout<<"a valid triangle";
    }
    else {
        cout<<"not a valid triangle";
    }

    

    return 0;
}
```

### Arithmetic progression 

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, d, n;
    cout << "Enter first term (a): ";
    cin >> a;
    cout << "Enter common difference (d): ";
    cin >> d;
    cout << "Enter number of terms (n): ";
    cin >> n;

    cout << "Arithmetic Progression: ";
    for(int i = 0; i < n; i++) {
        cout << a + (i * d) << " ";
    }

    return 0;
}
```






