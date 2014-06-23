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

