# Stack

## A. Definisi

**Stacks** adalah satu struktur data dimana penambahan dan penghapusan data, hanya dapat dilakukan pada satu ujung yang **sama**, atau yang biasa dikenal dengan istilah **top**.

Semakin data jauh berada dari posisi top, maka data tersebut diindikasikan berada di stack lebih lama dibandingkan dengan data yang berada dekat pada data di posisi top.

Jika terdapat data baru yang ditambahkan di stack, maka data ini pulalah yang akan dihapus ketika terdapat proses penghapusan data. Konsep ini dikenal dengan nama **LIFO-Last In First Out**.

## B. Ilustrasi 

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\stackketutrare.JPG)

Jika Ingin Melakukan Perubahan Susunan Balok Diatas, Maka Yang Dapat Diambil Adalah Balok paling atas, sama halnya ketika ingin mengambil balok paling bawah, maka harus mengambil balok-balok yang berada diatasnya terlebih dahulu.

**C. Operasi Stack**

| **stack()**    | membuat suatu stack baru yang kosong. Tidak memerlukan parameter dan mengembalikan suatu stack kosong. |
| -------------- | ------------------------------------------------------------ |
| **push(item)** | menambahkan suatu item baru ke atas (top) dari stack. Perlu item dan tidak mengembalikan apapun. |
| **pop()**      | menghapus item teratas dari stack. Tidak perlu parameter dan mengembalikan item. Stack berubah. |
| **peek()**     | mengembalikan top item dari stack tetapi tidak menghapusnya. Tidak memerlukan parameter dan stack tidak berubah. |
| **isEmpty()**  | memeriksa apakah stack dalam keadaan kosong. Tidak memerlukan parameter dan mengembalikan nilai boolean. |
| **size()**     | mengembalikan jumlah item di dalam stack. Tidak memerlukan parameter dan mengembalikan suatu integer. |

**D. Code**

Dibawah ini merupakan fungsi-fungsi untuk implementasi stack

```python
def stack():
    s=[]
    return (s)
def push(s,data):
    s.append(data)
def pop(s):
    data=s.pop()
    return(data)
def peek(s):
    return(s[len(s)-1])
def isEmpty(s):
    return (s==[])
def size(s):
    return(len(s))
```

Berikut Contoh Implementasi Sederhana :

``` python
st=stack()
isEmpty(st)
```

Output : True

```python
push(st,5)
push(st,4)
push(st,3)
pop(st)
push(st,10)
pop(st)
print(st)
```

Output : [5, 4]

**E. Latihan**

**Program Balik Kata**

```python
def stack():
    s=[]
    return(s)

def push(s,data):
    s.append(data)
    
def pop(s):
    data=s.pop()
    return(data)

def peek(s):
    return(s[len(s)-1])

def isEmpty(s):
    return (s==[])
    
def size(s):
    return (len(s))

def balik(teks):
    a=stack()
    hasil =''
    for i in range(len(teks)):
        push(a, teks[i])
    for i in range (len(teks)):
        hasil=hasil+pop(a)
    return hasil
print(balik('arek'))
```

```python
Output:
kera
```



**Program Konversi bilangan desimal ke bilangan biner**

Konversi Bilangan Sangat Diperlukan Dalam dunia komputer, bahkan sangat di butuhkan ketika akan mengkonversi bilangan untuk satu alamat IP Jaringan.

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\desToBin2.png)

```python
def stack():
    s=[]
    return(s)

def push(s,data):
    s.append(data)
    
def pop(s):
    data=s.pop()
    return(data)

def peek(s):
    return(s[len(s)-1])

def isEmpty(s):
    return (s==[])
    
def size(s):
    return (len(s))

def biner(desi):
    st=stack()
    des=desi
    while des>0:
        push(st,str(des%2))
        des=des//2
    hasil=''
    while not isEmpty(st):
        if len(st)==1:
            hasil=hasil+st.pop()
        else:
            hasil=hasil+st.pop()+"."
    return(hasil)

s=int(input("masukkan nilai desimal:"))
print("biner:"+biner(s))

masukkan nilai desimal:234
              biner:1.1.1.0.1.0.1.0
```

```python
Output
masukkan nilai desimal: 234 
biner: 1.1.1.0.1.0.1.0
```

