Getting started
###############

Creating your first MoWAKi project is as simple as::

    curl -sL https://git.io/mowaki-create | bash -s - ./newproject

Or if you don't feel like running some untrusted script from the Internet, have a look at the source code `here <script-source_>`_.

Also, visit the `MoWAKi project on GitHub <github_>`_ for more information.


.. _script-source: https://github.com/rshk/mowaki/blob/master/bin/create
.. _github: https://github.com/rshk/mowaki
.. _pipenv: https://pipenv.readthedocs.io/en/latest/


Installing dependencies
=======================

Backend dependencies can be installed via pipenv_::

    pipenv install

Frontend dependencies can be installed using npm::

    cd web && npm install


Configuring
===========

Create an ``.env`` file containing the necessary configuration::

    PYTHONPATH=.
    SECRET_KEY=notasecret
    DATABASE_URL=postgres://postgres:@localhost:5432/default
    REDIS_URL=redis://localhost:6379

**Note:** ``DATABASE_URL`` and ``REDIS_URL`` are only needed if you're
going to use those services, see below.


Running in development mode
===========================

Start the backend service::

    pipenv run start


Start the frontend build / server::

    cd web && npm start


Using a database
================

The project is pre-configured for quickly setting up a PostgreSQL database.

A PostgreSQL 10 instance can be started using docker-compose_::

    docker-compose up


.. _docker-compose: https://docs.docker.com/compose/

To run the necessary database migrations::

    pipenv run alembic upgrade head
