# Buttons

## Raised Button

![](../images/raised-button-intro-v2.png)

!!! quote "摘自 google material design [文档](https://material.io/guidelines/components/buttons.html#buttons-raised-buttons)."
    一个典型的矩形 material 按钮在手指抬起和按下的时候会展现墨水在纸上散开的效果。

### 如何添加?

I. 在你的 `build.gradle` 文件末尾添加 `appcompat` 库.

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 创建你的 activity 并继承自 `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 内的任意位置声明你的 `Button`

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"/>
```

### 如何设置样式?

![raised-button-style-v2](https://www.materialdoc.com/images/raised-button-style-v2.png)

I. 在你的 `styles.xml` 内定义自定义样式。

```
<style name="MyButton" parent="Theme.AppCompat.Light">
    <item name="colorControlHighlight">@color/indigo</item>
    <item name="colorButtonNormal">@color/pink</item>
</style>
```

II. 通过 `android:theme` 属性应用这个样式到你的 `Button` 。

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    android:theme="@style/MyButton"/>
```

### 兼容性问题

I. 切换 `Button` 按下状态的颜色你可以使用主题的 `colorControlHighlight` 属性，虽然它仅仅影响 Lollipop 版本的系统。

II. Android `elevation` 只在 Lollipop 设备上有效，因此你在
Lollipop 之前的设备上将看不到 `Button` 周围的阴影。

## Flat Button

![](../images/flat-button-intro-v2.png)

!!! quote "摘自 google material design [文档](http://www.google.com.ua/design/spec/components/buttons.html#buttons-flat-raised-buttons)"
    一个在按下的时候会展现墨水散开的效果但没有凸起效果由墨水形成的按钮。

### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat` 库.

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 创建你的 activity 并继承自 `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 内的任意位置声明你的 `Button` 并设置  `Borderless` 样式.

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    style="@style/Widget.AppCompat.Button.Borderless"/>
```

### 如何设置样式?

![](../images/flat-button-style-v2.png)

I. 在你的 `styles.xml` 内定义自定义样式。

```xml
<style name="MyButton" parent="Theme.AppCompat.Light">
    <item name="colorControlHighlight">@color/pink</item>
</style>
```

III. 通过 `android:theme` 属性应用这个样式到你的 `Button`。

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Button"
    android:theme="@style/MyButton"
    style="@style/Widget.AppCompat.Button.Borderless"/>
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者:Dmytro Danylyk
    原文链接: [Buttons](https://materialdoc.com/components/buttons/)
