# Java-Program-to-Find-Prime-Number-between-1-to-100

Finding Prime number between 1 to 100
Here, in this section we will discuss a program to find prime number between 1 to 100 in java. A prime number is a positive integer having exactly two factors. If 11 is a prime, then it’s only factors are necessarily 1 and 11 itself

Prime number between 1 to 100
Methods Discussed on page
Method 1: Basic checking prime by only checking first n
Method 2: Basic checking prime by only checking first n/2 divisors
Method 3: Checking prime by only checking first √n divisors
Method 4: Checking prime by only checking first √n divisors, but also skipping even iterations.

Method used to check prime
Here we use the usual method to check prime. If given number is prime then we print it else we move ahead to the next number and check if that is prime and keep going till 100
Method 1
Basic checking prime by only checking first n

Java Code
Run
public class Main
{   
    
	public static void main(String[] args) {
		int a=1,b=100;
		for(int i=a;i<=b;i++){
		    if(checkPrime(i)){
		        System.out.print(i+" " );
		    }
		}
	}
	public static boolean checkPrime(int num){
	    
	    // 0, 1 and negative numbers are not prime
	    if(num<2){
	        return false;
	    }
	    else{
	        
	 // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways. 
    // Example 36 wont be divisible by anything b/w 19-35
	        int x= num/2;
	        for(int i=2;i<x;i++){
	            if(num%i==0){
	                return false;
	            }
	        }
	    }
	    // the number would be prime if we reach here
	    return true;
	}
}
Output
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
Algorithm (Method 2)
Basic checking prime by only checking first n/2 divisors

Run a loop in the iteration of (i) b/w 1 and 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to the next iteration
Method used to check prime
Here we use the usual method to check prime. We however check the divisibility only till num/2.

As the range(num/2 + 1, num) won't be divisible anyways. Example 36 won't be divisible by anything b/w 19-35
Java Code
Run
public class Main
{
	public static void main(String[] args) {
		
		for(int i=1;i<=100;i++){
		    if(checkPrime(i)){
		        System.out.print(i+" " );
		    }
		}
	}
	public static boolean checkPrime(int num){
	    
	   // 0, 1 and negative numbers are not prime
	    if(num<2){
	        return false;
	    }
	    else{
	        // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways. 
    // Example 36 wont be divisible by anything b/w 19-35
	        int x= num/2;
	        for(int i=2;i<x;i++){
	            if(num%i==0){
	                return false;
	            }
	        }
	    }
	    // the number would be prime if we reach here
	    return true;
	}
}
Output
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
Related Pages
Count possible decoding of a given digit sequence

Find the prime numbers between 1 to 100

Calculate the number of digits in an integer

Convert digit/number to words

Counting number of days in a given month of a year

Method 3
Checking prime by only checking first √n divisors

The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has better time complexity of O(√N)

Run a loop in the iteration of (i) b/w 1 and 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
A number n is not a prime if it can be factored into two factors a & b:
n = a * b

Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n.

So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.

So we only need to run loop till sqrt(n) and not n or n/2
Java Code
Run
import java.lang.Math;
public class Main
{
	public static void main(String[] args)
	{
		
		for(int i=1;i<=100;i++)
		{
		    if(checkPrime(i))
		    {
		        System.out.print(i+" " );
		    }
		}
	}
	public static boolean checkPrime(int num)
	{
	    // 0, 1 and negative numbers are not prime
	    if(num<2)
	    {
	        return false;
	    }
	    else
	    {
	        // A number n is not a prime, if it can be factored into two factors a & b:
            // n = a * b
            /*Now a and b can't be both greater than the square root of n, since
            then the product a * b would be greater than sqrt(n) * sqrt(n) = n.
            So in any factorization of n, at least one of the factors must be
            smaller than the square root of n, and if we can't find any factors
            less than or equal to the square root, n must be a prime.*/
            for(int i=2;i<Math.sqrt(num);i++)
	        {
	            if(num%i==0)
	            {
	                return false;
	            }
	        }
	    }
	    // the number would be prime if we reach here
	    return true;
	}
}

// This method is obviously  faster as has better time complexity
Output
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
Method 4
Checking prime by only checking first √n divisors, but also skipping even iterations.

The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has same time complexity of O(√N).

But makes around half lesser checks

Run a loop in the iteration of (i) b/w 1 to 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
This method uses the assumption that –

We can simply check all divisors between [2, √num]
2 is the only even prime number
We can skip all even iterations in the loop
Java Code
Run
import java.lang.Math;
public class Main
{
	public static void main(String[] args) {
		
		for(int i=1;i<=100;i++){
		    if(checkPrime(i)){
		        System.out.print(i+" " );
		    }
		}
	}
	public static boolean checkPrime(int n){
	// 0 and 1 are not prime numbers
    // negative numbers are not prime
	    if(n<=1){
	        return false;
	        
	    // special case as 2 is the only even number that is prime
	    }else if(n==2){
	        return true;
	        
	    // Check if n is a multiple of 2 thus all these won't be prime     
	    }else if(n%2==0){
	        return false;
	    }
	    // If not, then just check the odds 
	    for(int i=3;i<Math.sqrt(n);i+=2){
	            if(n%i==0){
	                return false;
	            }
	        }
	    
	    return true;
	}
}

// This method is obviously faster as makes around half lesser comparision due skipping even iterations in the loop
Output
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
