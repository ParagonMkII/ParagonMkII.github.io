# 第一步
1.1 创建项目，点击Empty Views Activity
1.2 选择Java语言
1.3 RGB取色网站推荐https://link.fobshanghai.com/rgbcolor.htm

# 第二步
2.1 打开app/res/layout/activity_main.xml
2.2 将第二行的`androidx.constraintlayout.widget.ConstraintLayout`改为`RelativeLayout`
2.3 将中间的hello world的TextView代码块删掉
2.4 在Android Studio中打开app/res/drawable文件夹
2.5 右键这个文件夹并点击“打开于”再点击“资源管理器”
2.6 将你的照片和箭头图片导入该文件夹（复制进去）

2.5 在中间复制代码进去

    <ImageView
        android:layout_marginTop="30dp"
        android:layout_width="wrap_content"
        android:layout_height="200dp"
        android:layout_centerHorizontal="true"
        android:src="@drawable/你的照片名字"
        android:layout_marginBottom="30dp"/>

    <Button
        android:id="@+id/button_1"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_centerInParent="true"
        android:background="@drawable/startt"/>

    <Button
        android:layout_marginTop="100dp"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_above="@+id/button_1"
        android:layout_alignLeft="@id/button_1"
        android:background="@drawable/up"/>

    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_below="@+id/button_1"
        android:layout_alignLeft="@id/button_1"
        android:background="@drawable/down"/>
    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toLeftOf="@id/button_1"
        android:layout_alignTop="@id/button_1"
        android:background="@drawable/left" />
    <Button
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:layout_toRightOf="@id/button_1"
        android:layout_alignTop="@id/button_1"
        android:background="@drawable/right" />

# 第三步
3.1 打开app/res/values/strings.xml
3.2 将第二行删除并改为以下代码

    <string name="app_name">21251109999_XXX_31UIR</string>

改为你的学号的姓名

3.3 打开app/res/values/themes/themes.xml
3.4 将`    <style name="Base.Theme.项目名" parent="XXX">`中的`XXX`改为`Theme.MaterialComponents.DayNight.DarkActionBar.Bridge`
3.5 并在下一行写入：

        <item name="colorPrimary">#你喜欢的颜色</item>

# 第四步
4.1 创建项目，点击Empty Views Activity
4.2 选择Java语言
4.3 在Android Studio中打开app/res/drawable文件夹
4.4 右键这个文件夹并点击“打开于”再点击“资源管理器”
4.5 将你的背景图片导入该文件夹（复制进去）
4.6 打开app/res/layout/activity_main.xml
4.7 将代码全部删除，将以下代码复制进去

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="@drawable/你的背景图片"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="用户登录"
        android:textSize="35sp"
        android:textColor="#你的颜色"
        android:textStyle="文字样式"
        android:layout_marginTop="100dp"
        android:layout_marginBottom="100dp"
        android:layout_gravity="center"/>

    <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:layout_marginTop="20dp"
    android:layout_marginLeft="10dp"
    android:layout_marginRight="10dp"
    android:gravity="center">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="用户名："
        android:textSize="25sp"
        android:textStyle="文字样式"
        android:textColor="#你的颜色"/>

    <EditText
        android:id="@+id/edit_inputname"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="请输入用户名"
        android:textSize="25sp"
        android:textColor="#你的颜色"/>
    </LinearLayout>

    <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:layout_marginTop="20dp"
    android:layout_marginLeft="10dp"
    android:layout_marginRight="10dp"
    android:gravity="center">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="密    码："
        android:textStyle="文字样式"
        android:textSize="25sp"
        android:textColor="#文字颜色"/>

    <EditText
        android:id="@+id/edit_inputpwd"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="请输入密码"
        android:inputType="textPassword"
        android:textSize="25sp"
        android:textColor="#文字颜色"/>

    </LinearLayout>

    <CheckBox
    android:id="@+id/check_remeber"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="记住密码"
    android:textStyle="文字样式"
    android:textSize="15sp"
    android:layout_gravity="right"
    android:layout_margin="10dp"
    android:textColor="#文字颜色"/>

    <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:layout_marginTop="20dp"
    android:layout_marginLeft="10dp"
    android:layout_marginRight="10dp"
    android:gravity="center">

    <Button
        android:id="@+id/button_no"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="取消"
        android:textSize="25sp"
        android:textStyle="文字样式"
        android:textColor="#文字颜色"
        android:background="#背景颜色"
        android:layout_weight="1"/>

    <Button
        android:id="@+id/button_yes"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="登录"
        android:textStyle="文字样式"
        android:textSize="25sp"
        android:textColor="#文字颜色"
        android:background="#背景颜色"  
        android:layout_weight="1"/>

    </LinearLayout>


     </LinearLayout>

4.8 打开app/res/values/strings.xml
4.9 将第二行删除并改为以下代码

    <string name="app_name">21251109999_XXX_31UIL</string>

4.10 打开app/res/values/themes/themes.xml
4.11 将`    <style name="Base.Theme.项目名" parent="XXX">`中的`XXX`改为`Theme.MaterialComponents.DayNight.DarkActionBar.Bridge`
4.12 并在下一行写入：

        <item name="colorPrimary">#你喜欢的颜色</item>
