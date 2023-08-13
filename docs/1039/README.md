# VENV

To create a virtualenv use the following command:

```python
python -m venv ./venv
```
* After running this command, a directory named venv will be created. This is the directory which contains all the necessary executables to use the packages that a Python project would need. This is where Python packages will be installed. To list the files in the folder type below command in the terminal:

`dir ./venv`

* The pip command still points to the global environment. We need to explicitly activate the created virtual environment to configure the current shell session to use pip commands from the virtualenv folder and don’t end up installing packages in the global environment: To activate venv first change the directory to venv\Scripts.

`cd venv\Scripts`

* After changing the directory type the below command.

`$ Source venv_name\Scripts> activate`

* Once the virtual environment is activated, the name of your virtual environment will appear on left side of terminal. This will let you know that the virtual environment is currently active. In the image below, venv named virtual environment is active. 

(Note: try `“./activate”` instead of `“activate”` if using powershell terminal)


* The Python interpreter as well would run the version from the virtual environment and not the global one. We can verify where the Python environment currently resides by below command:

`where python`

* The virtual environment is an almost clean Python environment. Run `pip list` to see a list with packages installed:

* Now you can install dependencies related to the project in this virtual environment. For example if you are using Django 1.9 for a project, you can install it like you install other packages.

`(venv_name)$ pip install Django==1.9`

*Once you are done with the work, you can deactivate the virtual environment by the following command:

`(venv_name)$ deactivate`
