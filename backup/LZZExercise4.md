# LZZExercise4
## 第一步
1.1 创建项目，点击Empty Views Activity
1.2 选择Java语言
1.3 RGB取色网站推荐https://link.fobshanghai.com/rgbcolor.htm

## 第二步
### 创建工具栏
**2.1 打开app/res/layout/activity_main.xml**
将hello world代码块改为以下代码

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="21251109999_XXX_27XSStar"
        app:titleTextColor="@android:color/white"/>

修改为自己的学号与姓名

### 修改整体布局

**2.2 将`<?xml version="1.0" encoding="utf-8"?>`下方代码块改为以下代码**

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/你的背景图名字"
    android:orientation="vertical"
    tools:context=".MainActivity">

并将该文件最后一行代码改为：`</LinearLayout>`
确保该布局能包裹住页面所有元素

### 加入首页元素

**2.3 在工具栏代码块下方写入以下代码：**

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="#你的文字颜色"
        android:textSize="你的文字大小"
        android:text="星座简介："
        android:textStyle="你的文字样式"
        android:layout_margin="5dp"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="你的文字大小"
        android:textColor="#你的文字颜色"
        android:textStyle="你的文字样式"
        android:text="在西方占星学上，黄道12星座是字宙方位的代名词，一个人出生时，各星体落入黄道上的位置，说明了一个人的先天性格及天赋。黄道12星座象征心理层面，反映出一个人行为的表现的方式。于是将黄道分成12个星座，称为黄道12星座。依次为白羊座、金牛座、双子座、巨蟹座、狮子座、处女座、天秤座、天蝎座、射手座、魔蝎座、水瓶座、双鱼座。"
        android:layout_margin="5dp"
        />

    <Button
        android:id="@+id/button_search"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textStyle="你的字体样式"
        android:textSize="你的文字大小"
        android:textColor="#你的文字颜色"
        android:text="星座测算"
        android:layout_margin="5dp"
        android:layout_gravity="center_horizontal"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="你的文字大小"
        android:textColor="#你的文字颜色"
        android:textStyle="你的文字样式"
        android:text="请输入您的姓名："
        android:layout_margin="5dp"
        />

    <EditText
        android:id="@+id/edit_inputname"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="你的文字大小"
        android:textColor="#你的颜色"
        android:background="#你的颜色"
        android:layout_margin="5dp"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="你的文字大小"
        android:textColor="#你的颜色"
        android:text="请输入您的出生日期："
        android:layout_margin="5dp"
        android:textStyle="你的字体样式"
        />

    <DatePicker
        android:id="@+id/datePicker_birth"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="#你的颜色"
        android:layout_gravity="center_horizontal"
        />

## 第三步

### 导入图片

3.1 在Android Studio中打开app/res/drawable文件夹

3.2 右键这个文件夹并点击“打开于”再点击“资源管理器”

3.3 将你的照片导入该文件夹（复制进去）并注意将2.2步骤中的`android:background="@drawable/你的图片名字"`修改为你背景图片的名字
*例如我将点击按钮前的照片名字改为before，点击按钮后的照片名字改为after*

3.4 再将后面需要的星座图片导入进去

星座图片可以去网课下载
https://www.icourse163.org/learn/SZIUT-1449945183?tid=1465433530#/learn/announce

或者去此处：
通过网盘分享的文件：drawable.zip
链接: https://pan.baidu.com/s/1ZJZcnAxWrWI8O64ZlRqilw 提取码: tmyq 
--来自百度网盘超级会员v5的分享

## 第四步

### 打开MainActivity文件

4.1 打开app/java/com.example.你的项目名文件夹

4.2 打开MainActivity文件

4.3 导入以下的库

    import android.content.Intent;
    import android.view.View;
    import android.widget.Button;
    import android.widget.DatePicker;
    import android.widget.EditText;

4.4在`public class MainActivity extends AppCompatActivity {`下方写入以下代码：

    //第一步，定义对象
    Button btn_search;
    EditText edit_inputname;
    DatePicker date_birth;

4.5在

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

下方写入以下代码：

        //第二步，绑定控件
        btn_search = findViewById(R.id.button_search);
        edit_inputname = findViewById(R.id.edit_inputname);
        date_birth = findViewById(R.id.datePicker_birth);

        //第三步，按钮单击事件
        btn_search.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this , SecondActivity.class);
                intent.putExtra("name",edit_inputname.getText().toString());
                intent.putExtra("year",date_birth.getYear());
                intent.putExtra("yue",date_birth.getMonth());
                intent.putExtra("ri",date_birth.getDayOfMonth());
                startActivity(intent);
            }
        });
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

## 第五步

### 创建新的页面

