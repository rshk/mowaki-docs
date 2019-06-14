Using Bootstrap
###############

While you can use Bootstrap_ directly, there are many advantages in
using a library such as Reactstrap_ to provide ready-made React
components, instead of having to reference bootstrap classes manually.

.. _Bootstrap: https://getbootstrap.com/
.. _Reactstrap: https://reactstrap.github.io/


.. warning::

   Make sure you are in the ``web`` folder before running the commands below::

       cd ./web


Installation
============

Install dependencies from NPM::

    npm install --save bootstrap reactstrap


Then load the Boostrap CSS from ``src/index.js``:

.. code-block:: javascript

    import 'bootstrap/dist/css/bootstrap.min.css';


Usage
=====

Refer to `Reactstrap documentation`_ for more information.

.. _Reactstrap documentation: https://reactstrap.github.io/components/


Advanced: customize bootstrap
=============================

Bootstrap can be customized by loading the SCSS files instead, and
providing custom configuration variables.

This allows tweaking things like colors, sizes, etc.

To keep things organized, we'll start creating a ``style`` folder::

    mkdir src/style

Create a ``src/style/_vars.scss`` file, to load all the customized variables

.. code-block:: scss

    @import "~bootstrap/scss/functions";
    @import "./custom";
    @import "~bootstrap/scss/variables";

.. note::

   The main advantage of having this as a separate file, rather than in
   ``index.global.scss`` is we can then load variables from this file
   into any of our other scss files.

Then, copy the bootstrap variables to ``_custom.scss``::

    cp ./node_modules/bootstrap/scss/_variables.scss ./src/style/_custom.scss


.. note::

    While just adding overridden variables to ``_custom.scss`` would
    be enough, we find it makes life a lot easier to be able to search
    for variables / tweak them directly in one file.

    Keep  in mind  you can  remove the  ``!default`` marker  from
    variables as you customize their values.


You can then create a ``src/style/index.scss`` to load all the
bootstrap SCSS, along with the required customizations:

.. code-block:: scss

    @import "./vars";
    @import "~bootstrap/scss/bootstrap";


.. note::

   You can load individual components instead of the whole ``bootstrap.scss``.

   This has the benefit of reducing bundle size (and compile time).

   Have a look at ``node_modules/bootstrap/scss/bootstrap.scss`` to
   see which imports you're going to need.


Finally, load it from ``src/index.global.scss``:

.. code-block:: sass

    @import "~style/index";
