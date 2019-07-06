# Classes

### A. Definisi

class merupakan sebuah objek yang di dalam nya biasanya terdapat beberapa metode yang memang merupakan isi dari sebuah class ini. Class dan metode ini biasa di sebut sebagai (PBO) atau Pemrograman Berorientasi Obyek. Dan (PBO) ini memang fungsinya untuk memudahkan proses atau kegiatan programing. 

Berikut beberapa hal yang harus diketahui untuk pengenalan Pemrograman Berorientasi Obyek (PBO).

```php+HTML
1. String dan List
2. Istilah dalam PBO
3. Constructur
4. Method
5. Overide Method
```

1. ### String dan List

Merupakan tipe data class yang sudah diketahui dan diginakan sebelumnya, adalah tipe data lists ataupun string. Suatu variabel yang berbentuk *lists* ataupun *string*, memiliki dua buah elemen yang terkandung di dalam variabel tersebut, yaitu nilai atau yang disebut dengan *state*/*property*, serta *method* atau fungsi, yang dapat digunakan untuk mengolah nilai pada variabel tersebut. 
Method atau fungsi yang melekat pada suatu variabel dapat diakses dengan menggunakan syntax.

```python
namaObyek.NamaMethod()
```

Contoh :

Berikut adalah contoh tipe data string dan lists, yang memiliki nilai sekaligus method.

```python
# String
dataStr='Choirul' 
print(dataStr)
dataStr=dataStr.upper()
print(dataStr)
```

Pada Contoh diatas terdapat variabel dataStr, berbentuk string. dimana property dari dataStr adalah 'Choirul', Contoh method yang digunakan adalah method upper()*u**p**p**e**r*(), yang berfungsi untuk merubah semua karakter pada dataStr*d**a**t**a**S**t**r* menjadi huruf kapital. Beberapa contoh method lain yang dapat digunakan adalah capitalize()*c**a**p**i**t**a**l**i**z**e*(), lower()*l**o**w**e**r*(), find()*f**i**n**d*(), dll

```python
# Lists
dataLs=[12, 13, 14]
print(dataLs)
data.append(45)
print(dataLs)
```

Pada contoh code diatas, terdapat variabel dataLs*d**a**t**a**L**s* yang berbentuk *lists*. Variabel ini memiliki tiga buah nilai, yaitu 12, 113, dan 14. Contoh method yang digunakan adalah append()*a**p**p**e**n**d*(), yaitu menambah data pada variabel berbentuk *lists*. Contoh method method lain yang dimiliki tipe data lists yang bisa dimanfaatkan, misalkan pop()*p**o**p*(), insert()*i**n**s**e**r**t*(), clear()*c**l**e**a**r*(), reverse()*r**e**v**e**r**s**e*(), dsb.

2. ### Istilah Dalam PBO

Kelebihan dari bahasa pemrogaraman berbasis object, adalah bahasa tersebut menyediakan beberapa fitur agar *programmer* dapat membuat *class* sendiri yang sesuai dengan kebutuhan. Beberapa istilah dasar yang terdapat pada pemrograman berbasis object ini antara lain :

- *class*, tipe data yang tidak hanya berisi data tetapi juga method
- *object*, suatu variabel dengan tipe data *class*
- *state, property*, bagian data dari suatu class yang berisi nilai, dapat berupa string, integer, float
- *method*, fungsi yang melekat pada class
- *constructor*, fungsi yang dijalankan oleh python ketika pertama kali suatu objek dibuat. Method constructor ini dibuat dengan cara mendefinisikan fungsi _ *init* _ (dua *underscore*)
- *self*, merupakan suatu argumen atau parameter spesial agar nilai balik dari method dikembalikan ke objek itu sendiri. Argumen ini tidak perlu dipanggil (walaupun sudah didefinisikan)pada saat pemanggilan method
- *instance*, suatu objek yang telah dibuat
- *override*, mendefinisikan kembali fungsi-fungsi umum yang sudah ada, agar sesuai dengan kebutuhan *programmer*

3. ### Constructor

Syntax untuk membuat suatu class, adalah sebagai berikut :

```python
class namaClass:
    def _init_() : #constructor
    def namaMethod () : #Method
```

Sedangkan untuk membuat suatu obyek dengan tipe data class tertentu (proses pembuatan *instance*) adalah :

```python
namaObyek=namaClass()
```

**Constructor** merupakan method yang otomatis dijalankan ketika suatu obyek dibuat. Syntax untuk pembuatan *constructor* ini adalah :

```python
def __init__()
```

Contoh :

```python
class BilanganKompleks:
    def __init__(self,a,b):
        self.real=a
        self.im=b
        
data=BilanganKompleks(4,6)
print(data)
```

untuk menampilkan property atau nilai yang dimiliki oleh suatu obyek, tidak dapat dilakukan dengan syntax `print()` seperti biasa.

Terdapat dua cara agar objek yang sudah dibuat dapat ditampilkan di layar sesuai dengan yang diinginkan, yaitu:

- Membuat method baru untuk menampilkan data
- *override* method standar dari sebuah class

4. ### Method

Method merupakan fungsi-fungsi yang terdapat di dalam suatu class. Contoh method yang akan dibuat adalah method yang berfungsi untuk menampilkan *property* atau *state* yang terdapat di dalam suatu obyek. 
Syntax pembuatan method adalah :

```python
def namaMethod():
```

Sedangkan untuk memanggil method suatu class adalah : 

```python
namaObyek.namaMethod()
```

Contoh :

Berikut adalah contoh pembuatan method `display()` yang berfungsi untuk menampilkan *property* yang terdapat pada class Bilangan Kompleks.

```python
class BilanganKompleks:
    def __init__(self,a,b): # constructor
        self.real=a
        self.im=b
    def display(self): # method untuk menampilkan state
        print (self.real,'+',self.im,'i')
data1=BilanganKompleks(4,6)
data1.display()
data2=BilanganKompleks(2,3)
data2.display()
```

Pada contoh code diatas, terdapat method tambahan pada class BilanganKompleks*B**i**l**a**n**g**a**n**K**o**m**p**l**e**k**s*, yaitu method `display()`, yang berfungsi untuk menampilkan *state* atau *property* obyek dari class BilanganKompleks*B**i**l**a**n**g**a**n**K**o**m**p**l**e**k**s*. 
Di dalam method tersebut, digunakan syntax print yang berfungsi untuk menampilkan suatu data. Perintah `self.real` adalah perintah untuk mengakses *state* atau *property* real*r**e**a**l*, yang dimiliki oleh class BilanganKompleks*B**i**l**a**n**g**a**n**K**o**m**p**l**e**k**s*, begitu juga dengan perintah `self.im`, digunakan untuk mengakses *property* im*i**m*. Karena property real*r**e**a**l* dan im*i**m* bertipe data integer, maka syntax `print()` dapat dilakukan pada dua *property* tersebut

### 5. Override Method

**Override Method** merupakan penambahan fungsi-fungsi pada syntax-syntax yang sudah ada. Seperti yang dijelaskan sebelumnya, untuk menampilkan *property* yang terdapat pada suatu obyek, tidak dapat dilakukan dengan menggunakan perintah `print()`. 
Cara pertama yang sudah dijelaskan adalah membuat method baru di dalam class, yang berfungsi untuk menampilkan *property* suatu class. 
Cara kedua adalah dengan cara override method fungsi yang sudah tersedia oleh bahasa pemrograman. Syntax yang akan di*override* adalah syntax `print()`. 
Yang perlu dilakukan agar suatu object dapat dipanggil dengan perintah *print* adalah object tersebut harus dirubah menjadi string. Untuk merubah suatu variabel menjadi string, maka suatu class dilengkapi dengan method `__str__`. Hanya saja method ini tidak bisa berfungsi secara sempurna sesuai dengan apa yang diinginkan oleh programmer, yaitu agar syntax `print` dapat digunakan langsung untuk menampilkan *property* yang terdapat pada suatu class.

Contoh Code :

Berikut contoh override method `__str__` pada class BilanganKompleks

```python
class BilanganKompleks:
    def __init__(self,a,b):
        self.real=a
        self.im=b
    def display(self):
        print (self.real,"+",self.im,"i")
    def __str__(self):
        return str(self.real)+" + "+str(self.im)+" i "
data1=BilanganKompleks(4,6)
data2=BilanganKompleks(2,5)
print('Override Method')
print(data1)
print(data2)
print('Method dalam Class')
data1.display()
data2.display()
```

```python
Output :
Override Method
4+6i
2+5i
Method dalam Class
4 + 6 i
2 + 5 i
```

Penjumlahan dua buah bilangan kompleks berbeda dengan penjumlahan bilangan yang lain, karena bilangan kompleks ini terdiri dari dua bagian yaitu real dan imajiner. Untuk menjumlahkan bilangan kompleks. maka bagian real harus dijumlahkan pada bagian real juga dari bilangan lain, dan bagian imajiner harus ditambahkan dengan bagian imajiner.

### B. Code

Contoh code berikut adalah pembuatan method baru di dalam class, yang berfungsi untuk menjumlahkan dua buah bilangan kompleks.

```python
class BilanganKompleks:
    def __init__(self,a,b):
        self.real=a
        self.im=b
    def display(self):
        print (self.real,'+',self.im,'i')
    def __str__(self):
        return str(self.real) + " + " + str(self.im) + " i "
    def addKompleks(self,obj):
        a=self.real+obj.real
        b=self.im+obj.im
        return BilanganKompleks(a,b)
data1=BilanganKompleks(4,6)
data2=BilanganKompleks(2,5)
jumlah=data1.addKompleks(data2)
data1.display()
data2.display()
print(jumlah)
```

```python
Output :
4 + 6 i
2 + 5 i
6 + 11 i 
```

Ketika ingin melakukan operasi penjumlahan dengan menggunakan operator '+', maka tidak dapat langsung dilakukan perintah sebagai berikut :

```python
data1=BilanganKompleks(4,6)
data2=BilanganKompleks(2,5)
jumlah=data1+data2
```

Operasi penjumlahan dengan operator '+' hanya dapat dilakukan dengan *override* fungsi `__add__` yang sudah tersedia.

**Latihan Praktikum**

1. . Buatlah class Matrix dengan beberapa method seperti berikut :
   a. Constructor : untuk inisialisasi matriks, dengan parameter berupa jumlah
   baris dan kolom suatu matrix, dan elemen matriks merupakan inputan dari user (di dalam
   constructor)
   b. Override method __str__ : untuk menampilkan matriks
   Gunakan formatting string jika diperlukan
   c. Override method __add__ : untuk menjumlahkan dua buah matriks
   Pada method ini, haruslah dilakukan pengecekan, jika ukuran dua buah matriks yang akan
   dijumlahkan tidak sama, maka akan mengeluarkan warning bahwa ukuran tidak sama
   d. Override method __mul__ : untuk mengalikan dua buah matriks
   Pada method ini, haruslah dilakukan pengecakan, jika jumlah kolom pada matriks pertama
   tidak sama dengan jumlah baris pada matriks kedua, maka akan mengeluarkan warning
   bahwa ukuran matriks tidak sesuai. 

```python
#Ach Choirul Umamm
#160411100075
#StrukdatD2
class matriks:
    #mat = {}
    def __init__(self, baris, kolom):
        self.b = []
        self.baris = baris
        self.kolom = kolom
        for line in range(self.baris):
            k = []
            for cols in range(self.kolom):
                k.append(0)
            self.b.append(k)
        inp = int(input("masukkan jumlah element : "))
        for i in range(inp):
            bar = int(input("baris ke? : "))
            kol = int(input("kolom ke? : "))
            element = int(input("baris [{}][{}] : ".format(bar,kol)))
            self.b[bar][kol] = element

    def __str__(self):
        data = ""
        for i in range(len(self.b)):
            data += "| "
            for t in range(len(self.b[0])):
                data += str(self.b[i][t])
            data += " |\n"
        return data

    def __add__(self, tambah):
        angka = "1234567890"
        mat1 = []
        kol1 = []
        hasil = []
        data = ""
        for t in range(len(tambah.b)):
            if str(tambah.b[t]) in angka:
                kol1.append(tambah.b[t])
            else:
                kol1 = []
                mat1.append(kol1)
        if len(self.b) == len(tambah.b):
            if len(tambah.b[0]) == len(self.b[0]):
                for u in range(len(self.b)):
                    data += "| "
                    kolo = []
                    for j in range(len(self.b[0])):
                        has = tambah.b[u][j] + self.b[u][j]
                        data += str(has)
                        kolo.append(has)
                    mat1.append(kolo)
                    data += " |\n"
                return "hasil Penjumlahan\n" + data
            else:
                return "penjumlahan tidak bisa dilakukan karena jumlah kolom tidak sama"
        else:
            return "penjumlahan tidak bisa dilakukan karena Jumlah baris tidak sama"

    def __mul__(self, kali):
        angka = "1234567890"
        data = ""
        mat1 = []
        kol1 = []
        for t in range(len(kali.b)):
            if str(kali.b[t]) in angka:
                kol1.append(kali.b[t])
            else:
                kol1 = []
                mat1.append(kol1)
        if len(self.b[0]) == len(kali.b):
            mat_bar = []
            for i in range(len(self.b)):
                data += "| "
                hasil = 0
                mat_kol = []
                for y in range(len(kali.b[0])):
                    for t in range(len(self.b[0])):
                        a = self.b[i][t]
                        b = kali.b[t][y]
                        perkalian = a*b
                        hasil = hasil + perkalian
                    data += str(hasil)
                    mat_kol.append(hasil)
                mat_bar.append(mat_kol)
                data += " |\n"
            return "hasil dari perkalian = \n" + data
        else:
            return "perkalian tidak bisa dilakukan karena jumlah kolom matrik1 tidak sama dengan jumlah kolom matrik2"
                        
            
obj1 = matriks(2,2)
print(obj1)
obj2 = matriks(2,2)
print(obj2)
jumlah = obj1.__add__(obj2)
print(jumlah)

kali = obj1.__mul__(obj2)
print(kali)
```

```python
Output :
    masukkan jumlah element : 2
baris ke? : 0
kolom ke? : 1
baris [0][1] : 2
baris ke? : 1
kolom ke? : 1
baris [1][1] : 2
| 02 |
| 02 |

masukkan jumlah element : 2
baris ke? : 0
kolom ke? : 1
baris [0][1] : 3
baris ke? : 1
kolom ke? : 0
baris [1][0] : 1
| 03 |
| 10 |

hasil Penjumlahan
| 05 |
| 12 |

hasil dari perkalian = 
| 22 |
| 22 |
```

2. Buatlah class LinkedList, dengan beberapa method tambahan pada class LinkedList seperti
   berikut (untuk constructor LinkedList, dan class Node dapat dilihat pada materi perkuliahan):
   a. addRear : untuk menambahkan node di belakang linkedlist
   b. override method __str__ : untuk menampilkan data linked list
   c. override method __add__ : untuk menambahkan data dari dua buah linked list,
   dengan ketentuan, jumlah node pada linked list hasil penjumlahan sama dengan jumlah
   node terbanyak dari linked list yang akan dijumlahkan. 

```python
#Ach. Choirul Umam
#160411100075
class Node:
    def __init__(self,init_data):
        self.data = init_data
        self.next = None
    def getData(self):
        return self.data
    def getNext(self):
        return self.next
    def setData(self,new_data):
        self.data = new_data
    def setNext(self,next_data):
        self.next = next_data


class LinkedList:
    def __init__(self):
        self.head = None
        
    def isEmpty(self):
        return self.head==None
    
    def addprev(self,item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
        
    def addnext(self,item):
        temp = Node(item)
        current=self.head
        while current.getNext()!=None:
            current=current.getNext()
        current.setNext(temp)
        
    def size(self):
        current = self.head
        count=0
        while current != None:
            count=count+1
            current=current.getNext()
        return count

    def search(self,item):
        current=self.head
        found=False
        while current != None and not found:
            if current.getData() == item:
                found=True
            else:
                current=current.getNext()
        return found
    
    def tampil(self):
        current=self.head
        print("head->",end=" ")
        while current:
            print(current.getData(),end="->")
            current=current.getNext()
        print("none")
        
    def remove(self,item):
        current=self.head
        found=False
        previous= None
        while not found:
            if current.getData()==item:
                found=True
            else:
                previous = current
                current = current.getNext()
        if previous == None:
            self.head=current.getNext()
        else:
            previous.setNext(current.getNext())
            
    def index(self, item):
        count = 0;current = self.head
        if item < 0: item = self.size()+item
        while current != None:
            if count==item: return current.getData()
            current = current.getNext()
            count += 1
        print('Index melebihi jumlah data')  
#========================================================
#===================  LINKED LIST  =========================
#========================================================
mylist=LinkedList()
mylist2=LinkedList()
mylist3=LinkedList()
#=======================================================
list1="y"
c=input("masukkan angka list ke-1:")
mylist.addprev(c)
while list1=="y":
    a=input("masukkan angka list ke-1:")
    mylist.addnext(a)
    list1=input("tekan y jika lagi dan tekan t jika tidak:")

#=====================================================
list2="y"
d=input("masukkan angka list ke-2:")
mylist2.addprev(d)
while list2=="y":
    b=input("masukkan angka list ke-2:")
    mylist2.addnext(b)
    list2=input("tekan y jika lagi dan tekan t jika tidak:")
#====================================================
print("\n==============================")
mylist.tampil()
mylist2.tampil()
print("==============================")
print("Hasil Dari Penjumlahan nya adalah :")

#====================================================
if mylist.size()>mylist2.size():
    ha=mylist.size()-mylist2.size()
    for i in range(ha):
        mylist2.addnext(0)
    
    
elif mylist.size()<mylist2.size():
    ha=mylist2.size()-mylist.size()
    for i in range(ha):
        mylist.addnext(0)
#====================================================       
tambahawal=int(mylist.index(0))+int(mylist2.index(0))
mylist3.addprev(tambahawal)
for i in range(1,mylist.size()):
    tambah=int(mylist.index(i))+int(mylist2.index(i))
    mylist3.addnext(tambah)
mylist3.tampil()
print("==============================")    


```

```python
Output :
    masukkan angka list ke-1:1
masukkan angka list ke-1:1
tekan y jika lagi dan tekan t jika tidak:y
masukkan angka list ke-1:3
tekan y jika lagi dan tekan t jika tidak:y
masukkan angka list ke-1:3
tekan y jika lagi dan tekan t jika tidak:t
masukkan angka list ke-2:1
masukkan angka list ke-2:1
tekan y jika lagi dan tekan t jika tidak:y
masukkan angka list ke-2:2
tekan y jika lagi dan tekan t jika tidak:y
masukkan angka list ke-2:2
tekan y jika lagi dan tekan t jika tidak:t

==============================
head-> 1->1->3->3->none
head-> 1->1->2->2->none
==============================
Hasil Dari Penjumlahan nya adalah :
head-> 2->2->5->5->none
==============================
```

