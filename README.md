一个简易的webpack，目前所有的配置都是直接写入的，没有从config文件中读取，等有时间了在写个从config文件中读取的功能

解析流程：

1. 首先读入要解析的文件
2. 使用 babel.babylon 将其转化为用 commonjs 加载的 ast 树
3. 然后加载转化 loader：babel.traverse 将代码从 es6 转化为 es5
4. 使用广度优先遍历的方法将其依赖的文件也依次转义为 es5
5. 将转义出的所有代码作为 commonjs 的输入值输入（string）
6. 输出该文件