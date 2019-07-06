# Rekursif

### A.Definisi

Fungsi rekursif dalam pemrograman merupakan fungsi yang memanggil dirinya sendiri. Fungsi rekursif sering saya bayangkan seperti perulangan. Karena tingkah lakunya yang mengulang-ulang setiap pemanggilan dirinya.

### Iteratif

Iteratif merupakan penyelesaian permasalahan dengan perulangan, menggunakan syntax `for` atau `while` (pada Python). 

Contoh :

Berikut adalah code untuk perhitungan faktorial suatu bilangan dengan menggunakan cara iteratif. 
Pada code ini, terdapat iterasi while, yang menghitung perkalian, mulai dari n*n*, sampai dengan 2.

```python
#Cara Iteratif
def factorialIteratif(bilangan):
    if bilangan <=1:
        return(1)
    else:
        temp=bilangan
        hasil=1
        while temp>1:
            hasil=hasil*temp
            temp=temp-1
        return(hasil)
 print(factorialIteratif(4))
```

Rekursif merupakan suatu teknik pemrograman yang memecah permasalahan menjadi permasalahan dengan ukuran yang lebih kecil dan lebih kecil lagi, sehingga permasalahan dengan ukuran kecil tersebut dapat dengan mudah dipecahkan. Teknik ini dapat dilakukan dengan cara memanggil fungsi itu sendiri seperti definisi diatas. 

```python
#Cara Rekursif
def factorialRekursif(bilangan):
    if bilangan <=1:
        return(1)
    else:
        return(bilangan * factorialRekursif(bilangan-1))
data=factorialRekursif(4)
print(data)      
```

Dari Fungsi tersubut terlihat beberapa perbedaan, dapat disimak bahwa teknik rekursif ini melibatkan pemaggilan fungsinya sendiri, dengan parameter yang berukuran lebih kecil. adapun aturan dalam teknik rekursif :

- Fungsi rekursif harus memiliki *base case*, *base case* inilah yang berfungsi untuk menghentikan pemanggilan terus menerus fungsi rekursif
- fungsi rekursif harus memiliki sintaks yang dapat merubah state dari permasalahan, sehingga semakin lama solusi permasalahan menuju *base case* yang sudah dibuat
- Fungsi rekursif harus memanggil dirinya sendiri

### B. Code

Contoh :

Berikut fungsi rekursif untuk konversi bilangan desimal menjadi bilangan base yang lain.

```python
def konversiDesimal(bilangan,base):
    charBilangan='0123456789ABCDEF'
    if bilangan<base:
        return(charBilangan[bilangan])
    else:
        temp=bilangan//base
        ind=bilangan % base
        print(type(temp),temp,type(ind),ind)
        return(konversiDesimal(temp,base)+charBilangan[ind])
 konversiDesimal(5,2)
```

### Visualisasi Rekursif

### Fractal

Fractal merupakan cabang matematika dan memiliki banyak kesamaan dengan teknik rekursif. Fraktal memiliki bentuk dasar, dan bentuk dasar ini dikembangkan secara berulang terus menerus.

Contoh :

```python
import turtle
def draw_triangle(points, color, my_turtle):   
    my_turtle.speed('slowest')
    my_turtle.fillcolor(color)
    my_turtle.up()
    my_turtle.goto(points[0][0],points[0][1])
    my_turtle.down()
    my_turtle.begin_fill()
    my_turtle.goto(points[1][0], points[1][1])
    my_turtle.goto(points[2][0], points[2][1])
    my_turtle.goto(points[0][0], points[0][1])
    my_turtle.end_fill()
def get_mid(p1, p2):
    return ((p1[0] + p2[0]) / 2, (p1[1] + p2[1]) / 2)
def sierpinski(points, degree, my_turtle):
    color_map = ["blue", "red" , "green", "white" , "yellow" ,"violet" , "orange"]
    draw_triangle(points, color_map[degree], my_turtle)
    if degree > 0:
        sierpinski([points[0],get_mid(points[0], points[1]), get_mid(points[0], points[2])], degree-1, my_turtle)
        sierpinski([points[1],get_mid(points[0], points[1]), get_mid(points[1], points[2])], degree-1, my_turtle)
        sierpinski([points[2],get_mid(points[2], points[1]), get_mid(points[0], points[2])], degree-1, my_turtle)

def main():
    my_turtle = turtle.Turtle()
    my_win = turtle.Screen()
    my_points = [[-100, -50], [0, 100], [100, -50]]
    sierpinski(my_points, 2, my_turtle)
    my_win.exitonclick()

main()
```

### Latihan Praktikum

1.

```python
import turtle
my_turtle = turtle.Turtle()
my_win = turtle.Screen()

def draw_square(my_turtle, line_len,a,banyak_level,b):
    if b<banyak_level+1:
        if a<4:
            if line_len > 0:
                my_turtle.forward(line_len/2)
                my_turtle.right(90)
                my_turtle.forward(line_len)
                my_turtle.right(90)
                my_turtle.forward(line_len/2)
                my_turtle.right(90)
                draw_square(my_turtle, line_len,a+1,banyak_level,b)
        else:
            draw_square(my_turtle, line_len/2,0,banyak_level,b+1)

draw_square(my_turtle, 200,0,6,0)
my_win.exitonclick()

```



![](C:\Users\Choirul\AppData\Local\Programs\Python\Python37-32\Scripts\struktur_data\docs\assets\images\Untitled.png)