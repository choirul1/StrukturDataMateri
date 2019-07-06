# Linked List

### A. Definisi 

Linked List adalah suatu struktur data linier. Berbeda dengan array yang juga merupakan struktur data linier dan tipe data komposit, linked list dibentuk secara dinamik. Pada saat awal program dijalankan elemen linked list belum data. Elemen linked list (disebut node) dibentuk sambil jalan sesuai instruksi. Apabila setiap elemen array dapat diakses secara langsung dengan menggunakan indeks, sebuah node linked list diakses dengan menggunakan pointer yang mengacu (menunjuk) ke node tersebut.

#### Node

Untuk membuat struktur data linked list, terlebih dahulu dibuat **node-node** penyusun linked list tersebut. **Node** ini harus memiliki setidaknya dua informasi, yaitu informasi mengenai data atau nilai, dan informasi mengenai node berikutnya. Oleh karena itu **node** dibuat menjadi sebuah tipe data baru yang bertipe **class**, dengan dua informasi yaitu *data* dan *next*.

Terdapat beberapa method penting pada class **node** ini, antara lain:

- **constructor**, yang akan dijalankan setiap instansiasi class
- **getData**, untuk mengetahui informasi data yang terdapat pada node tersebut
- **getNext**, untuk mengetahui informasi node berikutnya, jika tidak ada node berikutnya maka nilai balik berupa *None*
- **setData**, untuk merubah informasi data yang terdapat pada node tersebut
- **setNext**, untuk menentukan node berikutnya yang ditunjukan oleh informasi *next* dari node tersebut

Contoh :

Berikut adalah pembuatan class Node yang merupakan representasi dari sebuah node. *Property* atau *state* yang terdapat pada class Node ini :

1. data : berisi nilai dari node
2. next : berisi informasi berikutnya yang ditunjuk oleh node. Proses intansiasi, property next ini diset `None` yang merupakan representasi Nil atau Ground, berarti tidak ada node yang ditunjuk oleh node ini

```python
class Node:
    def __init__(self, init_data):
        self.data = init_data
        self.next = None
    def getData(self):
        return self.data
    def getNext(self):
        return self.next
    def setData(self, newdata):
        self.data = newdata
    def setNext(self, new_next):
        self.next = new_next
a=Node(11)
b=Node(110)
print(a.getNext())
print(b.getNext())
a.setNext(b)
print(a.getNext())
```

Di dalam Contoh diatas, terdapat obyek a dan obyek b dimana obyek tersebut memiliki tipe data class node. pada saat inisialisasi, kedua obyek bernilai 11 dan 110   , serta property next bernilai **None**. Pada baris ke-17, terdapat perintah `a.setNext(b)`, yang berarti property `next` dari obyek `a` akan menunjuk ke obyek `b`. Sehingga ketika dilakukan perintah `print(a.getNext())` akan menunjukkan ke suatu class Node.

### Link List

merupakan kumpulan dari node-node yang terhubung satu sama lain. Untuk mengakses node-node yang terdapat pada linked list.

Contoh :

Berikut adalah class untuk linked list, dimana pada class tersebut terdapat pointer yang menunjukkan node pertama dari suatu linked list (*head*). Terdapat dua buah method utama pada class LinkedList ini, antara lain:

1. *constructor*, `__init__`, yang merupakan method yang dijalankan pada saat pembuatan obyek. Karena obyek baru pertama kali dibuat, maka linked list masih kosong, sehingga pointer *head* masih bernilai *None*.
2. Method `isEmpty`, untuk pengecekan apakah linked list memiliki node ataukah tidak. Jika pointer *head* masih menunjuk pada *None*, maka linked list masih tidak memiliki node, sehingga return value adalah True.

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
 mylist=LinkedList()