5.1 打开“app/java/com.example.你的项目名”文件夹

5.2 右键这个文件夹，点击“新建”，再点击“Activity”，再点击"Empty Views Activity"
然后我命名为SecondActivity，你想命名啥都行

**5.3 打开app/res/layout/activity_second.xml文件（名字不同可能是你命名不同，总之点击新的文件）**

### 修改布局

5.4 将`<?xml version="1.0" encoding="utf-8"?>`下方的一块布局代码改为：

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="@drawable/after"
    tools:context=".SecondActivity">

5.5 将代码最后一行改为`</LinearLayout>`

### 写入各种元素

5.6 在中间写入：

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="21251109999_XXX_27XSStar"
        app:titleTextColor="@android:color/white"/>

    <TextView
        android:id="@+id/textView_getname"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示获取到的用户名"
        android:textStyle="你的字体样式"
        android:textColor="#你的字体颜色"
        android:textSize="你的字体大小"
        android:layout_margin="5dp"/>

    <TextView
        android:id="@+id/textView_getbirth"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示获取到的出生日期"
        android:textStyle="你的字体样式"
        android:textColor="#你的字体颜色"
        android:textSize="你的字体大小"
        android:layout_margin="5dp"/>

    <ImageView
        android:id="@+id/imageView_imgstar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/ic_launcher_background"
        android:layout_gravity="center"
        android:layout_margin="20dp"/>
    
    <TextView
        android:id="@+id/textView_contentstar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示星座的性格特点"
        android:textColor="#你的字体颜色"
        android:textStyle="你的字体样式"
        android:textSize="你的字体大小"
        android:layout_margin="5dp"/>

## 第六步

### 让新的页面接收数据

6.1 打开app/res/values文件夹，打开strings.xml文件
在该文件中间写入以下代码：

    <string name="白羊座">白羊座（3月21日～4月20日）：热情、自信、坚毅、乐观，但同时也显得有些鲁莽、急躁、粗心大意。白羊座的人总是充满了热情和活力，他们可以迅速地掌握新的事物，并愿意为自己追求的梦想奋斗到底。</string>
    <string name="金牛座">金牛座（4月21日～5月21日）：稳重、勤劳、务实、细致，但天生奉献者的他们，有时会显得固执，不善于改变。金牛座的人总是注重现实和实用性，他们内心深知自己所追求的东西，会持之以恒地为之奋斗。</string>
    <string name="双子座">双子座（5月22日～6月21日）：好奇、机智、灵活、聪慧，但有时显得不够专注，容易分心。双子座的人总是充满了好奇心和热情，他们善于社交，善于沟通，脑子活络，让他们成为人群中的佼佼者。</string>
    <string name="巨蟹座">巨蟹座（6月22日～7月22日）：敏感、温和、善良、细腻，但有时显得过于情绪化和依赖。巨蟹座的人总是充满了感性和温暖，他们善于倾听他人的心声，也会付出自己的爱和关怀，是朋友和家人们心灵的寄托。</string>
    <string name="狮子座">狮子座（7月23日～8月23日）：自信、热情、领袖气质、勇气，但有时会显得过于自我和独断。狮子座的人总是充满了自信和热情，他们总是希望成为众人瞩目的焦点，并且愿意为此奉献自己的力量和才华。</string>
    <string name="处女座">处女座（8月24日～9月23日）：细致、勤奋、聪明、谨慎，但有时显得过于苛求完美和难以满足。处女座的人总是注重细节和实用性，他们不但能够在事业上取得较好的成绩，也在生活中精心打理自己的一切，让自己的生活更加充实和有品质。</string>
    <string name="天秤座">天秤座（9月24日～10月23日）：和谐、美感、公正、理智，但有时显得过于优柔寡断和理想化。天秤座的人总是注重平衡和正义，他们善于协调各方利益，追求美感和艺术，让自己的生活充满了色彩和美感。</string>
    <string name="天蝎座">天蝎座（10月24日～11月22日）：神秘、坚定、敏锐、具有洞察力，但有时显得过于孤傲和复杂。天蝎座的人总是充满了神秘和力量，他们善于洞察他人的秘密和欲望，也有着蜕变和重生的能力，让自己的内心充满了动力和力量。</string>
    <string name="射手座">射手座（11月23日～12月21日）：开朗、热情、乐观、有玩心，但有时显得不够负责任和缺乏深度。射手座的人总是充满了冒险精神和好奇心，他们喜欢旅游和探险，也善于社交和交流，让自己的生活充满了挑战和乐趣。</string>
    <string name="魔蝎座">魔蝎座（12月22日～1月20日）：稳重、谨慎、冷静、有耐心，但有时显得过于保守和过于功利。摩羯座的人总是注重事业和实用性，他们勤劳踏实、具备组织才能和领导力，也在威严和权威中体现自己的价值。</string>
    <string name="水瓶座">水瓶座（1月21日～2月19日）：开放、思想先进、自由、创新，但有时显得过于理想化和缺乏责任心。水瓶座的人总是充满了好奇心和创造力，他们敢于打破常规，追求自由和创新，让自己的内心充满了新鲜感和刺激。</string>
    <string name="双鱼座">双鱼座（2月20日～3月20日）：敏感、温情、浪漫、梦幻，但有时显得过于感性和缺乏理性。双鱼座的人总是充满了浪漫与梦想，他们敏感而富有同情心，希望能够帮助他人，也会给予自己充分的关爱和支持。</string>


