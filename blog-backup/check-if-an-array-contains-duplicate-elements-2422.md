


## Question : Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

#### Examples:
```
Input: nums = [1,2,3,1]
Output: true

Input: nums = [1,2,3,4]
Output: false
```


_Problem : <a href="https://leetcode.com/problems/contains-duplicate/">Link to LeetCode</a>_ 

This Problem can be solved in 4 ways:

### Technique 1 : <u>**Brute Force**</u>

We will iterate through each element of the array and then check again if the element is present in the array more than one time.

```
Algorithm:

Loop (on individual item and store it in a variable -> i)
    Loop(again on individual elements and store it in a variable -> j)
    Initialize a counter with 0
        If (i equals j)
            Increase a counter

        If the counter is greater than one, after the inner loop then there is duplicate in the array.

```

```kotlin
class Solution {
    fun containsDuplicate(nums: IntArray): Boolean {
        for(i in nums){
            var counter = 0
            for(j in nums){
                if(i == j){
                    counter++
                }
            }
            if(counter > 1){
                return true
            }
        }
        return false 
    }
}
```
**Complexiy :**

| | Time |  Space  |
|:-----|:--------:|:--------:|
|| O(n<sup>2</sup>)   | O(1) |
|**Reason**| We are using 2 nested loops | No extra space is required |

### Technique 2 : <u>**Brute Force but a bit better**</u>

In this technique we will remove the counter variable as it adds an extra check.

```kotlin
class Solution {
    fun containsDuplicate(nums: IntArray): Boolean {
        for(i in 0..<nums.size){
            for(j in 0..<nums.size){
                if(i != j && nums[i] == nums[j]){
                    return true
                }
            }
        }
        return false
    }
}
```
Here we are using the index to compare the elements.

In Line no 5 `if(i != j && nums[i] == nums[j])` we are checking `i != j` as we can skip the same indexes and `nums[i] == nums[j]` we are checking if any other element is same or not.

**Complexiy :**

| | Time |  Space  |
|:-----|:--------:|:--------:|
|| O(n<sup>2</sup>)   | O(1) |
|**Reason**| We are using 2 nested loops | No extra space is required |

### Technique 3 : <u>**Reduce Time Complexity using sorting**</u>

Here we will first sort the array:
```
Input: nums = [1,2,3,1]
Sorted nums = [1,1,2,3]
```
Now if we compare the adjacent elements and both are equal we can say that there is a duplicate.

```kotlin
class Solution {
    fun containsDuplicate(nums: IntArray): Boolean {
        val arr = nums.sorted()
        for(i in 0..<arr.size-1){
            if(arr[i] == arr[i+1]){
                return true
            }
        }
        return false
    }
}
```
So here we need to run the loop to position 0 to size-2 as we need to compare the last element of the array.

| | Time |  Space  |
|:-----|:--------:|:--------:|
|| O(n log n)   | O(1) in theory but in Kotlin O(n) as we cannot sort the function parameter. |
|**Reason**| *n* - Because we are iterating over the loop and *log n* - for sorting | No extra space is required for other languages, but in Kotlin as we cannot sort the function parameter. |

### Technique 3 : <u>**Reduce Time Complexity But Increase the Space Complexity**</u>

In this technique we will use a `Set` where we will check if the set contains the element and if not insert the element in the set.

```kotlin
class Solution {
    fun containsDuplicate(nums: IntArray): Boolean {
        val set = mutableSetOf<Int>()
        for(i in nums){
            if(i in set){
                return true
            }
            set.add(i)
        }

        return false
    }
}
```

| | Time |  Space  |
|:-----|:--------:|:--------:|
|| O(n)   | O(n) |
|**Reason**|  Loop the array only once | We will keep inserting all the elements of the array in the set if no match is found |

**In all the solutions we are returning `true` as soon as we are finding any match. We are not waiting for the loop or function to complete as it ends the function much early if any match is found.**




