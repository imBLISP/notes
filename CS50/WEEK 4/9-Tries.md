# TRIES

https://www.youtube.com/watch?v=MC-iQHFdEDI&list=PLhQjrBD2T381k8ul4WQ8SQ165XqY149WW&index=49

We have seen a few data structures that handle the mapping of key-value pairs.

- Arrays: The key is the element index, the value is the data at location.
- Hash tables: The key is the hash code of the data, the value is a linked list of data hashing to that hash code.

What about a slightly different kind of data structure where the key is guaranteed to be unique, and the value could be as simple as a Boolean that tells you whether the data exists in the structure?

Tries combine and pointers together to store data in an interesting way.

The data to be searched for in the trie is now a roadmap.

- If you can follow the map from the beginning to the end, the data exists in the trie.
- If you can't, it doesn't.

Unlike with hash table, there are no collisions, and no two pieces of data (unless they are identical) have the same path.

Let's map key-value pairs where the keys are four-digit years (YYYY) and the values are names of universities founded during those years.

In a trie, the paths from a central **root** node to a **leaf** node (where the school names would be), would be labeled with digits of the year.

Each node on the path from root to leaf could have 10 pointers emanating from it, one for each digit.

To insert and element into the trie, simply build the correct parh from the root to the leaf.

```c
typedef struct _trie
{
    char university[20];
    struct _trie* paths[10];
}
trie;
```

To search for an element in the trie, use successive digits to navigate from the root, and if you can make it to the end without hitting a dead end (a `NULL` pointer), you've found it.