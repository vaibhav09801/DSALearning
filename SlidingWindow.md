### DSALearning

# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the longest substring without repeating characters.

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.


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
