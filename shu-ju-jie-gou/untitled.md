# hashtable



![](../.gitbook/assets/image%20%2823%29.png)

![](../.gitbook/assets/image%20%2826%29.png)

```java
package com.heng.datastructure;

public class HashTableDemo {
    public static void main(String[] args) {
        HashTab ht = new HashTab(10);
        ht.add(new Emp(1, "Bob"));
        ht.add(new Emp(2, "Jay"));
        ht.add(new Emp(189, "Tom"));
        ht.add(new Emp(199, "Jerry"));
        ht.add(new Emp(31, "Q"));
        ht.add(new Emp(88, "TJ"));
        ht.add(new Emp(23, "Drew"));
        ht.print();
        System.out.println();
        System.out.println(ht.getById(88).getName());
    }
}
class HashTab{
    private EmpLinkedList[] empArray;
    private int size;
    public HashTab(int size) {
        this.size = size;
        empArray = new EmpLinkedList[size];
        for(int i = 0; i < size; i++){
            empArray[i] = new EmpLinkedList();
        }
    }
    public void add(Emp emp){
        int listNum = hashing(emp.getId());
        empArray[listNum].add(emp);
    }
    public void print(){
        for(int i = 0; i < size; i++){
            empArray[i].print( i + 1 );
        }
    }
    public Emp getById(int id){
        int listNum = hashing(id);
        return empArray[listNum].getEmp(id);
    }
    public int hashing (int id){
        return id % size;
    }
}
class Emp {
    private int id;
    private String name;
    public Emp next;
    public Emp(int id, String name) {
        this.id = id;
        this.name = name;
    }
    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }
}
class EmpLinkedList {
    private Emp head;
    public void add(Emp emp) {
        if(head == null) {
            head = emp;
            return;
        }
        Emp cur = head;
        while(cur.next != null) {
            cur = cur.next;
        }
        cur.next = emp;
    }
    public void print(int i){
        if(head == null){
            System.out.println("Number " + i + " list is Empty");
            return;
        }
        System.out.printf("Number %d list ", i);
        Emp cur = head;
        while(cur != null){
            System.out.printf(" => Current Employee's id is %d, name is %s", cur.getId(), cur.getName());
            cur = cur.next;
        }
        System.out.println();
    }
    public Emp getEmp(int id){
        Emp cur = head;
        while(cur != null){
            if(cur.getId() == id){
                return cur;
            }
        }
        return null;
    }
}
```

