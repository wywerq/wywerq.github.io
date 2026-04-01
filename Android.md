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

### 应用清单

定义：
- 权限
- Activity
- Service
- receiver
- Provider
