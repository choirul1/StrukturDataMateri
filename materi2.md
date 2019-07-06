# Infix, Prefix dan postfix

## **A. Definisi**

### Infix

 adalah cara penulisan atau ungkapan yang meletakan operator di tengah antara 2 operand dalam hal ini dalam kurung sangat menentukan posisi.

Contoh Infix :

A + B

( A - B ) * C



### Prefix 

adalah cara penulisan atau ungkapan yang meletakan operator disebelah kiri 2 operand dan dalam kurung sangat menentukan posisi.

Contoh Prefix :

\+ A B

\* - A B C



### Posfix

 adalah cara penulisan yang meletakan operator disebelah kanan 2 operand dan posisi operand yang berada di dalam kurung sangat menentukan.

Contoh Postfix :

A B +

A B - C *

## **B. Ilustrasi**

**> Ilustrasi Konversi Infix ke Prefix**

Contoh : 

**A * B + C**

proses : 

infix dibalik menjadi C + B * A

Looping Dimulia

| Karakter Yang Dibaca | Isi Stack | Karakter Tercetak | Hasil Postfix |
| -------------------- | --------- | ----------------- | ------------- |
| C                    |           | C                 | C             |
| +                    | +         |                   |               |
| B                    |           | B                 | CB            |
| *                    | +*        |                   | CB            |
| A                    | +*        | A                 | CBA           |
|                      | +         | *                 | CBA*          |
|                      |           | +                 | CBA*+         |

Hasil Postfix = C B A + *

Hasil Postfix dibalik untuk menjadi hasil prefix

Hasil Prefix = * + A B C

**> Ilustrasi Konversi Infix ke Postfix**

Contoh :

**A * B  + C**

Proses :

| Karakter Yang Dibaca | Isi Stack | Karakter Tercetak | Hasil Postfix |
| -------------------- | --------- | ----------------- | ------------- |
| A                    |           | A                 | A             |
| *                    | *         |                   |               |
| B                    |           | B                 | AB            |
| +                    | +         | *                 | AB*           |
| C                    | +         | C                 | AB*C          |
|                      |           | +                 | AB*C+         |

Hasil Postfix = A B * C +

Contoh Aritmatik infix dan konversi ke prefix dan postfix

| Infix       | Prefix     | Postfix   |
| ----------- | ---------- | --------- |
| A + B       | + A B      | A B +     |
| (A+B)*C     | *+ABC      | AB+C*     |
| (A+B)*(C-D) | *+AB-CD    | AB+CD-*   |
| A+B*C-D     | -+A*BCD    | ABC*+D-   |
| A+B-C+D     | +-+ABCD    | AB+C-D+   |
| A*B - C * D | -* AB * CD | AB * CD*- |

### C. Algoritma

Berikut ini algoritma dari konversi Infix ke Postfix:

1. Buat presisi atau kekuatan operator ( Penjumlahan dan Pengurangan bernilai 2 , Perkalian dan Pembagian bernilai 3 , Kurang buka dan tutup bernilai 1 )
2. Input data dalam bentuk infix
3. Pisahkan data infix menggunakan split menjadi bentuk List
4. Periksa semua data yang berada di dalam list secara urut mulai dari awal hingga akhir
5. Jika bertemu operand, maka masukan data ke PostfixList untuk dicetak
6. Jika bertemu kurung buka '(' maka masukan ke Stack Operator
7. Jika bertemu kurung tutup ')' maka Stack Operator yang paling atas dan bukan kurung buka '(' diambil untuk dicetak ke PostfixList
8. Jika bertemu operator maka jika Stack Operator tidak kosong dan kekuatan operator yang digunakan lebih kecil dari kekuatan operator yang berada di top Stack Operator maka operator yang berada di Stack Operator diambil (pop) untuk dicetak di PostfixList. lalu masukan operator yang digunakan ke dalam Stack Operator.
9. Begitu seterusnya sampai List yang berisi data Infix habis.
10. Jika Stack Operator masih ada isinya maka ambil dan tambahkan ke PostfixList untuk dicetak.
11. Cetak PostfixList

Berikut ini Algoritma dari konversi Infix ke Prefix:

1. Balikan data Infix
2. Jika operator kurung buka '(' maka ganti dengan kurung tutup ')' begitu sebaliknya
3. Masukan data tersebut ke konversi Infix ke Postfix 
4. Setelah keluar hasil, Balikan lagi hasil tersebut
5. Maka keluar bentuk Prefix

**D. Kode Program**

Berikut ini kode program Konversi dari Infix ke bentuk Postfix :

