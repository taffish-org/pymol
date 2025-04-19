# taf-pymol

- This is a taf-app(taf-tool), you can use taffish(https://www.taffish.com) to use this taf-app.
- This app is from https://github.com/schrodinger/pymol-open-source

PyMOL is a source-available molecular visualization system created by Warren Lyford DeLano.

> 我们为 pymol 提供了普通命令行模式与 gui 模式，对于有 gui 需求的用户请获取 pymol:v3.1.0.gui，只有命令行需求的用户可以仅获取 pymol:v3.1.0

## pymol:v3.1.0.gui -- Use gui of pymol in your browser

对于 gui 模式，我们通过 VNC 与 noVNC 一起完成，实现了通过浏览器访问 gui 版本 pymol 的可能，具体教程如下：

1. 在命令行运行如下命令
  ```
  taf update
  taf install -y pymol:v3.1.0.gui
  # restart terminal or [$ source ~/.bashrc] or [$ source ~/.zshrc] ... 
  taf-pymol-v3.1.0.gui --c {docker/podman} --passwd 12345678 --port 5801
  # --c only support docker and podman, chose yours              [default container]
  # --passwd will be used when you try to connect the gui        [default 12345678]
  # --port will be used when you try to connect the gui          [default 5801]
  #        it will only be set once when you first run taf-pymol
  ```
2. 检查输出与网址
  等待运行完成，是否有错误，在程序最后您可以获得一个网址，例如：
  ``>>> pymol-GUI ===> http://localhost:5801/vnc.html <<<``
  复制网址并在浏览器中打开即可访问 pymol-gui
  <img width="1448" alt="image" src="https://github.com/user-attachments/assets/fac4efc9-377a-4ddc-af7e-8b9295a33067" />

4. 输入密码：输入在运行时设定的 passwd 密码
