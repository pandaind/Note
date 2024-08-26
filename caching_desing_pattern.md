### Plan
1. Create a `Cache` interface with methods for adding, retrieving, and removing items.
2. Implement a `SimpleCache` class that uses a `HashMap` to store cache items.
3. Demonstrate the usage of the `SimpleCache` in the `Main` class.

### Cache Interface
```java
public interface Cache<K, V> {
    void put(K key, V value);
    V get(K key);
    void remove(K key);
}
```

### SimpleCache Implementation
```java
import java.util.HashMap;
import java.util.Map;

public class SimpleCache<K, V> implements Cache<K, V> {
    private final Map<K, V> cache;

    public SimpleCache() {
        this.cache = new HashMap<>();
    }

    @Override
    public void put(K key, V value) {
        cache.put(key, value);
    }

    @Override
    public V get(K key) {
        return cache.get(key);
    }

    @Override
    public void remove(K key) {
        cache.remove(key);
    }
}
```

### Main Class Usage
```java
public class Main {
    public static void main(String[] args) {
        Cache<String, String> cache = new SimpleCache<>();
        cache.put("key1", "value1");
        System.out.println("Retrieved: " + cache.get("key1"));
        cache.remove("key1");
        System.out.println("Retrieved after removal: " + cache.get("key1"));
    }
}
```
