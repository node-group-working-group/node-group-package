## Metadata Schema
`metadata.json` defines all descriptive information associated with a file, including its source, authors, and any other relevant contextual details. Here's an example of how it looks like:

```
{
    "title": "...",
    "subject": "...",
    "contributors": 
    [
        {
            "name": "...",
            "contribution": "..."
        },
        ...
    ],
    "publisher" "...",
    "description": "...",
    "date": "...",
    "identifier": "...",
    "language": "...",
    "license": "...",
    "@version": "..."
    "other": { ... }
}
```
### Metadata Breakdown
Any field starting with `@` is used for system management and should not be edited manually by any user.
* `title`: The file's title.
* `subject`: The file's subject or academic field.
* `contributors`: The file's contributos. Contributors have the following fields:
    * `name`: The contributor's full name.
    * `contribution`: The contributor's role in this file.
* `publisher`: The file's publisher.
* `description`: The file's description.
* `date`: The file's publication date.
* `identifier`: The file's identifier (e.g. ISBN).
* `language`: The file's content display language.
* `license`: The file's license.
* `@version`: The file's version.
* `other`: Any other variable that isn't specified here in this specification.
