# Hash Table Project


### Objective

In this project, our objective is to understand how to use Hashing with Open Addressing technique.

### Problem


Create a `delete` method to remove a `key` from the hash table.

### Implementation

* Calculate the initial index for the key using the hash function (to determine the initial slot where the key might be stored).
* Use a while loop to search for the key in the table, the loop should continue as long as the value at `table[index]` is not 0 (indicating an empty slot).
* Within the loop, check if the value at `table[index]` is equal to the key being deleted. If there is a match, proceed to remove the key from the table.
* To delete the key, assign the value -1 to `table[index]`. This acts as a deleted flag.
* Decrement the size by 1 to reflect the removal of an element.
* Return true to indicate a successful deletion.
* If the loop completes without finding a match the value at table[index] is 0), return false to indicate an unsuccessful deletion.


```java

public class OpenAddressingHashTable {
    private int[] table;
    private int capacity;
    private int size;

    public OpenAddressingHashTable(int capacity) {
        this.capacity = capacity;
        this.table = new int[capacity];
        this.size = 0;
    }

    public boolean insert(int key) {
        if (size == capacity)
            return false;

        int index = hash(key);

        while (table[index] != 0 && table[index] != -1) {
            index = (index + 1) % capacity;
        }

        table[index] = key;
        size++;
        return true;
    }

    public boolean search(int key) {
        int index = hash(key);

        while (table[index] != 0) {
            if (table[index] == key)
                return true;

            index = (index + 1) % capacity;
        }

        return false;
    }

    public boolean delete(int key) {

         /* write your code here */
    }

    private int hash(int key) {
        return key % capacity;
    }

    public static void main(String[] args) {

        OpenAddressingHashTable hashTable = new OpenAddressingHashTable(10);

        hashTable.insert(5);
        hashTable.insert(15);
        hashTable.insert(25);
        hashTable.insert(35);

        System.out.println("Search 15: " + hashTable.search(15));

        System.out.println("Search 20: " + hashTable.search(20));
    }
}
```
