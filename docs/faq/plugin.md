# How do I check I have the latest version of the ChaosIQ plugin

To connect the Chaos Toolkit to ChaosIQ you need to [install and run the chaosiq-cloud plugin](/gettingstarted/add-chaos-iq). The plugin is added to the python environment where you run the Chaos Toolkit, so navigate to you terminal window where you have the Chaos Toolkit setup, and enter the following command.

```bash
$ pip list | grep chaosiq-cloud
```

You should see output resembling the following:

![Pip list output][listOutput]



The output shows chaosiq-cloud is installed and is version 0.10.0. The ChaosIQ Cloud plugin is distributed using the [Python Package Index (PyPI)](https://pypi.org/) which is a repository of software for the Python programming language. If you navigate to [PyPi](https://pypi.org/) and enter ```chaosiq-cloud``` in the search box the first link on the results page will be for the chaosiq-cloud plugin:

![Pypi Search Output][pypiSearch]

By selecting the first link on the search results page, you will be taken to the [chaosiq-cloud 0.10.0 Project page](https://pypi.org/project/chaosiq-cloud/), this explains the details of the project and shows its current version (0.10.0 at the time of writing):

![ChaosIQ Plugin Project][chaosiq-project]

You can view installation and usage information by scrolling down the page, and if you want to know the [Release history](https://pypi.org/project/chaosiq-cloud/#history), there is a link in the Navigation sidebar on the project page. Normally you would expect to be using the latest version.


[listOutput]: ./images/pip-list-ouput.png
[pypiSearch]: ./images/pypi-search-chaosiq-plugin.png
[chaosiq-project]: ./images/chaosiq-plugin-project-page.png
