### DSALearning

## Longest Substring Without Repeating Characters

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
