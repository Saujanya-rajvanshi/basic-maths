# Basic Maths


### basic maths codes

```
MATH
├── Digit Manipulation
├── Bit Manipulation
├── Number Properties
├── Carry Handling
├── Binary Search on Answer
├── Fast Exponentiation
├── Prime & Sieve
├── Factor & Divisibility
├── Number Pattern
└── Simulation
```

## 1. DIGIT MANIPULATION

- [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)  digit extraction $
- [9. palindrom number](https://leetcode.com/problems/palindrome-number/) reverse / compare $
- [258. Add Digits](https://leetcode.com/problems/add-digits/) digit sum / math trick $
- [2544. Alternating Digit Sum](https://leetcode.com/problems/alternating-digit-sum/) $
- [202. Happy Number](https://leetcode.com/problems/happy-number/) digit square sum $
- [1837. Sum of Digits in Base K](https://leetcode.com/problems/sum-of-digits-in-base-k/) $
- [1281. Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/) $
- [1323. Maximum 69 Number](https://leetcode.com/problems/maximum-69-number/) $

### 🧠 Pattern:
Digit Problems = Extract → Process → Rebuild <br><br>

1. Extract → n % 10 <br>
2. Remove → n / 10 <br>
3. Build → ans = ans * 10 + digit <br>
4. Traverse → right to left (default) <br>
5. Optional → string or divisor method <br>

* changing **int into string** : `string s = to_string(x);` **accessing** : `for(char c : s) { cout << c << " "; }` or by loop and : `s[i]` imdexing is from left to right
* **Build** : also reversing a integer : **manually** `rev = rev * 10 + digit`   or using **string manipulation** `string rev = s;` `reverse(rev.begin(), rev.end());`
* **add digit** until it becmes one digit number
```cpp
if(num == 0) return 0;   
return 1 + (num - 1) % 9;
```
* changing **string into int** : `int num = stoi(s);` **accsesing** : `int dig = s[i] - '0';`

### extra
* Left → Right traversal without string
```cpp
int div = 1;
while(num / div >= 10) div *= 10;

while(div > 0) {
    int digit = num / div;
    num %= div;
    div /= 10;
}
```

```cpp
while(num > 0) {
    digits.push_back(num % 10);
    num /= 10;
}
for(int d : digits) {
    cout << d << " ";
}
```

* Before rev * 10 → check overflow
```cpp
if(rev > INT_MAX/10 || rev < INT_MIN/10) return 0;
```

* Use set to detect cycle (repetition)
```cpp
unordered_set<int> seen;
// Some numbers never reach 1, they loop forever: 2 → 4 → 16 → 37 → 58 → 89 → 145 → 42 → 20 → 4 → ...
while(n != 1 && seen.find(n) == seen.end()){ // n is not in set → continue
    seen.insert(n);
```

* Time Complexity section : Most digit problems → O(digits) ≈ O(log n)

## 2. BIT MANIPULATION 

- [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/) bitt manipulation $
- [231. Power of Two](https://leetcode.com/problems/power-of-two/) bit / math $
- [342. Power of Four](https://leetcode.com/problems/power-of-four/) math + bit $
- [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) $
- [338. Counting Bits](https://leetcode.com/problems/counting-bits/) $
- [136. Single Number](https://leetcode.com/problems/single-number/)-[ex](https://chatgpt.com/s/t_69df4b2bdf488191846dd1939a3c2cfc) $
- [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
- [260. Single Number III](https://leetcode.com/problems/single-number-iii/)
- [combined single number solution](https://chatgpt.com/s/t_69df4d96672c819180edeefff5abf6c8)
- [268. Missing Number](https://leetcode.com/problems/missing-number/)
- [371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/) -[ex](https://chatgpt.com/s/t_69df5c903f7c819197279202fbf76222)
- [78. Subsets (bitmasking)](https://leetcode.com/problems/subsets/description/) -[ex](https://chatgpt.com/s/t_69e05501cc908191bcc653f7b4b34a85)
- [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/) -[ex](https://chatgpt.com/s/t_69e17d59d9508191959107059b8421f1)
- [421. Maximum XOR of Two Numbers](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)
- [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/description/) -[ex](https://chatgpt.com/s/t_69e181ed512c8191963648b562dbe504)
  
## 🔹 OPTIONAL (if time)
* Gray Code
* Subsets II

### 🧠 Pattern:

* 32 bit ans : `uint32_t` loop from 0 to < 32
* reverse   shift left , add , shift right 
```cpp
rev = (rev << 1) | (n & 1);
n >>= 1; 
```
* convert **int to bit** : bitset<32> b(n);
* convert **bit to string** : string s = b.to_string();
* **&  AND** → both 1 → 1 , used for extracting last bit 
```
n = 1011
    0001
---------
    0001  → 1
```
* **|  OR**  → any 1 → 1
```
bit = 1        bit = 0
 1010           1010
 0001           0000
------         ------
 1011           1010
```
* **^  XOR** → different → 1
* **~  NOT** → flip bits
* Shifts , majing space to add something 
    * <<  → left shift  → ×2
    * >>  → right shift → ÷2
* Core Bit Tricks 
    * Check ith bit  : (n >> i) & 1
    * Set ith bit : n | (1 << i)
    * Clear ith bit : n & ~(1 << i)
    * Toggle ith bit : n ^ (1 << i)
* Important Patterns
    * Remove last set bit : n = n & (n - 1)
    * Check power of 2 : n > 0 && (n & (n - 1)) == 0
    * Get lowest set bit : n & (-n)
* Count Bits :
    * Built-in
```cpp
__builtin_popcount(n)
__builtin_popcountll(n)
Counts number of `1`s in binary
```
    * Manual
```cpp
while(n){
    count += n & 1;
    n >>= 1;
}
```
    * Fast (Brian Kernighan)
```cpp
while(n){
    n = n & (n - 1);
    count++;
}
```
    * DP Bit Trick
```cpp
ans[i] = ans[i >> 1] + (i & 1)
```
    * XOR Properties
```text
a ^ a = 0
a ^ 0 = a
Used in:
    single number
    missing number
```








### extras 

* changing int to binary
```cpp
// using loop
string toBinary(int n) {
    string res = "";

    while(n > 0) {
        res += (n % 2) + '0';  // get last bit
        n /= 2;
    }

    reverse(res.begin(), res.end());
    return res;
}
```
```cpp
// using bit method
string toBinary(int n) {
    string res = "";

    while(n > 0) {
        res += (n & 1) + '0';  // last bit
        n >>= 1;
    }

    reverse(res.begin(), res.end());
    return res;
}
```
```cpp
#include <bitset>

bitset<32> b(n);
cout << b;
```



## 3. NUMBER PROPERTIES

### ✅ You did:

- [263. Ugly Number](https://leetcode.com/problems/ugly-number/)  prime factor check (2,3,5) $
- [326. Power of Three](https://leetcode.com/problems/power-of-three/description/)  math / division $
- [1523. Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/) $
- [507. Perfect Number](https://leetcode.com/problems/perfect-number/) $
- [728. Self Dividing Numbers](https://leetcode.com/problems/self-dividing-numbers/)
- [2520. Count Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/)

### 🧠 Pattern:

## 1. DIVISIBILITY & FACTOR LOGIC

### Core Idea

```text
If a % b == 0 → b is a factor of a
```

### Patterns

#### ➤ Factor Checking

* loop till √n
* use divisor pairs

```cpp
for(int i = 2; i <= n / i; i++) {
    if(n % i == 0) {
        // i and n/i are factors
    }
}
```

#### ➤ Problems

* Perfect Number
* Count Primes


### Key Property

```text
Factors come in pairs → (i, n/i)
```

## 2. PRIME FACTOR / FACTOR STRIPPING

### Core Idea

```text
Keep dividing by allowed factors
Check what remains
```

#### ➤ Template

```cpp
for(prime in allowed_primes) {
    while(n % prime == 0) {
        n /= prime;
    }
}
return n == 1;
```

#### ➤ Problems

* Ugly Number
* Power of Three

### Key Property

```text
If only allowed primes exist → number reduces to 1
```

## 3. DIGIT MANIPULATION + DIVISIBILITY

### Core Idea

```text
Break number into digits → apply logic on each digit
```

#### ➤ Template

```cpp
while(num > 0) {
    int digit = num % 10;

    // apply condition

    num /= 10;
}
```

#### ➤ Problems

* Self Dividing Numbers
* Count Digits That Divide a Number

### Key Properties

```text
digit = num % 10
num /= 10
digit != 0 (avoid division by zero)
```

## 4. RANGE COUNTING (MATH OPTIMIZATION)

### Core Idea

```text
Avoid loops → use formula
```

#### ➤ Odd Numbers

```cpp
(high + 1)/2 - (low / 2)
```

#### ➤ Problem

* Count Odd Numbers in an Interval Range

### Key Property

```text
Every 2 numbers → 1 odd
```

## 5. DIVISOR SUM / PERFECT NUMBER

### Core Idea

```text
Sum of proper divisors = number
```

#### ➤ Pattern

```cpp
sum = 1;

for(int i = 2; i <= n / i; i++) {
    if(n % i == 0) {
        sum += i;

        if(i != n/i)
            sum += n/i;
    }
}
```

#### ➤ Problem

* Perfect Number

### Key Property

```text
Use divisor pairs + avoid duplicates
```

## 6. POWER CHECK (REPEATED DIVISION)

### Core Idea

```text
Divide until 1 → only allowed factor should exist
```

#### ➤ Pattern

```cpp
while(n > 1) {
    if(n % k != 0) return false;
    n /= k;
}
return true;
```

#### ➤ Problems

* Power of Three
* Power of Two

### Key Property

```text
n = k^x
```


| Pattern           | Use When                  |
| ----------------- | ------------------------- |
| Factor pairs      | divisors / perfect number |
| Factor stripping  | allowed primes            |
| Digit extraction  | digit-based problems      |
| Range formula     | counting problems         |
| Repeated division | power check               |

```text
Factors → √n loop  
Prime check → divide repeatedly  
Digits → %10, /10  
Range → formula  
Power → divide till 1
```




## 4. CARRY / NUMBER SYSTEM

- [67. Add Binary](https://leetcode.com/problems/add-binary/) $
- [66. Plus One](https://leetcode.com/problems/plus-one/) carry handling $
- [415. Add Strings]()

### 🧠 Pattern:

* add binary string

```cpp
        string res = "";
        int i = a.size() - 1;         // = 1
        int j = b.size() - 1;         // = 0
        int carry = 0;

        while(i >= 0 || j >= 0 || carry) {             // if any true       
            int sum = carry;                           // sum = 0              // sum = 1         // sum = 1

            if(i >= 0) sum += a[i--] - '0';            // i = 1  sum = 0 + 1 = '1'       // i = 0 sum = 1 + 1 = 2
            if(j >= 0) sum += b[j--] - '0';            // i = 0  sum = 1 + 1 = '2'       

            res.push_back((sum % 2) + '0');            // "0"                           // "001"
            carry = sum / 2;                           // carry = 2/2 = 1               // carry = 2/2 = 1
        }

        reverse(res.begin(), res.end());        // "100"
        return res;
```

* carry in binary array

```cpp
        int n = digits.size();      // n =  3  [1,2,9]

        for(int i = n-1; i >= 0; i--){        // i = 2         i = 1
            if(digits[i] < 9){                // 9 = 9  X      // 2 < 0
                digits[i]++;                                   // [1,3,0]
                return digits;                                 
            }
            digits[i] = 0;                    // [1,2,0]
        }
        digits.insert(digits.begin(), 1);
        return digits;
```

* add decimal string

```cpp
            res.push_back((sum % 10) + '0');           
            carry = sum / 10;
```



## 5. BINARY SEARCH ON ANSWER

- [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/) basic math / binary search $
- [367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/) binary search / math $
- [441. Arranging Coins]()

### 🧠 Pattern:

* sqrt
```cpp
    int i = 1;
        while(i <= x / i){
            i++;
        }
    return i - 1;
```
* arranging coins 
```cpp
        long long left = 0, right = n;

        while(left <= right) {
            long long mid = left + (right - left)/2;
            long long sum = mid * (mid + 1) / 2;

            if(sum == n) return mid;
            else if(sum < n) left = mid + 1;
            else right = mid - 1;
        }

        return right;
```

```cpp
        return (int)((-1 + sqrt(1 + 8LL * n)) / 2);
```


## 6. FAST MATHEMATICS

- [50. Pow(x, n)](https://leetcode.com/problems/powx-n/description/) fast exponentiation $
- [372. Super Pow](https://leetcode.com/problems/super-pow/)

### 🧠 Pattern:

```cpp
class Solution {
public:
    double myPow(double x, int n) {

        long long pow = n;

        if(pow < 0){
            x = 1/x;    // handling negative power 
            pow = -pow;  // making n positive pow = n
        }

        double ans = 1;

        while(pow > 0){
            if(pow % 2 == 1){   // odd
                ans *= x;
            }
            x *= x;            // square
            pow /= 2;          //x^n = (x^2)^(n/2)
        }
        
    return ans;
    }
};
```

```cpp
class Solution {
public:
    int mod = 1337;

    int power(int x, int n) {
        int res = 1;
        x %= mod;

        while(n > 0) {
            if(n & 1) res = (res * x) % mod;
            x = (x * x) % mod;
            n >>= 1;
        }
        return res;
    }

    int superPow(int a, vector<int>& b) {
        int result = 1;

        for(int digit : b) {
            result = power(result, 10) * power(a, digit) % mod;
        }

        return result;
    }
};
```



## 7. PRIME & SIEVE

- [204. Count Primes]() sieve of eratostheness

### 🧠 Pattern:

* sieve of eratosthenes

### 🔥 Add:

* **2523. Closest Prime Numbers in Range**
* **1175. Prime Arrangements**

## 8. FACTOR & DIVISIBILITY

- [172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/) count 5s $
- [1006. clumsy factorial](https://leetcode.com/problems/clumsy-factorial/) $
- [1492. The kth Factor of n](https://leetcode.com/problems/the-kth-factor-of-n/)
- [2427. Number of Common Factors](https://leetcode.com/problems/number-of-common-factors/)

### 🧠 Pattern:

* count factors

* find zero
```cpp
while(n > 0){        // 5 > 0  
            n /= 5;          // n = 5/5 = 1
            count += n;      // count = 0 + 1;
        }
```

* divide repeatedly

* clumsy factorial
```cpp
  while(i >= 1){                        // 4 > 1    // 0<1   X
            int mul = i;                      // mul = 4
            if(i-1 > 0) mul *= (i-1);         // 3 > 0 , mul = 4*3 = 12

            int dev = mul;                    // dev = 3 
            if(i-2 > 0) dev /= (i-2);         // 2 > 0 , dev = 12/2 = 6

            if(firstBlock){                   // first block = true
                result += dev;                // result = 6
                firstBlock = false;
            } else {
                result -= dev;
            }
            if(i-3 > 0)                       // 1 > 0
                result += (i-3);              // result = 6 + 1 = 7
            i -= 4;                           // i = 4 - 4 = 0

        }
```

* common factors
```cpp
int m = min(a,b);
        int count = 0 ;
        for(int i = 1;i <= m ;i++){
            if(a%i == 0 && b%i == 0){
                count += 1;
            }
        }
```


## 9. NUMBER PATTERN / INDEXING

- [400. Nth Digit](https://leetcode.com/problems/nth-digit/) number pattern $
- [168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)
- [171. Excel Sheet Column Number]()

### 🧠 Pattern:

* nth digit
```cpp
class Solution {
public:
    int findNthDigit(int n) {    // eg n = 250
        long long i = 1;         // digits per number
        long long count = 9;     // how many numbers in this group
        long long start = 1;     // starting number

    while(n > i * count) {     // 250 > 1 * 9 , 241 > 2 * 90 ,           [61 < 3 * 900] stop
        n -= i * count;        // remove digits of current group  ,  n = 250 - (1 * 9) = 241 , n = 241 - (2 * 90) = 61
        i += 1;                // move to next digit length  ,  i = 2 , i = 3
        count *= 10;           // numbers increase (9 → 90 → 900)  , count = 90 , count = 900
        start *= 10;           // starting number (1 → 10 → 100)  , start = 10 , start = 100 

        // Skip 1-digit → n = 250 - 9 = 241 Skip 2-dig it → n = 241 - 180 = 61
    }

    long long number = start + (n-1)/i;     // = 100 + (61-1)/3 = 120
    std::string s = std::to_string(number);      // s = "120"  s[0] = '1' , s[1] = '2' , s[2] = '0'
    return s[(n - 1) % i] - '0';    //  (61-1) % 3 = 60 % 3 = 0    which is = s[0] = 1 
    }
};
```
* number to asci
```cpp
class Solution {
public:
    string convertToTitle(int columnNumber) {
        string result = "";

        while (columnNumber > 0) {
            columnNumber--;  // adjust for 1-based indexing
            char ch = 'A' + (columnNumber % 26);
            result = ch + result;
            columnNumber /= 26;
        }

        return result;
    }
};
```



* asci to number
```cpp
class Solution {
public:
    int titleToNumber(string columnTitle) {
        int result = 0;

        for (char ch : columnTitle) {
            result = result * 26 + (ch - 'A' + 1);
        }

        return result;
    }
};
```









## 10. SIMULATION / FORMULA

- [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/) $
- [2652. Sum Multiples](https://leetcode.com/problems/sum-multiples/) $
- [1342. Number of Steps to Reduce a Number to Zero]()

### 🧠 Pattern:

```cpp
class Solution {
public:
    vector<string> fizzBuzz(int n) {                         // n = 3
        vector<string> ans;                                    
        for(int i = 1 ; i <= n ;i++){                        // i = 1 , i = 2 , i = 3
            if(i%3 == 0 || i%5 == 0){                        // X   , X  , true
                if(i%3 == 0 && i%5 == 0) {                   //   ,    ,   X 
                    ans.push_back("FizzBuzz");
                }
                else if(i%3 == 0) ans.push_back("Fizz");     // 3%3 = 0
                else if(i%5 == 0) ans.push_back("Buzz");     //   ,     ,  X
            }
            else ans.push_back(to_string(i));                 // push 1, push 2
        }
    return ans;      // ans = 1, 2, "Fizz"
    }
};
```






### learnings 
* reverse
* changing num to string and string to binary
* changing binary to int and int to binary  
* carry handling 
* modulo 9
* extracting digits from string left to right 
```cpp
for(int i = 0; i < s.size(); i++){  // left to right
            int dig = s[i] - '0';   // subtract '0' to convert char → integer
```
* power





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
class Solution {
public:
    double myPow(double x, int n) {

        long long pow = n;

        if(pow < 0){
            x = 1/x;    // handling negative power 
            pow = -pow;  // making n positive pow = n
        }

        double ans = 1;

        while(pow > 0){
            if(pow % 2 == 1){   // odd
                ans *= x;
            }
            x *= x;            // square
            pow /= 2;          //x^n = (x^2)^(n/2)
        }
        
    return ans;
    }
};
```

* add digit
```cpp
    int addDigits(int num) {
        if(num == 0) return 0;   
        return 1 + (num - 1) % 9; 
   }
```

* add sub alternatively
```cpp
    int alternateDigitSum(int n) {
        string s = to_string(n); // convert int to string 
        int sum = 0;

        for(int i = 0; i < s.size(); i++){  // left to right
            int dig = s[i] - '0';   // subtract '0' to convert char → integer

            if(i % 2 == 0) sum += dig;
            else sum -= dig;
        }

        return sum;
    }
```

* Add Binary
```cpp
    string addBinary(string a, string b) {
        string res = "";
        int i = a.size() - 1;
        int j = b.size() - 1;
        int carry = 0;

        while(i >= 0 || j >= 0 || carry) {
            int sum = carry;

            if(i >= 0) sum += a[i--] - '0';
            if(j >= 0) sum += b[j--] - '0';

            res.push_back((sum % 2) + '0');
            carry = sum / 2;
        }

        reverse(res.begin(), res.end());
        return res;
```

for finding if a number n is power of a number x 
```cpp
        if(n <= 0) return false;
        while(n > 1){
            if(n%x != 0) return false;
            n = n / x;
        }
```

```cpp 
    bool isPerfectSquare(int num) {
        long long left = 1, right = num;

        while(left <= right) {
            long long mid = left + (right - left) / 2;
            long long sq = mid * mid;

            if(sq == num) return true;
            else if(sq < num) left = mid + 1;
            else right = mid - 1;
        }

        return false;
    }

```

* perfect aquare 
```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        if(num <= 1) return false;

        long long sum = 1;

        for(int i = 2; i <= num / i; i++) {
            if(num % i == 0) {
                sum += i;

                if(i != num / i) {
                    sum += num / i;
                }
            }
        }

        return sum == num;
    }
};
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








## modulo 9 

* Any number `% 9` is equal to the **sum of its digits % 9**
* Repeating digit sum doesn’t change this remainder
* So final single digit = **num % 9**
* But if `% 9 == 0`, answer should be **9 (not 0)**

👉 That’s why we use:

```cpp
1 + (num - 1) % 9
```

---

👉 **One-liner:**
*Digit sum repeatedly reduces a number without changing its mod 9 value.*
















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






