Technologies Used
====

.. _Cisco ASA:

Cisco ASA
------------

We chose to use the Cisco ASA 
.. We choose to implement the ASA line of products because of its well-established presence in the IT Security Industry and for ease of configuration and Maintenace as well as support.


Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

