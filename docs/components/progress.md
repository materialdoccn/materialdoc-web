# Progress & activity

## Circular

![](../images/circular-progress-1.gif)

!!! quote "摘自 google material design [文档](http://www.google.com/design/spec/components/progress-activity.html#)"
     Minimize visual changes that occur while your app loads content by representing each operation with a single activity indicator. 例如，一个刷新操作应该显示一个 refresh bar 或者 activity circle 的任何一个，但是不能同时显示。

### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 创建你的 activity 并继承自 android.support.v7.app.AppCompatActivity。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 内的任意位置声明你的 `ProgressBar`。

```xml
<ProgressBar
    style="@style/Widget.AppCompat.ProgressBar"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

### 如何设置样式?

![](../images/circular-progress-2.gif)

I. 在你的 `styles.xml` 内定义自定义样式。

```xml
<style name="CircularProgress" parent="Theme.AppCompat.Light">
    <item name="colorAccent">@color/indigo</item>
</style>
```

II. 通过 `android:theme` 属性应用这个样式到你的 `ProgressBar` 。

```xml
<ProgressBar
    android:theme="@style/CircularProgress"
    style="@style/Widget.AppCompat.ProgressBar"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

## Linear

![](../images/linear-progress-1.gif)

!!! quote "摘自 google material design [文档](http://www.google.com/design/spec/components/progress-activity.html#)"
    一个 linear progress 指示器应该总是从 0% 填充到 100%，绝对不能反着填充。 It should be represented by bars on the edge of a header or sheet that appear and disappear.

### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 创建你的 activity 并继承自 `android.support.v7.app.AppCompatActivity`。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 内的任意位置声明你的 `ProgressBar`。

```xml
<ProgressBar
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

#### 不确定的

创建不确定的 `ProgressBar` 设置 `android:indeterminate` 属性的值为 true。

```xml
<ProgressBar
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminate="true"/>
```

#### 确定的

I. 创建确定的 `ProgressBar` 设置 `android:indeterminate` 属性的值为 false。

```xml
<ProgressBar
    android:id="@+id/progressBar"
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminate="false"
    android:max="100"
    android:progress="20"/>
```

使用 `android:max` 属性去指定最大进度数。它默认等于100。

使用 `android:progress` 属性设置进度默认位置。

II. 从 UI 线程使用 `setProgress(int progress) ` 方法去更新进度位置。

```java
ProgressBar progressBar = (ProgressBar) findViewById(R.id.progressBar);
progressBar.setProgress(50);
```

#### 缓冲的

I. 创建缓冲的 `ProgressBar` 设置 `android:indeterminate` 属性的值为 false。

```xml
<ProgressBar
    android:id="@+id/progressBar"
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminate="false"
    android:max="100"
    android:progress="10"
    android:secondaryProgress="50"/>
```

使用 `android:secondaryProgress` 属性设置默认的缓冲值。

II. 使用 `setSecondaryProgress(int progress) ` 方法去更新缓冲进度位置。

```java
ProgressBar progressBar = (ProgressBar) findViewById(R.id.progressBar);

// set current progress
progressBar.setProgress(20);

// set buffered progress
progressBar.setSecondaryProgress(50);
```

#### 不确定的和确定的

创建不确定的 `ProgressBar` 设置 `android:indeterminate` 属性的值为 true。

```xml
<ProgressBar
    android:id="@+id/progressBar"
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminate="true"/>
```

每当你需要从不确定的切换到确定的进度，可以使用 `setIndeterminate(boolean indeterminate)` 方法。

```java
ProgressBar progressBar = (ProgressBar) findViewById(R.id.progressBar);
progressBar.setIndeterminate(false);
```

## 如何设置样式?

![](../images/linear-progress-1.gif)

I. 在你的 `values-v21/styles.xml` 内定义自定义样式。

```xml
<style name="LinearProgress" parent="Theme.AppCompat.Light">
    <item name="colorAccent">@color/indigo</item>
    <item name="android:progressBackgroundTint">@color/pink</item>
</style>
```

II. 通过 `android:theme` 属性应用这个样式到你的 `ProgressBar`。

```xml
<ProgressBar
    android:theme="@style/LinearProgress"
    style="@style/Widget.AppCompat.ProgressBar.Horizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

!!! note "备注"
    `android:progressBackgroundTint` 属性只工作在确定的 `ProgressBar`。


!!! warning "翻译水平有限，欢迎批评指正"
    原文作者：Yakiv Mospan
    原文链接：[Progress](https://materialdoc.com/components/progress)
