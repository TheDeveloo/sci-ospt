# Image

    ┌──(kali㉿kali)-[/kali-share/downloads]
    └─$ binwalk -e king
    
    DECIMAL       HEXADECIMAL     DESCRIPTION
    --------------------------------------------------------------------------------
    0             0x0             JPEG image data, EXIF standard
    12            0xC             TIFF image data, big-endian, offset of first image directory: 8
    1429567       0x15D03F        Zip archive data, at least v2.0 to extract, compressed size: 53, uncompressed size: 92, name: user
    1429740       0x15D0EC        End of Zip archive, footer length: 22