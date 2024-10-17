# 第一步
1.创建项目，点击Empty Views Activity
2.选择Java语言
3.RGB取色网站推荐https://link.fobshanghai.com/rgbcolor.htm
# 第二步
## 创建工具栏
2.1 打开app/res/layout/activity_main.xml

**删除掉hello world的代码块**

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

2.2 将`<?xml version="1.0" encoding="utf-8"?>`下方的一大块代码修改为：

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/你的图片名字"
    android:orientation="vertical"
    tools:context=".MainActivity">

2.3 将文件最后一行代码修改为`</LinearLayout>`

## 加入输入框
2.4 在工具栏代码块下方写入：

**文字大小例子：10dp**
**`layout_marginTop`可以修改不同模块之间的间隔距离，例如：30dp**
**`textStyle`可以将文字修改为粗体或者斜体**

        <EditText
            android:id="@+id/EditText"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="请输入你的姓名"
            android:textSize="输入你的文字大小"
            android:textColor="#输入你的颜色代码"/>

 修改完大小可以预览

## 加入文字框
2.5 在edittext代码块下方写入：

        <TextView
            android:id="@+id/TextView"
            android:layout_marginTop="15dp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="请选择您的出生日期："
            android:textSize="输入你的文字大小"
            android:textColor="#输入颜色代码"/>

## 加入选择日期模块
2.6 在TextView代码块下方写入

        <DatePicker
            android:id="@+id/DatePicker"
            android:layout_marginTop="15dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:calendarViewShown="false"
            android:background="#输入颜色代码"/>

## 加入跳转按钮
2.7在DatePicker代码块下方写入

        <android.widget.Button
            android:id="@+id/Button"
            android:textColor="修改你的颜色"
            android:background="#修改你的颜色"
            android:layout_marginTop="修改你的间隔"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:textSize="修改你的文字大小"
            android:fontFamily="serif-monospace"
            android:text="单击跳转到下一页"
            android:textStyle="修改文字样式"
            android:layout_gravity="center_horizontal" />

# 第三步
## 导入图片
3.1 在Android Studio中打开app/res/drawable文件夹

3.2 右键这个文件夹并点击“打开于”再点击“资源管理器”

3.3 将你的照片导入该文件夹（复制进去）并注意将**2.2步骤**中的`android:background="@drawable/你的图片名字"`修改为你图片的名字
**例如我将点击按钮前的照片名字改为before，点击按钮后的照片名字改为after**

# 第四步
## 修改MainActivity文件
4.1 打开app/java/com.example.你的项目名文件夹

**4.2 打开MainActivity文件**

4.3 在`package com.examle.项目名;`下方写入：
对照一下，保证有以下的库

    import android.os.Bundle;
    import androidx.activity.EdgeToEdge;
    import androidx.appcompat.app.AppCompatActivity;
    import androidx.core.graphics.Insets;
    import androidx.core.view.ViewCompat;
    import androidx.core.view.WindowInsetsCompat;
    import android.widget.EditText;
    import android.content.Intent;
    import android.view.View;
    import android.widget.Button;
    import android.widget.DatePicker;

4.4 在`public class MainActivity extends AppCompatActivity {`下一行写入
    //第一步，定义对象

    Button button;
    EditText editview;
    DatePicker datePicker;
    int year;
    int month;
    int day;

4.5 在

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

下方写入

        //第二步，绑定控件
        button = findViewById(R.id.Button);
        editview = findViewById(R.id.EditText);
        datePicker = findViewById(R.id.DatePicker);

        //第三步，按钮单击事件
        button.setOnClickListener(new View.OnClickListener() {
            //页面跳转逻辑
            @Override
            public void onClick(View view) {
                //记录日期
                year = datePicker.getYear();
                month = datePicker.getMonth();
                day = datePicker.getDayOfMonth();

                //设置意图
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("info",editview.getText().toString());
                intent.putExtra("Selected_date",year + "年" + (month+1) + "月" + day + "日");
                startActivity(intent);
            }
        });

**月份需要+1是因为这里的月份是从0开始计算（即0月表示1月）**

# 第五步
## 创建新的页面
5.1 打开“app/java/com.example.你的项目名”文件夹

5.2 右键这个文件夹，点击“新建”，再点击“Activity”，再点击"Empty Views Activity"
然后我命名为SecondActivity，你想命名啥都行

**5.3 打开app/res/layout/activity_second.xml文件（名字不同可能是你命名不同，总之点击新的文件）**

## 修改布局
5.4  将`<?xml version="1.0" encoding="utf-8"?>`下方的一块布局代码改为：

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="@drawable/你的图片名字"
    tools:context=".SecondActivity">

**此处需要修改背景图片**

5.5 将这个文件的最后一行代码改为`</LinearLayout>`

5.6 在布局代码块下方写入：

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="21251109999_XXX_25DatePicker26Intent"
        app:titleTextColor="@android:color/white"/>

    <TextView
        android:id="@+id/TextView_2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:text="传递接收的数值"
        android:textSize="修改文字大小"
        android:textStyle="修改文字样式"
        android:textColor="修改文字颜色"/>

    <TextView
        android:id="@+id/TextView_3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="修改上下间隔"
        android:textStyle="修改文字样式"
        android:text="出生日期"
        android:textSize="修改文字大小"
        android:textColor="修改文字颜色"/>

# 第六步
## 让新的页面接收数据

6.1 打开app/java/com.example.你的项目名文件夹

6.2 打开SecondActivity（你新建页面的名字）

6.3 保证有以下的库：

    import android.os.Bundle;

    import androidx.activity.EdgeToEdge;
    import androidx.appcompat.app.AppCompatActivity;
    import androidx.core.graphics.Insets;
    import androidx.core.view.ViewCompat;
    import androidx.core.view.WindowInsetsCompat;
    import android.widget.TextView;

6.4 在`public class SecondActivity extends AppCompatActivity {`下方写入

    //定义对应
    TextView textView_2;
    TextView textView_3;

6.5 在

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

的下方写入：

        //绑定控件
        textView_2 = findViewById(R.id.TextView_2);
        textView_3 = findViewById(R.id.TextView_3);
        //接收数据，并使用变量提取数据
        String str1 = getIntent().getStringExtra("info");
        String selectedDate = getIntent().getStringExtra("Selected_date");
        //将数据传递至textview
        textView_2.setText(str1);
        textView_3.setText("我的出生日期为："+selectedDate);

6.6 完成