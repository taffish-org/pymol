# taf-pymol

- This is a taf-app(taf-tool), you can use taffish(https://www.taffish.com) to use this taf-app.
- This app is from https://github.com/schrodinger/pymol-open-source

PyMOL is a source-available molecular visualization system created by Warren Lyford DeLano.

> We provide normal command line mode and GUI mode for pymol, for users who need GUI please get pymol:v3.1.0.gui, and for users who only need command line, you can only get pymol:v3.1.0

## pymol:v3.1.0.gui -- Use gui of pymol in your browser

For the gui mode, we do it together with noVNC through VNC, which makes it possible to access the gui version of pymol through a browser, as shown in the following tutorials:

### 1. Run the following command on the CLI:
  
  ```bash
  taf update
  taf install -y pymol:v3.1.0.gui
  # restart terminal or [$ source ~/.bashrc] or [$ source ~/.zshrc] ... 
  taf-pymol-v3.1.0.gui --c {docker/podman} --passwd 12345678 --port 5801
  # --c only support docker and podman, chose yours              [default container]
  # --passwd will be used when you try to connect the gui        [default 12345678]
  # --port will be used when you try to connect the gui          [default 5801]
  #        it will only be set once when you first run taf-pymol
  ```

### 2. Check the output and the URL

  Wait for the run to finish, check for errors, and if everything is fine, look at the end of the output, you can get a web address, for example:
  
  ```
  >>> pymol-GUI ===> http://localhost:5801/vnc.html <<<
  ```
  
  Copy the URL and open it in your browser to access pymol-gui:
  
  <img width="1448" alt="image" src="https://github.com/user-attachments/assets/fac4efc9-377a-4ddc-af7e-8b9295a33067" />


### 3. Enter the password and enter the GUI interface (the password is the --passwd set at runtime, the default is 12345678)

  <img width="1449" alt="image" src="https://github.com/user-attachments/assets/f7babc62-b53f-43a1-b8fe-72a27329ab53" />

  
### 4. Open the terminal in the GUI and enter pymol to open pymol in the GUI interface

  <img width="1448" alt="image" src="https://github.com/user-attachments/assets/ff73fb1c-2646-485c-99c6-33d4475bf76d" />


### 5. Use pymol-gui

  <img width="1448" alt="image" src="https://github.com/user-attachments/assets/b57426c8-33b7-4492-ab69-049f4d204af7" />
  
  <img width="1449" alt="image" src="https://github.com/user-attachments/assets/8bd8676e-3b78-4aab-bb6a-7963df6d1c76" />

  Note:
  
    - By default, the /root/ path in the container needs to be retrieved from the global path /home/$USER
    - For the remote server, you can change the localhost in the URL to the server IP to access the pymol-gui on the remote server
    - If you want to start a new service, please open a new docker/podman container and select a new port
