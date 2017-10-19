# Pickers

## Date Picker

<img src="/images/date-picker-1.png" width="360"/>

!!! quote "摘自 Google Material Design [文档](https://www.google.com/design/spec/components/pickers.html#pickers-date-pickers)"
    对话框选择器用来在手机上选择日期。
    被选中的一天，用与其他日期不同的颜色和着重类型的实心圆来表示。

### 如何添加？

I. 在 `build.gradle` 里添加最新的 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 Activity 继承自 `android.support.v7.app.AppCompatActivity` 并实现 `DatePickerDialog.OnDateSetListener` 接口。
```Java
public class MainActivity extends AppCompatActivity
    implements DatePickerDialog.OnDateSetListener {
```

III. 创建你的 `DatePickerDialog` ，并传入 context, listener, startYear, starthMonth, startDay 等参数。
```Java
DatePickerDialog datePickerDialog = new DatePickerDialog(
    context, listener, startYear, starthMonth, startDay);
```
IV. 使用 `DatePickerDialog` 的 `show` 方法展示对话框。
```Java
datePickerDialog.show();
```

### 如何设置样式？

<img src="/images/date-picker-2.png" width="360"/>

I. 为对话框背景声明自定义 `drawable.xml` 。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- From: support/v7/appcompat/res/drawable/abc_dialog_material_background_light.xml -->
<inset xmlns:android="http://schemas.android.com/apk/res/android"
    android:insetLeft="16dp"
    android:insetTop="16dp"
    android:insetRight="16dp"
    android:insetBottom="16dp">

    <shape android:shape="rectangle">
        <corners android:radius="2dp" />
        <solid android:color="@color/indigo" />
    </shape>

</inset>
```

II. 在 `styles.xml` 声明自定义样式。
```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
    <item name="colorControlNormal">@android:color/white</item>
    <item name="colorControlActivated">@color/pink</item>
    <item name="textColorAlertDialogListItem">@android:color/white</item>
    <item name="colorAccent">@color/pink</item>
    <item name="android:textColorPrimary">@android:color/white</item>
    <item name="android:windowBackground">@drawable/background_dialog</item>
</style>
```

III. 设置你的自定义样式为 `DatePickerDialog` 的一个参数。
```Java
DatePickerDialog datePickerDialog = new DatePickerDialog(
    this, R.style.MyDialogTheme, listener, 2016, 21, 3);
```
IV. 使用 `show` 方法展示你的 `DatePickerDialog` 。
```Java
datePickerDialog.show();
```

## Time Picker

<img src="/images/time-picker-1.png" width="360"/>

!!! quote "摘自 Google Material Design [文档](https://material.io/guidelines/components/pickers.html#pickers-time-pickers)"
    一个时间选择器根据用户的首选时间设置（即12小时或24小时格式）进行调整。
    对话框选择器用于在移动设备上选择一次（小时：分钟）。

### 如何添加?

I. 在你的 `build.gradle` 文件里添加最新版本的 `appcompat` 库。

```
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 activity 继承自 `android.support.v7.app.AppCompatActivity` 并且实现  `TimePickerDialog.OnTimeSetListener` 接口。

```java
public class MainActivity extends AppCompatActivity
    implements TimePickerDialog.OnTimeSetListener {
      ...
    }
```

III. 创建你的 `TimePickerDialog` 并设置 context，监听器的实现，一天的开始时间，分钟和一个 `boolean` 值，指示对话框是否显示为 24 小时格式。

```java
TimePickerDialog timePickerDialog =
    new TimePickerDialog(context, listener, startHour, startMinute, is24HourFormat);
```

IV. 通过 `TimePickerDialog` 的 `show` 方法显示你的对话框。

```java
timePickerDialog.show();
```

### 如何设置样式?

<img src="/images/time-picker-2.png" width="360"/>

I. 创建对话框自定义背景文件 `drawable.xml`。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- From: support/v7/appcompat/res/drawable/abc_dialog_material_background_light.xml -->
<inset xmlns:android="http://schemas.android.com/apk/res/android"
    android:insetLeft="16dp"
    android:insetTop="16dp"
    android:insetRight="16dp"
    android:insetBottom="16dp">

    <shape android:shape="rectangle">
        <corners android:radius="2dp" />
        <solid android:color="@color/indigo" />
    </shape>

</inset>
```

II. 在`styles.xml` 文件内添加你的自定义样式。

```xml
    <style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
        <item name="colorControlNormal">@color/indigo</item>
        <item name="colorControlActivated">@color/pink</item>
        <item name="textColorAlertDialogListItem">@color/indigo</item>
        <item name="colorAccent">@color/pink</item>
        <item name="android:textColorPrimary">@color/indigo</item>
        <item name="android:windowBackground">@drawable/background_dialog</item>
    </style>
```

III. 将你的自定义作为创建 `DatePickerDialog` 时的一个参数。

```java
TimePickerDialog timePickerDialog = new TimePickerDialog(
    context, R.style.MyDialogTheme, listener,
    startHour, startMinute, is24HourFormat);
