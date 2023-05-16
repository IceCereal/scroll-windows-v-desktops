# Scroll Windows Virtual Desktops

This tool scrolls through your virtual desktops. See https://medium.com/p/cbb659435849 for more details.

This fork contains one difference in the `scroll-desktops.py` program - the ability to pass an argument (via sys.argv[1]) as the config file. This is done for launching the created executable on login. Check [Running This Program On Log In](#running-this-program-on-log-in) below.

## Install requirements

```sh
pip install -r requirements.txt
```

## Build

```sh
pyinstaller --onefile scroll-desktops.py
```

Builded file is in `./dist`

If you get an `Import Error` while running the compiled exe try to use the following command:

```sh
pyinstaller --hidden-import "pynput.keyboard._win32" --hidden-import "pynput.mouse._win32" --onefile scroll-desktops.py
```

If you don't want to see a window when you open the exe add the following flags to the pyinstaller command:

```sh
--nowindowed --noconsole
```

## Create config

- Copy the `config.json` from `.` into `./dist`
- Set `printPosition` to `true`
- Every time you scroll your mouse position is printed. Use those values to determine your scroll area and put those coordinates into `config.json`
- Test if everything works
- Set `printPosition` to `false`

## Running This Program on Log In

- Open Task Scheduler
- Create new basic task
- Give it a name and a description
- Trigger: When I log on
- Action: Start a program
- Program/Script:
  - Set it to the path of the created executable
  - Add Arguments: set the path to the config file