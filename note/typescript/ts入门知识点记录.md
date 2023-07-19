[ts保姆级教程，别再说你不会ts了](https://juejin.cn/post/7092415149809598500)

##### ts类型

基础类型：

- 原始类型：string/number/boolean/null/undefined/symbol
- 对象类习惯：object

新增类型：

- 联合类型
- 自定义类型（类型别名）
- 接口
- 元组
- 字面量类型
- 枚举
- void
- any

##### ts工具类型（语法糖）

- **Partial**    将接口或者类型别名定义的所有参数变成可缺省参数

  ```typescript
  interface IPerson1  {
    name: string;
    age:number;
    getName():string
  }
  let p1:Partial<IPerson1> = {
    name: 'woo'
  }
  type IPerson2 =  {
    name: string;
    age:number;
    getName():string
  }
  
  let p2:Partial<IPerson2> = {
    age: 18
  }
  ```

- **Required**   将接口或者类型别名定义的所有参数变成不可缺省参数 