
[给你一个整数数组 nums 和一个整数 k ，请你统计并返回 该数组中和为 k 的子数组的个数](https://leetcode.cn/problems/subarray-sum-equals-k/description/?envType=study-plan-v2&envId=top-100-liked#Popover19-toggle:~:text=%E7%BB%99%E4%BD%A0%E4%B8%80%E4%B8%AA%E6%95%B4%E6%95%B0%E6%95%B0%E7%BB%84%20nums%20%E5%92%8C%E4%B8%80%E4%B8%AA%E6%95%B4%E6%95%B0%20k%20%EF%BC%8C%E8%AF%B7%E4%BD%A0%E7%BB%9F%E8%AE%A1%E5%B9%B6%E8%BF%94%E5%9B%9E%20%E8%AF%A5%E6%95%B0%E7%BB%84%E4%B8%AD%E5%92%8C%E4%B8%BA%20k%20%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84%E7%9A%84%E4%B8%AA%E6%95%B0)
## 暴力循环


## 前缀和+哈希表优化

存储前缀和与其出现的次数
利用两数和的思想去查找另一个数出现的次数

```go
func subarraySum(nums []int, k int) int {
	count, pre := 0, 0
	m := map[int]int{}
	m[0] = 1
	for i := 0; i < len(nums); i++ {
		pre += nums[i]
		if times, ok := m[pre-k]; ok {
			count += times
		}
		m[pre] += 1
	}
	return count
}

```