# C++ STL的初学者教程


本篇教程分为以下几部分：STL的概述、STL常用容器、STL常用算法、STL常用迭代器以及STL的实现原理。

## 一、STL的概述

STL，即Standard Template Library（标准模板库），是C++的一个重要组成部分。STL具有很强的通用性，它提供了一系列容器、算法和迭代器，使得我们可以用相同的方式来处理各种数据类型。

STL的主要优势有：

1. 高度的通用性：STL中提供的容器和算法对各种数据类型都适用。

2. 高效的性能：STL中的容器和算法被实现为高效的C++代码，可以比手写代码更快、更节省内存。

3. 大量的封装：STL中的容器和算法的大量封装，使得我们不需要自己实现这些数据结构和算法，而直接使用就可以了。

4. 可移植性：由于STL遵循国际标准，因此程序员可以在不同的编译器和操作系统上使用相同的代码。

## 二、STL常用容器

容器是STL的核心组成部分，STL提供了多种容器类型。每种容器都有自己的特点和用途。

### 1. vector

vector是一种动态数组，它可以在尾部插入或删除元素，并支持随机访问。vector的底层实现是一个连续的内存空间。

使用vector需要包含头文件`<vector>`。

下面是vector的基本操作：

```c
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    // 创建一个空的vector对象
    vector<int> vec;

    // 在尾部插入元素
    vec.push_back(1);
    vec.push_back(2);
    vec.push_back(3);

    // 访问元素
    cout << vec[0] << endl;  // 输出1

    // 遍历vector
    for (int i = 0; i < vec.size(); ++i)
    {
        cout << vec[i] << " ";
    }
    cout << endl;

    // 在指定位置插入元素
    vec.insert(vec.begin() + 1, 4);

    // 删除最后一个元素
    vec.pop_back();

    // 删除指定位置的元素
    vec.erase(vec.begin() + 1);

    // 清空vector
    vec.clear();

    return 0;
}
```

### 2. list

list是一种双向链表，它支持在任意位置插入或删除元素，但不支持随机访问。

使用list需要包含头文件`<list>`。

下面是list的基本操作：

```c
#include <iostream>
#include <list>

using namespace std;

int main()
{
    // 创建一个空的list对象
    list<int> lst;

    // 在尾部插入元素
    lst.push_back(1);
    lst.push_back(2);
    lst.push_back(3);

    // 在头部插入元素
    lst.push_front(0);

    // 访问元素
    cout << lst.front() << endl;  // 输出0
    cout << lst.back() << endl;   // 输出3

    // 遍历list
    for (list<int>::iterator it = lst.begin(); it != lst.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    // 在指定位置插入元素
    lst.insert(++lst.begin(), 4);

    // 删除第一个元素
    lst.pop_front();

    // 删除最后一个元素
    lst.pop_back();

    // 删除指定位置的元素
    lst.erase(++lst.begin());

    // 清空list
    lst.clear();

    return 0;
}
```

### 3. map

map是一种关联数组，它将键值对储存在内部，支持快速查找和删除。map中的键是唯一的，值可以重复。

使用map需要包含头文件`<map>`。

下面是map的基本操作：

```c
#include <iostream>
#include <map>

using namespace std;

int main()
{
    // 创建一个空的map对象
    map<string, int> mp;

    // 插入键值对
    mp["apple"] = 1;
    mp["banana"] = 2;
    mp["orange"] = 3;

    // 访问元素
    cout << mp["apple"] << endl;  // 输出1

    // 遍历map
    for (map<string, int>::iterator it = mp.begin(); it != mp.end(); ++it)
    {
        cout << it->first << ":" << it->second << " ";
    }
    cout << endl;

    // 删除键值对
    mp.erase("banana");

    // 判断某个键是否存在
    if (mp.count("orange"))
    {
        cout << "orange exists" << endl;
    }

    // 清空map
    mp.clear();

    return 0;
}
```

