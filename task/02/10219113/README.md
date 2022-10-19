# 10219113
Kemal Rizky Fadhlurrohman


## materi sebelumnya
+ Metode Euler
+ Metode Runge-Kutta orde 4
+ Penyelesaian Persamaan ODE (Ordinary Differential Equation)
+ Lotka-Volterra Model
+ Heat Difussion Model
+ Osilasi (Underdamped, Overdamped, Critically Damped)
+ Osilasi Terkopel
+ Transformasi Fourier
+ Monter Carlo


## materi paling menarik
+ Penyelesaian persamaan diferensial untuk kasus osilasi, karena terdapat banyak aplikasi dari model osilasi ini dan ada beberapa kasus khusus osilasi yang menarik.


## materi paling membosankan
+ Model lotka-volterra, karena saya belum memahami aplikasinya.


## materi yang sudah dipami
+ Penyelesaian persamaan diferensial menggunakan metode euler dan runge kutta.
+ Heat diffusion model
+ Monte Carlo


## materi yang belum dipahami
+ Penyelesaian model osilasi terkopel.
+ Fourier transform
+ Aplikasi dari model lotka-volterra

## contoh program

```python
# Contoh Program Penyelesaian Numerik untuk Kasus Osilasi Teredam
import numpy as np
import matplotlib.pyplot as plt

# Define runge kutta method
def integrate(F,x,y,x_stop,h):

  def rk4(F,x,y,h):
    K0 = h*F(x,y)
    K1 = h*F(x + h/2.0, y + K0/2.0)
    K2 = h*F(x + h/2.0, y + K1/2.0)
    K3 = h*F(x +h, y + K2)
    return (K0 + 2.0*K1 + 2.0*K2 + K3)/6.0

  X = []
  Y = []
  X.append(x)
  Y.append(y)
  while x < x_stop:
    h = min(h,x_stop - x)
    y = y + rk4(F,x,y,h)
    x = x + h
    X.append(x)
    Y.append(y)
  return np.array(X),np.array(Y)

# Input data
m = 10.0
ko = 4.0
c = 2.0

# Persamaan diferensial biasa sistem pegas teredam
def F(x,y):
  F = np.zeros(2)
  F[0] = y[1]
  F[1] = -(ko/m)*y[0]-(c/m)*y[1]
  return F

t = 0.0 #Mulai menghitung
t_stop = 50 #Selesai menghitung
y = np.array([0.1,0.1]) #Kondisi awal (y)
delta_t = 0.1 #Step size

# Solusi numerik menggunakan Runge-Kutta orde4
X,Y = integrate(F,t,y,t_stop,delta_t)

# Memplot nilai solusi numerik
plt.subplot(2,1,1)
plt.plot(Y[:,0],Y[:,1],'-')
plt.title('Diagram Fase Sistem Pegas Teredam')
plt.xlabel('X');plt.ylabel('Y')
plt.grid(True)

plt.subplot(2,1,2)
plt.plot(X,Y[:,0],'o-',X,Y[:,1],'s-')
plt.title('Time Series Sistem Pegas Teredam')
plt.xlabel('Waktu t');plt.ylabel('Dinamika')
plt.legend(('x','y'),loc=0)
plt.grid(True)

plt.tight_layout()

```

Hasilnya adalah

<a href="https://imgbb.com/"><img src="https://i.ibb.co/n7t3HPT/output-onlinepngtools.png" alt="output-onlinepngtools" border="0"></a>

## cara perkuliahan
+ Cara kuliah sampai saat ini menggabungkan penjelasan teori dan metode hands on, namun masih lebih condong ke penjelasan teori karena keterbatasan ruangan. Metode kuliah yang menjadi 
preferensi saya adalah metode hands on dengan langsung mengaplikasikan teori yang dijelaskan di kelas dalam bentuk coding.


## topik sistem fisis
+ Sistem partikel yang bergerak secara GLBB akibat suatu gaya tertentu. Menarik karena banyak aplikasinya dalam image processing.


## simulasi dan visualisasi
+ Simulasi dan visualisasi gerakan sistem granular yang dipengaruhi oleh medan gaya tertentu
