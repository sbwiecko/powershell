```powershell
# install package
pip install virtualenv # as administrator

# set the python directory of interest
$python_path = 'C:\Program Files\Python36\python.exe'

# create the virtual environement in the destination directory
cd c:\to\dir
virtualenv.exe --python=$python_path .\venv_dir

# activate venv
.\venv_dir\Scripts\activate
python --version

# deactivate venv
deactivate
```

