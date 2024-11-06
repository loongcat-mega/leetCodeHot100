
[给定整数数组 nums 和整数 k，请返回数组中第 k 个最大的元素](https://leetcode.cn/problems/kth-largest-element-in-an-array/description/?envType=study-plan-v2&envId=top-100-liked#Popover19-toggle:~:text=%E7%BB%99%E5%AE%9A%E6%95%B4%E6%95%B0%E6%95%B0%E7%BB%84%20nums%20%E5%92%8C%E6%95%B4%E6%95%B0%20k%EF%BC%8C%E8%AF%B7%E8%BF%94%E5%9B%9E%E6%95%B0%E7%BB%84%E4%B8%AD%E7%AC%AC%20k%20%E4%B8%AA%E6%9C%80%E5%A4%A7%E7%9A%84%E5%85%83%E7%B4%A0)

## 堆排
```go
type intHeap struct {
	sort.IntSlice
}

func (h intHeap) Less(i, j int) bool { return h.IntSlice[i] > h.IntSlice[j] }
func (h *intHeap) Push(x any) {
		h.IntSlice = append(h.IntSlice, x.(int))
}
func (h *intHeap) Pop() any {
    	a := h.IntSlice
    	v := a[len(a)-1]
    	h.IntSlice = a[:len(a)-1]
    	return v
}

func findKthLargest(nums []int, k int) int {
    	q := &intHeap{make([]int, k)}
    	for i := 0; i < k; i++ {
    		q.IntSlice[i] = nums[i]
    	}
    	heap.Init(q)
    	for i := k; i < len(nums); i++ {
    		heap.Push(q, nums[i])
    	}
    	for i := 0; i < k-1; i++ {
    		heap.Pop(q)
    	}
    	return heap.Pop(q).(int)
}

```

## 快排


## 桶排

