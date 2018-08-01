---
title: golang类型判断
date: 2018-07-23 15:10:52
tags: golang
---

## 最近在学习golang 突发奇想 在golang中有没有 类似于js中的`typeof`这种方法那

### 确实有这个方法 就是不是特别的简单好用 具体来看代码

```golang

// 省略一堆包声明

type Verator struct {
  x,y int
}
type T interface {}

func main() {
  a := "hello golang"
  // 第二种写法 返回的第二个参数ok true 代表类型正确
  // 这种写法 可以来判断 自定义的类型 
  // 这种写法的格式为 interface{}(a).(string|bool|int....)
  _ ,ok := T(a).(string)
  if ok {
    // todo...
  }
}

// 这种写法 必须要在switch语句里面写  e.(type)
func typeof(e interface) {
  switch e.(type) {
    case int: 
      fmt.Println("int 类型")
    default:
      fmt.Println("其他类型")
  }
}

// 还可以借助 reflect包 来进行类型判断
// 当判断 struct和interface时 需要额外处理下  可能为 package.XXX  []package.XXX
func typeof2(e interface) string {
  return reflect.TypeOf(e)
}

// 可以使用fmt.Sprintf 包 来判断类型
// %T 是 值的类型的Go语法表示
// 当判断 struct和interface时 需要额外处理下  可能为 package.XXX  []package.XXX
func typeof3 (e interface) string {
  return fmt.Sprintf("%T", e)
}

```