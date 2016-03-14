*****************************
Reserve collections solr core
*****************************

This project aims to provide a multi core solr configuration to search for reserve collections and its related objects. `Apache Solr`_ is a java web application that provides full text search through the use of `Apache Lucene`_.


Installation
============

First of all get your working copy of this repository.

.. code-block:: shell

    git clone https://github.com/unibib-duisburg-essen/reserve-collections-solr-schema.git solr-home

*solr-home* is going to be our :code:`$SOLR_HOME` from here on.

To make use of the configuration you have to have a Java runtime environment and a running copy of apache solr. Download `Java`_ and the latest version of `Solr <http://lucene.apache.org/solr/mirrors-solr-latest-redir.html>`_. Inside the solr ``bin`` dir you can find several binaries to just run solr or install it as system service (Windows and Linux). For development just start solr inside the console using:

.. code-block:: shell

    bin/solr start -f -s $SOLR_HOME

:code:`$SOLR_HOME` should be the location you cloned this repository to. If solr successfully started you can access the application from `your browser <http://localhost:8983/solr/#/>`_

The installation is now finished and can be used by the reserve collection web application. If for example the application model changes it may be possible that the solr model must be modified.

Model
=====

There are four cores configured:

* ``reservecollectionview``
* ``bookjobview``
* ``copyrightview``
* ``scanjobview``

These cores are adressed by the reserve collections web application for crud operations. For example the list of all reserve collection loads its data form the :code:`reservecollectionview`. The list is filtered on query changes therefore must be very fast.

Take a look at the different :code:`schema.xml` files located in :code:`<core>/conf` to view all configured fields.

Dataimport
==========

Every core has one :code:`data-config.xml` file that can be used to perform a import from the database. Inside the :code:`dataConfig` element there are multiple :code:`dataSource` elements given, that contain information to connect to a database. The given data (driver, url ...) must be configured to match your local installation. Also make sure to install the correct jdbc driver to the :code:`$SOLR_HOME/lib` directory.

.. _Java: http://java.oracle.com
.. _Apache Lucene: http://lucene.apache.org
.. _Apache Solr: http://lucene.apache.org/solr/
