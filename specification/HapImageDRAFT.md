# Hap Images


## Introduction


The Hap Image format allows for the storage of a still image using the Hap codec. Hap stores images in a format that can be decoded in part by dedicated graphics hardware on modern computer systems. It is well suited to the display of very high resolution images when fast decoding is a priority.


## Scope


This document describes the content of Hap Image files. It makes no recommendation on the practical details of implementing an encoder or decoder.


## External References


The correct encoding and decoding of Hap Images depends on the [Hap Video specification][1] and the compression schemes outlined in that document.


## Hap Images

A Hap image must start with an identifying signature. All content after the signature uses the sectioned layout described in the Hap Video specification in the section _Hap Frames_. The same rules which apply to the ordering of sections and the handling of unrecognised sections in Hap Frames apply to Hap Images.


### Identifying Signature

The first four bytes of a Hap Image file must have the following hexadecimal values:

    0x88 0x48 0x61 0x70


### Image File Sections

Immediately following the Identifying Signature are a number of sections including at minimum a Frame Dimensions section and a complete Hap frame in one of the sections described in _Top-Level Sections_ in the Hap Video specification.


|Type Field Byte Value |Meaning          |
|----------------------|-----------------|
|0x05                  |Frame Dimensions |


##### Frame Dimensions

The section data is two four-byte fields being unsigned integers stored in little-endian byte order, indicating the width and the height of the frame in pixels, in that order. This section may only appear at the top level of a Hap Image.


## Names and Identifiers

Where Hap Images are stored in a file as described above, the following file characteristics are recommended:

|Human-Readable Description |File Extension |
|---------------------------|---------------|
|Hap Image                  |hpz            |


[1]: https://raw.githubusercontent.com/Vidvox/hap/master/documentation/HapVideoDRAFT.md
