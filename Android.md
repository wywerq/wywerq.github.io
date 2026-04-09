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

## 权限

### 安装时权限

### 一般权限

### 特殊权限

## Activity

### 声明

```c++
<manifest ... >
  <application ... >
      <activity android:name=".ExampleActivity" />
      ...
  </application ... >
  ...
</manifest >
```

### 回调

| 回调        | 描述                                                                                           |
| ----------- | ---------------------------------------------------------------------------------------------- |
| onCreate()  | 这是第一个回调，在活动第一次创建时调用                                                         |
| onStart()   | 这个回调在活动为用户可见时被调用                                                               |
| onResume()  | 这个回调在应用程序与用户开始可交互的时候调用                                                   |
| onPause()   | 被暂停的活动无法接受用户输入，不能执行任何代码。当前活动将要被暂停，上一个活动将要被恢复时调用 |
| onStop()    | 当活动不在可见时调用                                                                           |
| onDestroy() | 当活动被系统销毁之前调用                                                                       |
| onRestart() | 当活动被停止以后重新打开时调用                                                                 |
