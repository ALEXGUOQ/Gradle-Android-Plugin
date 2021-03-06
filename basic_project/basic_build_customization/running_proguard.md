# 运行 ProGuard

从 `Gradle Plugin for ProGuard version 4.10` 之后就开始支持 ProGuard。ProGuard 插件是自动添加进来的。如果 Build Type 的 `minifyEnabled` 属性被设置为 true，对应的 task 将会自动创建。

``` Groovy
android {
    buildTypes {
        release {
            minifyEnabled true
            proguardFile getDefaultProguardFile('proguard-android.txt')
        }
    }

    productFlavors {
        flavor1 {
        }
        flavor2 {
            proguardFile 'some-other-rules.txt'
        }
    }
}
```

发布版本将会使用它的 Build Type 中声明的规则文件，product flavor（定制的产品版本）将会使用对应的 flavor 中声明的规则文件。

这里有两个默认的规则文件：
* proguard-android.txt
* proguard-android-optimize.txt

这两个文件都在 SDK 的路径下。使用 `getDefaultProguardFile()` 可以获取这些文件的完整路径。它们除了是否要进行优化之外，其它都是相同的。
