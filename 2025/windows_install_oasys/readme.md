## 1) Download and (re)install Miniconda 3 

If you tried the automatic script to install Oasys and it failed, remove Miniconda 3 from the system, by deleting the folder:

```
C:\Users\<user name>\Miniconda3
```

replacing ```<user name>``` with the name of your current user.

Download the Miniconda 3 installer https://github.com/oasys-esrf-kit/oasys_hercules_2025/raw/refs/heads/main/windows_install_oasys/Miniconda3-py38_4.9.2-Windows-x86_64.exe . Run the executable and
- install Miniconda 3 with destination folder your home folder: 

```
C:\Users\<user name>\Miniconda3
```

- install it for a single user (Install for: Just Me (recommended)), do not update paths, do not register as system Python, and do not open tutorials. 

## 2) Download xraylib

This step was giving problems in the automatic installation. To overcome this problem do the following:

- Download the xraylib conda package from https://github.com/oasys-esrf-kit/oasys_hercules_2025/raw/refs/heads/main/windows_install_oasys/xraylib-4.1.2-py38h5d928e2_1.tar.bz2 .
- Move the downloaded file to the home directory C:\Users\<user name>\

## 3) Install packages

- Open a Command Prompt window (e.q. Search cmd) and sit (if is not done) the home directory C:\Users\<user name>\
- Activate Miniconda3 by:
```
Miniconda3\Scripts\activate
```
You may check that is working well:
```
where python
C:\<user name>\\Miniconda3\python.exe
...
```

Execute the following commands in succession:

```
pip install pip --upgrade
```

(note: ignore the error message on access denied/permissions, it's harmless. To be sure, retype the command and see if pip is declared up to date)

```
conda install xraylib-4.1.2-py38h5d928e2_1.tar.bz2
pip install oasys1 --upgrade
pip uninstall -y oasys-srwpy
pip install oasys-srwpy --upgrade
pip uninstall -y syned-gui
pip install syned-gui --upgrade
pip uninstall -y PyQtWebEngine
pip install PyQtWebEngine==5.14.0
```


## 4) Check OASYS, update libraries, and install add-ons

From the cmd prompt execute the following command:

```
python -m oasys.canvas -l4
```

Oasys should appear with no add-ons.

It asks you to update/install the internal libraries. Say "OK". 

Restart it.

Click the button "Add-Ons" in the initial form and install the required Add-ons. 


Check all the add-ons.

For HERCULES 2025 you need the ESRF add-on. Install it either
- inside Oasys, follow the instuctions in https://github.com/oasys-esrf-kit/OASYS1-ESRF-Extensions
- in the Command Prompt, enter
```
pip install OASYS1-ESRF-Extensions --upgrade
```

## 6) Start Oasys (at any moment)
You can start Oasys manually. Open Command Prompt (Search: cmd) and enter:

```
Miniconda3\Scripts\activate
python -m oasys.canvas -l4
```

To make this task easier, you can (optionally) create a shortcut in the Desktop. For that follow the next section.

## 7) Create Oasys Icon

This step is optional, but highly recommended. 

Click the right button of the mouse on an empty point of your desktop. Select New -> Shortcut

This for will appear:

<img width="648" alt="Screenshot 2023-05-31 at 10 56 28 AM" src="https://github.com/oasys-kit/oasys-installation-scripts/assets/6713598/5dc79ea9-f7dd-4cb8-baf4-d27f1b45421d">

In the "location of the item" field type (do not skip the " characters):

```
"C:\Users\<user name\Miniconda3\Scripts\activate.bat" & python -m oasys.canvas
```

then click Next, this form will appear: 

<img width="639" alt="Screenshot 2023-05-31 at 11 08 00 AM" src="https://github.com/oasys-kit/oasys-installation-scripts/assets/6713598/7371d262-8ea0-4cc2-8beb-45cde02201e8">

Name the shortcut: `Oasys 1.3`

Click Finish.

If you want, an icon provided in the installation script folder can be used in the newly made shortcut. Download the icon [here](https://raw.githubusercontent.com/oasys-kit/oasys-installation-scripts/refs/heads/master/Windows/aux_bin/oasys.ico).


## Known Issues

Recently, the Add-on ShadowOui-Advanced-Tools does not install correctly, since the package retrieved by pip is corrupted. You can either:

- By using File Explorer, download the installation package from [here](https://github.com/oasys-kit/oasys-installation-scripts/tree/master), go to the folder `Desktop\oasys-installation-scripts\Windows`, and double-click the executable `fix_addons1.3.bat`.

- Alternatively, you can download this script from [here](https://raw.githubusercontent.com/oasys-kit/oasys-installation-scripts/refs/heads/master/Windows/fix_addons1.3.bat) and double-open click on it.

***

High DPI displays may cause some problem to run Oasys. The solution is to override high DPI scaling behavior for the python executable of your Miniconda installation:


1. Right-click ```C:\Users\<user name>\Miniconda3\python.exe``` and select "Properties"
2. In the Compatibility tab, Click "Change high DPI settings"
3. Check "Override high DPI scaling behavior" and select "System (Enhanced)"
4. Click Ok and then Ok or Apply.