### 4. set

set是一种集合，它将数据储存在内部，支持快速查找和删除。set中的元素是唯一的。

使用set需要包含头文件`<set>`。

下面是set的基本操作：

```c
#include <iostream>
#include <set>

using namespace std;

int main()
{
    // 创建一个空的set对象
    set<int> st;

    // 插入元素
    st.insert(1);
    st.insert(2);
    st.insert(3);

    // 访问元素
    set<int>::iterator it = st.find(2);
    if (it != st.end())
    {
        cout << *it << endl;  // 输出2
    }

    // 遍历set
    for (set<int>::iterator it = st.begin(); it != st.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    // 删除元素
    st.erase(2);

    // 判断某个元素是否存在
    if (st.count(1))
    {
        cout << "1 exists" << endl;
    }

    // 清空set
    st.clear();

    return 0;
}
```

### 5. deque

deque是一种双端队列，它支持在两端插入或删除元素，并支持随机访问。

使用deque需要包含头文件`<deque>`。

下面是deque的基本操作：

```c
#include <iostream>
#include <deque>

using namespace std;

int main()
{
    // 创建一个空的deque对象
    deque<int> deq;

    // 在尾部插入元素
    deq.push_back(1);
    deq.push_back(2);
    deq.push_back(3);

    // 在头部插入元素
    deq.push_front(0);

    // 访问元素
    cout << deq[0] << endl;  // 输出0

    // 遍历deque
    for (deque<int>::iterator it = deq.begin(); it != deq.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    // 在指定位置插入元素
    deq.insert(deq.begin() + 1, 4);

    // 删除第一个元素
    deq.pop_front();

    // 删除最后一个元素
    deq.pop_back();

    // 删除指定位置的元素
    deq.erase(deq.begin() + 1);

    // 清空deque
    deq.clear();

    return 0;
}
```

## 三、STL常用算法

STL中还提供了许多常用算法，这些算法可以对容器中的元素进行排序、查找、遍历等操作，使用这些算法可以大量减少我们的代码量。

使用STL常用算法需要包含头文件`<algorithm>`。

下面是一些常用算法的示例：

### 1. sort

sort是一种排序算法，它可以对容器中的元素进行排序。sort默认按升序排序，也可以自定义比较函数来实现其他排序方式。

使用sort需要包含头文件`<algorithm>`。

下面是sort的示例：

```c
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

bool cmp(int a, int b)
{
    return a > b;  // 自定义比较方式，降序排列
}

int main()
{
    // 创建一个vector对象
    vector<int> vec;
    vec.push_back(3);
    vec.push_back(1);
    vec.push_back(4);
    vec.push_back(2);

    // 对vector进行排序
    sort(vec.begin(), vec.end());  // 默认按升序排序

    // 输出排序结果
    for (int i = 0; i < vec.size(); ++i)
    {
        cout << vec[i] << " ";
    }
    cout << endl;

    // 按降序排列
    sort(vec.begin(), vec.end(), cmp);

    // 输出排序结果
    for (int i = 0; i < vec.size(); ++i)
    {
        cout << vec[i] << " ";
    }
    cout << endl;

    return 0;
}
```

### 2. find

find是一种查找算法，它可以在容器中查找某个元素。如果元素不存在，返回的迭代器等于容器的end()。

使用find需要包含头文件`<algorithm>`。

下面是find的示例：

```c
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    // 创建一个vector对象
    vector<int> vec;
    vec.push_back(3);
    vec.push_back(1);
    vec.push_back(4);
    vec.push_back(2);

    // 查找元素2
    vector<int>::iterator it = find(vec.begin(), vec.end(), 2);
    if (it != vec.end())
    {
        cout << "Found " << *it << endl;
    }
    else
    {
        cout << "Not found" << endl;
    }

    return 0;
}
```

### 3. for_each

for_each是一种遍历算法，它可以对容器中的每个元素执行相同的操作。

