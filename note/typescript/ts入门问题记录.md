# ts noob

##### 1.无法重新声明块范围变量“name”。ts(2451) lib.dom.d.ts(17878, 15): 此处也声明了 "name"

- 场景：当前问题发生于我在新建的文件夹里直接创建了一个hello.ts的文件
- 分析：在默认状态下，ts会将DOM typings 作为全局的运行环境，所以我生命的name会与DOM全局window对象下的name属性重复

- 处理：添加一个tsconfig.json,内容：

  ```json
  {
    "compilerOptions":{
      "lib":[
        "es2015"
      ]
    }
  }
  ```

  

2.

