A unordered sets is similar to a [[Unordered Hash maps]] . The purpose is same, fast retrieval **(o(1))** or **(o(n))** for worst.

The main difference is that rather than having a key pair,  we only have values like arrays or vectors but the value itself represents a . 

# Syntax 

### Creation

```
unordered_set<type> set_name;
```

---
### Insertion

```
set_name.insert(value);
```

- To check if a value exist while insertion 

```
set_name.insert(value).second

Returns true if exist or false if doesn't
```

---

