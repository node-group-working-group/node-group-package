## Layout Structure and File Integrity
Files are composed of three essential elements:

* `index.db`, which keeps track of all the nodes and edges,
* `assets`, the assets folder that holds all the node blobs,
* ...and `metadata.json`, which stores related metadata (e.g. attributions, authorship, source, etc.) about this file.

This is then wrapped into a Zstd compressed container. Files not following these rules are considered **malformed**.

Other important actions for file integrity include:
* cleaning orphaned asset folders from deleted nodes,
* checking file hashes to prevent unwanted modifications,
* ensure correct encoding of `content` in `index.db`,
* and checking conflicts on `metadata.json` when merging files.