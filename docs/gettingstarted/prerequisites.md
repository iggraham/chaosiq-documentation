# ChaosIQ Prerequisites

Before getting started with running your first Verification with the Chaos Toolkit and publish the results to ChaosIQ, some prerequisite steps are required.

We will go through the prerequisite steps so you are ready to get your first Verification running and published into ChaosIQ:

1. [Install the Chaos Toolkit](#creating-a-new-chaos-toolkit-cli-installation-using-pip).
1. [Add the ChaosIQ Plugin](#add-the-chaosiq-plugin-to-your-chaos-toolkit).

**If you’ve already got a working installation of the Chaos Toolkit CLI then you can skip directly to [Add the ChaosIQ Plugin](#add-the-chaosiq-plugin-to-your-chaos-toolkit)**

## Creating a new Chaos Toolkit CLI Installation using pip

The Chaos Toolkit CLI is implemented in Python 3 and so needs a working Python installation at version 3.5+. When you execute the python3 command on your machine you see something like the following then you are all set:

```
$ python3 --version
Python 3.7.6
```

If you see a version lower than 3.5 then you’ll first need to install a later version of Python. This is well documented on the [Chaos Toolkit install page](https://docs.chaostoolkit.org/reference/usage/install/)

#### Create a Python Virtual Environment

Dependencies can be installed for your Python installation through pip and it’s often a good idea to create a Python [Virtual Environment](https://docs.python.org/3/tutorial/venv.html) to contain your Chaos Toolkit CLI installation libraries.

To create a Python virtual environment called ```chaostk``` execute the following:

```
python3 -m venv ~/.venvs/chaostk
```

Now you can activate your virtual environment by executing:

```
$ source  ~/.venvs/chaostk/bin/activate
  (chaostk) $
```

!!! tip
    You may want to use [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) to make this process much nicer.


#### Install the Chaos Toolkit CLI using pip

You install the Chaos Toolkit CLI as the Python chaostoolkit module into your virtual environment by using pip:

```
(chaostk) $ pip install chaostoolkit
```

You can verify the Chaos Toolkit CLI was installed by running:

```
(chaostk) $ chaos --version
chaos, version 1.4.1
```


## Add the ChaosIQ Plugin to your Chaos Toolkit

In order for the Chaos Toolkit to communicate with ChaosIQ you need to add the chaosiq-cloud plugin to your Chaos Toolkit installation.

The chaosiq-cloud plugin is a Python package and can be found in the Python Package Index (PyPI) [chaosiq-cloud](https://pypi.org/project/chaosiq-cloud/).

 The ChaosIQ features can be added to your Chaos Toolkit CLI installation by executing:

```bash
(chaostk) $ pip install chaosiq-cloud
```

*That’s it!* You’ve got a working installation of the Chaos Toolkit CLI and the chaosiq-cloud plugin installed. The next step is to set up your Chaos Toolkit CLI to use your ChaosIQ account.
