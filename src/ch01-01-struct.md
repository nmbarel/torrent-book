# The Bencode Enum
In the enum, I have to represent all the possible values that are present in a bencoded file:
```rust,Bencode.rs
pub enum Bencode {
    Int(i64),
    Bytes(Vec<u8>),
    List(Vec<Bencode>),
    Dict(BTreeMap<Vec<u8>, Bencode>),
}
```
[^1]

[^1]: I have chosen to use a BTreeMap instead of a regular HashMap as the keys in the BTreeMap are stored in order, so there is no overhead to write them in order, which is a requirement (for some reason..) for the .torrent files.

Now we have all of the options our bencoded value can be! we just need a way to reach inside and grab it:

```rust,Bencode.rs
impl Bencode {
    pub fn as_int(&self) -> Option<i64> {
        if let Bencode::Int(i) = self { Some(*i) } else { None }
    }

    pub fn as_bytes(&self) -> Option<&[u8]> {
        if let Bencode::Bytes(b) = self { Some(b) } else { None }
    }

    pub fn as_str(&self) -> Option<String> {
        if let Bencode::Bytes(s) = self {Some(String::from_utf8_lossy(s).to_string())} else { None }
    }

    pub fn as_list(&self) -> Option<&[Bencode]> {
        if let Bencode::List(l) = self { Some(l) } else { None }
    }

    pub fn as_dict(&self) -> Option<&BTreeMap<Vec<u8>, Bencode>> {
        if let Bencode::Dict(d) = self { Some(d) } else { None }
    }
}
```
I think this is pretty self explanitory, just grab the reference of the value held in Bencode, the only noteworthy thing here is the as_str method, as encoded u8 can represent both bytes (sha1 of pieces) and str (pretty much all of the rest) values, so i made a helper method to do this conversion we can use whenever appropriate.

Now we have a way to store and retreive this data, we just need to actually use it.