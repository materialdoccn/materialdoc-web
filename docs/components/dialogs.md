# Dialogs

## Alerts

![](../images/dialog_alert_simple.png)

!!! quote "摘自 Google material design [文档](http://www.google.com.ua/design/spec/components/dialogs.html#dialogs-alerts)"
    Alerts 用在需要告知用户一些情况信息的时候，是一种紧急中断，需要用户确认操作。

### 如何添加？

I. 在你的 `build.gradle` 添加最新版本的 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 使你的 Activity 继承自 `android.support.v7.app.AppCompatActivity` 。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 用 `android.support.v7.app.AlertDialog.Builder` 创建你的 dialog 。

```java
private void showLocationDialog() {
    AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
    builder.setTitle(getString(R.string.dialog_title));
    builder.setMessage(getString(R.string.dialog_message));

    String positiveText = getString(android.R.string.ok);
    builder.setPositiveButton(positiveText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // positive button logic
        }
    });

    String negativeText = getString(android.R.string.cancel);
    builder.setNegativeButton(negativeText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // negative button logic
        }
    });

    AlertDialog dialog = builder.create();
    // display dialog
    dialog.show();
}
```

### 如何设置样式

![](../images/dialog_alert_styled.png)

I. 给 dialog 背景声明自定义的 `drawable.xml` 。

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

II. 在 `styles.xml` 里声明自定义的样式。

```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
    <!--buttons color-->
    <item name="colorAccent">@color/pink</item>
    <!--title and message color-->
    <item name="android:textColorPrimary">@android:color/white</item>
    <!--dialog background-->
    <item name="android:windowBackground">@drawable/background_dialog</item>
</style>
```

III. 把上面定义的 `style` 样式作为参数传入 `AlertDialog.Builder` 来创建 dialog 。

```java
AlertDialog.Builder builder = new AlertDialog.Builder(this, R.style.MyDialogTheme);
...
AlertDialog dialog = builder.create();
// display dialog
dialog.show();
```

!!! note "备注"
    你同样可以在你的 activity theme 里通过 `alertDialogTheme` 属性设置 dialog 的样式。

## Confirmation Dialogs

![](../images/dialog_confirmation_small.png)

!!! quote "摘自 Google material design [文档](http://www.google.com.ua/design/spec/components/dialogs.html#dialogs-confirmation-dialogs)"
    确认 dialogs 需要用户在提交之前明确的确认他们选择的选项。例如，用户可以试听多个铃声，但是只有点击 “确定” 才是最终选择。
    
    在确认 dialogs 中点击 “取消” 或者按下返回键会取消一个动作，丢弃任何改动和关闭 dialogs 。

### 如何添加?

I. 在你的 `build.grade` 文件里添加最新版本的 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II.使你的 activity 继承自 `android.support.v7.app.AppCompatActivity`.

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 使用 `android.support.v7.app.AlertDialog.Builder` 创建 dialogs 。

#### 单选 dialogs

在你的 `builder` 对象上使用 `setSingleChoiceItems` 方法创建一个单选列表 dialogs 。

```java
public void showDialog() {
    AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
    builder.setTitle(R.string.dialog_title);

    //list of items
    String[] items = getResources().getStringArray(R.array.ringtone_list);
    builder.setSingleChoiceItems(items, 0,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // item selected logic
        }
    });

    String positiveText = getString(android.R.string.ok);
    builder.setPositiveButton(positiveText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // positive button logic
        }
    });

    String negativeText = getString(android.R.string.cancel);
    builder.setNegativeButton(negativeText,
            new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialog, int which) {
            // negative button logic
        }
    });

    AlertDialog dialog = builder.create();
    // display dialog
    dialog.show();
}
```

#### 多选 dialogs

在你的 `builder` 对象上使用 `setMultiChoiceItems ` 方法创建一个多选列表 dialogs 。

```java
builder.setMultiChoiceItems(items, selectedItemsArray,
        new DialogInterface.OnMultiChoiceClickListener() {
    @Override
    public void onClick(DialogInterface dialog, int which, boolean isChecked) {
        //item checked logic
    }
});
```

### 如何设置样式？

![](../images/dialog_confirmation_styled_small.png)

I. 声明自定义的 dialogs 背景 `drawable.xml`

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

II. 在你的 `styles.xml` 文件里声明自定义样式。

```xml
<style name="MyDialogTheme" parent="Theme.AppCompat.Light.Dialog.Alert">
    <!--item RadioButton or CheckBox color-->
    <item name="colorControlNormal">@android:color/white</item>
    <item name="colorControlActivated">@color/pink</item>
    <!--item text color-->
    <item name="textColorAlertDialogListItem">@android:color/white</item>
    <!--buttons color-->
    <item name="colorAccent">@color/pink</item>
    <!--title and message color-->
    <item name="android:textColorPrimary">@android:color/white</item>
    <!--dialog background-->
    <item name="android:windowBackground">@drawable/background_dialog</item>
</style>
```

III. 使用样式作为 `AlertDialog.Builder` 的参数来创建你的 dialogs 。

```java
AlertDialog.Builder builder =
        new AlertDialog.Builder(this, R.style.MyDialogTheme);
...
AlertDialog dialog = builder.create();
// display dialog
dialog.show();
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者：Volodymyr Yatsykiv
    原文地址：[Dialogs](https://materialdoc.com/components/dialogs)