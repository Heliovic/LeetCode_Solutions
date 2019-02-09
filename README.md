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
