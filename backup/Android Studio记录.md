在MainActivity中，如果将

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

删除，那么状态栏就可以达到与工具栏颜色相同
如果未删除，则与页面背景颜色相同

此代码为创建项目时默认生成，可能的作用为：
这段代码是用来处理 Android 应用中的 窗口插入（Window Insets），特别是系统栏（如状态栏和导航栏）的插入。这些插入通常会影响视图的布局和外观。

1. `ViewCompat.setOnApplyWindowInsetsListener`
`ViewCompat` 是 Android 支持库中的一个类，用于在不同版本的 Android 系统上提供一致的视图操作。
`setOnApplyWindowInsetsListener` 方法为指定视图设置一个窗口插入监听器。它允许你处理和响应窗口插入的变化。
2. `findViewById(R.id.main)`
`findViewById` 方法用于查找布局中 ID 为 main 的视图。这通常是一个根视图或某个重要的容器视图。
3. `(v, insets) -> {...}`
这部分是一个 Lambda 表达式，实现了 `OnApplyWindowInsetsListener` 接口的 `onApplyWindowInsets` 方法。
v 是触发事件的视图。
insets 是一个 `WindowInsetsCompat` 对象，包含关于系统栏、状态栏和其他插入的相关信息。
4. `Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());`
使用 `insets.getInsets(WindowInsetsCompat.Type.systemBars())` 方法提取系统栏的插入。
`systemBars` 对象包含了当前系统栏的左、上、右、下的插入值，通常用于计算视图的 `padding`。
5. `v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);`
通过 `setPadding` 方法为视图设置合适的内边距（padding），以便将系统栏的插入值应用到视图上。
这样做的目的是确保视图内容不会被系统栏覆盖，保持良好的用户体验。
6. `return insets;`
返回原始的 `insets` 对象，以便进一步处理（如果有其他监听器或操作需要该信息）。
总结
这段代码的目的是在 `main` 视图上设置一个监听器，以响应窗口插入的变化。它通过调整视图的内边距，确保内容不会被系统栏覆盖，从而提高用户界面的可用性和视觉效果。这在设计全屏应用或者需要兼容不同屏幕尺寸和方向的应用时特别重要。