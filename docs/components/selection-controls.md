# Selection Controls

## Check Box

![](../images/check-box-intro-v1.png)

!!! quote "摘自 google material design [文档](https://www.google.com/design/spec/components/selection-controls.html#)"
    Checkboxes允许用户从一组选项中选择多个选项。
    如果你有多个选项出现在列表中,你可以通过使用 Checkboxes 代替 on/off Switches 来节省空间。
    如果你只有一个选项，避免使用一个 Checkbox，但是可以使用一个 on/off switch。

### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 Activity 继承自 `android.support.v7.app.AppCompatActivity`。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 文件内任一位置声明你的 `CheckBox`

```xml
<CheckBox
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true"
    android:text="Check Box"/>
```

### 如何设置样式?

![check box style v1](../images/check-box-style-v1.png)

I. 在 `styles.xml` 文件内声明你的自定义样式.

```xml
<style name="MyCheckBox" parent="Theme.AppCompat.Light">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. 将这个样式通过 `android:theme` 属性应用到你的 `CheckBox`.

```xml
<CheckBox
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true"
    android:text="Check Box"
    android:theme="@style/MyCheckBox"/>
```

## Radio Button

![](../images/radio-button-intro-v1.png)

!!! quote "摘自 google material design [文档](https://www.google.com/design/spec/components/selection-controls.html#selection-controls-radio-button)"
    Radio buttons 允许用户从一组选项中选择一个选项。如果你觉得用户需要并排看到所有可选项，并用 radio buttons 从中选择唯一的一个选项。
    那么，可以考虑用一个下拉菜单，相对于显示所有选项会占用更少的空间。

### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat`库.

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 activity 继承自 `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在 `layout.xml` 文件内任意位置声明你的 `RadioButton`

```xml
<RadioButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true"
    android:text="Radio Button"/>
```

### 如何设置样式?

![radio-button-style-v1](../images/radio-button-style-v1.png)

I. 在 `styles.xml` 文件内声明你的自定义样式.

```xml
<style name="MyRadioButton" parent="Theme.AppCompat.Light">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. 通过 `android:theme` 属性将这个样式应用到你的 `RadioButton` .

```xml
<RadioButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true"
    android:text="Radio Button"
    android:theme="@style/MyRadioButton"/>
```

## Switch

![](../images/switch-intro-v1.png)

!!! quote "摘自 google material design [文档](https://www.google.com/design/spec/components/selection-controls.html#selection-controls-switch)"
    On/off Switches 切换可以设置单选状态。开关控制的选项，以及它所处的状态，应该通过与它对应一致的内部标签明确地展示出来，以达到与 radio button（单选按钮）相同的视觉效果。
    on/off 滑动开关用文字标示 “on” 和 “off” 的做法已被弃用。请用文首所示图例来代替。


### 如何添加?

I. 在你的 `build.grade` 文件末尾添加 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 `activity` 继承自 `android.support.v7.app.AppCompatActivity`。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在任意的 `layout.xml` 文件内声明你的 `SwitchCompat` 。

```xml
<android.support.v7.widget.SwitchCompat
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true" />
```

> SwitchCompat 是 Switch 控件的向下兼容版本。

### 如何设置样式?

![](../images/switch-style-v1.png)

I. 在你的 `styles.xml` 文件内声明自定义样式。

```xml
<style name="MySwitch" parent="Theme.AppCompat.Light">
    <!-- active thumb & track color (30% transparency) -->
    <item name="colorControlActivated">@color/indigo</item>

    <!-- inactive thumb color -->
    <item name="colorSwitchThumbNormal">@color/pink</item>

    <!-- inactive track color (30% transparency) -->
    <item name="android:colorForeground">@color/grey</item>
</style>
```

II. 在你的 `SwitchCompat` 声明里设置 `android:theme` 的属性值为你自定义的样式。

```xml
<android.support.v7.widget.SwitchCompat
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true"
    android:theme="@style/MySwitch" />
```

!!! note "备注"
    Android 会自动给 `SwitchCompat` 的 `colorControlActivated` 和 `android:colorForeground` 增加 30% 的透明度。

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者：Dmytro Danylyk
    原文链接：[Selection Controls](https://materialdoc.com/components/selection-controls/)
