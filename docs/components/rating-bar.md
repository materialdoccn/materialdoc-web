# Rating Bar

![](../images/rating-bar-1.png)

!!! quote "摘自 Google 的[文档](http://developer.android.com/reference/android/widget/RatingBar.html)"
    RatingBar 是 SeekBar 和 ProgressBar 的一个扩展组件，可以使用星星来作为评分展示。当使用默认尺寸的 RatingBar 的时候，用户可以通过触摸/拖拽操作或者方向键设置评分。[ratingBarStyleSmall](http://developer.android.com/reference/android/R.attr.html#ratingBarStyleSmall) 和 [ratingBarStyleIndicator](http://developer.android.com/reference/android/R.attr.html#ratingBarStyleIndicator) 不支持与用户交互，只能被作为指示器来使用。

### 如何添加？

I. 在你的 `build.gradle` 里添加最新版本的 `appcompat` 库。

```groovy
dependencies {
    compile 'com.android.support:appcompat-v7:X.X.X' // where X.X.X version
}
```

II. 让你的 Activity 继承自 `android.support.v7.app.AppCompatActivity` 。

```java
public class MainActivity extends AppCompatActivity {
    ...
}
```

III. 在任意的 `layout.xml` 声明 `RatingBar` 。

```xml
<RatingBar
    android:rating="3.5"
    android:stepSize="0.5"
    android:numStars="5"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

### 如何设置样式？

![](../images/rating-bar-2.png)

I. 在 `styles.xml` 里声明自定义的样式。

```xml
<style name="RatingBar" parent="Theme.AppCompat">
    <item name="colorControlNormal">@color/indigo</item>
    <item name="colorControlActivated">@color/pink</item>
</style>
```

II. 设置 `RatingBar` 的 `android:theme` 属性值为上面自定义的样式。

```xml
<RatingBar
    android:theme="@style/RatingBar"
    android:rating="3"
    android:stepSize="0.5"
    android:numStars="5"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

!!! warning "翻译水平有限，欢迎批评指正"
    原文作者: Yakiv Mospan
    原文链接: [Rating Bar](https://materialdoc.com/components/rating-bar/)

