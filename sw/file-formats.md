---
title: Designing File Formats
parent: Software Engineering
---

# Designing File Formats

## General Tips

* Clearly document the format spec so others' can easily adopt it
  * Define core features that all applications MUST implement
  * Define extra features that some applications MAY implement
  * Define how to handle common parsing errors or corruption
* Release a reference parser implementation, or suggest a method for parsing the format
* Consider adding features to allow applications to parse the file even if they may not understand all of the data

## Text Formats

*

## Binary Formats

* Include metadata to make file traversal easier
  * Record section locations at the beginning of the file
  * Record section lengths at the beginning each section

## Further Reading

* [Zip - How not to design a file format.](https://games.greggman.com/game/zip-rant/)
