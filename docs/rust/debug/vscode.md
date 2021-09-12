# VScode如何attach进程
## 1. 前提条件
### 安装rust插件
![rust plugin](../../../resources/rust/debug/rust_plugin.png)
### 安装codelldb
![code lldb](../../../resources/rust/debug/codelldb.png)
## 2. 确认是debug编译模式的产物
![debug taget](../../../resources/rust/debug/debug_target.png)
## 3. 找到占用文件的进程ID
```shell
lsof 文件名称
```
![lsof pid](../../../resources/rust/debug/lsof_pid.png)
## 4. attach进程
### 快捷键：cmd+shift+p
### 搜索"lldb",选择"Attach to Process"
![search attach](../../../resources/rust/debug/search_attach.png)
### 填写进程id
![attach pid](../../../resources/rust/debug/attach_pid.png)
### 5. 查看调用栈和变量
![view](../../../resources/rust/debug/view.png)