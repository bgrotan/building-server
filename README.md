# Building server

This is a prototype for a simple WFS server that retrieves polyhedral surfaces from a POSTGIS database and sends them back in a glTF file.

## Installation

### Python configuration

The server uses python 2.

dependencies:

    - cython
    - numpy
    - triangle
    - psycopg2

pip install .

## Configuration

Modify the settings.py file to match your postgres configuration.

## Generating the quadtree and the tile association

    python processDB.py

## launch the server with uwsgi

    uwsgi --http :9090 --wsgi-file server.py

## test

    http://localhost:9090/?query=getCities&city=montreal&tile=1/4/2&format=GeoJSON
    http://localhost:9090/?query=getGeometry&city=montreal&tile=1/4/2&format=GeoJSON
