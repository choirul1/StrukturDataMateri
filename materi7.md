# Hashing

### A. Definisi

Hashing adalah teknik atau metode memetakan data ke sebuah tempat dimana data sebenarnya dirubah dalam bentuk lain. semisal huruf a menjadi huruf e. Teknik ini biasanya digunakan untuk mengenkrispsi sebuah password didalam database seperti MySQL. 
Pada python, cara metode Hashing dengan membuat sebuah List yang akan diisi oleh data masukan. Data masukan diberi 2 buah nilai yaitu value sebagai data tersebut dan juga key sebagai alat untuk memasukan value ke List.

Di dalam algoritma hashing ini terdapat beberapa istilah dasar sebagai berikut:

- **Hash Table**, yaitu sebuah tempat penyimpanan data, yang dibuat sedemikian rupa, sehingga dapat memudahkan pencarian. Tipe data list di python dapat digunakan untuk merepresentasikan hash table
- **slot**, yaitu posisi (indeks) yang terdapat pada hash table sebagai tempat penyimpanan setiap data. Karena slot berfungsi seperti halnya indeks, maka nilai slot adalah nilai integer mulai dari nol sampai dengan ukurang dari hash table, misalkan slot 0, slot 1, slot 2, .... , slot n*n*.
- **Hash function**, yaitu suatu fungsi yang memetakan antara data dengan slot di dalam hash table

**Algoritma** Hashing sebagai berikut :

1. Membuat tabel hash yang berisikan None
2. Memasukan data yang ingin dimasukan 
3. Data masukan terdiri dari value dan keynya
4. Lakukan pencarian modulus dari key yang dibagi panjang tabel hash
5. Masukan value dari data tersebut ke dalam tabel hash sesuai indexnya.

Ilustrasi Hashing :

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\IMG_20170608_103423.jpg)

### Fungsi Hash

Hash function sangat berperan penting dalam algoritma hashing, dengan hash function, data didalam list disusun berdasarkan nilai hash, dan pencarian data dilakukan berdasarkan **nilai hash** dari hash function ini.

Contoh :

Berikut adalah fungsi-fungsi yang diperlukan untuk algoritma hashing , antara lain :

- hash function (gunakan remainder function, yaitu data dimodulus dengan 11), nilai balik merupakan nilai hash
- createHashTable, untuk membuat hash table, dengan inisialisasi semua slot berisi 'none'
- putData, yaitu menyusun data ke dalam hash table, berdasarkan nilai hash yang dihasilkan
- searchHash, argumen merupakan data yang dicari, dan nilai balik berupa True or False, yaitu apakah data ditemukan di dalam hash table

**Permasalahan** yang terjadi pada hashing adalah apabila pada index yang terjadi banyak value, inilah yang disebut Collision. Cara mengatasinya ada tiga yang sudah saya pelajari, yaitu linear hashing, aquadratic hashing dan chainning.

**1. linier hashing**

Linear Hashing

Penyelesaian dengan linear yaitu melakukan penambahan 1 tiap index yang terjadi collision, misalnya, collison terjadi pada index 3, maka data selanjutnya yang berindex 3 akan ditambahkan ke index 4, jika index 4 sudah terdapat value atau isi maka data terdebut ditaruh di index 5.

Contoh :

