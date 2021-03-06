===========================
Plugin Parameter collection
===========================

.. _Collection+JSON: http://amundsen.com/media-types/collection/

.. _`link relation`: http://amundsen.com/media-types/collection/format/#link-relations

.. _`plugin parameter`: ../items/plugin_parameter.html


**Read-only**


This resource type refers to the collection of a plugin's `plugin parameter`_ items.

In other Collection+JSON_ resource representations this resource type is linked by any
`link relation`_ with attribute:

``"rel": "parameters"``


.. http:get:: /api/v1/(int:plugin_id)/parameters/

   :synopsis: Gets the list of parameters for the plugin (`plugin_id`).

   **Example request**:

   .. sourcecode:: http

      GET /api/v1/1/parameters/ HTTP/1.1
      Host: localhost:8010
      Accept: application/vnd.collection+json


   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Allow: GET
      Content-Type: application/vnd.collection+json

        {
            "collection": {
                "href": "http://localhost:8010/api/v1/1/parameters/",
                "items": [
                    {
                        "data": [
                            {
                                "name": "name",
                                "value": "dir"
                            },
                            {
                                "name": "type",
                                "value": "path"
                            },
                            {
                                "name": "optional",
                                "value": true
                            },
                            {
                                "name": "default",
                                "value": "./"
                            },
                            {
                                "name": "help",
                                "value": "look up directory"
                            }
                        ],
                        "href": "http://localhost:8010/api/v1/parameters/1/",
                        "links": [
                            {
                                "href": "http://localhost:8010/api/v1/1/",
                                "rel": "plugin"
                            }
                        ]
                    }
                ],
                "links": [],
                "version": "1.0"
            }
        }

   :reqheader Accept: application/vnd.collection+json
   :resheader Content-Type: application/vnd.collection+json
   :statuscode 200: no error
   :statuscode 401: authentication credentials were not provided
   :statuscode 404: not found

   .. |--| unicode:: U+2013   .. en dash

   .. _Properties: http://amundsen.com/media-types/collection/format/#properties
   .. _`Link Relations`: http://amundsen.com/media-types/collection/format/#link-relations

   Properties_ (API semantic descriptors):

    - `plugin parameter`_ item properties

   `Link Relations`_:

    - `plugin parameter`_ item link relations
    - **plugin** |--| links to the corresponding plugin_

   .. _plugin: ../items/plugin.html
