..
      Copyright (c) 2015 Hewlett-Packard Development Company, L.P.
      All Rights Reserved.

      Licensed under the Apache License, Version 2.0 (the "License"); you may
      not use this file except in compliance with the License. You may obtain
      a copy of the License at

          http://www.apache.org/licenses/LICENSE-2.0

      Unless required by applicable law or agreed to in writing, software
      distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
      WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
      License for the specific language governing permissions and limitations
      under the License.

Searchlight Indexing
====================
In order for the Searchlight API service to return results, information
must be indexed. The two primary mechanisms by which this happens are indexing
from the source (which allows a complete index rebuild) and indexing
information received via notifications. The types of information that can be
indexed is determined by a plugin model.

Search plugins
--------------
The search service determines the types of information that is searchable
via a plugin mechanism.  Within ``setup.cfg`` the setting within 
``[entry_points]`` named ``searchlight.elasticsearch.plugins.index_backend``
should list the available indexable types. The default provided plugins
to index glance images and glance metadefs are:

* ``image = searchlight.elasticsearch.plugins.images.ImageIndex``
* ``metadef = searchlight.elasticsearch.plugins.metadefs.MetadefIndex``

Additional plugins can be added to this list.

Bulk indexing
-------------
To initially create the catalog index (or add to it later), run the
searchlight-index command::

    $> searchlight-index

This will iterate through all registered search plugins and request that
they index all data that's available to them.

Notifications
-------------
TODO: Information about how indexing via notification works.
