```java
import java.util.LinkedList;

public class MyHashSet {
    // Array of linked lists to handle collisions
    private LinkedList<Integer>[] buckets;
    private int bucketSize;

    // Constructor to initialize the hash set with a fixed size
    public MyHashSet() {
        bucketSize = 1000; // default bucket size
        buckets = new LinkedList[bucketSize];
        for (int i = 0; i < bucketSize; i++) {
            buckets[i] = new LinkedList<>();
        }
    }

    // Hash function to map a key to a bucket index
    private int hashFunction(int key) {
        return key % bucketSize;
    }

    // Add a key to the hash set
    public void add(int key) {
        int bucketIndex = hashFunction(key);
        LinkedList<Integer> bucket = buckets[bucketIndex];
        if (!bucket.contains(key)) {
            bucket.add(key);
        }
    }

    // Remove a key from the hash set
    public void remove(int key) {
        int bucketIndex = hashFunction(key);
        LinkedList<Integer> bucket = buckets[bucketIndex];
        bucket.remove(Integer.valueOf(key));
    }

    // Check if the hash set contains a key
    public boolean contains(int key) {
        int bucketIndex = hashFunction(key);
        LinkedList<Integer> bucket = buckets[bucketIndex];
        return bucket.contains(key);
    }

    // Main method to test the hash set
    public static void main(String[] args) {
        MyHashSet hashSet = new MyHashSet();
        hashSet.add(1);
        hashSet.add(2);
        System.out.println(hashSet.contains(1)); // true
        System.out.println(hashSet.contains(3)); // false
        hashSet.add(2);
        System.out.println(hashSet.contains(2)); // true
        hashSet.remove(2);
        System.out.println(hashSet.contains(2)); // false
    }
}

```

```java
import java.util.LinkedList;

public class MyHashMap {

    // Node class to represent each key-value pair in the HashMap
    private class Node {
        int key;
        int value;

        Node(int key, int value) {
            this.key = key;
            this.value = value;
        }
    }

    // Array of linked lists to handle collisions
    private LinkedList<Node>[] buckets;
    private int bucketSize;

    // Constructor to initialize the hash map with a fixed size
    public MyHashMap() {
        bucketSize = 1000; // default bucket size
        buckets = new LinkedList[bucketSize];
        for (int i = 0; i < bucketSize; i++) {
            buckets[i] = new LinkedList<>();
        }
    }

    // Hash function to map a key to a bucket index
    private int hashFunction(int key) {
        return key % bucketSize;
    }

    // Put a key-value pair into the hash map
    public void put(int key, int value) {
        int bucketIndex = hashFunction(key);
        LinkedList<Node> bucket = buckets[bucketIndex];
        
        for (Node node : bucket) {
            if (node.key == key) {
                node.value = value; // Update the value if the key already exists
                return;
            }
        }
        
        bucket.add(new Node(key, value)); // Add a new key-value pair if the key doesn't exist
    }

    // Get the value for a key from the hash map
    public int get(int key) {
        int bucketIndex = hashFunction(key);
        LinkedList<Node> bucket = buckets[bucketIndex];
        
        for (Node node : bucket) {
            if (node.key == key) {
                return node.value; // Return the value if the key is found
            }
        }
        
        return -1; // Return -1 if the key is not found
    }

    // Remove a key-value pair from the hash map
    public void remove(int key) {
        int bucketIndex = hashFunction(key);
        LinkedList<Node> bucket = buckets[bucketIndex];
        
        Node toRemove = null;
        for (Node node : bucket) {
            if (node.key == key) {
                toRemove = node;
                break;
            }
        }

        if (toRemove != null) {
            bucket.remove(toRemove); // Remove the key-value pair if the key is found
        }
    }

    // Main method to test the hash map
    public static void main(String[] args) {
        MyHashMap hashMap = new MyHashMap();
        hashMap.put(1, 1);
        hashMap.put(2, 2);
        System.out.println(hashMap.get(1)); // Output: 1
        System.out.println(hashMap.get(3)); // Output: -1
        hashMap.put(2, 1); 
        System.out.println(hashMap.get(2)); // Output: 1
        hashMap.remove(2); 
        System.out.println(hashMap.get(2)); // Output: -1
    }
}

```