```python
class Stack:
     def __init__(self):
         self.items = []
     def isEmpty(self):
         return self.items == []
     def push(self, item):
         self.items.append(item)
     def pop(self):
         return self.items.pop()
     def peek(self):
         return self.items[len(self.items)-1]
     def size(self):
         return len(self.items)
     def showList(self):
          return self.items

def infixToPostfix(infixexpr):
    prec = {}
    prec["*"] = 3
    prec["/"] = 3
    prec["+"] = 2
    prec["-"] = 2
    prec["("] = 1
    opStack = Stack()
    postfixList = []
    tokenList = infixexpr.split()
    print(tokenList)
    

    for token in tokenList:
        if token in "ABCDEFGHIJKLMNOPQRSTUVWXYZ" or token in "0123456789":
            postfixList.append(token)
        elif token == '(':
            opStack.push(token)
        elif token == ')':
            topToken = opStack.pop()
            
            while topToken != '(':
                postfixList.append(topToken)
                topToken = opStack.pop()
        else:
            while (not opStack.isEmpty()) and \
               (prec[opStack.peek()] >= prec[token]):
                  postfixList.append(opStack.pop())
            opStack.push(token)
        print('isi postix ',str(postfixList))

    while not opStack.isEmpty():
        postfixList.append(opStack.pop())
    print('isi postix ',str(postfixList))
    return " ".join(postfixList)

print(infixToPostfix("A * B - C * D"))
print(infixToPostfix("( A + B ) * C - ( D - E ) * ( F + G )"))



```

```python
Output :
    ['A', '*', 'B', '-', 'C', '*', 'D']
('isi postix ', "['A']")
('isi postix ', "['A']")
('isi postix ', "['A', 'B']")
('isi postix ', "['A', 'B', '*']")
('isi postix ', "['A', 'B', '*', 'C']")
('isi postix ', "['A', 'B', '*', 'C']")
('isi postix ', "['A', 'B', '*', 'C', 'D']")
('isi postix ', "['A', 'B', '*', 'C', 'D', '*', '-']")
A B * C D * -
['(', 'A', '+', 'B', ')', '*', 'C', '-', '(', 'D', '-', 'E', ')', '*', '(', 'F', '+', 'G', ')']
('isi postix ', '[]')
('isi postix ', "['A']")
('isi postix ', "['A']")
('isi postix ', "['A', 'B']")
('isi postix ', "['A', 'B', '+']")
('isi postix ', "['A', 'B', '+']")
('isi postix ', "['A', 'B', '+', 'C']")
('isi postix ', "['A', 'B', '+', 'C', '*']")
('isi postix ', "['A', 'B', '+', 'C', '*']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-', 'F']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-', 'F']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-', 'F', 'G']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-', 'F', 'G', '+']")
('isi postix ', "['A', 'B', '+', 'C', '*', 'D', 'E', '-', 'F', 'G', '+', '*', '-']")
A B + C * D E - F G + * -
```

Berikut Kode Program konversi Infix ke Prefix :

```python
class Stack:
     def __init__(self):
         self.items = []
     def isEmpty(self):
         return self.items == []
     def push(self, item):
         self.items.append(item)
     def pop(self):
         return self.items.pop()
     def peek(self):
         return self.items[len(self.items)-1]
     def size(self):
         return len(self.items)
     def showList(self):
          return self.items
# No 1
def infixToPrefix(infixexpr):
    
    prec = {'*':3, '/':3 , '+':2, '-':2 , '(':1}
    opStack = Stack()
    prefixList = []
    tokenList = infixexpr.split()
    tokenList.reverse()
    for i in range(len(tokenList)):
         if tokenList[i] == '(':
              tokenList[i]=')'
         elif tokenList[i] == ')':
              tokenList[i]='('
    for token in tokenList:
        if token in "ABCDEFGHIJKLMNOPQRSTUVWXYZ" or token in "0123456789":
            prefixList.append(token)
        elif token == '(':
            opStack.push(token)
        elif token == ')':
            topToken = opStack.pop()
            
            while topToken != '(':
                prefixList.append(topToken)
                topToken = opStack.pop()
        else:
            while (not opStack.isEmpty()) and \
               (prec[opStack.peek()] >= prec[token]):
                  prefixList.append(opStack.pop())
            opStack.push(token)

    while not opStack.isEmpty():
        prefixList.append(opStack.pop())
    prefixList = prefixList[::-1]
    return " ".join(prefixList)

print('No 1')
print(infixToPrefix("A * B - C * D"))
print(infixToPrefix("( A + B ) * C - ( D - E ) * ( F + G )"))
```

```python
Output :
No 1
- * A B * C D
- * + A B C * - D E + F G
```

**Latihan Praktikum**

1. reverseWord (kata) :
   Gunakan fungsi-fungsi yang terdapat pada modul stack untuk membalik suatu kata. Output dari
   fungsi reverseWord(kata) ini adalah kata yang sudah disusun secara terbalik, 

```python
#Ach. choirul Umam
#160411100075
#no1

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
print(balik('madura'))

```

```python
Output :
arudam
```

2. decToBin(num) :
   Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengkonversi suatu bilangan
   decimal menjadi bilangan biner, 

```python
#Ach. choirul Umam
#160411100075
#no2

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
print("HAsil biner : "+biner(s))

```

```python
Output :
    masukkan nilai desimal:25
    HAsil biner : 1.1.0.0.1
```

