# basic-maths


### basic maths codes 
- [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)  digit extraction $
- [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/) bitt manipulation $
- [9. palindrom number](https://leetcode.com/problems/palindrome-number/) reverse / compare $
- [66. Plus One](https://leetcode.com/problems/plus-one/) carry handling 
- [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/) basic math / binary search
- [50. Pow(x, n)](https://leetcode.com/problems/powx-n/description/) fast exponentiation
- [258. Add Digits](https://leetcode.com/problems/add-digits/) digit sum / math trick
- [202. Happy Number](https://leetcode.com/problems/happy-number/)  digit square sum
- [263. Ugly Number](https://leetcode.com/problems/ugly-number/)  prime factor check (2,3,5)
- [204. Count Primes]() sieve of eratosthenes
- [326. Power of Three](https://leetcode.com/problems/power-of-three/description/) math / division
- [231. Power of Two](https://leetcode.com/problems/power-of-two/) bit / math
- [342. Power of Four](https://leetcode.com/problems/power-of-four/) math + bit
- [367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/) binary search / math
- [400. Nth Digit](https://leetcode.com/problems/nth-digit/) number pattern
- [172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/) count 5s
- [1006. clumsy factorial](https://leetcode.com/problems/clumsy-factorial/)
- [258. Add Digits](https://leetcode.com/problems/add-digits/) 
- [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)
- [1523. Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)
- [231. Power of Two](https://leetcode.com/problems/power-of-two/)
- [326. Power of Three](https://leetcode.com/problems/power-of-three/)
- [202. Happy Number](https://leetcode.com/problems/happy-number/)



### learnings 
* reverse
* changing num to string and string to binary
* changing binary to int and int to binary  








### short forms

* reverse string
```cpp
        string s = to_string(x);
        reverse(rev.begin(), rev.end());
```

* reverse bits
```cpp
class Solution {
public:
    int reverseBits(int n) {
        string s = bitset<32>(n).to_string(); //number to binary 

        reverse(s.begin(), s.end()); //reverse

        int rev = 0;  

        for(char c : s) {    // binary to number 
            rev = rev * 2 + (c - '0');
        } 

        
    return rev;
    }
};
```
```cpp
//better
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t rev = 0;

        for(int i = 0; i < 32; i++) {
            rev = (rev << 1) | (n & 1);
            n >>= 1;
        }

        return rev;
    }
};
```





* insert digit 
```cpp
        digits.insert(digits.begin(), 1);
```


* sqrt
```cpp
    int mySqrt(int x) {
        int i = 1;
        while(i <= x / i){
            i++;
        }
    return i - 1;
    }
```

* pow(x,n)
```cpp
    double myPow(double x, int n) {

        long long pow = n;

        if(pow < 0){
            x = 1/x;
            pow = -pow;
        }

        double ans = 1;

        while(pow > 0){
            if(pow % 2 == 1){   // odd
                ans *= x;
            }
            x *= x;            // square
            pow /= 2;
        }
        
    return ans;
    }
```

* add digit
```cpp
    int addDigits(int num) {
        if(num == 0) return 0;   
        return 1 + (num - 1) % 9; 
   }
```









### concept

## 1. DIGIT MANIPULATION 

### Concepts:

* Extract digit → `n % 10`
* Remove digit → `n / 10`
* Build number → `ans = ans * 10 + digit`

### Questions:

* Reverse Integer
* Palindrome Number
* Add Digits
* Happy Number

### Patterns:

* Loop until `n == 0`
* Use slow-fast or set for cycles (Happy Number)

---

# 🔹 2. NUMBER PROPERTIES

### A. Even / Odd / Range

* Count Odd Numbers in Range
* Fizz Buzz

👉 Formula:

```
odd_count = (high + 1) / 2 - (low / 2)
```

---

### B. Power Problems

### Questions:

* Power of Two
* Power of Three
* Power of Four

### Patterns:

* Division loop → `while(n % k == 0)`
* Bit trick (only for power of 2):

```
n & (n - 1) == 0
```

---

### C. Perfect Square

### Questions:

* Valid Perfect Square
* Sqrt(x)

### Approach:

* Binary Search (IMPORTANT)
* Avoid `sqrt()` in interviews

---

# 🔹 3. CARRY & ARRAY NUMBER SYSTEM

### Questions:

* Plus One

### Pattern:

* Start from end
* Handle carry propagation

---

# 🔹 4. FAST MATHEMATICAL COMPUTATION

### A. Fast Exponentiation

### Question:

* Pow(x, n)

### Pattern:

```
if n is even → x^n = (x*x)^(n/2)
if n is odd → x * x^(n-1)
```

Time: **O(log n)**

---

# 🔹 5. PRIME & FACTORIZATION

### A. Prime Counting

### Question:

* Count Primes

### Concept:

* Sieve of Eratosthenes

---

### B. Factor-Based Problems

### Questions:

* Ugly Number
* Factorial Trailing Zeroes

### Patterns:

* Divide repeatedly by factors (2,3,5)
* Count 5s:

```
n/5 + n/25 + n/125 ...
```

---

# 🔹 6. NUMBER PATTERN / POSITION BASED

### Questions:

* Nth Digit

### Concept:

* Numbers grouped by digits:

  * 1-digit → 9 numbers
  * 2-digit → 90 numbers
  * 3-digit → 900 numbers

---

# 🔹 7. SIMULATION / FORMULA BASED

### Questions:

* Clumsy Factorial
* Fizz Buzz

### Approach:

* Follow rules carefully
* Optimize pattern after observing sequence

---

# 🔹 8. CYCLE DETECTION IN MATH

### Question:

* Happy Number

### Techniques:

* HashSet OR
* Floyd Cycle Detection (advanced)

---

# 🔹 9. IMPORTANT PATTERNS SUMMARY

### 🔥 Must Remember:

* Digit extraction → `% 10`
* Reverse → `ans * 10 + digit`
* Binary search on answer
* Fast exponentiation → log(n)
* Sieve → primes
* Factor counting → divide repeatedly
* Bit trick → power of 2

---

# 🔹 10. INTERVIEW STRATEGY

When you see a math problem, ask:

1. Can I reduce it to digits?
2. Is there a pattern or formula?
3. Can I use binary search?
4. Can I optimize brute force?
5. Is this a number property problem?

---

# 🔹 FINAL STRUCTURE (TREE VIEW)

```
MATH
├── Digit Manipulation
├── Number Properties
│   ├── Even/Odd
│   ├── Power
│   └── Perfect Square
├── Carry Handling
├── Fast Computation
├── Prime & Factors
├── Number Patterns
├── Simulation
└── Cycle Detection
```

---

# ⚡ Reality Check (Important)

No single note will make you solve *ALL* math problems.

What will:

* Practice + pattern recognition
* Revisiting mistakes
* Writing code from memory

---

If you want next step:
👉 I can create a **“pattern → code template sheet”** (super short, interview-ready).



## importants

### digit extraction : 
```
digit = x % 10
x = x / 10
rev = rev * 10 + digit
```

### if overflow
1. You are building a number digit by digit
2. The problem has a range constraint
3. You are using only int (32-bit)

add this :
```
if(rev > INT_MAX/10 || rev < INT_MIN/10) return 0;
```

## reversing an number by making string 
```
string s = to_string(x);
string rev = s;
reverse(rev.begin(), rev.end());
```

## carry handling
```
digits.insert(digits.begin(), 1);
```

## sqrt
```
int i = 1;
while(i <= x / i){
    i++;
}
```

## pow x,n 

```
class Solution {
public:
    double myPow(double x, int n) {
        if(n == 0) return 1;

        double real = x;

        long long a = n;
        if(n < 0){
            n = -n;
        }
        for(int i = 1; i < n ;i++){
            x = real*x;
        }
        if(a < 0){
            return 1/x;
        }
    return x;
    }
};
```
```
class Solution {
public:
    double myPow(double x, int n) {

        long long pow = n;

        if(pow < 0){
            x = 1/x;
            pow = -pow;
        }

        double ans = 1;

        for(int i = 0; i < pow ;i++){
            ans *= x;
        }
        
    return ans;
    }
};
```

```cpp
class Solution {
public:
    double myPow(double x, int n) {

        long long pow = n;

        if(pow < 0){
            x = 1/x;
            pow = -pow;
        }

        double ans = 1;

        while(pow > 0){
            if(pow % 2 == 1){   // odd
                ans *= x;
            }
            x *= x;            // square
            pow /= 2;
        }
        
    return ans;
    }
};
```

## add digit 

use modulo nine work foe addition , mul etc
```cpp
        if(num == 0) return 0;   
        return 1 + (num - 1) % 9; 
```

## digit square sum

repeatedly transform number,  <br>
Two possibilities: <br>
reaches 1 → happy number <br>
enters a cycle (loop) → never reaches 1 <- use set <br>

```
while(n != 1 && seen.find(n) == seen.end()) // Keep going until we reach 1 (happy number) && n is not in the set yet
```

## Ugly Number,  prime factor check (2,3,5)

```cpp
        while(n % 2 == 0) n /= 2;
        while(n % 3 == 0) n /= 3;
        while(n % 5 == 0) n /= 5;

        return n == 1;
```

## if you want to check idf it gets inside the loop
```
bool is = true;
            for(int j = 2; j < i; j++){
                if(i%j == 0){
                    is = false;
                    break;
```

## count prime


## if a number n is power of num 2/3/4

```cpp
int temp = n;
        if(n <= 0) return false;
        while(temp > 1){
            if(temp%num != 0) return false;
            temp = temp / num;
        }

    return true;
```

## factorial trailing zeroes 

```cpp
int count = 0;
while(n > 0){
    n /= 5;
    count += n;
}
return count;
```



Here are your **complete, clean notes (DSA-focused 🚀)** for all 4 conversions:

---

# 🔥 1. String → Integer

## ✅ Built-in

```cpp
int num = stoi(s);
```

---

## ✅ Manual (IMPORTANT 🔥)

```cpp
int num = 0;
for(char c : s) {
    num = num * 10 + (c - '0');
}
```

### 🧠 Core Idea

```
num = num * base + digit
(base = 10)
```

---

## ⚠️ With Negative

```cpp
int i = 0, sign = 1;
if(s[0] == '-') {
    sign = -1;
    i = 1;
}

int num = 0;
for(; i < s.size(); i++) {
    num = num * 10 + (s[i] - '0');
}

num *= sign;
```

---

# 🔥 2. Integer → String

## ✅ Built-in

```cpp
string s = to_string(num);
```

---

## ✅ Manual (IMPORTANT 🔥)

```cpp
string s = "";

while(num > 0) {
    s.push_back((num % 10) + '0');
    num /= 10;
}

reverse(s.begin(), s.end());
```

---

## ⚠️ Handle 0 & Negative

```cpp
if(num == 0) return "0";

bool neg = false;
if(num < 0) {
    neg = true;
    num = -num;
}

string s = "";
while(num > 0) {
    s.push_back((num % 10) + '0');
    num /= 10;
}

if(neg) s.push_back('-');
reverse(s.begin(), s.end());
```

---

# 🔥 3. Binary → Integer

## ✅ Built-in

```cpp
int num = stoi(s, 0, 2);
```

---

## ✅ Manual (MOST IMPORTANT 🔥)

```cpp
int num = 0;

for(char c : s) {
    num = num * 2 + (c - '0');
}
```

### 🧠 Core Idea

```
num = num * base + digit
(base = 2)
```

---

# 🔥 4. Integer → Binary

## ✅ Manual (MOST IMPORTANT 🔥)

```cpp
if(num == 0) return "0";

string s = "";

while(num > 0) {
    s.push_back((num % 2) + '0');
    num /= 2;
}

reverse(s.begin(), s.end());
```

---

## ✅ Using bitset

```cpp
string s = bitset<32>(num).to_string();
```

---

# 🧠 MASTER PATTERN (VERY IMPORTANT)

## ⭐ Universal Formula

```
num = num * base + digit
```

| Conversion   | Base |
| ------------ | ---- |
| String → Int | 10   |
| Binary → Int | 2    |

---

## ⭐ Reverse Conversion

```
digit = num % base
num = num / base
```

| Conversion   | Base |
| ------------ | ---- |
| Int → String | 10   |
| Int → Binary | 2    |

---

# 🚀 Interview Cheatsheet

* Use **manual method** → for DSA problems
* Use **built-in** → for normal coding
* Always remember:

  * `'0' → 48`, `'1' → 49`
  * so → `c - '0'`

---

# 🔥 Most Asked Mistakes

❌ Forgetting `reverse()`
❌ Not handling `0`
❌ Ignoring negative numbers
❌ Using wrong base

---

If you want next level:
👉 I can give **combined template (all conversions in one code)**
👉 or **top LeetCode questions using these patterns**
























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
- [Decimal place value](#Decimal-place-value)
- [Conversion fraction to decimal](#Conversion-fraction-to-decimal)
- [Percentages](#Percentages)
- []()
- [loss or profit by cp and sp](#loss-or-profit-by-cp-and-sp)
- [validation of triangle](#validation-of-triangle)
- [Arithmetic progression](#Arithmetic-progression)
Percentages
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
### Decimal place value
```cpp
#include <iostream>
using namespace std;

int main() {
    double n;
    cout << "enter the number : ";
    cin >> n;

    int intPart = (int)n;
    double fracPart = n - intPart;

    cout << "find place value of : ";
    int pn;
    cin >> pn;

    double temp = n;
    int count = 1;
    int digit = 0;
    
    for(int i = 0; i < 10; i++) {
        fracPart *= 10;
        digit = (int)fracPart;
        fracPart -= digit;
        count *= 10;
        
        if(digit == pn) {
            break;   // or do something
        }
    }

    cout << "you number " << pn << " has a place value : " << count << "th";

    return 0;
}
```
### Conversion fraction to decimal
```cpp
#include <iostream>
using namespace std;

int main() {
    int num ;
    cout << "enter the numerator : ";
    cin >> num ;

    int den ;
    cout << "enter the denominator : ";
    cin >> den ;

    double decimal = (double)num / den ;

    cout << num << "/" << den << "=" << decimal ;

    return 0;
}
```
### Percentages
```cpp
#include <iostream>
using namespace std;

int main() {
    int part ;
    cout << "enter the part : ";
    cin >> part ;

    int total ;
    cout << "enter the total : ";
    cin >> total ;

    float percentage = ((float)part / total) * 100;

    cout << part << " is " << percentage << "% of " << total ;

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