print(mylist.head)
mylist.isEmpty()
```

### Penambahan Data Pada Link list

Penambahan data baru diletakkan pada awal link list yang terdapat pada pointer head.

Algoritma :

- Tautkan node baru ini ke node awal dari linked list

- modifikasi head dari linked list agar menunjuk pada node baru

  ![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\addList1.png)

Urutan tahapan ini **tidak boleh dibalik**, karena jika dibalik maka linked list yang awal tidak lagi dapat ditemukan.

Contoh :

Penambahan method add() pada link list.

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
mylist=LinkedList()
print(mylist.head)
mylist.isEmpty()
mylist.add(34)
print(mylist.head)
mylist.add(45)
print(mylist.head)
print(mylist.head.data)
mylist.add(21)
```

```python
Setelah dilakukan penambahan node terakhir diatas, output mylist berisi =[21, 45, 34]
```

### Transversal Link List

Cara mengetahui ukuran dari list, diperlukan tahapan **traverse**, yaitu menelusuri setiap node yang terdapat pada linked list.

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\pic007.jpg)

Pada proses penelusuran atau *traversal* dibutuhkan pointer bantuan. Pointer bantuan yang ditunjukkan pada Gambar diatas, adalah pointer curent yang bergerak dari node awal sampai dengan node akhir. 
Proses traversal ini dibutuhkan untuk beberapa hal, seperti untuk menghitung jumlah node yang terdapat pada Linked List, untuk mencari node pada linked list, untuk menampilkan seluruh node dari linked list, untuk menyisipkan node setelah atau sebelum node yang sudah terdapat pada linked list, dan untuk menghapus suatu node.

Contoh :

Implementasi yang akan dibuat adalah pembuatan method size(), untuk menghitung jumlah node.

Algoritma :

1. pointer bantuan curent berada pada node yang ditunjuk oleh head (yaitu node pertama)
2. pointer curent bergerak, dengan perintah `curent=curent.getNext()`, sekaligus dilakukan increment variabel count, yang merepresentasikan jumlah node
3. pergerakan atau traversal ini akan berakhir ketika pointer curent menunjuk pada None, yang merepresentasikan, tidak ada lagi node yang terdapat pada Linked list

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
    def size(self):
        curent = self.head
        count = 0
        while curent != None:
            count = count + 1
            
            curent = curent.getNext()           
        return count
 mylist=LinkedList()
mylist.add(45)
mylist.add(34)
mylist.add(70)
print(mylist.size())
```

### Pencarian Node pada Link List

Untuk pencarian node di dalam linked list juga perlu dilakukan *traverse*linked list seperti sebelumnya, hanya saja setiap berada pada suatu node, maka dilakukan pencocokan apakah node tersebut adalah node yang dicari

Contoh :

penambahan method `search()` pada class LinkedList. Method `search()` ini hampir sama dengan method `size`, hanya saja jika ditambahkan apakah node yang ditunjukkan oleh pointer curent adalah node yang dicari, dengan perintah:

```python
if curent.getData() == item: #dimana item adalah node yang dicari
```

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
    def size(self):
        curent = self.head
        count = 0
        while curent != None:
            count = count + 1
            curent = curent.getNext()
        return count
    def search(self,item):
        curent = self.head
        found = False
        while curent != None and not found:
            if curent.getData() == item:
                found = True
            else:
                curent = curent.getNext()
        return found
 mylist=LinkedList()
 mylist.add(45)
 mylist.add(34)
 mylist.add(70)
 mylist.add(84)
 mylist.size()
 mylist.search(34)
```

### Display data pada link list

Proses traversal juga dapat digunakan untuk menampilkan data pada seluruh node yang terdapat pada Linked List.

Contoh :

Berikut method `display()` untuk menampilkan data dari seluruh node pada linked list.

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
    def size(self):
        curent = self.head
        count = 0
        while curent != None:
            count = count + 1
            curent = curent.getNext()
        return count
    def search(self,item):
        curent = self.head
        found = False
        while curent != None and not found:
            if curent.getData() == item:
                found = True
            else:
                curent = curent.getNext()
        return found
    def display(self):
        curent = self.head
        while curent != None:
            print(curent.getData())
            curent = curent.getNext()
