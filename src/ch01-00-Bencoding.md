# Chapter 1
Before we can do anything torrent related, we must be able to bencode/bdecode, as is it the main way torrent metadata is delivered.

I have decided to go with a Bencode enum to list all the possible values (int/bytes/list/dict) and then write structs that can perform conversions between the bencoded string to the actual values and back. 