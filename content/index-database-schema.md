## Index Database Schema
Each file has an SQLite database called `index.db`. This file contains all necessary information for keeping track of:
* "Who is this node?" (`id`),
* "How is this node related to other nodes?" (`edge`),
* "What is this node?" (`node_type`),
* ...and finally "What **DATA** is in this node?" (`content`).

![Entity relationship diagram of the Index Database Schema](/content/assets/er_diagram_index.png)

### Database Breakdown

#### node
A node is a basic unit of information.
* `id`: The node's identifier. Primary key.
* `node_type_id`: The foreign key pointing to this node's type.
* `content`: The node's content (JSON). For more details, check [Content and Media Assets](content-and-media-assets.md).
* `url`: The node's access point. Can be shared through multiple nodes.
#### node_type
Node types define what a node is, its schema and how it should look when rendered.
* `id`: The node's type identifier. Primary key.
* `name`: The node's type name. Must be short (hopefully not longer than two words), in snake case, and lowercase. Must be unique.
* `schema`: The node's type schema. Nodes must respect their type's schema. `schema` contains the node's type JSON schema.
* `schema_font`: The node's type schema font styles (JSON). If not null, keys declared in this field will store those keys "style".
#### edge
For more details, check [Node Relationships](#node-relationships).
* `id`: The edge's identifier. Primary key.
* `edge_type_id`: The foreign key pointing to this edge's type.
* `source_node_id`: The foreign key pointing to this edge's source node.
* `target_node_id`: The foreign key pointing to this edge's target node.
#### edge_type
Edge types describe how nodes relate to each other.
* `id`: The edge's type identifier. Primary key.
* `name`: The edge's type name. Must be unique.
    * Must not be too long (hopefully not longer than five words).
    * Must be in snake case and lowercase.
* `direction`: The edge's direction. This field should only carry the values `unidirectional` or `bidirectional`.

### Node Relationships
Nodes can form complex relationships between each other. These relationships are described in the `edge` table. They help organize and form links between units of information, using detailed labels. Exposing the `edge` table enhances the reader's experience when navigating the different nodes.

The following example illustrates how different nodes interact with each other enhancing information storage and consumption experience for users.

![Node relationship diagram example](/content/assets/node_relationship_diagram_example.png)

In this diagram, nodes are represented by circles displaying the node's type, with the URL and ID orbiting each circle denoted as `url(id)`. Nodes relate to one another in distinct ways; for instance, both `mapuche(32)` and `mapudungun(3)` share the same image node `media/mapuche(21)`. This illustration shows just a few of the ways information can be described within this storage system.
