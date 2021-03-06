# LeetCode_Solutions
🎉My LeetCode solutions

## 0001. Two Sum

[Problem description](https://leetcode.com/problems/two-sum/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0001_Two_Sum/solution.cpp)

## 0002. Add Two Numbers

[Problem description](https://leetcode.com/problems/add-two-numbers/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0002_Add_Two_Numbers/solution.cpp)

## 0003. Longest Substring Without Repeating Characters

[Problem description](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0003_Longest_Substring_Without_Repeating_Characters/solution.cpp)

### 解题思路

使用 ```st[i]``` 保存**以```i```结尾的最大非重复子串**，外层循环遍历以 i 结尾的子串，内层循环根据```st[i]```检查是否有重复。这种方法可以将时间复杂度从 O(n^3) 降低到 O(n^2)。

## 0004. Median of Two Sorted Arrays

[Problem description](https://leetcode.com/problems/median-of-two-sorted-arrays/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0004_Median_of_Two_Sorted_Arrays/solution.cpp)

### 解题思路

二分查找，并且使用了Median的性质。对于A的划分i，表示以第i - 1个元素结尾的子序列，则对B的划分j应受到Median性质的限制。即，i和j应有如下关系成立：```i + j = m + n - i - j（m + n 为偶数）```，```i + j = m + n - i - j + 1（m + n 为奇数）```。

初始时i的范围为[0, m]，其中m为较大长度序列的长度。对于一个正确的Median划分，left_part的所有元素都应小于等于right_part的元素，若有不满足，则应相应调整i的取值及其取值范围。

详见LeetCode上的[Discuss](https://leetcode.com/problems/median-of-two-sorted-arrays/discuss/2481/Share-my-O\(log\(min\(mn\)\)-solution-with-explanation)

此题还应注意对引用的交换。交换引用时不要直接覆盖：

```cpp
vector<int>& t = num1;
num1 = num2;    // WRONG!这样的交换会直接用num2覆盖原来num1处的数据，导致t也变成了num2的数据！
num2 = t;
```
## 0005. Longest Palindromic Substring

[Problem description](https://leetcode.com/problems/longest-palindromic-substring/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0005_Longest_Palindromic_Substring/solution.cpp)

### 解题思路

求最长回文子串，使用**动态规划**。

```is_palindromic[i][j]``` 表示从 i 到 j 的子串是否是回文的。

递推关系式：```is_palindromic[i][j] = is_palindromic[i + 1][i + k - 1] && s[i] == s[i + k]  ? 1 : 0;```

初始时：

```cpp
is_palindromic[i][i] = 1;
is_palindromic[i][i + 1] = s[i] == s[i + 1] ? 1 : 0;
```

循环中按照子串长度更新：```is_palindromic[i][i + k]``` k 从 1 到整个字符串长度减 1。

该方法时间复杂度 O(n^2)。

## 0006. ZigZag Conversion

[Problem description](https://leetcode.com/problems/zigzag-conversion/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0006_ZigZag_Conversion/solution.cpp)

### 解题思路

注意多维数组动态申请和释放。

越界写将产生 **Runtime Error:** ***Error in `sandbox run': free(): invalid next size (fast): \<ADDRESS>***

## 0007. Reverse Integer

[Problem description](https://leetcode.com/problems/reverse-integer/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0007_Reverse_Integer/solution.cpp)

### 解题思路

题目中要求溢出处理，这时可以用一个**取值范围更大的数**来判断是否溢出：

```cpp
long long xt = x;
// ...
long long rev = 0;
// ...
if (rev > INT_MAX)    // Overflow
    return 0;
```

## 0008. String to Integer (atoi)

[Problem description](https://leetcode.com/problems/string-to-integer-atoi/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0008_String_to_Integer_(atoi)/solution.cpp)

### 解题思路

溢出处理有更好的方法：从高位向低位十进制移位累加。累加低位前保存原数（old_num），累加后检查是否有 ```new_num / 10 == old_num``` 成立。若不成立，说明已经溢出。

## 0009. Palindrome Number

[Problem description](https://leetcode.com/problems/palindrome-number/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0009_Palindrome_Number/solution.cpp)

## 0011. Container With Most Water

[Problem description](https://leetcode.com/problems/container-with-most-water/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0011_Container_With_Most_Water/solution.cpp)

### 解题思路

Two Pointers 方法。i 和 j 指向当前考虑的索引和高度。初始时 i 指向头，j 指向尾。i 随着迭代进行而增大，j 随着迭代进行而减小。对于其中某次迭代，记录当前有效高度 min_height。在决定下次迭代的 i 和 j 时，注意到 j - i 必定减小，要找到更大的面积，**下一次的有效高度应大于本次的有效高度 min_height**。

## 0012. Integer to Roman

[Problem description](https://leetcode.com/problems/integer-to-roman/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0012_Integer_to_Roman/solution.cpp)

### 解题思路

字符串处理。

## 0013. Roman to Integer

[Problem description](https://leetcode.com/problems/roman-to-integer/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0013_Roman_to_Integer/solution.cpp)

### 解题思路

字符串处理。

## 0014. Longest Common Prefix

[Problem description](https://leetcode.com/problems/longest-common-prefix/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0014_Longest_Common_Prefix/solution.cpp)

### 解题思路

字符串处理。

## 0015. 3Sum

[Problem description](https://leetcode.com/problems/3sum/)

[C++ (Accepted) - 二分查找 364 ms](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0015_3Sum/solution-binary-search.cpp)

[C++ (Accepted) - Two Pointers 144 ms](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0015_3Sum/solution-two-pointers.cpp)

### 解题思路

先对整个数组进行非降序排序。

#### 二分查找

先固定第一、二个数（p、q 指针），这样也就是要找到 nums[r] = - (nums[p] + nums[q])。使用 low、high 指针二分查找确定 nums[r] 。

#### Two Pointers

先固定第一个数（p 指针），再使用 Two Pointers（q、r 指针）确定剩余两数。

## 0016. 3Sum Closest

[Problem description](https://leetcode.com/problems/3sum-closest/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0016_3Sum_Closest/solution.cpp)

### 解题思路

Two Pointers 或 二分查找。

## 0017. Letter Combinations of a Phone Number

[Problem description](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0017_Letter_Combinations_of_a_Phone_Number/solution.cpp)

### 解题思路

DFS。

## 0018. 4Sum

[Problem description](https://leetcode.com/problems/4sum/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0018_4Sum/solution.cpp)

### 解题思路

对于 N-Sum 问题，只需遍历前 N-2 个数，对剩余两个数使用 two pointers。若前后两个相邻的数相同，则进行优化，跳过这个与前面一个相同的数。

## 0019. Remove Nth Node From End of List

[Problem description](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0019_Remove_Nth_Node_From_End_of_List/solution.cpp)

### 解题思路

链表操作。

## 0020. Valid Parentheses

[Problem description](https://leetcode.com/problems/valid-parentheses/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0020_Valid_Parentheses/solution.cpp)

### 解题思路

表达式栈。

## 0021. Merge Two Sorted Lists

[Problem description](https://leetcode.com/problems/merge-two-sorted-lists/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0021_Merge_Two_Sorted_Lists/solution.cpp)

### 解题思路

链表操作。

## 0022. Generate Parentheses

[Problem description](https://leetcode.com/problems/generate-parentheses/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0022_Generate_Parentheses/solution.cpp)

### 解题思路

回溯。还有很大优化空间。

## 0023. Merge k Sorted Lists

[Problem description](https://leetcode.com/problems/merge-k-sorted-lists/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0023_Merge_k_Sorted_Lists/solution.cpp)

### 解题思路

priority_queue 应用于队列实时调整，又需要取当前队列里最大/最小值的情况。

## 0024. Swap Nodes in Pairs

[Problem description](https://leetcode.com/problems/swap-nodes-in-pairs/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0024_Swap_Nodes_in_Pairs/solution.cpp)

### 解题思路

链表操作。

## 0025. Reverse Nodes in k-Group

[Problem description](https://leetcode.com/problems/reverse-nodes-in-k-group/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0025_Reverse_Nodes_in_k-Group/solution.cpp)

### 解题思路

对于链表元素进行每 k 个元素反转。先利用 vector<ListNode*> 暂存，直到累积到 k 个元素后，进行反转。

## 0026. Remove Duplicates from Sorted Array

[Problem description](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0026_Remove_Duplicates_from_Sorted_Array/solution.cpp)

### 解题思路

使用两个指针，一个 (ptr) 指向保留的最后一个元素，另一个 (i) 指向遍历元素，i 不断遍历，若两者不等，nums[++ptr] = nums[i]。

## 0027. Remove Element

[Problem description](https://leetcode.com/problems/remove-element/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0027_Remove_Element/solution.cpp)

### 解题思路

类似 0026 题。

## 0028. Implement strStr()

[Problem description](https://leetcode.com/problems/implement-strstr/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0028_Implement_strStr()/solution.cpp)

### 解题思路

当然没那么简单啦。实现 KMP 算法，有空再看。

## 0031. Next Permutation

[Problem description](https://leetcode.com/problems/next-permutation/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0031_Next_Permutation/solution.cpp)

### 解题思路

生成下一个排列。

从后往前找第一个满足 nums[i - 1] < nums[i] 的，即，从后往前第一个下降的。则 nums[i], nums[i + 1], nums[i + 2], . . . 序列必然是非增的。从 nums[i], nums[i + 1], nums[i + 2], . . . 序列中选择最小的，但是比 nums[i - 1] 大的数 nums[k]。将 nums[i - 1] 与 nums[k] 交换，对交换后的 nums[i], nums[i + 1], nums[i + 2], . . . 进行倒序，即为下一个排列。

> 1 2 4 [6 5 3]
> 
> 1 2 **5** [6 **4** 3]
> 
> 1 2 5 [3 4 6] (Next Permutation)

## 0032. Longest Valid Parentheses

[Problem description](https://leetcode.com/problems/longest-valid-parentheses/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0032_Longest_Valid_Parentheses/solution.cpp)

### 解题思路

求最长有效括号序列。

使用 stack 进行模拟。进栈后能出栈的字符是有效的。对这些有效位置进行[打表](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0032_Longest_Valid_Parentheses/solution.cpp#L27)，之后使用[动态规划](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0032_Longest_Valid_Parentheses/solution.cpp#L46)求出最长连续有效字符。

## 0033. Search in Rotated Sorted Array

[Problem description](https://leetcode.com/problems/search-in-rotated-sorted-array/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0033_Search_in_Rotated_Sorted_Array/solution.cpp)

### 解题思路

二分查找。思路：[Java AC Solution using once binary search - LeetCode Discuss](https://leetcode.com/problems/search-in-rotated-sorted-array/discuss/14472/Java-AC-Solution-using-once-binary-search)

## 0034. Find First and Last Position of Element in Sorted Array

[Problem description](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0034_Find_First_and_Last_Position_of_Element_in_Sorted_Array/solution.cpp)

### 解题思路

二分查找，找到下界和上界（lower_bound、upper_bound）。

## 0035. Search Insert Position

[Problem description](https://leetcode.com/problems/search-insert-position/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0035_Search_Insert_Position/solution.cpp)

### 解题思路

二分查找，查找失败后 low 指针即为插入位置。

## 0036. Valid Sudoku

[Problem description](https://leetcode.com/problems/valid-sudoku/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0036_Valid_Sudoku/solution.cpp)

### 解题思路

遍历，打表检查。

## 0037. Sudoku Solver

[Problem description](https://leetcode.com/problems/sudoku-solver/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0037_Sudoku_Solver/solution.cpp)

### 解题思路

DFS。检查是否可行时，无需全局检查，只需检查改变了的列和 9 个方格。

## 0038. Count and Say

[Problem description](https://leetcode.com/problems/count-and-say/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0038_Count_and_Say/solution.cpp)

### 解题思路

无论如何确信，使用 stringstream 前先清空！

```cpp
stringstream ss
ss.str("");
ss.clear();
```

## 0039. Combination Sum

[Problem description](https://leetcode.com/problems/combination-sum/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0039_Combination_Sum/solution.cpp)

### 解题思路

DFS。注意使用有序数列进行[非降 DFS](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0039_Combination_Sum/solution.cpp#L19)保证所求结果没用重复，注意参数中的 i 所发挥的作用。

## 0040. Combination Sum II

[Problem description](https://leetcode.com/problems/combination-sum-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0040_Combination_Sum_II/solution.cpp)

### 解题思路

DFS 剪枝的重要思路：**排序、非降、同一层中不重复搜索相同值的元素**。

## 0042. Trapping Rain Water

[Problem description](https://leetcode.com/problems/trapping-rain-water/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0042_Trapping_Rain_Water/solution.cpp)

### 解题思路

使用两个指针，i 指针固定，j 指针从 i + 1 开始移动，找到第一个比 i 大的高度。计算 i、j 之间的体积，之后令 i = j，如此迭代。当 j == height.size() 时，说明 i 之后没有比 i 更高的了，这时应找到 i 和 j 之间比 i 小的最高的那个，记为 max_idx ，计算 i 和 max_idx 的体积，之后令 i = max_idx，继续迭代。

做题时请不要强迫症，该特判时果断特判！

## 0043. Multiply Strings

[Problem description](https://leetcode.com/problems/multiply-strings/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0043_Multiply_Strings/solution.cpp)

### 解题思路

大数乘法。

## 0045. Jump Game II

[Problem description](https://leetcode.com/problems/jump-game-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0045_Jump_Game_II/solution.cpp)

### 解题思路

farthest 保存当前可以到达的最大索引。3

ptr 是当前考虑的那个 num 下标，显然，farthest = max(farthest, ptr + num = ptr + nums[ptr])。

cur 是前一时刻可以到达的最大下标，当 ptr 超过 cur 时，cur 更新为前一次所能达到的最大距离，并跳数++。

## 0046. Permutations

[Problem description](https://leetcode.com/problems/permutations/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0046_Permutations/solution.cpp)

### 解题思路

求全排列。

## 0047. Permutations II

[Problem description](https://leetcode.com/problems/permutations-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0047_Permutations_II/solution.cpp)

### 解题思路

求**多重集**的全排列。

## 0048. Rotate Image

[Problem description](https://leetcode.com/problems/rotate-image/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0048_Rotate_Image/solution.cpp)

### 解题思路

矩阵旋转等价于：先将矩阵转置，再对矩阵进行左右翻转（镜像）。

## 0049. Group Anagrams

[Problem description](https://leetcode.com/problems/group-anagrams/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0049_Group_Anagrams/solution.cpp)

### 解题思路

STL 的 map 的使用。

## 0050. Pow(x, n)

[Problem description](https://leetcode.com/problems/powx-n/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0050_Pow(x%2C%20n)/solution.cpp)

### 解题思路

快速幂。注意在 int 范围内，-INT_MIN 会溢出。

## 0051. N-Queens

[Problem description](https://leetcode.com/problems/n-queens/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0051_N-Queens/solution.cpp)

### 解题思路

N 皇后问题。

## 0052. N-Queens II

[Problem description](https://leetcode.com/problems/n-queens-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0052_N-Queens_II/solution.cpp)

### 解题思路

N 皇后问题。

## 0053. Maximum Subarray

[Problem description](https://leetcode.com/problems/maximum-subarray/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0053_Maximum_Subarray/solution.cpp)

### 解题思路

动态规划求最长连续子串和。

## 0054. Spiral Matrix

[Problem description](https://leetcode.com/problems/spiral-matrix/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0054_Spiral_Matrix/solution.cpp)

### 解题思路

简单模拟。

## 0055. Jump Game

[Problem description](https://leetcode.com/problems/jump-game/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0055_Jump_Game/solution.cpp)

### 解题思路

参照 [0045. Jump Game II](https://github.com/Heliovic/LeetCode_Solutions#0045-jump-game-ii)。

## 0056. Merge Intervals

[Problem description](https://leetcode.com/problems/merge-intervals/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0056_Merge_Intervals/solution.cpp)

### 解题思路

合并区间。先将所有区间按照左数从小到大排序，再用 last 记录当前正在合并的区间。若对于考虑的某个区间，若其左数小于 last 的右数而其右数大于 last 的右数，则拓展 last 的右数到当前区间的右数。而若其右数小于 last 的右数，则说明该区间包含在 last 之内，可不必考虑。若其左数大于 last 的右数，则保存 last 到 ans，更新 last 为该区间。

## 0057. Insert Interval

[Problem description](https://leetcode.com/problems/insert-interval/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0057_Insert_Interval/solution.cpp)

### 解题思路

同上。

## 0058. Length of Last Word

[Problem description](https://leetcode.com/problems/length-of-last-word/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0058_Length_of_Last_Word/solution.cpp)

### 解题思路

字符串处理。

## 0059. Spiral Matrix II

[Problem description](https://leetcode.com/problems/spiral-matrix-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0059_Spiral_Matrix_II/solution.cpp)

### 解题思路

模拟。

## 0060. Permutation Sequence

[Problem description](https://leetcode.com/problems/permutation-sequence/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0060_Permutation_Sequence/solution.cpp)

### 解题思路

找规律。对于某个长度为 n 的子序列的第 k 个元素，其首位为 numbers[k / (n - 1)!]。其中 numbers 保存当前可选的数字序列。

## 0061. Rotate List

[Problem description](https://leetcode.com/problems/rotate-list/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0061_Rotate_List/solution.cpp)

### 解题思路

模拟，链表操作。

## 0062. Unique Paths

[Problem description](https://leetcode.com/problems/unique-paths/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0062_Unique_Paths/solution.cpp)

### 解题思路

递推。matrix[i][j] = matrix[i + 1][j] + matrix[i][j + 1]。初始时，matrix[m - 1][n - 1] = 1。

## 0063. Unique Paths II

[Problem description](https://leetcode.com/problems/unique-paths-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0063_Unique_Paths_II/solution.cpp)

### 解题思路

递推。

## 0064. Minimum Path Sum

[Problem description](https://leetcode.com/problems/minimum-path-sum/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0064_Minimum_Path_Sum/solution.cpp)

### 解题思路

动态规划。

## 0066. Plus One

[Problem description](https://leetcode.com/problems/plus-one/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0066_Plus_One/solution.cpp)

### 解题思路

模拟加法。

## 0067. Add Binary

[Problem description](https://leetcode.com/problems/add-binary/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0067_Add_Binary/solution.cpp)

### 解题思路

二进制加法。

## 0068. Text Justification

[Problem description](https://leetcode.com/problems/text-justification/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0068_Text_Justification/solution.cpp)

### 解题思路

字符串处理。

## 0069. Sqrt(x)

[Problem description](https://leetcode.com/problems/sqrtx/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0069_Sqrt(x)/solution.cpp)

### 解题思路

二分。

## 0070. Climbing Stairs

[Problem description](https://leetcode.com/problems/climbing-stairs/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0070_Climbing_Stairs/solution.cpp)

### 解题思路

记忆化递推。

## 0071. Simplify Path

[Problem description](https://leetcode.com/problems/simplify-path/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0071_Simplify_Path/solution.cpp)

### 解题思路

字符串处理。先用 "/" 替换 "//"，再根据 "/" 进行分割。使用栈模拟路径转移。

## 0073. Set Matrix Zeroes

[Problem description](https://leetcode.com/problems/set-matrix-zeroes/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0073_Set_Matrix_Zeroes/solution.cpp)

## 0074. Search a 2D Matrix

[Problem description](https://leetcode.com/problems/search-a-2d-matrix/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0074_Search_a_2D_Matrix/solution.cpp)

### 解题思路

二分查找。

## 0075. Sort Colors

[Problem description](https://leetcode.com/problems/sort-colors/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0075_Sort_Colors/solution.cpp)

### 解题思路

模拟，Two Pointers。

## 0077. Combinations

[Problem description](https://leetcode.com/problems/combinations/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0077_Combinations/solution.cpp)

### 解题思路

DFS，组合数生成。

## 0078. Subsets

[Problem description](https://leetcode.com/problems/subsets/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0078_Subsets/solution.cpp)

### 解题思路

DFS，子集生成。

## 0079. Word Search

[Problem description](https://leetcode.com/problems/word-search/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0079_Word_Search/solution.cpp)

### 解题思路

DFS。

## 0080. Remove Duplicates from Sorted Array II

[Problem description](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0080_Remove_Duplicates_from_Sorted_Array_II/solution.cpp)

### 解题思路

Two Pointers。

## 0081. Search in Rotated Sorted Array II

[Problem description](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0081_Search_in_Rotated_Sorted_Array_II/solution.cpp)

### 解题思路

二分查找。相关题型见 [0033. Search in Rotated Sorted Array](https://github.com/Heliovic/LeetCode_Solutions#0033-search-in-rotated-sorted-array)

这里与第 33 题不同之处在于，该数组中可能会有重复元素，这样当 nums[low] == nums[mid] 时，无法判断应该向左还是向右移动。可以使用[此处](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/discuss/28218/My-8ms-C%2B%2B-solution-(o(logn)-on-average-o(n)-worst-case))的 trick 处理掉这种情况。代码见 https://github.com/Heliovic/LeetCode_Solutions/blob/master/0081_Search_in_Rotated_Sorted_Array_II/solution.cpp#L12

## 0082. Remove Duplicates from Sorted List II

[Problem description](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0082_Remove_Duplicates_from_Sorted_List_II/solution.cpp)

### 解题思路

链表去重。

## 0083. Remove Duplicates from Sorted List

[Problem description](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0083_Remove_Duplicates_from_Sorted_List/solution.cpp)

### 解题思路

链表操作。

## 0084. Largest Rectangle in Histogram

[Problem description](https://leetcode.com/problems/largest-rectangle-in-histogram/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0084_Largest_Rectangle_in_Histogram/solution.cpp)

### 解题思路

直方图最大矩形面积。

算法参考：

https://blog.csdn.net/u012534831/article/details/74356851

https://leetcode.com/problems/largest-rectangle-in-histogram/discuss/28900/O(n)-stack-based-JAVA-solution

## 0086. Partition List

[Problem description](https://leetcode.com/problems/partition-list/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0086_Partition_List/solution.cpp)

### 解题思路

链表操作。

## 0087. Scramble String

[Problem description](https://leetcode.com/problems/scramble-string/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0087_Scramble_String/solution.cpp)

### 解题思路

递归判断。若两字符串是 Scramble String，则必有长度相等且字符串中每个字符出现次数相等。递归出口是输入的两个字符串相等。

递归过程：对于给定的某个长度 len，以下应有一条满足：

1. s1 子串 s11(0~len-1) 和 s2 子串 s21(0~len-1) 是 Scramble String 且 s1 子串 s12(s1.size() - len, s1.size() - 1) 和 s2 子串 s22(s2.size() - len, s2.size() - 1) 是 Scramble String

2. s1 子串 s11(0~len-1) 和 s2 子串 s11(s2.size() - len, s2.size() - 1) 是 Scramble String 且 s1 子串 s11(s1.size() - len, s1.size() - 1) 和 s2 子串 s11(0~len-1) 是 Scramble String

若对所有长度都不满足，则不是 Scramble String

## 0088. Merge Sorted Array

[Problem description](https://leetcode.com/problems/merge-sorted-array/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0088_Merge_Sorted_Array/solution.cpp)

## 0089. Gray Code

[Problem description](https://leetcode.com/problems/gray-code/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0089_Gray_Code/solution.cpp)

### 解题思路

在前一个 n 的基础上构造 n + 1。构造方法：将 n 的结果复制一遍，在加入 n 的倒序，并将这些高位置 1。

https://leetcode.com/problems/gray-code/discuss/29891/Share-my-solution

## 0090. Subsets II

[Problem description](https://leetcode.com/problems/subsets-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0090_Subsets_II/solution.cpp)

### 解题思路

DFS 构建子集。特别注意[此处去重复操作](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0090_Subsets_II/solution.cpp#L18)。

## 0091. Decode Ways

[Problem description](https://leetcode.com/problems/decode-ways/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0091_Decode_Ways/solution.cpp)

### 解题思路

动态规划。设 dp[i] 为长度为 i 的串存在的方案数，则有：

* 当 str[i] == '0' 而 str[i - 1] + str[i] 非法时，dp[i] = 0

* 当 str[i] == '0' 而 str[i - 1] + str[i] 在 [1, 26] 范围内时，dp[i] = dp[i - 2]

* 当 str[i] 合法而 str[i - 1] + str[i] 非法时，dp[i] = dp[i - 1]

* 当 str[i] 合法且 str[i - 1] + str[i] 合法时，dp[i] = dp[i - 1] + dp[i - 2]

## 0092. Reverse Linked List II

[Problem description](https://leetcode.com/problems/reverse-linked-list-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0092_Reverse_Linked_List_II/solution.cpp)

### 解题思路

链表操作。

## 0093. Restore IP Addresses

[Problem description](https://leetcode.com/problems/restore-ip-addresses/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0093_Restore_IP_Addresses/solution.cpp)

### 解题思路

DFS。

## 0094. Binary Tree Inorder Traversal

[Problem description](https://leetcode.com/problems/binary-tree-inorder-traversal/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0094_Binary_Tree_Inorder_Traversal/solution.cpp)

### 解题思路

中序遍历。

## 0095. Unique Binary Search Trees II

[Problem description](https://leetcode.com/problems/unique-binary-search-trees-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0095_Unique_Binary_Search_Trees_II/solution.cpp)

### 解题思路

递归构建所有可能的子树。

由于二叉树序列是有序的。create(lp, rp) 意为构建从 lp 到 rp 的所有子树的根节点。则其构造过程为：遍历 [lp, rp]，分别作为根，递归构建其左右子树的根。

## 0096. Unique Binary Search Trees

[Problem description](https://leetcode.com/problems/unique-binary-search-trees/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0096_Unique_Binary_Search_Trees/solution.cpp)

### 解题思路

记忆化搜索或DP。

## 0097. Interleaving String

[Problem description](https://leetcode.com/problems/interleaving-string/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0097_Interleaving_String/solution.cpp)

### 解题思路

记忆化搜索或DP。

## 0098. Validate Binary Search Tree

[Problem description](https://leetcode.com/problems/validate-binary-search-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0098_Validate_Binary_Search_Tree/solution.cpp)

### 解题思路

DFS。

## 0100. Same Tree

[Problem description](https://leetcode.com/problems/same-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0100_Same_Tree/solution.cpp)

## 0101. Symmetric Tree

[Problem description](https://leetcode.com/problems/symmetric-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0101_Symmetric_Tree/solution.cpp)

## 0102. Binary Tree Level Order Traversal

[Problem description](https://leetcode.com/problems/symmetric-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0102_Binary_Tree_Level_Order_Traversal/solution.cpp)

## 0103. Binary Tree Zigzag Level Order Traversal

[Problem description](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0103_Binary_Tree_Zigzag_Level_Order_Traversal/solution.cpp)

## 0104. Maximum Depth of Binary Tree

[Problem description](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0104_Maximum_Depth_of_Binary_Tree/solution.cpp)

## 0105. Construct Binary Tree from Preorder and Inorder Traversal

[Problem description](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0105_Construct_Binary_Tree_from_Preorder_and_Inorder_Traversal/solution.cpp)

### 解题思路

二叉树重建。

## 0106. Construct Binary Tree from Inorder and Postorder Traversal

[Problem description](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0106_Construct_Binary_Tree_from_Inorder_and_Postorder_Traversal/solution.cpp)

### 解题思路

二叉树重建。

## 0106. Construct Binary Tree from Inorder and Postorder Traversal

[Problem description](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0107_Binary_Tree_Level_Order_Traversal_II/solution.cpp)

## 0108. Convert Sorted Array to Binary Search Tree

[Problem description](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0108_Convert_Sorted_Array_to_Binary_Search_Tree/solution.cpp)

### 解题思路

分治，将左右子树一分为二，各占一半后继续构建。

## 0109. Convert Sorted List to Binary Search Tree

[Problem description](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0109_Convert_Sorted_List_to_Binary_Search_Tree/solution.cpp)

### 解题思路

先遍历一次链表，确定有多少个数，再使用中序遍历的方式，确定左右子树的节点个数相同，构建二叉查找树。

## 0110. Balanced Binary Tree

[Problem description](https://leetcode.com/problems/balanced-binary-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0110_Balanced_Binary_Tree/solution.cpp)

## 0111. Minimum Depth of Binary Tree

[Problem description](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0111_Minimum_Depth_of_Binary_Tree/solution.cpp)

### 解题思路

求深度先考虑 BFS。

## 0112. Path Sum

[Problem description](https://leetcode.com/problems/path-sum/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0112_Path_Sum/solution.cpp)

## 0113. Path Sum II

[Problem description](https://leetcode.com/problems/path-sum-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0113_Path_Sum_II/solution.cpp)

## 0115. Distinct Subsequences

[Problem description](https://leetcode.com/problems/distinct-subsequences/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0115_Distinct_Subsequences/solution.cpp)

### 解题思路

动态规划。

dp[i][j] 表示以 s[i] 和 t[j] 结尾的两个字符串所可能的方案数，则：

* 若 s[i] == t[j]，则 dp[i][j] 可能的方案数：
    * 不取 s[i] 这个字符与 t[j] 匹配，有 dp[i - 1][j] 种方案
    * 取 s[i] 这个字符与 t[j] 匹配，，有 dp[i - 1][j - 1] 种方案
    * 所以，dp[i][j] = dp[i - 1][j] + dp[i - 1][j - 1]

* 若 s[i] != t[j]，则 dp[i][j] 可能的方案数为 dp[i - 1][j]

## 0116. Populating Next Right Pointers in Each Node

[Problem description](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0116_Populating_Next_Right_Pointers_in_Each_Node/solution.cpp)

## 0117. Populating Next Right Pointers in Each Node II

[Problem description](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0117_Populating_Next_Right_Pointers_in_Each_Node_II/solution.cpp)

## 0118. Pascal's Triangle

[Problem description](https://leetcode.com/problems/pascals-triangle/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0118_Pascal's_Triangle/solution.cpp)

## 0119. Pascal's Triangle II

[Problem description](https://leetcode.com/problems/pascals-triangle-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0119_Pascal's_Triangle_II/solution.cpp)

## 0120. Triangle

[Problem description](https://leetcode.com/problems/triangle/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0120_Triangle/solution.cpp)

### 解题思路

动态规划。

## 0121. Best Time to Buy and Sell Stock

[Problem description](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0121_Best_Time_to_Buy_and_Sell_Stock/solution.cpp)

## 0122. Best Time to Buy and Sell Stock II

[Problem description](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/0122_Best_Time_to_Buy_and_Sell_Stock_II/solution.cpp)

### 解题思路

求一个序列中能获得的最大收益。只需关注单调不减的那些子序列即可。

## 0125. Valid Palindrome

[Problem description](https://leetcode.com/problems/valid-palindrome/)

[C++ (Accepted)](https://github.com/Heliovic/LeetCode_Solutions/blob/master/125_Valid_Palindrome/solution.cpp)

### 解题思路

Two Pointers。
