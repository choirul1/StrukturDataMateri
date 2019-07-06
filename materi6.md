# Searching

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\binary-and-linear-search-animations.gif)

### 1. Sequential Searching

### A. Definisi

Linear Searching atau sequential search adalah sebuah metode pencaran data dengan cara membandingkan nilai yang dicari dengan nilai dari setiap elemen list , mulai dari elemen pertama (indeks = 0) sampai nilai yang dicari ditemukan atau sampai elemen terakhir (indeks - n). Untuk lebih jelasnya perhatikan gambar animasi di bawah ini.

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\linear_search.gif)

​    Misalnya kita memiliki sebuah list, anggap saja list a. Di dalam list itu terdapat beberapa elemen yang terdiri dari beberapa angka acak. Katakanlah 8,5,7,9,2. Kita ingin mencari sebuah angka dari dalam list tersebut, misalnya angka 7. Dan juga kita bisa juga sekaligus mendapatkan informasi pada indeks ke-berapa letak angka tersebut berada, berapa kali iterasinya (proses perulangan saat mencari data tersebut). 

### Unordered Sequential Search

Pada *unordered list sequential search*, data berada pada keadaan acak, tidak terurut, sehingga pencarian harus dilakukan mulai dari indeks awal sampai indeks terakhir dari data, atau pencarian berhenti ketika data sudah ditemukan.

Contoh :

 implementasi algoritma *unordered list sequential search*.

```python
def seqSearch(listData, data):
    ind = 0
    found = False
    while ind < len(listData) and not found:
        if listData[ind] == data:
            found = True
        else:
            ind = ind+1
    return found
a=[12,5,9,8,1,10,26]
seqSearch(a,1)
```

Ordered equential List

Pada ordered list sequential search, data sudah dalam keadaan terurut, hal ini tentunya dapat mengurangi waktu komputasi pencarian. 

Contoh :

```python
def orderedSeqSearch(listData, data):
    ind = 0
    found = False
    stop = False
    position=[]
    while ind < len(listData) and not found and not stop:
        if listData[ind] == data:
            found = True
            position.append(ind)
        else:
            if listData[ind] > data:
                stop = True
            else:
                ind = ind+1
    
    if found:
        return ind
    else:
        return ('Data tidak ada')
 a=[1,1,5,5,5,8,9,10,12,26]
ind=orderedSeqSearch(a,5)
print(ind)
```



### 2. Binary Seraching

Binary Search merupakan metode pencarian data dengan membagi 2 atau pencarian dimulai dari indeks list bagian tengah, lalu membandingkannya. Jika bertemu dengan angka yang lebih kecil dari pada yang dicari, maka langsung dibuangnya, begitu seterusnya hingga nilai yang dicari (==)  cocok.

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\binary.gif)

Cara kerja algoritma pencarian bagi-dua adalah dengan membagi elemen-elemen list menjadi dua bagian secara berulang. Jika nlai yang dicari (value) lebih kecil dari elemen tengah (alist[middle]), maka proses pencarian dilakukan pada bagian list sebelah kiri. Jika lebih besar, maka pencarian dilakukan pada bagian list sebelah kanan; dengan asumsi bahwa elemen-elemen list terurut secara menaik (ascending).

Contoh :

Berikut code untuk binary search dengan metode iteratif

```python
def binarySearch(listData, data):
    first = 0
    last = len(listData) - 1
    found = False
        
    while first <= last and not found:
        midpoint = (first + last) // 2
        if listData[midpoint] == data:
            found = True
            
        else:
            if data < listData[midpoint]:
                last = midpoint - 1
            else:
                first = midpoint + 1
    
    return found
a=[4,6,10,34,56,78,99]
print(binarySearch(a,34))
```

### Latihan Praktikum

1. 

```python
# nomer 1

def seqSearch(listData, data):
	iterasi = 0
	hasil = []
	found = 'Data tidak ada'
	for i in range(len(listData)):
		if listData[i] == data:
			hasil.append(i)
			found = hasil
			iterasi = iterasi+1
	return found,iterasi

a = [1,5,9,8,1,5,10,26,5,12]
[hasil,jumlahIterasi] = seqSearch(a,5)
print("===========SequentialSearch=====================")
print("data",a)
print('Posisi Data =',hasil)
print('Jumlah Iterasi =',jumlahIterasi)

# nomer 2

def orderedSeqSearch(listData, data):
	ind = 0
	iterasi = 0
	found = False
	stop = False
	position=[]
	while ind < len(listData) and not found and not stop:
		if listData[ind] == data and listData[ind+1] == data:
			position.append(ind)
			found = False
			iterasi += 1
			ind = ind+1
		elif listData[ind] == data and listData[ind+1] != data:
			position.append(ind)
			iterasi += 2
			found = True
		else:
			if listData[ind] > data:
				iterasi += 1
				stop = True
			else:
				iterasi += 1
				ind = ind+1

	if found:
		return position,iterasi	
	else:
		return ('Data tidak ada',iterasi)

a = [1,1,5,5,5,8,9,10,12,26]
[hasil,iterasi] = orderedSeqSearch(a,5)
print("==================orderedSeqSearch================")
print("data",a)
print('Posisi Data =',hasil)
print('Jumlah Iterasi =',iterasi)

# nomer 3

def binarySearch(listData, data):
	first = 0
	iterasi = 0
	last = len(listData) - 1
	found = False
	hasil = []
	while first <= last and not found:
		midpoint = (first + last) // 2
		if listData[midpoint] == data and listData[midpoint-1] == data and listData[midpoint-2] != data:
			found = True
			hasil.append(midpoint)
			hasil.append(midpoint-1)
			iterasi += 2
		elif listData[midpoint]==data and listData[midpoint-1] == data and listData[midpoint-2] ==data:
			found = True
			hasil.append(midpoint)
			hasil.append(midpoint-2)
			hasil.append(midpoint-1)
			iterasi += 4
		elif listData[midpoint]==data and listData[midpoint-1] != data:
			found = True
			hasil.append(midpoint)
			iterasi += 1
		else:
			if data < listData[midpoint]:
				last = midpoint - 1
				iterasi += 1
			else:
				first = midpoint + 1
				iterasi += 1
	if found :
		return hasil,iterasi
	else:
		return "data tidak ada",iterasi
a = [1,1,5,5,5,8,9,10,12,26,30]
[hasil,iterasi] = binarySearch(a,26)
print("===========Binary Search=====================")
print("data",a)
print('Posisi Data =',hasil)
print('Jumlah Iterasi =',iterasi)

```

```python
Output :
===========SequentialSearch=====================
data [1, 5, 9, 8, 1, 5, 10, 26, 5, 12]
Posisi Data = [1, 5, 8]
Jumlah Iterasi = 3
==================orderedSeqSearch================
data [1, 1, 5, 5, 5, 8, 9, 10, 12, 26]
Posisi Data = [2, 3, 4]
Jumlah Iterasi = 6
===========Binary Search=====================
data [1, 1, 5, 5, 5, 8, 9, 10, 12, 26, 30]
Posisi Data = [9]
Jumlah Iterasi = 3
```

