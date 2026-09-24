# Node Group Package File Specification
The Node Group Package File Specification defines a way to store and exchange content nodes for editing, publishing and consumption.

The specification consists of the following parts:
* [Layout Structure and File Integrity](content/layout-structure-and-file-integrity.md)
* [Index Database Schema](content/index-database-schema.md)
* [Content and Media Assets](content/content-and-media-assets.md)
* [Metadata Schema](content/metadata-schema.md)

Additionally, this page contains some key starting information needed for understanding the scope of the file format.
### Purpose
A Node Group Package file stores units of information, called "nodes". Nodes contain information (JSON) and can also point to other media assets (images, sounds, videos, etc.) stored within the package. It supports node edges with edge types, and node types, thus enabling developers to define a set of behaviors depending on a node's type.