```python
print('=============== Program Hashing Data Numerik (Linear Probbing) ================ ')
l = 'y'
while l == 'y':
    table = int(input('Masukan panjang tabel Hash = '))
    table = [None] * table
    print('Panjang Tabel Hash = %i'%(len(table)))

    def hash(x,table):
        return x % len(table)

    def insert(table,key,value):
        index = hash(key,table)
        if table[index] == None:
            table[index] = value
        else:
            collusion = index
            found = False
            ind = collusion + 1
            if ind > len(table) - 1:
                    ind = 0
            while (ind <= len(table)-1) and not found:
                if table[ind] == None:
                    found = True
                    table[ind] = value
                ind = ind+1
                
    #Jika ingin mencari data dengan hasil True dan False
    '''def searchHash(data,table):
        if data in table:
            print('Data ditemukan')
        else:
            print('Data tidak ditemukan')'''
    
    #Jika ingin mencari data dengan hasil index data yang dicari
    '''def searchHash(data,table):
        x = 0
        found = False
        while x < len(table) and not found:
            if table[x] == data:
                found = True
            if found ==False:
                x+=1
        if found == True:
            print('Data %s berada pada di index %s dari table'%(data,x))
        else:
            print('Data %s tidak ditemukan'%data)'''

    #Jika ingin mencari data dengan cara hash dengan hasil True/False beserta indeks
    def searchHash(data,table):
        index = hash(data,table)
        if table[index] == data:
            print('True')
            print('Data %s berada pada index %s'(data,index))
            return True 
        else:
            col = index
            found = False
            ind = col + 1
            if ind > len(table) - 1:
                ind = 0
            kali = 1
            while (ind <= len(table)-1) and not found:
                if table[ind] == data:
                    found = True
                    print('True')
                    print('Data %s berada pada index %s'%(data,ind))
                    return True
                ind+=1
                if ind> len(table)-1:
                    ind = 0
                if kali>len(table):
                    found = True
                    print('False')
                    print('Data %s data tidak temukan'%data)
                    return False
                kali+=1
    
    
    masuk = 'y'
    while masuk == 'y':
        nginput = int(input('Masukan berapa kali ingin memasukan data ke Tabel Hash = '))
        if nginput > len(table):
            print('Panjang data masukan lebih dari panjang Tabel Hash')
            print('Tolong masukan ulang')
        else:
            masuk = 'n'
    b = 1
    while b<=nginput:
        masukan = int(input('Masukan angka yang ingin dimasukan ke Tabel Hash = '))
        insert(table,masukan,masukan)
        b+=1

    print(table)
            
    nginput = True
    while nginput:
        q = input('Apakah ingin mencari Data ? (y/n) ')
        if q == 'y':
            dicari = int(input('Masukan angka yang ingin dicari = '))
            searchHash(dicari,table)
        elif q == 'n':
            nginput = False
        else:
            print('Masukan y atau n!')
            nginput = True

    k = 'y'
    while k =='y':
        l = input('Apakah ingin melanjutkan program ? (y/n) ')
        if l == 'y':
            k = 'n'
        elif l == 'n':
            print('Terima Kasih')
            k = 'n'
        else:
            print('Masukan y atau n!')
            k = 'y'

```

**2. Aquadratic Hashing**

Penyelesaian dengan Quadratic/Aquadratic ini sama seperti linear akan tetapi penambahan tidak satu persatu, melainkan penambahnya di kuadratkan lalu dimodulus dengan panjang tabel hash.

Misalnya yang terjadi collison pada index 3 dan panjang tabel hash 10 maka jika ditambahkan data yang berindex 3 maka data terbut ditaruh pada index ke 3 yang ditambah 1 kuadrat 2 jadi berindex 4 lalu dimodulus panjang tabel hash jadi index 4. Jika index 4 sudah terisi maka index ditambah 2 kuadrat 2 jadi 3+4 yaitu 7 dan dimodulus panjang tabel hash yaitu 10 menjadi index 7, begitu seterusnya hingga data dapat ditempakan ditempat kosong pada tabel hash.

Contoh :

```python
print('============= Program Hashing Data Numerik (Qudratic Probbing) ================ ')
l = 'y'
while l == 'y':
    table = int(input('Masukan panjang tabel Hash = '))
    table = [None] * table
    print('Panjang Tabel Hash = %i'%(len(table)))

    def hash(x,table):
        return x % len(table)

    def insert(table,key,value):
        index = hash(key,table)
        if table[index] == None:
            table[index] = value
        else:
            collusion = index
            found = False
            i = 1
            while i > 0 and not found:
                ind = collusion + i**2
                ind = ind % len(table)
                if table[ind] == None:
                    found = True
                    table[ind] = value
                i+=1

    #Jika ingin mencari data dengan hasil True dan False
    '''def searchHash(data,table):
        if data in table:
            print('Data ditemukan')
        else:
            print('Data tidak ditemukan')'''
    
    #Jika ingin mencari data dengan hasil index data yang dicari
    def searchHash(x,table):
        posisi = 0
        found = False
        while posisi < len(table) and not found:
            if table[posisi] == x:
                found = True
            if found==False:
                posisi += 1
        print('Angka yang dicari adalah %s pada tabel %s'%(x,table))
        print('Angka %s terdapat pada index = %s'%(x,posisi))

    def searchHash(data,table):
        index = hash(data,table)
        if table[index] == data:
            print('True')
            print('Data %s berada pada index %s'(data,ind))
            return True
        else:
            collusion = index
            found = False
            i = 1
            kali = 1
            while i > 0 and not found:
                ind = collusion + i**2
                ind = ind % len(table)
                if table[ind] == data:
                    found = True
                    print('True')
                    print('Data %s berada pada index %s'(data,ind))
                i+=1
                if kali > len(table):
                    found = True
                    print('False')
                    print('Data %s tidak ditemukan'%data)
                    return False
                kali+=1

    masuk = 'y'
    while masuk == 'y':
        nginput = int(input('Masukan berapa kali ingin memasukan data ke Tabel Hash = '))
        if nginput > len(table):
            print('Panjang data masukan lebih dari panjang Tabel Hash')
            print('Tolong masukan ulang')
        else:
            masuk = 'n'
    b = 1
    while b<=nginput:
        masukan = int(input('Masukan angka yang ingin dimasukan ke Tabel Hash = '))
        insert(table,masukan,masukan)
        b+=1

    print(table)
            
    nginput = True
    while nginput:
        q = input('Apakah ingin mencari Data ? (y/n) ')
        if q == 'y':
            dicari = int(input('Masukan angka yang ingin dicari = '))
            searchHash(dicari,table)
        elif q == 'n':
            nginput = False
        else:
            print('Masukan y atau n!')
            nginput = True

    k = 'y'
    while k =='y':
        l = input('Apakah ingin melanjutkan program ? (y/n) ')
        if l == 'y':
            k = 'n'
        elif l == 'n':
            print('Terima Kasih')
            k = 'n'
        else:
            print('Masukan y atau n!')
            k = 'y'

```

