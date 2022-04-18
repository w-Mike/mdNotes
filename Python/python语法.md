 1、 a[x:y:z]指的是从下标x开始y结束（应该是左闭右开），每隔z个取一个元素组成切片,如果 z为负数 则表示从	最后后一个往前
2、 创建空集合不能用 setName = {},而是用 setName = set()
3、 for循环也有else语句的：当循环“自然”终结（循环条件为假）时 else 从句会被执行一次，而当循环是由 break 语句中断时，else 从句就不被执行。
4、 enumerate(,) ：将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据					下标
5、 map()方法 ：map() 会根据提供的函数对指定序列做映射。
	第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函		数返回值的新列表。

6 、        方法			说明
    lst.append(x)	将元素x添加至列表lst尾部
    lst.extend(L)	将列表L中所有元素添加至列表lst尾部
    lst.insert(index, x)	在列表lst指定位置index处添加元素x，该位置后面的所有元素后移一个	位置
    lst.remove(x)	在列表lst中删除首次出现的指定元素，该元素之后的所有元素前移一个位置
    lst.pop([index])	删除并返回列表lst中下标为index（默认为-1）的元素
    lst.clear()			删除列表lst中所有元素，但保留列表对象
    lst.index(x)	返回列表lst中第一个值为x的元素的下标，若不存在值为x的元素则抛出异常
    lst.count(x)	返回指定元素x在列表lst中的出现次数
    lst.reverse()	对列表lst所有元素进行逆序
    lst.sort(key=None, reverse=False)	对列表lst中的元素进行排序，key用来指定排序依据，		reverse决定升序（False）还是降序（True）
    lst.copy()	返回列表lst的浅复制

7、Counter类： Counter(可迭代对象)： 返回一个每个item的出现次数
8、sorted:  sorted(iterable, key=None, reverse=False)  
	sort: list.sort(cmp=None, key=None, reverse=False)
   sort 与 sorted 区别：
    sort 是应用在 list 上的方法，sorted 可以对所有可迭代的对象进行排序操作。
    list 的 sort 方法返回的是对已经存在的列表进行操作，而内建函数 sorted 方法返回的是一个新的 		list，而不是在原来的基础上进行的操作。
9. isinstance(变量名 ,  数据类型） 
10.  