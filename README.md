# maven-dependency-demo
maven 依赖传递机制演示

# maven 依赖冲突

同一个项目中同时(直接或间接)引用了多个同坐标不同版本的包

# 依赖传递原则

依据就近原则：路径最短为准、同路径先引用为准，直接引用的以“最新”的为准

# 常见场景

## 准备

直接引用不同版本 lombok 的两个包：package-lombok-1.12.2、package-lombok-1.18.30

间接引用 lombok 的包：indirection-package-lombok-1.18.30

声明了 lombok 引用规范的包以及使用此 pom 的包：pom-lombok-1.16.22、package-lombok-with-pom

上面的包基本可以覆盖所有的场景了

## 没有父pom的项目

### 1）引用 `indirection-package-lombok-1.18.30` 和 `package-lombok-1.12.2`

### 2）引用 `package-lombok-1.12.2` 和 `package-lombok-1.18.30`

### 3）引用 `package-lombok-with-pom` 和 `package-lombok-1.18.30`

### 4）引用 `indirection-package-lombok-1.18.30` 和 `package-lombok-with-pom`

### 5）同时引用 `org.projectlombok:lombok:1.18.30` 和 `org.projectlombok:lombok:1.16.22`

## 有父pom的项目，父pom中声明lombok的版本为 1.14.8

### 1）不直接引入 org.projectlombok:lombok，引用其他所有间接引入了 lombok 的包

### 2）直接引入 org.projectlombok:lombok:1.16.12

### ps：父 pom 的 dependencyManagement 可以声明子项目引入的依赖的版本、exclusions等信息，子项目引入时就不用再次声明这些信息了


