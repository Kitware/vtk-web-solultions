# client/server

This project expect you to build the [cxx-engine](./cxx-engine/README.md) and then show you how you can expose it via different technologies.

## Requirements

On top of **cxx-engine** we need to create a Python Virtual Environment for additional web package that may not be bundled with VTK.

```bash
python3.9 -m venv .venv
source ./.venv/bin/activate
pip install -U pip
pip install "trame>=3.6.0" trame-vtk trame-vuetify numpy
```

## Trame only

Trame can let you expose the **cxx-engine** via a single file that let you define both your server and your client UI.

To run it just execute the following

```bash
export PYTHONPATH=$PWD/install/engine/python
./install/vtk/bin/vtkpython ./client-server/trame-client-server.py --venv .venv
```

## Vue client

We will still use trame but only for its server side by serving a locally built vue.js application.

### Build client

```bash
cd vue-client
npm install
npm run build
```

### Run server

```bash
export PYTHONPATH=$PWD/install/engine/python
./install/vtk/bin/vtkpython ./client-server/trame-server.py --venv .venv --content ./client-server/vue-client/dist
```

## React client

We will still use trame but only for its server side by serving a locally built react application.

### Build client

```bash
cd react-client
npm install
npm run build
```

### Run server

```bash
export PYTHONPATH=$PWD/install/engine/python
./install/vtk/bin/vtkpython ./client-server/trame-server.py --venv .venv --content ./client-server/react-client/dist
```
