## Chapter 1:  Arrays and Strings

Array questions and string questions are often interchangeable.

### Hash Tables

That maps keys to values for highly efficient lookup.

### ArrayList

Dynamically resizing array.

### StringBuffer

It simply creates an **array** of all the strings, copying them back to a string only when necessary.

```java
public String joinWords(String[] words) {
    StringBuffer sentence = new StringBuffer();
    for ( String w : words) {
        sentence.append(w);
    }
    return sentence.toString();
}
```

### Questions

#### 1.1

**Implement an algorithm to determine if a string has all unique characters What if you can not use additional data structures?**

首先要想到的是，这个String是ASCII string还是Unicode String。

对于ASCII，可以用256个int表示。简介：http://goo.gl/ySMceK

算法一：如果string长度大于256，肯定有重复的，返回false。如果不，新建一个256的数组，如果某个字符出现过，就将数组中相应地位置设为true，如果在遍历中重复到了某个为true的值，则说明有重复的，返回false。

```java
public static boolean isUniqueChars2(String str) {
    if (str.length() > 256 ) return false;
    
    boolean[] char_set = new boolean[256];
    for (int i = 0; i < str.length(); i++) {
        int val = str.charAt(i);
        if (char_set[val]) return false;
        char_set[val] = true;
    }
    return true;
}
```

算法二：为减少space，可以考虑用bit vector。此算法不再介绍。

其它算法：

1、 运用两个循环，检测每个char与其它char是否重复。需要O(n^2) time.

```java
public boolean isUniqueChars3(String str) {
	if (str.length() > 256) return false;
	
	for (int i = 0; i < str.length(); i++) {
		for (int j = i + 1; j < str.length(); j++) {
			if (str.charAt(i) == str.charAt(j)) return false;
		}
	}
	return true;
}
```

2、 如果原字符串可以更改，则先对其进行排序O(n logn)，然后比较相邻的两个char是否重复。

### 1.2

**Implement a function void reverse(char* str) in C or C++ which reverses a null-terminated string.**

注意要原地反转（in place）。让两个指针从string两端同时遍历，并相互交换值，知道两个指针相遇为止。

### 1.3

**Given two strings, write a method to decide if one is a permutation of the other.**

注意首先思考两点：1. 是否是case sensitive的，2. 空格算不算

而且还要意识到一点：如果两个字符串长度不一样，肯定false。

算法一：

先排序，在比较。如果互为permutation，排序后肯定一样。

```java
public String sort(String s) {
	char[] content = s.toCharArray();
	java.util.Arrays.sort(content);
	return new String(content);
}

public boolean permutation(String s, String t) {
	if (s.length() != t.length()) return false;
	return sort(s).equals(sort(t));
}
```

算法二：

如果互为permutation，则他们的每个字母的个数是相同的。数一数便知（数的时候考虑用ASCII 256特性）。

```java
public boolean permutation(String s, String t) {
	if (s.length() != t.length()) return false;
	
	int[] letters = new int[256];
	
	// 先数s中的
	char[] s_array = s.toCharArray();
	for (char c : s_array) {
		letters[c]++;
	}
	
	// 然后对于t，遍历，遇到每个char就把统计的s的char相应的数量减少1
	for (int i = 0; i < t.length(); i++) {
		int c = (int) t.charAt(i);
		if (--letters[c] < 0) {
			return false;
		}
	}
	return true;
}
```





