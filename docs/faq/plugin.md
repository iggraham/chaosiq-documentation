# How do I check I have the latest version of the ChaosIQ plugin?

To connect the Chaos Toolkit to ChaosIQ you need to [install and run the chaosiq-cloud plugin](/gettingstarted/add-chaos-iq). The plugin is added to the python environment where you run the Chaos Toolkit, so navigate to you terminal window where you have the Chaos Toolkit setup, and enter:

```bash
$ pip search 'chaosiq'
chaosiq-cloud (0.10.0)  - ChaosIQ plugin for the Chaos Toolkit CLI
  INSTALLED: 0.9.0
  LATEST:    0.10.0
```

The output shows in this case version 0.9.0 of the chaosiq-cloud is installed and the latest version is 0.10.0.

Normally you would expect to be using the latest version if you want to install the latest version enter:

```bash
pip install --upgrade chaosiq-cloud
```

The command will output a lot of dependency information for the   chaosiq-cloud package, which is omitted for brevity, but it will finish with the following text:


```bash
Installing collected packages: chaosiq-cloud
  Attempting uninstall: chaosiq-cloud
    Found existing installation: chaosiq-cloud 0.9.0
    Uninstalling chaosiq-cloud-0.9.0:
      Successfully uninstalled chaosiq-cloud-0.9.0
Successfully installed chaosiq-cloud-0.10.0
```

This shows the package has now been installed with the latest version.
