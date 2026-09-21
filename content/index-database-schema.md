## Index Database Schema
Each file has an SQLite database called `index.db`. This file contains all necessary information for keeping track of:
* "Who is this node?" (`id`),
* "How is this node related to other nodes?" (`edge`),
* "What is this node?" (`node_type`),
* ...and finally "What **DATA** is in this node?" (`content`).

![Entity relationship diagram of the Index Database Schema](/content/assets/er_diagram_index.png)

### Database Breakdown

#### node
* `id`: The node's identifier. Primary key.
* `node_type_id`: The foreign key pointing to this node's type.
* `content`: The node's content (JSON). Refer to ["Content and Media Assets"](content-and-media-assets.md).
#### node_type
* `id`: The node's type identifier. Primary key.
* `name`: The node's type name. Must be short (hopefully not longer than two words), in snake case, and lowercase.
* `scheme`: The node's type scheme. Nodes must respect their type's scheme. `scheme` contains the node's type JSON schema.
* `scheme_font`: The node's type scheme font (JSON). If not null, keys declared in this field will store the key's "style".
#### edge
Refer to ["Node Relationships"](#node-relationships).
* `id`: The edge's identifier. Primary key.
* `edge_type_id`: The foreign key pointing to this edge's type.
* `source_node_id`: The foreign key pointing to this edge's source node.
* `target_node_id`: The foreign key pointing to this edge's target node.
#### edge_type
* `id`: The edge's type identifier. Primary key.
* `name`: The edge's type name. 
    * Must always start with "has" (e.g. `has_reference`).
    * Must not be too long (hopefully not longer than five words).
    * Must be in snake case and lowercase.

### Node Relationships
Nodes can form complex relationships between each other. These relationships are described in the `edge` table. They help organize and form links between units of information, using detailed labels. Exposing the `edge` table enhances the reader's experience when navigating the different nodes.
