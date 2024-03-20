### DSALearning

# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the longest substring without repeating characters.

## Approach

We can solve this problem efficiently using a sliding window approach. We'll maintain a hashmap to store the most recent index of each character we've encountered. We'll also use a pointer to keep track of the starting index of the current substring. 

As we iterate through the string, if we encounter a character that is already present in our hashmap, we update the pointer to skip over the characters that have been repeated. We then update the answer by calculating the length of the current substring and comparing it with the previous answer. Finally, we update the hashmap with the most recent index of the current character.

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