**3.Chaining**

Penyelesaian dengan cara Chainning yaitu membuat list didalam tabel hash sehingga data yang berindex sama tidak terjadi collison karena data tersebut ditumpuk ke dalam sebuah list yang telah dibuat.

Contoh :

```python
print('============= Program Hashing Data Numerik (Chaining Probbing) ================ ')
l = 'y'
while l == 'y':
    table = int(input('Masukan panjang tabel Hash = '))
    table = [ [] for _ in range(table) ]

    def hash(x,table):
        return x % len(table)

    def insert(table,key,value):
        table[hash(key,table)].append(value)

    #Jika ingin mencari data dengan hasil True dan False
    '''def searchHash(data,table):
        found = False
        i = 0
        j = 0
        while i < len(table) and not found:
            if data in table[i]:
                print('Data ditemukan')
                found = True
            i+=1
        if found == False:
            print('Data tidak ditemukan')'''
    #Jika ingin mencari data dengan hasil index data yang dicari
    '''def searchHash(data,table):
        found = False
        i = 0
        
        while i < len(table) and not found:
            j = 0
            while j < len(table[i]) and not found:
                if data == table[i][j]:
                    found = True
                if found==False:
                    j+=1
            if found==False:
                i+=1
        if found == True:
            print('Data %s berada pada list ke-%s index ke-%s'%(data,(i+1),j))
        else:
            print('Data %s tidak ditemukan'%data)'''

    def searchHash(data,table):
        index = hash(data,table)
        if data in table[index]:
            print('True')
            jml = len(table[index])
            for i in range(jml):
                if data == table[index[i]]:
                    break
            print('Data %s berada di dalam list %s index %s'%(data,index,i))
        else:
            print('Data %s tidak ditemukan'%data)

    
    nginput = int(input('Masukan berapa kali ingin memasukan data ke Tabel Hash = '))
    b = 1
    while b<=nginput:
        masukan = int(input('Masukan angka yang ingin dimasukan ke Tabel Hash = '))
        insert(table,masukan,masukan)
        b+=1

    print(table)
            
    nginput = True
    while nginput:
        q = input('Apakah ingin mencari Data ? (y/n) ')
        if q == 'y':
            dicari = int(input('Masukan angka yang ingin dicari = '))
            searchHash(dicari,table)
        elif q == 'n':
            nginput = False
        else:
            print('Masukan y atau n!')
            nginput = True

    k = 'y'
    while k =='y':
        l = input('Apakah ingin melanjutkan program ? (y/n) ')
        if l == 'y':
            k = 'n'
        elif l == 'n':
            print('Terima Kasih')
            k = 'n'
        else:
            print('Masukan y atau n!')
            k = 'y'
```

**Latihan Praktikum**

1. 

```python
table=[[]for i in range(10)]
def remainder(data, num):
    return (data%num)
slot = remainder(55,10)
print(slot)

def hash(x):
    a = []
    for i in range (x):
        a.append("none")
    return x % 10
hashTable = hash(11)
print(hashTable)
def insert(table,key,value):
    index=hash(key)
    table[index].append(value)

def search(table,value):
    index=hash(value)
    if len(table[index])-1 > 0:
        index2=table[index]
        i=0
        found=False
        while i <=len(table[index]) and not found:
            if index2[i]== value:
                found=True
                print(value,"ada di list ke",index,"index ke-",i)
            else:
                i=i+1
    else:
        i=0
        print( value, "ada di list ke", index, "index ke-", i)



insert(table,2,2)
insert(table,3,3)
insert(table,12,12)
insert(table,13,13)
insert(table,23,23)
insert(table,10,10)
insert(table,4,22)
insert(table,3,33)
print(table)
search(table,3)
search(table,2)
search(table,12)
search(table,13)
search(table,23)
search(table,10)

```

```python
Output :
5
1
[[10], [], [2, 12], [3, 13, 23, 33], [22], [], [], [], [], []]
3 ada di list ke 3 index ke- 0
2 ada di list ke 2 index ke- 0
12 ada di list ke 2 index ke- 1
13 ada di list ke 3 index ke- 1
23 ada di list ke 3 index ke- 2
10 ada di list ke 0 index ke- 0
```