使用for_each需要包含头文件`<algorithm>`。

下面是for_each的示例：

```c
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void print(int x)
{
    cout << x << " ";
}

int main()
{
    // 创建一个vector对象
    vector<int> vec;
    vec.push_back(3);
    vec.push_back(1);
    vec.push_back(4);
    vec.push_back(2);

    // 对vector中的每个元素执行print函数
    for_each(vec.begin(), vec.end(), print);
    cout << endl;

    return 0;
}
```

## 四、STL常用迭代器

迭代器是STL的另一个核心组成部分，它是一种类似于指针的对象，用于遍历容器中的元素。STL中提供了多种迭代器类型，每种迭代器都有自己的特点和使用方式。

下面是STL常用迭代器的示例：

### 1. vector迭代器

vector迭代器支持随机访问，可以直接访问指定位置的元素。

```c
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    // 创建一个vector对象
    vector<int> vec;
    vec.push_back(3);
    vec.push_back(1);
    vec.push_back(4);
    vec.push_back(2);

    // 使用迭代器输出vector中的元素
    for (vector<int>::iterator it = vec.begin(); it != vec.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    // 访问指定位置的元素
    cout << vec[0] << endl;              // 输出3
    cout << *(vec.begin() + 1) << endl;  // 输出1

    return 0;
}
```

### 2. list迭代器

list迭代器支持双向遍历，可以在任意位置插入或删除元素。

```c
#include <iostream>
#include <list>

using namespace std;

int main()
{
    // 创建一个list对象
    list<int> lst;
    lst.push_back(3);
    lst.push_back(1);
    lst.push_back(4);
    lst.push_back(2);

    // 使用迭代器输出list中的元素
    for (list<int>::iterator it = lst.begin(); it != lst.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    // 在指定位置插入元素
    lst.insert(++lst.begin(), 5);

    // 删除指定位置的元素
    lst.erase(--lst.end());

    // 使用迭代器反向遍历list
    for (list<int>::reverse_iterator it = lst.rbegin(); it != lst.rend(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

### 3. map迭代器

map迭代器是一个pair类型，第一个元素表示键，第二个元素表示值。

```c
#include <iostream>
#include <map>

using namespace std;

int main()
{
    // 创建一个map对象
    map<string, int> mp;
    mp["apple"] = 1;
    mp["banana"] = 2;
    mp["orange"] = 3;

    // 使用迭代器输出map中的元素
    for (map<string, int>::iterator it = mp.begin(); it != mp.end(); ++it)
    {
        cout << it->first << ":" << it->second << " ";
    }
    cout << endl;

    return 0;
}
```

### 4. set迭代器

set迭代器支持顺序遍历，但不支持随机访问。

```c
#include <iostream>
#include <set>

using namespace std;

int main()
{
    // 创建一个set对象
    set<int> st;
    st.insert(3);
    st.insert(1);
    st.insert(4);
    st.insert(2);

    // 使用迭代器输出set中的元素
    for (set<int>::iterator it = st.begin(); it != st.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

## 五、STL的实现原理

STL的内部实现非常复杂，它是通过模板和泛型编程技术来实现的。在STL中，容器和算法都是通过模板来实现的，因此STL可以非常方便地处理各种数据类型。

STL的实现基于两个重要的概念：迭代器和仿函数。迭代器是一个类似于指针的对象，用于遍历容器中的元素；仿函数是一个类或函数指针，用于对容器中的元素进行操作。

STL的容器分为顺序容器和关联容器两种。顺序容器是通过数组、链表等数据结构来实现的，而关联容器是通过红黑树等数据结构来实现的。

STL的算法包括排序、查找、遍历等操作，它们都是通过迭代器和仿函数来实现的。STL的算法和容器是完全独立的，因此我们可以在任何容器中使用STL的算法。

总之，STL是一个非常强大的工具，它提供了丰富的容器、算法和迭代器，可以大大提高我们的代码效率。