# Tree

Pada materi sebelumnya kita telah belajar mengenai menyimpanan data secara linear, seperti hasing, stack, queue dan linked list. Pada mater kali ini kita akan mempelajari Tree yang memiliki cara penyimpanan data non-linear melainkan secara hierarki. Bagaimana maksudnya? Untuk mempermudahnya kita bayangkan saja susunan keluarga yang kita miliki. Jika diperhatikan dalam susunan tersebut kita akan menemukan siapa kakek kita, orang tua kita, saudara orang tua atau paman kita, sepepupu kita, saudara kita, atau bahkan cucu kita bukan? Begitulah kira - kira penggambarannya dari pengertian Tree penyimpanan data secara hierarki yang tersusun secara urut dari kakek hingga cucu. Berikut atribut - atribut yang terdapat dalam Tree :

| **Node**,      | merupakan bagian dari tree yang menyimpan informasi atau juga disebut sebagai *key* |
| -------------- | ------------------------------------------------------------ |
| **Edge**       | yang menghubungkan antara node yang satu dengan yang lain. Hanya ada satu edge yang masuk ke dalam node, dan satu atau lebih edge yang keluar dari suatu node |
| **Root**       | node yang terletak di paling atas, tidak ada edge yang masuk ke dalam node root ini, tapi root mempunyai satu atau lebih dari satu edge yang keluar. |
| **path**       | merupakan urutan node dari root sampai tujuan, misalkan computer --> D: --> Mata Kuliah --> Struktur Data |
| **children**,  | merupakan node-node yang memiliki edge yang masuk dari node yang sama. Misalkan program files, users, dan windows merupakan children, krn memiliki edge masuk yang sama-sama berasal dari node C: |
| **Parent**     | node yang memiliki edge yang keluar dari node tersebut, misalkan node C: adalah parent dari program files, users, dan windows |
| **Siblings**   | adalah node-node yang berasal dari parent yang sama          |
| **subtree**    | kumpulan dari node dan edge yang terdiri dari parent dan semua node setelah parent |
| **leaf node**, | node yang tidak memiliki edge yang keluar, node yang tidak memiliki children |
| **level**,     | tingkatan dari node. Root merupakan level ke-0, semakin kebawah maka level dari node tersebut semakin besar, misalkan struktur data berada di level ke-3 |
| **height**     | merupakan tinggi tree, nilai dari height ini adalah level maksimum dari tree |

### 1. Binary Tree

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\maxresdefault.jpg)

**Binary tree** merupakan *tree* dimana setiap *parent* hanya memiliki dua buah atau satu *node children* saja.

```python
class BinaryTree:
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
myTree=BinaryTree(10)
print(myTree.leftChild)
```

Contoh :

```python
class BinaryTree:
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
    def insertLeft(self, new_node):
        if self.leftChild == None:
            self.leftChild = BinaryTree(new_node)
        else:
            t = BinaryTree(new_node)
            t.leftChild = self.leftChild
            self.leftChild = t
    def insertRight(self, new_node):
        if self.rightChild == None:
            self.rightChild = BinaryTree(new_node)            
        else:
            t = BinaryTree(new_node)
            t.rightChild = self.rightChild
            self.rightChild = t
```

Di mehod insertLeft perlu dilakukan pengecekan terlebih dahulu, apakah child kiri dari node yang akan disisipi subtree baru masih kosong, jika iya maka subtree tersebut dimasukkan pada leftChild. Dapat Menggunakan Perintah:

```python
self.leftChild=BinaryTree(new_node)
```

Namun, jika setelah dilakukan pengecekan pada binary tree, ternyata leftChild tersebut tidak kosong, Misalkan terdapat tree 'u', dimana tree 'u' tersebut, memiliki leftchild, yaitu 'm'. Jika ingin dilakukan penyisipan tree baru, yaitu 't', maka tahapan yang harus dilakukan adalah :

```python
1. t.leftChild = self.leftChild
2. self.leftChild = t
```

Contoh :

Berikut tambahan method pada class BinaryTree, untuk mendapatkan informasi mengenai left child, right child, dan root dari suatu binary tree

```python
class BinaryTree:
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
    def insertLeft(self, new_node):
        if self.leftChild == None:           
            self.leftChild = BinaryTree(new_node)         
        else:
            t = BinaryTree(new_node)
            t.leftChild = self.leftChild
            self.leftChild = t
           
    def insertRight(self, new_node):
        if self.rightChild == None:
            self.rightChild = BinaryTree(new_node)            
        else:
            t = BinaryTree(new_node)
            t.rightChild = self.rightChild
            self.rightChild = t

    def getRightChild(self):
        return self.rightChild
    def getLeftChild(self):
        return self.leftChild
    def setRootVal(self, obj):
        self.key = obj
    def getRootVal(self):
        return self.key
       
```

### 2.Parsing Binary Tree

![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\meParse.png)

Binary Tree Juga Dapat Digunakan Untuk Penyelesaina Persamaan matematika, penyelesaian persamaan matematika tergantung, pada operator dan keberadaan kurung, Jika terdapat tanda kurung buka maupun tutup, maka persamaan di dalam kurung tersebut haruslah diselesaikan pertama kali walapun level operator precedence lebih rendah dibandingkan operator yang berada di luar kurung

 Ada 2 Tahap Untuk penyelesaian persamaan matematika :

