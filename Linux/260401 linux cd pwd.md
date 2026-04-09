### Linux cd pwd (Linux Navigation Basics)

- **cd [路径]**: 跳转到该路径 (Change directory to the specified path)
- **cd**: 回到 home 目录下 (Return to home directory)
- **pwd**: 查看当前路径 (Print working directory)

#### 路径概念 (Path Concepts)
- **绝对路径**: 以 `/` 根目录开头 (Absolute path: starts from root `/`)
- **相对路径**: 以当前目录为起点，无需以 `/` 开头 (Relative path: starts from current directory)

#### 特殊符号 (Special Symbols)
- **.** : 表示当前目录。例如 `cd ./desktop` 等价于 `cd desktop`
- **..** : 表示上一级目录。如 `cd ..` 可切换到上一级，`cd ../..` 表示切换到上两级
- **~** : 表示 `/home/用户名`。/home里面这一层装的是不同的用户，~只指向自己的家目录，如果想访问别的用户的目录里的文件夹，需要在有权限的情况下使用**绝对路径**
