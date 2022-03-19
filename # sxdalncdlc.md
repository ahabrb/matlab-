# 在任意工作区配置vscode+c/c++
添加源代码文件#
在文件资源管理器标题栏中，选择新建文件按钮并将文件命名为helloworld.cpp。

添加hello world源代码#
现在粘贴此源代码：

    #include <iostream>
    #include <vector>
    #include <string>
    using namespace std;
    int main()
    {
        vector<string> msg {"Hello", "C++", "World", "from", "VS Code", "and the C++ extension!"};

        for (const string& word : msg)
        {
            cout << word << " ";
        }
        cout << endl;
    }
现在按Ctrl+S保存文件。请注意您刚刚添加的文件是如何出现在VS Code 侧栏中的文件资源管理器视图 ( Ctrl+Shift+E ) 中的：
构建 helloworld.cpp #
接下来，您将创建一个tasks.json文件来告诉 VS Code 如何构建（编译）程序。此任务将调用 g++ 编译器以基于源代码创建可执行文件。

从主菜单中，选择终端>配置默认构建任务。在下拉列表中，将显示一个任务下拉列表，其中列出了 C++ 编译器的各种预定义构建任务。选择g++.exe build active file，它将构建当前在编辑器中显示（活动）的文件。
![选择](https://code.visualstudio.com/assets/docs/cpp/mingw/build-active-file.png)
这将在文件夹中创建一个tasks.json文件.vscode并在编辑器中打开它。
运行构建#
回到helloworld.cpp. 您的任务构建活动文件并且您想要构建helloworld.cpp.

要运行中定义的构建任务tasks.json，请按Ctrl+Shift+B或从终端主菜单中选择运行构建任务。

当任务开始时，您应该会看到集成终端面板出现在源代码编辑器下方。任务完成后，终端会显示编译器的输出，指示构建是成功还是失败。对于成功的 g++ 构建，输出如下所示：
![](https://code.visualstudio.com/assets/docs/cpp/mingw/mingw-build-output.png)
使用+按钮创建一个新终端，您将拥有一个以helloworld文件夹作为工作目录的新终端。运行dir，您现在应该会看到可执行文件helloworld.exe。
接下来，您将创建一个launch.json文件来配置 VS Code，以便在您按F5调试程序时启动 GDB 调试器。

从主菜单中，选择Run > Add Configuration...，然后选择C++ (GDB/LLDB)。
然后，您将看到各种预定义调试配置的下拉列表。选择g++.exe 构建和调试活动文件。
![](https://code.visualstudio.com/assets/docs/cpp/mingw/build-and-debug-active-file.png)
开始调试会话#
返回helloworld.cpp，使其成为活动文件。
按F5或从主菜单中选择Run > Start Debugging。在开始逐步浏览源代码之前，让我们花点时间注意用户界面的一些变化：
集成终端出现在源代码编辑器的底部。在“调试输出”选项卡中，您会看到指示调试器已启动并正在运行的输出。

编辑器突出显示方法中的第一条语句main。这是 C++ 扩展自动为您设置的断点：