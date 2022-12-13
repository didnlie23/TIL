# ArrayList 정렬 vs LinkedList 정렬

[Does a linkedList takes longer to be sorted?](https://stackoverflow.com/questions/65151287/does-a-linkedlist-takes-longer-to-be-sorted)

## 결론

두 자료구조 toArray 함수에 의해 배열로 변경된 후 동일한 로직으로 정렬되기 때문에 시간 복잡도 면에서 큰 차이는 없다.

```java
default void sort(Comparator<? super E> c) {
	      Object[] a = this.toArray();
        Arrays.sort(a, (Comparator) c);
        ListIterator<E> i = this.listIterator();
        for (Object e : a) {
            i.next();
            i.set((E) e);
        }
}
```

하지만 toArray 함수에 의해 배열로 변경되는 과정에 당연한 차이가 있다.

### LinkedList

```java
public Object[] toArray() {
        Object[] result = new Object[size];
        int i = 0;
        for (Node<E> x = first; x != null; x = x.next)
            result[i++] = x.item;
        return result;
}
```

### ArrayList

```java
public Object[] toArray() {
        return Arrays.copyOf(elementData, size);
}
```

연속된 메모리에 값들이 저장되는 ArrayList와 다르게 LinkedList는 메모리에 불연속적으로 값들이 저장되어 있기 때문에, 단순히 전체 리스트를 순회하는 과정에서도 속도 차이가 발생할 수 밖에 없다.
