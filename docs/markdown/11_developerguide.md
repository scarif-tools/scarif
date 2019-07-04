# Developer Guide
This guide is for everyone who wants to play around with the Scarif pipeline code and possibly extend it.

## Getting the repositories
To start developing you have to clone the relevant Scarif repositiories. 
It is recommended to have one root "scarif-dev" directory where you clone all repos which makes it easier further down the road.
- /scarif-dev
    - /scarif
    - /scarif-core
    - /scarif-apps
    - /scarif-db
    - ...

> Repositories: https://github.com/scarif-tools

## Development Environment
We recommend to use PyCharm as IDE as it is very easy to manage different repos under one project as well as to handle 
many virtual environments at the same time.

To use your editable codebase while developing Scarif extensions or editing the core, you need to put your
project in _Development Mode_. You find the details on how to do that on the [Project Manager page](./04_projectsetup.md).

## Creating a new Scarif extension

Creating a new Scarif extension is as easy as running the ``scarif-boilerplate`` executable in the environment 
you also used for ``scarif-install``.

```
scarif-boilerplate --help
usage: scarif-boilerplate [-h] [-ov] [-ve VERSION] output_dir

Helper script. Creates a new extension template for you to work with.

positional arguments:
  output_dir            Root directory where your new Scarif extension
                        directory will be created.

optional arguments:
  -h, --help            show this help message and exit
  -ov, --overwrite      Overwrites existing project at 'output_dir' if exists.
  -ve VERSION, --version VERSION
                        Define a branch or version (tag) to use (checkout).
```

This command will run an interactive wizard where you can define the name of your extension and
details like supported Hosts, if you are planning on writing a new application integration for Scarif.

## Release a new extension version

Releasing a new version of an extension (or the first), requires you to run a set of commands. 

You also need access to your own PyPI server or publish your extension at [PyPi.org](https://pypi.org).


### Bump version number

Requires: [bumpversion](https://pypi.org/project/bumpversion/)

```
$ cd /home/user/scarif-dev/my-extension
$ bumpversion [release | minor | patch]
```

### Build Wheel

Requires: [wheel](https://pypi.org/project/wheel/)

```
$ cd /home/user/scarif-dev/my-extension
$ python setup.py bdist_wheel
```

### Upload Wheel to PyPI

Requires: [PyPi Uploader](https://pypi.org/project/pypi-uploader/)

First you need to create a valid credentials file in your user folder: ``~/.pypirc``

(On Windows you might need to create the file in some editor, then rename it appropriately via commandline)

**Example file:**

```
[aipy]
username: okrennic
password: super_secure_pw
repository: https://pypi.myserver.com
```

Then run the ``pypiupload`` command and specify the built wheel and server.

```
$ cd /home/user/scarif-dev/my-extension
$ pypiupload files dist/my_extension-0.0.1.whl -i aipy
```

Note: If you are intending on publishing to [PyPi.org](https://pypi.org), 
make sure to follow [the guide for the upload step](https://packaging.python.org/tutorials/packaging-projects/#uploading-the-distribution-archives).