# Floating Action Button

![Floating action button Mini](../images/fab-1.png)

!!! quote "摘自谷歌官方的 Material Design [文档](http://www.google.com/design/spec/components/buttons-floating-action-button.html#buttons-floating-action-button-floating-action-button)"
    
    FAB 用于主要的功能按钮。FAB 是一个漂浮在 UI 之上的圆形图标，并且当点击该按钮的时候，通常具有 变形、位移 等动画效果。

### 如何添加？

I. 在 `build.gradle` 中添加最新的 `appcompat` 和`design` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
    compile 'com.android.support:design:X.X.X' // where X.X.X version
}
```

II. 继承至 `android.support.v7.app.AppCompatActivity` Activity。
> 让你的 Activity 继承自 android.support.v7.app.AppCompatActivity 。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 布局文件中使用 `FloatingActionButton`。

```prettyprint lang-xml
<android.support.design.widget.FloatingActionButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_call" />
```

### 如何修改样式

![Mini FAB](https://materialdoc.com/images/device-2016-01-02-153733.png)

#### 背景颜色

I. 在 values/styles.xml 中定义一个 style。

```xml
<style name="MyFloatingButton" parent="Theme.AppCompat.Light">
    <item name="colorAccent">@color/pink</item>
</style>
```

II. 通过 `android:theme` 属性在 `FloatingActionButton` 上使用自定义的 style。

```xml
<android.support.design.widget.FloatingActionButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_call"
    android:theme="@style/MyFloatingButton" />
```

#### Ripple 效果颜色

使用 `app:rippleColor` 属性来修改当点击 `FloatingActionButton` 时候的 水波纹 的颜色。

```java
<android.support.design.widget.FloatingActionButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_call"
    app:rippleColor="@color/indigo" />
```

#### 图标

使用 `android:src` 来指定 `FloatingActionButton` 的图标。

```xml
<android.support.design.widget.FloatingActionButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_favorite"/>
```

#### 大小

!!! quote "在谷歌官方的 Material Deisgn [文档](http://www.google.com/design/spec/components/buttons-floating-action-button.html#buttons-floating-action-button-floating-action-button)"
    FAB 有两种尺寸：
    * 默认尺寸：适合大部分情况
    * 迷你尺寸：当默认尺寸和当前 UI 的其他元素不协调的时候使用迷你尺寸

使用 `app:fabSize`  来修改 `FloatingActionButton` 的大小，其取值为预设的两个常量： `mini` 或者 `normal`。

```xml
<android.support.design.widget.FloatingActionButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_mini"
    app:fabSize="mini"/>
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者：Paresh Mayani
    原文地址：[Fab](https://materialdoc.com/components/fab/)
    译者：[Goodev](http://blog.chengyunfeng.com/)
    校对：[Ailurus](http://www.easydone.cn)
