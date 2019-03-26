# VW-Compression-Zip-Write
Basic support for writing ZIP archives. Corresponds to version 2.0 of the ZIP specification.
Reading and updating is not supported. Use Compression-Zip to read archives.

## Example
Create a ZIP archive and add `$(VISUALWORKS)/doc/BasicLibraries.pdf` as `pdf/BasicLibraries.pdf`
```
| archive file |
archive := Zip.Archive newOnFilename: 'BasicLibraries.zip'.
archive comment: 'Library documentation'.
[   
    file := Filename fromComponents: #('$(VISUALWORKS)' 'doc' 'BasicLibraries.pdf').
    archive addFilename: file relocateFrom: file directory to: 'pdf' asFilename.
] ensure: [
    archive close
].
```
Protocol `writing` of WritableArchive contains various methods to add content to an archive.