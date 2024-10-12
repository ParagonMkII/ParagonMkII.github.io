# 第一步
创建项目，点击Empty Views Activity
选择Java语言
# 第二步
## 创建工具栏
打开app/res/activity_main.xml
写入

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="21251109999_XXX_23Button"
        app:titleTextColor="@android:color/white"/>

将app:title里的内容改为自己的学号与姓名
# 第三步
## 导入你的图片
打开app项目文件存放位置

*例如我的：E:\AndroidProject\Exercise2r\app\src\main\res\drawable*

把两张照片存入并改名为*before.jpg*与*after.jpg*
# 第四步
## 写入ImageView与Button
**由于Button标签无法改变背景颜色，故采用android.widget.Button**
***
写入activity_main.xml

    <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="400dp"
        android:layout_height="500dp"
        android:scaleType="centerCrop"
        android:src="@drawable/before2"
        android:layout_marginBottom="25dp" />

    <android.widget.Button
        android:id="@+id/button1"
        android:layout_width="220dp"
        android:background="@color/buttonBackgroundColor"
        android:layout_height="100dp"
        android:gravity="center"
        android:textSize="30dp"
        android:fontFamily="serif-monospace"
        android:text="21251109155"
        android:textStyle="bold"
        android:textColor="@color/buttonTextColor"
        android:layout_gravity="center_horizontal" />
    </LinearLayout>

*fontFamily*修改字体
*textSize*修改文字大小
*layout_width和layout_height*修改长与宽
***
## 修改颜色
**打开app/res/values/colors.xml**
在resources中写入

    <color name="buttonTextColor">#ffffff</color>
    <color name="buttonBackgroundColor">#000000</color>

可修改颜色#
# 第五步
## 实现跳转
### 1
**打开app/java/com.example.项目名/MainActivity.java**
**确保import的库**

    import android.os.Bundle;
    import androidx.appcompat.app.AppCompatActivity;
    import androidx.appcompat.widget.Toolbar;
    import androidx.activity.EdgeToEdge;
    import androidx.core.graphics.Insets;
    import androidx.core.view.ViewCompat;
    import androidx.core.view.WindowInsetsCompat;
    import android.view.View;
    import android.widget.Button;
    import android.widget.ImageView;

### 2
在public class MainActivity extends AppCompatActivity {下方写入

    private ImageView imageView;
    private Button button;

在setContentView(R.layout.activity_main);下方写入

        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
        imageView = findViewById(R.id.imageView);
        button = findViewById(R.id.button1);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                imageView.setImageResource(R.drawable.after);
                button.setText("21251109999\n名字");
            }
        });


