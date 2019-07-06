# Graph 

### A. Definisi

*Graph* adalah salah satu metode pemetaan data dengan memberikan informasi pada kumpulan titik (*node*) yang dihubungkan dengan segmen garis. Titik ini atau Node disebut *verteks*sedangkan segmen garis disebut dengan ruas (*edge*).

### B. Algoritma

Alur program dari graph untuk mencari semua path, path terpendek, dan path terpanjang yang akan dicontohkan di kode program dibawah ini adalah :
1. Membuat fungsi yang berisi paramater graph tersebut, permulaan path, akhir path, variabel tempat yang akan diisi path.
2. Variabel tempat yang akan diisi path ditambah permulaan path.
3. Jika permulaan path sama dengan akhir path maka variabel tempat yang akan diisi path di tampilkan.
4. Jika permulaan path tidak berada di graph tersebut maka hasilnya adalah None atau tidak ada.
5. Pengulangan dimulai dari graph yang berobjek permulaan path.
6. Jika node tidak berada di path maka memulai fungsi pencarian nomor 1 dengan parametergraph tersebut,  node, akhir path, variabel terakhir yang akan diisi path.

Istilah Dalam graph :

| **Vertex (V)** | adalah bagian paling dasar dari grafik atau yang disebut juga sebagai *node*/titik |
| -------------- | ------------------------------------------------------------ |
| **Edge (E)**   | adalah bagian dari *graph* yang menghubungkan 2 *vertex*/*node*/titik |
| **Weight (W)** | adalah sebuah nilai dalam *graph* atau yang menunjukan biaya yang dibutuhkan untuk berpindah dari satu titik ke titik yang lain. Misalnya sebuah peta diinterpestasikan dalam *graph*, maka jarak satu kota ke kota lain disebut *Weight*. |
| **Path**       | adalah serangkaian *vertex* yang berbeda-beda yang berdekatan dihubungkan oleh *edge* dan berturut-turut dari *vertex* satu ke *vertex*berikutnya. *Path* dari a*a* ke c*c* adalah urutan *vertex* (a,b,c)(*a*,*b*,*c*) yang terdiri dari beberapa pasang *Edge* \{(a,b), (b,c)\}{(*a*,*b*),(*b*,*c*)} atau urutan *vertex* (a,d,c)(*a*,*d*,*c*) yang terdiri dari beberapa pasang *Edge* \{(a,d), (b,c)\}{(*a*,*d*),(*b*,*c*)} |

### C. Kode Program

Contoh program dari *graph* adalah sebagai berikut ini : 

```python
def find_path(graph, start, end, path=[]):
    path+=[start]
    print('Path Awal', path)
    if start == end:
        return path
    if start not in graph:
        return None
    for node in graph[start]:
        print('Node sekarang %s dari Start %s'%(node,start))
        if node not in path:
            print('Path Kedua', node)
            newpath = find_path(graph, node, end,path)
            print('Newpath = ',newpath)
            if newpath: return newpath
    return None

def find_all_paths(graph, start, end, path=[]):
    path = path + [start]
    print('Path Awal', path)
    if start == end:
        return [path]
    if start not in graph:
        return []
    paths = []
    for node in graph[start]:
        print('Node sekarang %s dari Start %s'%(node,start))
        if node not in path:
            newpaths = find_all_paths(graph, node, end, path)
            print('Newpaths = ', newpaths)
            for newpath in newpaths:
                paths.append(newpath)
    print('Semua Path', paths)
    return paths

def find_shortest_path(graph, start, end, path=[]):
    path = path + [start]
    print('Path Awal =',path)
    if start == end:
        return path
    if start not in graph:
        return None
    shortest = None
    
    for node in graph[start]:
        print('Node sekarang %s dari Start %s'%(node,start))
        if node not in path:
            newpath = find_shortest_path(graph, node, end, path)
            print('Newpath = ', newpath)
            if newpath:
                if not shortest or len(newpath) < len(shortest):
                    shortest = newpath
    print('Path Terpendek = ',shortest)
    return shortest

def find_longest_path(graph, start, end, path=[]):
    path = path + [start]
    print('Path Awal',path)
    if start == end:
        return path
    if start not in graph:
        return None
    longest = None
    
    for node in graph[start]:
        print('Node sekarang %s dari Start %s'%(node,start))
        if node not in path:
            newpath = find_longest_path(graph, node, end, path)
            print('Newpath = ', newpath)
            if newpath:
                if not longest or len(newpath) > len(longest):
                    longest = newpath         
    print('Path Terpanjang = ',longest)
    return longest


graph = {'A' : ['B','C'],
         'B' : ['C','D'],
         'C' : ['D'],
         'D' : ['C'],
         'E' : ['F'],
         'F' : ['C']}
print('================ Mencari Path ===================')
print('hasil akhir', find_path(graph, 'A', 'C'))
print('================ Mencari Semua Path ===================')
print('hasil akhir semua path', find_all_paths(graph, 'A', 'C'))
print('================ Mencari Path Terpendek ===================')
print('hasil akhir path terpendek', find_shortest_path(graph, 'A', 'C'))
print('================ Mencari Path Terpanjang ===================')
print('hasil akhir path terpanjang', find_longest_path(graph, 'A', 'C'))

```



### Representasi Graph

Terdapat Beberapa Representasi untuk graph yaitu :

1. Adjacency List
2. Adjacency Matrix

### GRaph Traversal

*Graph Traversal* merupakan proses mengunjungi setiap *vertex*/*node* . *Graph Traversal* digunakan untuk mencari jalur dalam suatu *graph* dari titik asal ke titik tujuan, mencari jalur terpendek antara dua *node*/*vertex*, menemukan semua jalur yang bisa dilalui dari titik asal ke titik tujuan. 

Contoh :

```python
graph = {'a': ['b', 'd'],'b': ['a', 'd'], 'c': ['d'], 'd': ['a', 'b', 'c']}
def find_path(graph, start, end, path=[]):
    path = path + [start]
    for node in graph[start]:
        if not node in path:
            newpath = find_path(graph, node, end, path)
            if newpath:
                return newpath
    if start == end:
        return path
    if not start in graph:
        return None
    return None

print(find_path(graph,'a','d'))

```



