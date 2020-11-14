[242. 有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/)
> 输入: s = "anagram", t = "nagaram" <br>输出: true<br>
> 输入: s = "rat", t = "car" <br> 输出: false
```python
def isAnagram(s, t):
    arr1 = [0] * 26
    arr2 = [0] * 26
    for i in s:
        # 以a为基准
        arr1[ord(i) - ord('a')] += 1
    for i in t:
        arr2[ord(i) - ord('a')] += 1
    return arr1 == arr2
```
[49. 字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)
> 给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。<br>
> 输入: ["eat", "tea", "tan", "ate", "nat", "bat"] <br>
  输出: [["ate","eat","tea"],["nat","tan"],["bat"]]
```python
def groupAnagrams(strs):
    mapping = {}
    for i in strs:
        # string->list->排序->string
        tmp = ''.join(sorted(list(i)))
        if mapping.get(tmp) is None:
            mapping[tmp] = [i]
        else:
            mapping[tmp].append(i)
    return mapping.values()
```
[1. 两数之和](https://leetcode-cn.com/problems/two-sum/)
> 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。<br>
> 给定 nums = [2, 7, 11, 15], target = 9 <br> 因为 nums[0] + nums[1] = 2 + 7 = 9, 所以返回 [0, 1]
```python
def twoSum(nums, target):
    mapping = {}
    for i in range(len(nums)):
        if nums[i] in mapping:
            return [i, mapping[nums[i]]]
        else:
            mapping[target-nums[i]] = i 
```
> 相似题目: <br>三数之和(https://leetcode-cn.com/problems/3sum/)<br>四数之和(https://leetcode-cn.com/problems/4sum/)