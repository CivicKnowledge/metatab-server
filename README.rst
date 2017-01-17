Metatab Server
==============

Running a Metatab Server in Docker
----------------------------------

The ``docker`` directory contains Dockerfiles and Makefiles to operate them. The numbers are redis containers are needed
only for production systems and the Google Spreadsheet plugin that generate ID numbers; you can safely ignore them.

To build and run the test metatab container:

.. code-block:: bash

    $ cd docker/metatab
    $ make build
    $ make start
    $ ./test.sh

Run in development:

    FLASK_APP=metatab_server.server:app FLASK_DEBUG=1 flask run

Run with Gunicorn:

    gunicorn -w 4 --max-requests 10 --timeout 300 --access-logfile - --error-logfile - -b 0.0.0.0:80 metatab_server:app

Send a CSV file:

    curl -H "Content-Type: text/csv" --data-binary '@test/example1.csv' http://127.0.0.1:5000/v1/parse