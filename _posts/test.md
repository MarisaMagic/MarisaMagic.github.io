---
layout:     post   				        # 使用的布局（不需要改）
title:      My First Post 				# 标题 
subtitle:   Master Spark #副标题
date:       2024-06-30 				# 时间
author:     MarisaMagic 						# 作者
header-img: img/post-bg-2015.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - 生活
---

## **A 幻想乡纪年法**

### **题意描述**

一年 $12$ 个月，每个月 $30$ 天，每周 $5$ 天，分别为周一至周五。给定 $y_1$ 年 $m_1$ 月 $d_1$ 日以及这天是周几，求 $y_2$ 年 $m_2$ 月 $d_2$ 日是周几。

### **解题思路**

可以直接求两天的总天数，求出两数之差就可以得出是周几（注意差为负数，$\text{C++}$ 需要加上 $5$ 再对 $5$ 取模）。当然，由题意可知一年为 $360$ 天，一个月 $30$ 天，这些都正好是 $5$ 的倍数，所以答案之和天数之差 $d_2 - d_1$ 有关。因此可以不用计算总天数，只计算天数之差即可。

```c++
#include<bits/stdc++.h>
using namespace std;

#define ios ios::sync_with_stdio(false), cin.tie(0), cout.tie(0)

string to[6] = {"", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday"};
unordered_map<string, int> mp = {
    {"Monday", 1},
    {"Tuesday", 2},
    {"Wednesday", 3},
    {"Thursday", 4},
    {"Friday", 5}
};

int main(){
    ios;

    int T; cin >> T;
    while(T -- ){
        int y1, m1, d1; cin >> y1 >> m1 >> d1;
        string s; cin >> s;
        int y2, m2, d2; cin >> y2 >> m2 >> d2;

        int a = mp[s], d = d2 - d1; // d 天数之差
        int b = ((a + d - 1) % 5 + 5) % 5 + 1; // 注意负数
        cout << to[b] << "\n";
    }

    return 0;
}
```