mylist=LinkedList()
mylist.add(45)
mylist.add(34)
mylist.add(70)
mylist.add(84)
mylist.display()
```

### Remove data pada link list

Jika data yang dihapus berada di node awal dari linked list (yang ditunjukkan dengan nilai previous masih *None*, maka yang dilakukan pointer *head* langsung menunjuk pada node setelah node yang akan dihapus tersebut,

Contoh :

Berikut adalah penambahan method `remove()` untuk menghapus node yang diinginkan pada linked list.

```python
class LinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
    def size(self):
        curent = self.head
        count = 0
        while curent != None:
            count = count + 1
            curent = curent.getNext()
        return count
    def search(self,item):
        curent = self.head
        found = False
        while curent != None and not found:
            if curent.getData() == item:
                found = True
            else:
                curent = curent.getNext()
        return found
    def display(self):
        curent = self.head
        while curent != None:
            print(curent.getData())
            curent = curent.getNext()
    def remove(self, item):
        curent = self.head
        previous = None
        found = False
        while not found:
            if curent.getData() == item:
                found = True
            else:
                previous = curent
                curent = curent.getNext()
        if previous == None:
            self.head = curent.getNext()
        else:
            previous.setNext(curent.getNext())
mylist=LinkedList()
mylist.add(1)
mylist.add(3)
mylist.add(9)
mylist.add(12)
mylist.add(23)
mylist.display()
mylist.remove(3)
mylist.display()
```

### Ordered List

Proses pencarian pada linked list sebelumnya dilakukan dengan cara mencari node satu persatu sampai node terakhir. Proses pencarian ini akan menjadi lebih cepat jika data sudah dalam keadaan terurut, sehingga pencarian dapat dihentikan ketika ditemukan node dengan data lebih rendah atau lebih tinggi. Class Ordered List akan memudahkan pencarian suatu node, karena data yang terdapat pada class ini sudah dalam keadaan terurut.

Method yang terdapat pada ordered list, sama halnya dengan class linkedlist, hanya saja terdapat perbedaan pada method untuk **add data**(karena node yang terbentuk harus dalam keadaan terurut), dan method search data.

Contoh :

Berikut method untuk class ordered list :

```python
class OrderedLinkedList:
    def __init__(self):
        self.head = None
    def isEmpty(self):
        return self.head==None
    
    def size(self):
        curent = self.head
        count = 0
        while curent != None:
            count = count + 1
            curent = curent.getNext()
        return count
    
    def display(self):
        curent = self.head
        while curent != None:
            print(curent.getData())
            curent = curent.getNext()
    def remove(self, item):
        curent = self.head
        previous = None
        found = False
        while not found:
            if curent.getData() == item:
                found = True
            else:
                previous = curent
                curent = curent.getNext()
        if previous == None:
            self.head = curent.getNext()
        else:
            previous.setNext(curent.getNext())       
    def search(self,item):
        curent = self.head
        found = False
        stop=False
        while curent != None and not found and not stop:
            if curent.getData() == item:
                found = True
            else:
                if curent.getData() > item:
                    stop = True
                else:
                    curent = curent.getNext()
        return found
    def add(self, item):
        curent=self.head
        previous = None
        stop = False
        while curent != None and not stop:
            if curent.getData() > item:
                stop = True
            else:
                previous = curent
                curent = curent.getNext()
        
        temp = Node(item)
        if previous == None:
            temp.setNext(self.head)
            self.head = temp
        else: # ditautkan antara previous dengan curent
            temp.setNext(curent)
            previous.setNext(temp)
myList=OrderedLinkedList()
myList.add(9)
myList.add(14)
myList.display()
myList.add(100)
myList.display()
```

### Latihan Praktikum

1.

```python
#Ach. Choirul Umam
#160411100075
class Node:
    def __init__(self, init_data):
        self.data = init_data
        self.next = None
    def getData(self):
        return self.data
    def getNext(self):
        return self.next
    def setData(self, newdata):
        self.data = newdata
    def setNext(self, new_next):
        self.next = new_next
