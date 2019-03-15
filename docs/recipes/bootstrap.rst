Using Bootstrap
###############

While you can use Bootstrap_ directly, there are many advantages in
using a library such as Reactstrap_ to provide ready-made React
components, instead of having to reference bootstrap classes manually.

.. _Bootstrap: https://getbootstrap.com/
.. _Reactstrap: https://reactstrap.github.io/


Installation
============

::

    yarn add bootstrap reactstrap react react-dom


Make sure bootstrap CSS is loaded:

.. code-block:: javascript

    import 'bootstrap/dist/css/bootstrap.min.css';


Usage
=====

Refer to `Reactstrap documentation`_ for more information.

.. _Reactstrap documentation: https://reactstrap.github.io/components/


Advanced: customization
=======================

Bootstrap can be customized to your liking by making change to SCSS
variables, and creating a custom build.

To do so, we'll start by creating a ``style`` folder for our custom
SCSS:

::

    mkdir src/style
    touch src/style/_vars.scss
    touch src/style/_overrides.scss


In ``src/index.global.scss``:

.. code-block:: sass

    /*
     * Functions are useful when defining variables, so make sure
     * they're in scope.
     */
    @import "~bootstrap/scss/_functions.scss";

    /*
     * Local customizations.
     *
     * Look at node_modules/bootstrap/scss/_variables.scss to see what
     * can be customized.
     */
    @import "~style/vars";

    /*
     * Default variables.
     *
     * We import this file *after* our local customizations so that
     * derived variables are computed correctly.
     *
     * Local changes will take priority anyways, as default variables
     * are all set using !default.
     */
    @import "~bootstrap/scss/_variables.scss";

    /*
     * Main Bootstrap SCSS
     */
    @import "~bootstrap/scss/bootstrap";

    /*
     * Useful for overriding things that cannot simply be tweaked
     * using a variable.
     */
    @import "~style/overrides";