6.2 打开app/java/com.example.你的项目名文件夹
打开SecondActivity文件，写入以下的库：

    import android.widget.ImageView;
    import android.widget.TextView;

6.3 将`import android.widget.TextView;`以下的代码全部删除，导入我写的代码：

    public class SecondActivity extends AppCompatActivity {
    //第一步，定义对象
    TextView txt_getname, txt_getbirth, txt_contentstar;
    ImageView img_imgstar;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

        //第二步，绑定控件
        txt_getname = findViewById(R.id.textView_getname);
        txt_getbirth = findViewById(R.id.textView_getbirth);
        txt_contentstar = findViewById(R.id.textView_contentstar);
        img_imgstar = findViewById(R.id.imageView_imgstar);

        //第三步，接收第一页传递过来的值并显示到对应的文本控件里面
        String strl = getIntent().getStringExtra("name");
        int myyear = getIntent().getIntExtra("year", 0);
        int mymonthl = getIntent().getIntExtra("yue", 0);
        int mymonth = mymonthl + 1;
        int myday = getIntent().getIntExtra("ri", 0);
        txt_getname.setText("你好：" + strl);
        txt_getbirth.setText("您的出生日期为：" + myyear + "年" + mymonth + "月" + myday + "日");

        //第四步，从12张星座图片中与日期对应的一张照片，下标：0-11
        int[]
                imgarr = {R.drawable.baiyang, R.drawable.jinniu, R.drawable.shuangzi, R.drawable.juxie, R.drawable.shizi, R.drawable.chunv, R.drawable.tiancheng, R.drawable.tianxie, R.drawable.sheshou, R.drawable.mojie, R.drawable.shuiping, R.drawable.shuangyu};
        int[]
                contentarr = {R.string.白羊座, R.string.金牛座, R.string.双子座, R.string.巨蟹座, R.string.狮子座, R.string.处女座, R.string.天秤座, R.string.天蝎座, R.string.射手座, R.string.魔蝎座, R.string.水瓶座, R.string.双鱼座};

        //第五步，根据选择的年月日从数组里找对应的图片和文字
        int i = find(mymonth, myday);
        img_imgstar.setImageResource((imgarr[i]));
        txt_contentstar.setText(contentarr[i]);

        ViewCompat.setOnApplyWindowInsetsListener(

                findViewById(R.id.main), (v, insets) ->

                {
                    Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
                    v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
                    return insets;
                });

    }
        private int find( int mymonth, int myday){
            int i = 0;
            if (mymonth == 3 && myday >= 21 || mymonth == 4 && myday <= 19) {
                i = 0;
            }
            if (mymonth == 4 && myday >= 20 || mymonth == 5 && myday <= 20) {
                i = 1;
            }
            if ((mymonth == 5 && myday >= 21) || mymonth == 6 && myday <= 21) {
                i = 2;
            }

            if ((mymonth == 6 && myday >= 22) || mymonth == 7 && myday <= 22) {
                i = 3;
            }
            if ((mymonth == 7 && myday >= 23) || mymonth == 8 && myday <= 22) {
                i = 4;
            }
            if ((mymonth == 8 && myday >= 23) || mymonth == 9 && myday <= 22) {
                i = 5;
            }

            if ((mymonth == 9 && myday >= 23) || mymonth == 10 && myday <= 23) {
                i = 6;
            }
            if ((mymonth == 10 && myday >= 24) || mymonth == 11 && myday <= 22) {
                i = 7;
            }
            if ((mymonth == 11 && myday >= 23) || mymonth == 12 && myday <= 21) {
                i = 8;
            }

            if ((mymonth == 12 && myday >= 22) || mymonth == 1 && myday <= 19) {
                i = 9;
            }
            if ((mymonth == 1 && myday >= 20) || mymonth == 2 && myday <= 18) {
                i = 10;
            }
            if ((mymonth == 2 && myday >= 19) || mymonth == 3 && myday <= 20) {
                i = 11;
            }


            return i;
        }
    }

