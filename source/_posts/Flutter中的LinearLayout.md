---
title: Flutter中的LinearLayout
categories: Flutter
tags: Flutter布局Widget
copyright: true
comments: true
description: 
date: 22019年03月18日09:52:21
top:
photos: 
    - "/img/gaodehui_night.jpg"
---

# Row和Column
Flutter处理线性布局的时候不像Andriod中LinearLayout一样，Flutter根据布局的方向分为了Row(水平)和Column(垂直)两个控件，而在Android中，通过修改LinearLayout的属性就可以改变布局方向(水平或垂直)，不需要换其他控件。
<!--more-->
# Row的常用属性

| 属性| 默认值 | 说明 |
| ------ | ------ | ------ |
| textDirection | TextDirection.ltr | 子widget的布局顺序(是从左往右还是从右往左(TextDirection.rtl))|
| mainAxisSize | MainAxisSize.max | Row在主轴(水平)方向占用的空间。MainAxisSize.max 对应Android中的match_parent，MainAxisSize.min对应wrap_content |
| mainAxisAlignment | MainAxisAlignment.start | 表示子Widgets在Row所占用的水平空间内对齐方式 。当mainAxisSize为MainAxisSize.min，此属性无效，因为宽度是wrap_cotent。只有当mainAxisSize为MainAxisSize.max，此属性才有意义，MainAxisAlignment.start表示沿textDirection的初始方向对齐，如textDirection取值为TextDirection.ltr时，则MainAxisAlignment.start表示左对齐，textDirection取值为TextDirection.rtl时表示从右对齐。|
| verticalDirection | VerticalDirection.down | 表示Row纵轴（垂直）的对齐方向，有点类似于上面的textDirection属性 ,VerticalDirection.down表示从上到下|
| crossAxisAlignment | CrossAxisAlignment.start | 表示子Widgets在纵轴方向的对齐方式，Row的高度等于子Widgets中最高的子元素高度，它的取值和MainAxisAlignment一样(包含start、end、 center三个值)，不同的是crossAxisAlignment的参考系是verticalDirection，即verticalDirection值为VerticalDirection.down时crossAxisAlignment.start指顶部对齐，verticalDirection值为VerticalDirection.up时，crossAxisAlignment.start指底部对齐；而crossAxisAlignment.end和crossAxisAlignment.start正好相反；|
| children |  | 子控件Widgets数组 |

# 实例

## 子控件居中显示
```
          Row(
    //       子Widgets在Row所占用的水平空间内对齐方式
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text("Hello world"),
              Text(" Rc在努力"),
            ],
          ),
```
![device-2019-03-16-141913.png](https://upload-images.jianshu.io/upload_images/2018603-1e32b6cd5229ef98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


Row中的mainAxisSize默认MainAxisSize.max,即尽可能的占用Row的父控件的宽度，mainAxisAlignment: MainAxisAlignment.center 设置子控件的的对齐方式，所以这里会居中显示。

## 子控件对齐失效的原因

```
  Row(
            mainAxisSize: MainAxisSize.min,
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text("Hello world"),
              Text(" Rc在努力"),
            ],
          ),
```

当mainAxisSize设置为MainAxisSize.min，那么mainAxisAlignment将毫无意义。

## TextDirection改变子控件排列的顺序
```
   Row(
            textDirection: TextDirection.rtl,
            children: <Widget>[
              Text(" hello world "),
              Text(" Rc在努力 "),
            ],
          )
```


![device-2019-03-18-092349.png](https://upload-images.jianshu.io/upload_images/2018603-17e25250d4c9ec6f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

textDirection改为从右到左，所以最左边的是hello world，然后再到“ Rc在努力”


## 改变纵轴方向


```
 Row(
            textDirection: TextDirection.rtl,
            crossAxisAlignment: CrossAxisAlignment.start,
            verticalDirection: VerticalDirection.up,
            children: <Widget>[
              Text(" hello world ",style: TextStyle(fontSize: 30)) ,
              Text(" Rc在努力 "),
            ],
          )
```


![device-2019-03-18-093050.png](https://upload-images.jianshu.io/upload_images/2018603-1103c7f8cfa1d549.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

textDirection 设置子布局从右到左，crossAxisAlignment设置垂直对齐方向(参考系是verticalDirection)，verticalDirection设置垂直方向是由下到上。


## 参考
[线性布局Row和Column]([https://book.flutterchina.club/chapter4/row_and_column.html](https://book.flutterchina.club/chapter4/row_and_column.html)




