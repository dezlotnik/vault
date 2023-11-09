
> [!question] Problem
> Given an array `nums` of size `n`, return the *majority element*.
> The majority element is the element that appears more than `⌊n / 2⌋` times.
> You may assume that the majority element always exists in the array.

## Solution 1: Map / Dictionary
Use a [[Hash Table]] to store the frequency of numbers in the array. Return number with desired frequency.

time: O(n)
space: O(n)

## Solution 2: Voting Algorithm
https://www.topcoder.com/thrive/articles/boyer-moore-majority-vote-algorithm