```

IV. 通过 `show` 方法来显示你的 `TimePickerDialog`。

```java
timePickerDialog.show();
```

### Dark theme

<img src="/images/time-picker-3.png" width="360"/>

I. 使用 `R.style.Theme_AppCompat_Dialog_Alert` 主题作为`TimePickerDialog` 构造函数的样式参数。

```java
TimePickerDialog dialog = new TimePickerDialog(
    context, R.style.Theme_AppCompat_Dialog_Alert,
    listener, startingHour, startingMinute, is24HourFormat);
```

!!! note "备注"
    你也可以使用继承自 `Theme.AppCompat.Light.Dialog.Alert` 的自定义样式。

## Color Picker

<img src="/images/color-picker-1.png" width="480"/>

!!! note "摘自 Google material design [文档](https://www.google.com/design/spec/components/pickers.html)."
    Pickers 提供了一种从预先确定的集合中选择单个值的简单方法。

### 如何提添加?

I. 从 [Google open source repository](https://android.googlesource.com/platform/frameworks/opt/colorpicker/) 克隆 color picker 项目。

```
git clone https://android.googlesource.com/platform/frameworks/opt/colorpicker
```

II. 选择已经克隆的项目并作为一个新模块通过 **New/Import module** 菜单导入到 Android Studio。

III. 将新模块编译为你项目的一个依赖。

```
dependencies {
    compile project(':colorpicker')
}
```

IV. 在 `colors.xml` 资源文件中声明一些颜色。

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="red">#F6402C</color>
    <color name="pink">#EB1460</color>
    <color name="purple">#9C1AB1</color>
    <color name="deep_purple">#6633B9</color>
    <color name="indigo">#3D4DB7</color>
    <color name="blue">#1093F5</color>
    <color name="light_blue">#00A6F6</color>
    <color name="cyan">#00BBD5</color>
    <color name="teal">#009687</color>
    <color name="green">#46AF4A</color>
    <color name="light_green">#88C440</color>
    <color name="lime">#CCDD1E</color>
    <color name="yellow">#FFEC16</color>
    <color name="amber">#FFC100</color>
    <color name="orange">#FF9800</color>
    <color name="deep_orange">#FF5505</color>
    <color name="brown">#7A5547</color>
    <color name="grey">#9D9D9D</color>
    <color name="blue_grey">#5E7C8B</color>
</resources>
```

V. 使用标题、颜色数组、默认选择的颜色、列数和显示颜色的大小来初始化 `ColorPickerDialog`。

```java
ColorPickerDialog colorPickerDialog = new ColorPickerDialog();
colorPickerDialog.initialize(
    R.string.title, colors, selectedColor, numColumns, colors.length);
```

VI. 由于 `ColorPickerDialog` 继承自 `DialogFragment` ，所以可以通过 一个 `FragmentManager` 和 一个标签显示它。

```java
colorPickerDialog.show(getFragmentManager(), tag);
```

### 如何设置样式?

<img src="/images/color-picker-2.png" width="480"/>

I. 创建一个包含 `ColorPickerPalette` 的布局文件。

```xml
<com.android.colorpicker.ColorPickerPalette
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/palette"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_gravity="center"
    android:gravity="center"
    android:padding="16dp"
    />
```

!!! note "备注"
    `ColorPickerPalette` 继承自 `TableLayout` 类，所以你可以使用  `TableLayout` 的所有视图属性来设置自己的样式。

II. 为包含 `ColorPickerPalette` 的对话框定义一个暗色样式。

```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Dialog.Alert">
    <item name="colorAccent">@color/teal_light</item>
    <item name="android:textColorPrimary">@android:color/white</item>
</style>
```

III. Inflate your `ColorPickerPalette` in a view object.

```java
LayoutInflater layoutInflater = LayoutInflater.from(context);
ColorPickerPalette colorPickerPalette =
    (ColorPickerPalette) layoutInflater.inflate(R.layout.custom_picker, null);
```

IV. 用一些颜色和一个监听器设置你的 `ColorPickerPalette`。

```java
colorPickerPalette.init(colors.length, columns, mOnColorSelectedListener);
```

V. 使用一个颜色数组和默认的选中颜色作为参数调用 `ColorPickerPalette` 的 `colorPickerPalette` 方法。

```java
colorPickerPalette.drawPalette(colors, selectedColor);
```

VI. 用你的暗色主题和视图通过 `AlertDialog.Builder` 创建对话框。

```java
AlertDialog alert = new AlertDialog.Builder(this, R.style.MyDialogTheme)
    .setTitle(R.string.title_color_picker)
    .setPositiveButton(android.R.string.ok, mOnClickListener)
    .setNegativeButton(android.R.string.no, mOnClickListener)
    .setView(colorPickerPalette)
    .create();
```

VII. 显示你的对话框

```java
alert.show();
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文地址：[Pickers](https://materialdoc.com/components/pickers/)
    译者：[脉脉不得语](http://www.inferjay.com)
    译者：[Ailurus](http://www.easydone.cn)