class LinkedList:
    def __init__(self):
        self.head=None
    def isEmpty(self):
        return self.head==None
    def size(self):
        current = self.head
        count = 0
        while current != None:
            count+=1
            current=current.getNext()
        return count
    def addRear(self,item):
        temp=Node(item)
        if self.isEmpty()==True:
            self.head=temp
        else:
            current=self.head
            previous=None
            while current != None:
                previous=current
                current=current.getNext()
            previous.setNext(temp)
    def __str__(self):
        data="["
        current=self.head
        while current!=None:
            data+=str(current.data)
            current=current.getNext()
            if current!=None:
                data+=","
        data+="]"
        return(data)
    def insertPrevious(self,obj,item):
        temp=Node(item)
        current=self.head
        previous=None
        stop=False
        while current!=None and not stop:
            if current.getData()==obj:
                stop=True
            else:
                previous=current
                current=current.getNext()
        if stop==True:
            temp.setNext(current)
            previous.setNext(temp)
    def insertNext(self,obj,item):
        temp=Node(item)
        current=self.head
        previous=current
        stop=False
        while current!=None and not stop:
            if previous.getData()==obj:
                stop=True
            else:
                previous=current
                current=current.getNext()
        if stop==True:
            temp.setNext(current)
            previous.setNext(temp)
myList1=LinkedList()
myList1.addRear(5)
myList1.addRear(84)
myList1.addRear(12)
myList1.addRear(77)
print (myList1)
myList1.insertPrevious(84,100)
print(myList1)
myList1.insertNext(12,122)
print(myList1)

class Sorting:
    def __init__(self,a):
        self.Data=a
    def bubbleSort(self,pilihan):
        t1=time.time()/10000000000
        #print('Data yang akan diurutkan : ', self.Data)
        if pilihan=="a":
            for outIter in range(len(self.Data)-1,-1,-1):
                for i in range(outIter):
                    if self.Data[i]>self.Data[i+1]:
                        self.Data[i],self.Data[i+1]=self.Data[i+1],self.Data[i]
        elif pilihan=="d":
            for outIter in range(len(self.Data)-1,-1,-1):
                for i in range(outIter):
                    if self.Data[i]<self.Data[i+1]:
                        self.Data[i],self.Data[i+1]=self.Data[i+1],self.Data[i]
        return t1
    def selectionSort(self,pilihan):
        t1=time.time()/10000000000
        for outIter in range(len(self.Data)-1):       
            minIndex=outIter
            if pilihan=="a":
                for i in range(outIter+1,len(self.Data)):
                    if self.Data[i]<self.Data[minIndex]:
                        minIndex=i
                self.Data[outIter],self.Data[minIndex]=self.Data[minIndex],self.Data[outIter]
            if pilihan=="d":
                for i in range(outIter+1,len(self.Data)):
                    if self.Data[i]>self.Data[minIndex]:
                        minIndex=i
                self.Data[outIter],self.Data[minIndex]=self.Data[minIndex],self.Data[outIter]
        return t1
    def insertionSort(self,pilihan):
        t1=time.time()/10000000000
        for outIter in range(1,len(self.Data)):
            key=self.Data[outIter]
            ind=outIter
            if pilihan=="a":
                while (ind>0 and self.Data[ind-1]>key):
                    self.Data[ind]=self.Data[ind-1]
                    ind=ind-1
                self.Data[ind]=key
            if pilihan=="d":
                while (ind>0 and self.Data[ind-1]<key):
                    self.Data[ind]=self.Data[ind-1]
                    ind=ind-1
                self.Data[ind]=key
        return t1
import time
t1=time.time()
import random
a=randm.sample(range(0, 1000),500)
dataSort=Sorting(a)
t1=dataSort.bubbleSort("a")
print(dataSort.Data)
print('waktu komputasi',t1,'detik')

```