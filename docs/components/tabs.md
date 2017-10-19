# Tabs

![Tabs Default](../images/tabs_default.png)

!!! quote "摘自 google material design [文档](https://www.google.com/design/spec/components/tabs.html)"
    Tabs 让不同视图或功能之间的浏览切换和浏览分类数据集合变得很容易。

## 如何添加？

I. 在你的 `build.gradle` 里添加最新版本的 `design` 和 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X'
    compile 'com.android.support:design:X.X.X'
    compile 'com.android.support:support-v13:X.X.X'
    // where X.X.X version

    // if you want to support android sdk < 13
    // you need to add support library v4 instead of v13
}
```

II. 让你的 Activity 继承自 `android.support.v7.app.AppCompatActivity` 。

```java
public class MainActivity extends AppCompatActivity {
 ...
}
```

III. 在你的 `layout.xml` 文件里声明 `TabLayout` 和 `ViewPager` 。

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <android.support.design.widget.TabLayout
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="?attr/colorPrimary" />

    <android.support.v4.view.ViewPager
        android:id="@+id/viewPager"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</LinearLayout>
```

IV. 将 `TabLayout` 和 `ViewPager` 组合起来。

```java
ViewPager viewPager = (ViewPager) findViewById(R.id.viewPager);

//set adapter to your ViewPager
viewPager.setAdapter(new TabPagerAdapter(getFragmentManager()));

TabLayout tabLayout = (TabLayout) findViewById(R.id.tabLayout);
tabLayout.setupWithViewPager(viewPager);
```

V. 在 ViewPager 的 adapter 里重写 `getPageTitle` 方法，并返回 tab 标题。

```java
@Override
public CharSequence getPageTitle(int position) {
     switch (position) {
          case ITEM_ONE:
               return "Item One";
          ...
     }
}
```

## 如何设置样式?

![](../images/tabs_styled.png)

I. 在你的 `styles.xml` 里声明自定义样式。

```xml
<style name="TabLayoutStyle" parent="Widget.Design.TabLayout">
    <item name="tabMaxWidth">@dimen/tab_max_width</item>
    <item name="tabIndicatorColor">@color/pink</item>
    <item name="tabIndicatorHeight">2dp</item>
    <item name="tabPaddingStart">8dp</item>
    <item name="tabPaddingEnd">8dp</item>
    <item name="tabBackground">?attr/selectableItemBackground</item>
    <item name="tabTextAppearance">@style/TabTextAppearance</item>
    <item name="tabSelectedTextColor">@android:color/white</item>
</style>

<style name="TabTextAppearance" parent="TextAppearance.Design.Tab">
    <item name="android:textSize">14sp</item>
    <item name="android:textColor">@color/color_white_semitransparent</item>
    <item name="textAllCaps">true</item>
</style>
```

II. 设置你的 `TabLayout` 的 `style` 属性为上面声明的样式。

```xml
<android.support.design.widget.TabLayout
        style="@style/TabLayoutStyle"
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
```

### Tabs with icons and text

![](../images/tabs_with_icons_and_text.png)

I. 在 ViewPager 的 adapter 里重写 `getPageTitle` 方法，并返回 tab 标题。

```java
@Override
public CharSequence getPageTitle(int position) {
     switch (position) {
          case ITEM_ONE:
               return "Item One";
          ...
     }
}
```

II. 为每一个 tab 图标创建一个选择器。

```xml
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:state_selected="true"
        android:drawable="@drawable/ic_call_selected" />
    <item
        android:state_selected="false"
        android:drawable="@drawable/ic_call_unselected" />
</selector>
```

III. 使用 `TabLayout.Tab` 的 `setIcon` 方法改变 tab 的图标，你可以使用 `TabLayout` 的 `getTabAt` 方法，并传入 tab 的索引，来获取 `TabLayout.Tab` 对象。

```java
...
//after initialization TabLayout and ViewPager
TabLayout.Tab tabCall = tabLayout.getTabAt(ITEM_CALL);
tabCall.setIcon(R.drawable.selector_call);

//repeat this code for all your tabs
...
```

### Tabs with icons only

![](../images/tabs_with_icons_and_text.png)

I. 为每一个 tab 图标创建一个选择器。

```xml
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:state_selected="true"
        android:drawable="@drawable/ic_call_selected" />
    <item
        android:state_selected="false"
        android:drawable="@drawable/ic_call_unselected" />
</selector>
```

II. 使用 `TabLayout.Tab` 的 `setIcon` 方法改变 tab 的图标，你可以使用 `TabLayout` 的 `getTabAt` 方法，并传入 tab 的索引，来获取 `TabLayout.Tab` 对象。

```java
...
//after initialization TabLayout and ViewPager
TabLayout.Tab tabCall = tabLayout.getTabAt(ITEM_CALL);
tabCall.setIcon(R.drawable.selector_call);

//repeat this code for all your tabs
...
```

### Scrollable Tabs

要让你的 `TabLayout` 支持滚动，需要添加 `custom:tabMode` 属性，并设置其值为 `scrollable` 。

```xml
<android.support.design.widget.TabLayout
        xmlns:custom="http://schemas.android.com/apk/res-auto"
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        custom:tabMode="scrollable" />
```

### Centered tabs

![](../images/tabs_centered.png)

创建位置居中的 tabs 需要添加 `custom:tabGravity` 属性，并设置其值为 `center` 。

```xml
<android.support.design.widget.TabLayout
        xmlns:custom="http://schemas.android.com/apk/res-auto"
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        custom:tabGravity="center" />
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者: Volodymyr Yatsykiv
    原文链接: [Tabs](https://materialdoc.com/components/tabs/)
