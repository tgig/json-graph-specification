json-graph-specification
========================

A proposal for representing graph structure es / edges) in JSON.

Design principles
-----------------

- Use meaningful property names that reflect the semantic type of the value.
- Property names should not be excessively long.
- Property names should be plural when value is an array.
- Properties that allow a ``null`` value can be omitted.
- Define JSON schema for content validation purposes.

.. _properties:

Common Properties
-----------------

.. _id property:

**id property**

An `id` property is a primary key for an object (see Objects_) that is unique for the object type.  Its value is defined as a *JSON string* for flexibility.

**label property**

A `label` property provides a text display for an object.  Its value is defined as a *JSON string*.

**metadata property**

A `metadata` property allows for custom data on an object.  Its values is defined as a *JSON object*.


.. _objects:

Objects
-------

.. _node object:

**node object**

A node object represents a node in a graph.

**node properties**

- Includes all `Common Properties`_

.. _edge object:

**edge object**

An edge object represents an edge in a graph.

**edge properties**

- Includes all `Common Properties`_
- A `source` property provides the `id` value of the source `node object`_.  Its value is defined as a *JSON string*.
- A `target` property provides the `id` value of the target `node object`_.  Its value is defined as a *JSON string*.
- A `type` property provides semantic meaning to the edge (e.g. edge relationship).  Its value is defined as a *JSON string*.

.. _graph object:

**graph object**

A graph object represents a single conceptual graph.

**graph properties**

- Includes all `Common Properties`_
- A `type` property that provides the type of data represented in this graph.  Its value is a *JSON string*.
- A `nodes` property provides the nodes in the graph.  Its value is an array of `node object`_.
- An `edges` property provides the edges in the graph.  Its value is an array of `edge object`_.

Example
-------

.. _example:

.. code-block:: json

    {
        "graph": {
            "id": "default",
            "type": "movie characters",
            "label": "Usual Suspects",
            "nodes": [
                {
                    "id": "Roger Kint",
                    "label": "Roger Kint"
                    "metadata": {
                        "nickname": "Verbal",
                        "actor": "Kevin Spacey"
                    }
                },
                {
                    "id": "Keyser Söze",
                    "label": "Keyser Söze"
                    "metadata": {
                        "actor": "Kevin Spacey"
                    }
                }
            ],
            "edges": [
                {
                    "source": "Roger Kint",
                    "target": "Keyser Söze",
                    "type": "is"
                }
            ]
            "metadata": {
                "release year": "1995"
            }
        }
    }
