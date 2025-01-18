# Hash Table Data Structure in JavaScript 🚀  

A simple implementation of the **Hash Table** data structure in JavaScript. This repository demonstrates how to create a hash table class with essential methods and explains its functionality with practical examples.  

---

## What is a Hash Table?  
A **Hash Table** (or Hash Map) is a data structure that stores key-value pairs. It uses a hash function to compute an index (hash) into an array of buckets or slots, from which the desired value can be found. Hash tables provide fast access to data and are widely used for implementing associative arrays or database indexing.  

---

## Features  
- **Insert**: Add a key-value pair to the hash table.  
- **Delete**: Remove a key-value pair from the hash table.  
- **Search**: Find a value by its key.  
- **Size**: Get the number of key-value pairs in the table.  

---

## Code Implementation  

Here’s the JavaScript implementation of the hash table:  

```javascript
class HashTable {
    constructor(size = 50) {
        this.table = new Array(size); // Initialize the hash table with a given size
    }

    // Hash function to calculate the index
    hash(key) {
        let hash = 0;
        for (let i = 0; i < key.length; i++) {
            hash = (hash << 5) + hash + key.charCodeAt(i); // Hashing algorithm
        }
        return hash % this.table.length; // Return the index within table size
    }

    // Insert a key-value pair into the hash table
    insert(key, value) {
        const index = this.hash(key);
        if (!this.table[index]) {
            this.table[index] = [];
        }
        this.table[index].push([key, value]); // Handle collisions by chaining
    }

    // Delete a key-value pair from the hash table
    delete(key) {
        const index = this.hash(key);
        if (this.table[index]) {
            this.table[index] = this.table[index].filter(([k, v]) => k !== key);
        }
    }

    // Search for a value by its key
    search(key) {
        const index = this.hash(key);
        if (this.table[index]) {
            for (let [k, v] of this.table[index]) {
                if (k === key) {
                    return v;
                }
            }
        }
        return null; // Return null if key is not found
    }

    // Get the size of the hash table
    size() {
        let count = 0;
        for (let bucket of this.table) {
            if (bucket) {
                count += bucket.length;
            }
        }
        return count;
    }
}
```

---

## Example Usage  

```javascript
// Initialize the hash table
const hashTable = new HashTable();

// Insert key-value pairs
hashTable.insert("name", "John");
hashTable.insert("age", 30);
hashTable.insert("city", "New York");

// Search for a value by its key
console.log(hashTable.search("name")); // Output: John
console.log(hashTable.search("age")); // Output: 30

// Delete a key-value pair
hashTable.delete("age");
console.log(hashTable.search("age")); // Output: null

// Get the size of the hash table
console.log(hashTable.size()); // Output: 2
```

---

## Real-World Applications  
1. **Database Indexing**: Used in databases to quickly find records.  
2. **Caching**: Storing computed results for faster access.  
3. **Implementing Sets**: Storing unique elements without duplicates.  
4. **Associative Arrays**: Used in languages like JavaScript and Python to map keys to values.  

---

## TikTok Tutorial 🎥  
Want to see a quick tutorial on how to build this? Check out this TikTok video:  
[]()  

---

## How to Run the Code  
1. Clone the repository:  
   ```bash
   git clone https://github.com/your-username/hash-table-data-structure.git
   cd hash-table-data-structure
   ```
2. Open the file `hash-table.js` in your favorite code editor.  
3. Run the file using Node.js:  
   ```bash
   node hash-table.js
   ```

---

## Contributing  
Contributions are welcome! If you have suggestions or want to add new features, feel free to create a pull request.  

---

## License  
This project is licensed under the MIT License.  

---

## Connect with Me:
- [LinkedIn - Vitalii Semianchuk](https://www.linkedin.com/in/vitalii-semianchuk-9812a786/)
- [Telegram - @jsmentorfree](https://t.me/jsmentorfree) - We do a lot of free teaching on this channel! Join us to learn and grow in web development.
- [Tiktok - @jsmentoring](https://www.tiktok.com/@jsmentoring) Everyday new videos
- [Youtube - @jsmentor-uk](https://www.youtube.com/@jsmentor-uk) Mentor live streams
- [Dev.to - fix2015](https://dev.to/fix2015) Javascript featured, live, experience but about Hash Table
