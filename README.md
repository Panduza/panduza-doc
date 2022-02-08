# Panduza Documentation

Panduza Documentation is built with python Sphinx tool.

## Installing Sphinx tool

To install python-sphinx on ubuntu system

```bash
sudo apt-get install python3 python3-pip
sudo pip3 install sphinx sphinx-rtd-theme sphinx-gherkindoc
```

## Building the documentation

To build the html documentation

```bash
cd panduza-doc
make html
firefox ./_build/html/index.html &
```
