# Flask RESTFul 

This Python app runs using on top Python 3.6. You can install multiple Python version using [asdf-vm](https://asdf-vm.com/#/).

## Local development

Install Python plugin.
```bash
$ asdf plugin add python
```

Install Python 3.6.3
```bash
$ asdf install python 3.6.3
```

Enable Python 3.6.3 for this app only
```bash
$ cd flask-api
$ asdf local python 3.6.3
```

Enable virtual environment using built-in module
```bash
$ python -m venv myvirtualenv
```

Install all requirements
```bash
$ pip install -r requirements.txt
```

Run the app
```bash
$ python main.py
```

## OpenShift Deployment

Using ephemeral Python environment in Kataconda.

```bash
oc login -u developer -p developer 

oc new-project app-demo

oc new-app python~https://github.com/rakhmad/flask-api.git --name=flask-demo

oc logs -f bc/flask-demo

oc expose svc/flask-demo

export URL="http://$(oc get route | grep flask-demo | awk '{print $2}')"

```
