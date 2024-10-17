# 第一步
1.创建项目，点击Empty Views Activity
2.选择Java语言
# 第二步
## 创建工具栏
2.1 打开app/res/activity_main.xml
写入代码

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="21251109999_XXX_25DatePicker26Intent"
        app:titleTextColor="@android:color/white"/>

将title内容改为自己的学号和姓名

## 修改整体布局
2.2 打开app/res/activity_main.xml

将<?xml version="1.0" encoding="utf-8"?>下方的一大块代码修改为：

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/before"
    android:orientation="vertical"
    tools:context=".MainActivity">