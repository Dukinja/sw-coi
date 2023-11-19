# SW-COI is made by [DanielSpaniel](https://github.com/DanielSpaniel8/chunk-overwrite-iniector/) and is fixed by Me. 

# COI file format

## Introduction

COI (chunk overwrite injector) is a python tool for replacing lua code chunks in Swordigo `.scl` and `.scene` files. COI works by replacing a sequence of bytes at a given offset, and then replacing the rest of the chunk with spaces, up to the length of the chunk. All the information which the script needs to work is stored in a `.coi` file. This document will give an explanation of the exact syntax used in `.coi` files. If you find it confusing, just read the examples.

## Format Specifications

A `.coi` file will supply four pieces of information to the injector script :

- The file to patch

- The offset (start) of the chunk

- The length of the chunk

- The code to be injected

The offset and length are both measured in bytes. The offset is the number of bytes that come before the chunk which is the offset of the byte. The length is the number of bytes in the chunk.

The code should be in hexadecimal format, with no characters of any sort seperating bytes.

One `.coi` file can contain any number of chunk overwrite patterns. Each pattern can affect a different file, and have a different offset, but still be included in the same `.coi` file.

## Syntax

The syntax is simple : the type of information on a line is indicated by the character at the start of the line. The characters are :

- File : #

- Offset : ?

- Length : -

- Code : |

Any line that doesn't start with one of these characters is disregarded.
 
## Examples

```
#assets/resources/snowy_part1
?371
-5
|2020202020
```

This will replace five bytes at offset 371 with space characters in the first mount atlon level.

```
#assets/resources/credits.scene
?73609
-2
|2D2D
```

This will replace two bytes with dash characters at offset 73609 in the credits scene.

```
#assets/resources/town_part1.scene

?7457

-1880

|436F6C6C6973696F6E53686170652E44697361626C65416C6C2873656C66290A6C6F63616C20626C6F62203D205363656E652E4372656174654F626A6563742822626C612065626C6F62222C2022626C616465626C6F6231322229
```

This will spawn a Bladeblob in Cairnwood Village Part 1 where the brasssword event happens. 
