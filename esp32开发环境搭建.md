# 开发环境

- [开发环境](#开发环境)
  - [目的](#目的)
  - [前期准备](#前期准备)
  - [搭建环境](#搭建环境)
  - [编译烧录](#编译烧录)
  - [测试](#测试)
  - [idf SDK 版本更新](#idf-sdk-版本更新)
  - [常见问题](#常见问题)

## 目的

- 快速完整的搭建 esp32 环境

- 杜绝项目因后期反复搭建环境浪费项目大量时间

## 前期准备

- [vscode](https://code.visualstudio.com/)
- [乐鑫官方文档](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c3/get-started/index.html)
- [git](https://git-scm.com/)

## 搭建环境

- 安装 vscode

- 安装 espressif IDF 插件

  ![](./png/1.png)

- 下载 idf(乐鑫 sdk) 和工具
  ![](./png/2.png)
  ![](./png/3.png)
  ![](./png/4.png)
  ![](./png/5.png)
-  根据提示更新 pip
  > python.exe -m pip install --upgrade pip

  ![](./png/6.png)
  ![](./png/7.png)

- 导入 wifi ap 历程
  - 按 F1 输入 show examples Projects
  ![](./png/8.png)
  ![](./png/9.png)
  ![](./png/10.png)
  ![](./png/11.png)
  ![](./png/12.png)
  - 选择导出的工程存储的目录
  ![](./png/13.png)
  ![](./png/14.png)

## 编译烧录

- 选择芯片
  ![](./png/15.png)
  ![](./png/16.png)
  ![](./png/17.png)
  
- 选择烧录口
  ![](./png/18.png)
  ![](./png/19.png)
  
- 编译(根据实际接口选择)
  ![](./png/20.png)
- 烧录(根据实际接口选择)
  ![](./png/21.png)
  ![](./png/22.png)
- 查看 log 信息
  ![](./png/23.png)
## 测试
  ![](./png/24.png)

## idf SDK 版本更新

- 进入 esp-idf 文件夹单击鼠标右键在此处打开 git 
  ![](./png/30.png)
  
- 更新 idf 版本

  > 1. git fetch  /* 从远端拉取更新的软件版本 */
  > 2. git pull    /* 拉取远端代码 */
  > 3. git checkout vX.Y.Z  /* 切换到自己需要的分支 */
  > 4. git submodule update --init --recursive /* 更新 idf 子模块 */
  > 5. git branch -a /* 查看分支信息 */
  
  ![](./png/31.png)


## 常见问题
- vscode 无法跳转？
> 1. 删除 .vscode 文件夹上的内容
> 2. 按 F1 输入 ESP-IDF: Add vscode configuration floder
![](./png/25.png)

- 如何添加用户文件？

  - 方法一：直接在 CMakeLists.txt 中添加(注意先清除工程再重新编译)
    ![](./png/26.png)
  - 方法二：使用系统工具添加
   > 1. 按 F1 输入 ESP-IDF:  Create new ESP-IDF Component
   > 2. 在输入框输入你需要添加的问题件名称，点击 enter 自动生成

    ![](./png/27.png)
    ![](./png/28.png)
    ![](./png/29.png)

- 为什么不能修改文件夹名称(个人感觉没必要这里给出查找到的原因)
  > 原因: 在 esp-idf/tools/cmake/project.cmake 中固定了这个目录
```c
        # Look for components in the usual places: CMAKE_CURRENT_LIST_DIR/main,
        # CMAKE_CURRENT_LIST_DIR/components, and the extra component dirs
        if(EXISTS "${CMAKE_CURRENT_LIST_DIR}/main")
            __project_component_dir("${CMAKE_CURRENT_LIST_DIR}/main")
        endif()
```