1. Pembentukan Parse Tree
2. Evaluasi Persamaan Matematika

### Pembuatan Parse Tree

Persamaan Matematika harus dipecah menjadi list token agar dapat dibuat menjadi parse tree.

- Kurung buka, kurung buka ini menandakan ekspressi baru yang akan dioperasi, oleh karena itu perlu dibuat subtree baru untuk menyelesaikan ekspressi baru ini
- kurung tutup, kurung tutup ini menandakan akhir dari ekspressi matematika
- operand, operand ini yang akan jadi *leaf node* dan *children* dari operator
- operator, operator merupakan *parent* dan punya *left* maupun *right child*

Algoritma : 

1. Jika *current token* adalah kurung buka, '(' , tambahkan node baru sebagai *left child* dari *current Node* dan jadikan node baru ini sebagai *current node*
2. jika *current token* adalah operator, set nilai key dari *current node*dengan operator tersebut. Tambahkan node baru sebagai right child dari current node, jadikan right child ini sebagai *current node*
3. jika *current token* adalah operand, maka set nilai key dari *current node* dengan operand tersebut dan jadikan parent dari node tersebut menjadi *current node*
4. jika *current token* adalah kurung tutup, ')', maka kembali ke parent dari current node

Contoh :

Berikut code untuk parsing atau pembuatan binary tree untuk persamaan matematika.

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

class BinaryTree:
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
    def insertLeft(self, new_node):
        if self.leftChild == None:           
            self.leftChild = BinaryTree(new_node)         
        else:
            t = BinaryTree(new_node)
            t.leftChild = self.leftChild
            self.leftChild = t
           
    def insertRight(self, new_node):
        if self.rightChild == None:
            self.rightChild = BinaryTree(new_node)            
        else:
            t = BinaryTree(new_node)
            t.rightChild = self.rightChild
            self.rightChild = t

    def getRightChild(self):
        return self.rightChild
    def getLeftChild(self):
        return self.leftChild
    def setRootVal(self, obj):
        self.key = obj
    def getRootVal(self):
        return self.key
    
    def buildParseTree(mathExp):
    tokenList = mathExp.split()
    parentStack = stack()
    expTree = BinaryTree(' ' )
    push(parentStack,expTree)
    print(tokenList)
    currentTree = expTree
    for i in tokenList:
        
        if i == '(' :
            print('if 1', i)
            currentTree.insertLeft(' ' )
            push(parentStack,currentTree)
            currentTree = currentTree.getLeftChild()
        elif i not in [ '+' , '-' , '*' , '/' , ')' ]:
            print('if 2', i)
            currentTree.setRootVal(int(i))
            
            parent = pop(parentStack)
            currentTree = parent
        elif i in [ '+' , '-' , '*' , '/' ]:
            print('if 3', i)
            currentTree.setRootVal(i)
            currentTree.insertRight(' ' )
            push(parentStack,currentTree)
            currentTree = currentTree.getRightChild()
        elif i == ')' :
            
            currentTree = pop(parentStack)
        else:
            raise ValueError
    return expTree

pt = buildParseTree(' ( 3 + ( 4 * 5 ) ) ')
print(pt.getRootVal())
tmp=pt.getLeftChild()
print(tmp.getRootVal())
if pt.getLeftChild():
    print('Tree')
```

### Latihan Praktikum

```python
class BinaryTree:
    rightChild = None
    leftChild = None
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
    def insertLeft(self, new_node):
        if self.leftChild == None:           
            self.leftChild = BinaryTree(new_node)         
        else:
            t = BinaryTree(new_node)
            t.leftChild = self.leftChild
            self.leftChild = t
           
    def insertRight(self, new_node):
        if self.rightChild == None:
            self.rightChild = BinaryTree(new_node)            
        else:
            t = BinaryTree(new_node)
            t.rightChild = self.rightChild
            self.rightChild = t

    def getRightChild(self):
        return self.rightChild
    def getLeftChild(self):
        return self.leftChild
    def setRootVal(self, obj):
        self.key = obj
    def getRootVal(self):
        return self.key

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

import operator
def evaluate(parse_tree):
    opers = { '+' :operator.add, '-' :operator.sub, '*' :operator.mul,'/' :operator.truediv}
    left = parse_tree.getLeftChild()
    right = parse_tree.getRightChild()
    if left and right:
        fn = opers[parse_tree.key]
        return fn(evaluate(left),evaluate(right))
    else:
        return parse_tree.key

def buildTree(i):
    s = stack()
    i = i.split()
    for x in i:
        if x in '1234567890':
            t = BinaryTree(x)
            push(s, t)
        elif x in '+-*/':
            sb = pop(s)
            sc = pop(s)
            a = BinaryTree(x)
            a.insertRight(sb.getRootVal())
            a.insertLeft(sc.getRootVal())
            push(s, a)

    return s[0]

a = '2 8 9 + *'
r = buildTree(a)
print(evaluate(r))

```

