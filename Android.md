## 结构

```
MyApp
│
├─ app
│ ├─ src
│ │ ├─ main
│ │ │ ├─ java / kotlin # 代码
│ │ │ ├─ res # 资源
│ │ │ ├─ assets # 原始资源
│ │ │ └─ AndroidManifest.xml # 应用清单
│ │ │
│ │ ├─ test # 单元测试
│ │ └─ androidTest # UI测试
│ │
│ ├─ libs # 第三方jar
│ └─ build.gradle
│
├─ gradle
├─ build.gradle
└─ settings.gradle
```

## build.gradle

### 模块

- 命名空间
- 编译Sdk版本
- 依赖

## 应用清单

定义：

- 命名空间
- 权限
- Activity
- Service
- receiver
- Provider
