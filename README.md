# C-Program-to-Find-the-Factors-of-a-Number

Factors of a Number in C
Here, in this page, we will discuss the program to find factors of a number in C programming language. We will discuss different methods to find the factors of the given number.

Example :

Input : 10
Output : 1, 2, 5, 10
Factors of a number in C
Methods Discussed
Method 1: Checking factors b/w [1, num]
Method 2: Checking factors b/w [1, num/2]
Method 3: Checking factors b/w [1, √num] and pair optimization
Method 4: Checking factors b/w [1, √num] and pair optimization with non jumbled result
Factors of a Number In C
Method 1 :
Run a loop from i=1 to i=n.
For, every i-th number check
If (num % i==0) then, print that number
Time and Space Complexity :
Time Complexity: O(n)
Space Complexity: O(1)
Code in C
Run
#include <stdio.h>


//main Program
int main()
{
    int n = 100;
    
    printf("Factors of %d are : \n", n);
    
    // finding and printing factors b/w 1 to num
    for(int i = 1; i <= n; i++)
    {
        // if n is divisible by i, then i is a factor of n
        if(n % i == 0)
            printf("%d, ", i);
    }
}
// Time Complexity: O(N)
// Space Complexity: O(1)
Output :
Factors of 100 are : 
1, 2, 4, 5, 10, 20, 25, 50, 100, 
Method 2 :
According to this method, all the divisors (Excluding the number itself) of the number are before n/2. 

Run a loop from i=1 to i=n/2.
For, every i-th number check
If (num % i==0) then, print that number
Finally print the number itself.
Time and Space Complexity :
Time Complexity: O(n)
Space Complexity: O(1)
Code in C
Run
#include <stdio.h>

int main()
{
    int num = 100;
    
    printf("Factors of %d are : \n", num);
    
    // finding and printing factors b/w 1 to num/2
    for(int i = 1; i <= num/2; i++)
    {
        // if num is divisible by i, then i is a factor of num
        if(num % i == 0)
            printf("%d, ", i);
    }
    
    // print the number itself too
    printf("%d", num);
    
    return 0;
}
// Time Complexity: O(N)
// Space Complexity: O(1)
// This method is better than previous method, even though the time complexity is the same
// it runs half lesser loop than previous method
// ran for loop num times, however, this runs num/2 times
Output :
Factors of 100 are : 
1, 2, 4, 5, 10, 20, 25, 50, 100, 
Related Pages
Factorial of a number

Power of a number

Factor of a number

Finding Prime Factors of a number

Strong number

Perfect number

While loop in C
Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
Method 3 :
Run a loop from i=1 to i=sqrt(n).
For, every i-th number check,
If (num%i==0) then, check if(num/i != i) then print i, otherwise print i and n/i
Note – Issue it prints the factors in jumbled order (check output)

Time and Space Complexity :
Time Complexity : O(sqrt(n))
Space Complexity : O(1)
Code in C
Run
#include <stdio.h>
#include <math.h>

void printFact(int n){
    
    for(int i = 1; i <= sqrt(n); ++i)
    {
        if (n % i == 0){
            
            // If both pair of factors are equal then we just print 
            // once, example for 100 : (a, b) : (10, 10) 
            // 10 should be printed just once
            if(i == n / i)
                printf("%d, ",i);
            
            // else print both the pairs
            else
                printf("%d, %d, ",i, n/i); 
        }
    }
}

int main()
{
    int n = 100;
    
    printFact(n);
}
// Time Complexity: O(sqrt(N))
// Space Complexity: O(1)
// Issue : The order of factors are jumbled
Output :
1, 100, 2, 50, 4, 25, 5, 20, 10,
Method 4 :
This method solves the problem caused by the previous method where factors were printed in jumbled order.

Time and Space Complexity :
Time Complexity : O(sqrt(n))
Space Complexity : O(1)
Code in C
Run
#include <stdio.h>
#include <math.h>

void printFact(int n){
    
    // Same i used in other for loop
    int i;
    // to avoid double printing
    int flag = 0;
    
    for(i = 1; i <= sqrt(n); i++) 
    { 
        if (n % i == 0) 
            printf("%d, ", i); 

        // To avoid double printing of equal pairs 
        // Example (10,10) we only want to print once 
        if(i == n/i) 
            flag = 1; 
    } 

    // if flag is '1' then we had double pairs like (10,10) 
    // we should do i-- so as not to do double printing of pair divisor 
    // doing i -=2 rather than i-- as in previous for loop we exited 
    // with i++, example, i = 10 became 11 and we need to start with 9 
    // so as to ignore 10 as its a double pair 
    if(flag) 
        i -= 2; 


    // printing pairs 
    for(;i>=1;i--)
    {
        if (n % i == 0)
            printf("%d, ", n/i);
    }
}

//main Program
int main()
{
    int n = 100;
    
    printFact(n);
}
// Time Complexity: O(sqrt(N))
// Space Complexity: O(1)
Output :
1, 2, 4, 5, 10, 20, 25, 50, 100, 
