### Longest Substring Without Repeating Characters

Given a string `s`, find the length of the longest substring without repeating characters.

## Example 1:

Input: `s = "abcabcbb"`  
Output: `3`  
Explanation: The answer is "abc", with the length of 3.

## Example 2:

Input: `s = "bbbbb"`  
Output: `1`  
Explanation: The answer is "b", with the length of 1.

## Example 3:

Input: `s = "pwwkew"`  
Output: `3`  
Explanation: The answer is "wke", with the length of 3. Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

Here's the Swift implementation:

```swift
func lengthOfLongestSubstring(_ s: String) -> Int {
    var ans = 0
    var hashMap: [Character: Int] = [:]
    var pointer = 0
    
    for (index, char) in s.enumerated() {
        if let prevIndex = hashMap[char] {
            pointer = max(prevIndex, pointer)
        }
        ans = max(ans, index - pointer + 1)
        hashMap[char] = index + 1
    }
    
    return ans
}
```





### Max Consecutive Ones III

Given a string `s`, find the length of the longest substring without repeating characters.

##Example 1:

Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
Output: 6
Explanation: [1,1,1,0,0,1,1,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

##Example 2:
Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3
Output: 10
Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

Here's the Swift implementation:

```swift
func longestOnes(_ nums: [Int], _ k: Int) -> Int {
    var left = 0
    var maxCount = 0
    var zeroCount = 0
    for right in 0..<nums.count {
        if nums[right] == 0 {
            zeroCount += 1
        }
        while zeroCount > k {
            if nums[left] == 0 {
                zeroCount -= 1
            }
            left += 1
        }
        maxCount = max(maxCount, right - left + 1)
    }
    return maxCount
}
```









