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
- [LCM](#LCM)
- [HCF](#HCF)
- [prime factorisation](#prime-factorisation)
- [Division method]()
- [fraction types](#fraction-types)
- [Addition & subtraction of fractions](#add-sub-fractions)
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
```cpp
#include <bits/stdc++.h>
using namespace std;

int types_of_number(int n){
    if(n == int(n)){
        cout << n << " is an integer number " ;
    }
    else if(n == int(n) && n >= 0 ){
        cout << n << " is an whole number " ;
    }
    else if(n == int(n) && n > 0){
        cout << n << " is an natural number " ;
    }
      
    return 0;
}

int main(){
    int n;
    cout << "enter first number : ";
    cin >> n ;

    types_of_number(n);
}
```

### even odd 
```cpp
#include <bits/stdc++.h>
using namespace std;

int even_odd(int n){
    if(n%2 == 0){
        cout << n << " is even number " ;
    }
    else{
        cout << n << " is odd number " ;
    }
    
    return 0;
}

int main(){
    int n;
    cout << "enter first number : ";
    cin >> n ;

    even_odd(n);
}
```

### Greater than less than equal to
```cpp
#include <bits/stdc++.h>
using namespace std;

int greater_less_equal(int m,int n){
    if(m > n){
        cout << m << " is greater than " << n ;
    }
    if(m < n){
        cout << n << " is greater than " << m ;
    }
    if(m == n){
        cout << m << " is equal to " << n ;
    }
    return 0;
}

int main(){
    int n;
    cout << "enter first number : ";
    cin >> n;
    int m;
    cout << "enter second number : ";
    cin >> m;
    
    greater_less_equal(m , n);
}
```

### Ascending descending
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> descending(vector<int>& arr ,int n){  
    cout << "the array descending order ";
    for(int i=0; i<n-1; i++){
        for(int k=0; k<n-1-i; k++){
            int temp = arr[i];
            if(arr[k] < arr[k+1]){
                temp = arr[k];
                arr[k] = arr[k+1];
                arr[k+1] = temp;
            }
        }
    }
    return arr;
}

vector<int> ascending(vector<int>& arr ,int n){  
    cout << "the array ascending order ";
    for(int i=0; i<n-1; i++){
        for(int k=0; k<n-1-i; k++){
            int temp = arr[i];
            if(arr[k] > arr[k+1]){
                temp = arr[k];
                arr[k] = arr[k+1];
                arr[k+1] = temp;
            }
        }
    }
    return arr;
}

void display(vector<int>& arr,int n) {
    for (int i = 0;i< n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main(){
    int n;
    cout << "size of array : ";
    cin >> n ;

    vector<int> arr(n);
    for(int i=0 ; i<n ; i++){
        cin >> arr[i];
    }

    ascending(arr, n);
    display(arr,n);
    cout << endl ;
    descending(arr , n);
    display(arr,n);
}
```

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
#### lcm with hcf 
```cpp
#include <bits/stdc++.h>
using namespace std;

int hcf(vector<int> &arr,int n){
    set<int> temp;
    int mn = *min_element(arr.begin(), arr.end());

    for(int i=1;i<=mn;i++){ //checking upto smallest number as hcf cant be greater than smallest number
        bool iscommon = true ;

        for(int j= 0;j<n;j++){
            if(arr[j]%i != 0){
                iscommon = false;
                break;
            }
        }

        if(iscommon){
            temp.insert(i);
        }
    }
    int multiply = 1;
    for (int x : arr) {
        multiply *= x;   // update the SAME variable
    }

    int hcfm = *temp.rbegin();
    
    //LCM(a,b)=   ∣a×b∣ / GCD(a,b);
    int lcm = multiply / hcfm ;

return lcm ;
}

int main() {
    int n;
    cout << "how many numbers : ";
    cin >> n;
    
    vector<int> arr(n);
    for(int i=0;i<n;i++){
        cin >> arr[i];
    }


    cout << "hcf: ";
    int answer = hcf(arr,n);
    cout << answer ;
    
    return 0;
}
```
#### lcm brute force 
* prime-factor–style logic
```cpp

```

### HCF
#### hcf brute force 
```cpp
#include <bits/stdc++.h>
using namespace std;

int hcf(vector<int> &arr,int n){
    set<int> temp;
    int mn = *min_element(arr.begin(), arr.end());      //checking upto smallest number as hcf cant be greater than smallest number

    for(int i=1;i<=mn;i++){
        bool iscommon = true ;

        for(int j= 0;j<n;j++){ //check i devides all elements
            if(arr[j]%i != 0){
                iscommon = false;    //break if any one element found which is not devisible 
                break;
            }
        }

        if(iscommon){
            temp.insert(i); // if devides every element insert in temp set 
        }
    }
    
    int hcfm = *temp.rbegin();

return hcfm ;
}

int main() {
    int n;
    cout << "how many numbers : ";
    cin >> n;
    
    vector<int> arr(n);
    for(int i=0;i<n;i++){
        cin >> arr[i];
    }


    cout << "hcf: ";
    int answer = hcf(arr,n);
    cout << answer ;
    
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

#### fraction types
```cpp
#include <bits/stdc++.h>
using namespace std;

int properandimproper(int numerator,int denominator){
    if(numerator < denominator){
        cout << "proper fraction";
    }
    if(numerator >= denominator){
        cout << "improper fraction";
    }
    int remainder = numerator%denominator ;
    if(remainder != 0){
        cout << "mixed fraction";
    }
   return 1;
}

int main() {
    int p;
    cout << "enter numerator : ";
    cin >> p;
    
    int q;
    cout << "enter denominator : ";
    cin >> q;

    cout << "the fraction is : ";
    properandimproper(p,q);

    return 0;
}
```
### add sub fractions
```cpp
#include <bits/stdc++.h>
#include <numeric>
using namespace std;

int findLCM(vector<int>& den) {
    int lc = den[0];
    for (int i = 1; i < den.size(); i++) {
        lc = lcm(lc, den[i]);
    }
    return lc;
}

int fractionadd(vector<int>& num, vector<int>& den, int l) {
    int sum = 0;
    for (int i = 0; i < num.size(); i++) {
        sum += num[i] * (l / den[i]);
    }
    return sum;
}

int fractionsub(vector<int>& num, vector<int>& den, int l) {
    int sub = num[0] * (l / den[0]);
    for (int i = 1; i < num.size(); i++) {
        sub -= num[i] * (l / den[i]);
    }
    return sub;
}

int main() {
    int n;
    cout << "How many fractions: ";
    cin >> n;

    vector<int> num(n), den(n);

    for (int i = 0; i < n; i++) {
        cout << "Enter numerator: ";
        cin >> num[i];
        cout << "Enter denominator: ";
        cin >> den[i];
    }

    int l = findLCM(den);

    cout << "Addition = " << fractionadd(num, den, l) << "/" << l << endl;
    cout << "Subtraction = " << fractionsub(num, den, l) << "/" << l << endl;

    return 0;
}

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






