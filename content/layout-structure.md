## Layout Structure
Files are composed of three essential elements:

* `index.db`, which keeps track of all the nodes and edges,
* `assets`, the assets folder that holds all the node blobs,
* ...and `metadata.json`, which stores related metadata (e.g. attributions, authorship, source, etc.) about this file.

Files not following these rules are considered malformed.

This is then wrapped into a Zstd compressed container.
