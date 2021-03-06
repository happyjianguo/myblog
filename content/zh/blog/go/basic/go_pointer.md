---
title: "go 指针"
authors: [kiki]
tags: [go]
categories: [blog]
draft: false
---

- 指针变量指向一个值的内存地址：不是所有值都有地址，但是所有变量都有地址
  - 每一个聚合类型变量的组成(结构体的成员或数组中的元素)都是变量，都有一个地址
- 先声明指针才可以使用指针
- 声明`var ptr_name *ptr_type`
  - `ptr_type`是指针类型
  - `ptr_name`是指针变量名
  - `*`用于指定变量是作为一个指针
- 通过 `&` 生成一个变量的指针变量

  ```go
  i := 42
  p = &i
  ```

- `*ptr`在指针类型前加`*`获取指针所指向的内容，也就是“间接引用”或“重定向”

  ```go
  fmt.Println(*p)
  *p = 21
  ```

- 和 C 不同，go 的指针没有数学运算
- 空指针 `nil`：指针定义后未分配到变量时值为 `nil`，类似其他语言的 `null/None/nil/NULL`
- 指针变量通常缩写为 ptr
- 指针数组，来存储地址，声明`var ptr_name [len]*ptr_type`
- 指向指针的指针，声明`var pptr_name **pptr_type`
  - `**pptr`在指针的指针类型前加`**`获取指针所指向的内容
- 指针作为函数参数，通过引用或地址传参可在函数内部改变变量值
