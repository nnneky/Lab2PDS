# Laboratorio 2 PDS

## Introducción:
El procesamiento de señales utiliza herramientas clave como la convolución, que modela la interacción entre una señal y un sistema; la correlación, que mide la similitud entre señales; y la transformada, que permite analizar las señales en el dominio de la frecuencia. Estas técnicas, implementadas en Python, facilitan un análisis más profundo y práctico del tema.

## Requerimientos:
- Interfaz de python (para este caso 3.12)
- Numpy
- Matplotlib
- Scipy.io
- Scipy.interpolate
- libreria time
- IPython.display

##  Convolución:
La convolución es una operación que muestra cómo una señal interactúa con un sistema. En procesamiento de señales, se usa para calcular la salida de un sistema cuando se le aplica una entrada, ayudando a entender cómo el sistema afecta a la señal.

Para esta práctica, se implementaron dos métodos de convolución. El primero fue calculado y escrito a mano, como se muestra a continuación:

 ![Imagen de WhatsApp 2025-02-11 a las 19 24 51_c2fabe90](https://github.com/user-attachments/assets/cb486130-b8f4-4a3e-b66c-0c092e963774)

 Dentro de la imagen se puede observar el calculo de la convolución realizado como una multiplicación de polinomios, seguido de otro método el cual se basa en una serie de multiplicaciones tipo tabla, en ambos casos se llego al mismo resultado. Finalmente al inferior de la página se encuentra la gráfica manual de la señal (1)  y del sistema (1) correspondientes al primer estudiante.

   ![Imagen de WhatsApp 2025-02-11 a las 19 24 51_1086e93e](https://github.com/user-attachments/assets/0fef8329-2bdc-4be2-8e71-57712c34014b)

 La imagen demuestra el resultado de la convolución entre el sistema y la señal del primer caso.

Para el caso del segundo estudiante se realizo el mismo proceso pero solo implementando el método tipo tabla, al igual que en el anteriormente se gráfica la señal (2) y el sistema (2)

   ![Imagen de WhatsApp 2025-02-11 a las 19 45 19_f2f5c492](https://github.com/user-attachments/assets/526e70f3-d48f-4f2c-a92b-99d074c8d801)

finalmente se gráfica la convolución entre la señal y el sistema obteniendo lo siguiente:

 ![Imagen de WhatsApp 2025-02-11 a las 19 45 34_76ac0a06](https://github.com/user-attachments/assets/1f3d4c34-d7fb-4c89-ac60-844f8dc834ad)

como segundo método propuesto por la guía, se realizo la convolución mediante funciones en phython,ademas de obtener una secuencia de la misma en cada caso.

La programación de lo enunciado es la siguiente: 

```bash
 
h = np.array([5,6,0,0,7,7,8]) #Señal de entrada [Código de estudiante] se crea un arreglo de valores para ambos casos
x = np.array([1,0,7,6,2,4,2,2,3,7]) #Señal de salida [C.C]

p = np.array([5,6,0,0,7,8,6]) ## al igual que arriba, se crea un arreglo de valores 
i = np.array([1,0,2,7,1,5,1,0,7,8])

#Se calcula la convolución.
y = np.convolve(h, x) ## mediante una función de numpy se calcula la convolución y se almacena en una variable
yy=  np.convolve(p, i)

#Índices de señales.
npx = np.arange(len(p)) ## Genera un arreglo de índices desde 0 hasta el tamaño de p -1 , utilizado para graficar p.
ni = np.arange(len(i)) ##  Genera los índices de la señal i (obtiene la cantidad de elementos de la señal - 1)
nyy = np.arange(len(yy)) ## genera un arreglo con tamaño yy-1

## mismo proceso que la señal anterior
nh = np.arange(len(h)) 
nx = np.arange(len(x))
ny = np.arange(len(y))
```

Luego se gráfica cada elemento de la siguiente forma:

```bash

## gráfico del primer sistema
plt.figure(figsize=(10, 4),facecolor='linen') ## se crea una figura del tamaño deseado 

plt.plot(nh, h, color='maroon') ## se definen las variables que deberá gráficar cada eje y el color seleccionado
plt.title('Señal h[n]  |Código Daniel|',color='darkslategray') ## titulo del gráfico
plt.xlabel('n' , color='darkslategray') ## titulo del eje x
plt.ylabel('Amplitud', color='darkslategray') ## titulo del eje y 
plt.grid () 
plt.show() ## mostrar la figura 

## gráfico de la primera señal, se realiza de la misma forma que la primera figura

plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(nx, x, color='maroon')
plt.title('Señal x[n]  |C.C Daniel|',color='darkslategray')
plt.xlabel('n',color='darkslategray')
plt.ylabel('Amplitud',color='darkslategray')
plt.grid ()
plt.show()  

## gráfico de la primera convolución, se realiza de la misma forma que la primera figura
plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(ny, y, color='maroon')
plt.title('Señal y[n]=h[n] * x[n]  |Daniel|',color='darkslategray')
plt.xlabel('n',color='darkslategray')
plt.ylabel('Amplitud',color='darkslategray')
plt.grid ()
plt.show()

## gráfico del segundo sistema, se realiza de la misma forma que la primera figura
plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(npx, p, color='maroon')
plt.title('Señal p[n]  |Código Isabel|',color='darkslategray')
plt.xlabel('n' , color='darkslategray')
plt.ylabel('Amplitud', color='darkslategray')
plt.grid ()
plt.show() 

## gráfico de la segunda señal, se realiza de la misma forma que la primera figura
plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(ni, i, color='maroon')
plt.title('Señal i[n]  |C.C Isabel|',color='darkslategray')
plt.xlabel('n',color='darkslategray')
plt.ylabel('Amplitud',color='darkslategray')
plt.grid ()
plt.show()  

## gráfico de la segunda convolución, se realiza de la misma forma que la primera figura
plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(nyy, yy, color='maroon')
plt.title('Señal yy[n]=h[n] * x[n]  |Isabel|',color='darkslategray')
plt.xlabel('n',color='darkslategray')
plt.ylabel('Amplitud',color='darkslategray')
plt.grid ()
plt.show()
```

# Gráficas de las convuluciones:

- Usando los datos de Daniel

![image](https://github.com/user-attachments/assets/fa5739ee-a46f-4c27-970c-6cf9b5ae0564)

![image](https://github.com/user-attachments/assets/624def76-bd5a-4be6-af28-40e18098d9fe)

![image](https://github.com/user-attachments/assets/ab6a1bf6-cf92-45be-a710-07b209f31f20)

- Usando los datos de Isabel

![image](https://github.com/user-attachments/assets/249231fd-f6ab-4b7e-8f10-0cb9e0a86e76)

![image](https://github.com/user-attachments/assets/5a3d5b70-ba0d-4213-8c31-b335a684d813)

![image](https://github.com/user-attachments/assets/b3fc2cbd-7c5b-45b2-8498-57e572f8a2d3)

Estas convoluciones muestran cómo la señal x[n] es filtrada o transformada por el sistema descrito por h[n], lo que tiene aplicaciones en procesamiento de señales, como filtrado, detección de patrones y análisis de sistemas.

## Animar las convoluciones de forma secuencial:

Para este indice de la guía se realizo una función que crea secuencialmente una serie de gráficos que ejemplifican el proceso de convolución, esto se realizo de la siguiente forma:
```bash
def animar_convolucion(x_signal, c_signal, y_signal, titulo): ## se crea una función con parametros necesarios (señal,sistema,resultado de la convolución y el tiyulo deseado)
    len_x = len(x_signal) ## aquí definimos el tamaño de cada componente basandonos en los datos de estrada de la función para todos los casos
    len_c = len(c_signal)
    len_y = len(y_signal)
    plt.figure(figsize=(10, 6)) ## se crea una figura de tamaño deseado

    for i in range(len_y): ## Se inicia un bucle que recorre cada muestra de la señal convolucionada para este caso y[n]
        plt.clf() ## borra la gráfica anterior para actualizarla en cada paso.

        # Graficar x[n]
        plt.subplot(3, 1, 1) ## Primera subgráfica de 3 filas.
        plt.stem(np.arange(len_x), x_signal, linefmt='b-', markerfmt='bo', basefmt="black") ## Gráfica de señal discreta x [n] con parametros de color 
        plt.title(f"{titulo} - Señal de Entrada x[n]") ## titulo de esa zona de la animación
        plt.xlabel("n") ## eje x
        plt.grid()

        # Graficar c[n] desplazado correctamente
        plt.subplot(3, 1, 2) ## segunda subgráfica
        ## Se calcula el desplazamiento de h[n] para simular el proceso de convolución:
        inicio = max(0, i - len_c + 1)  # Controla el desplazamiento del sistema (cuanto se debe desplazar h[n])
        desplazamiento = np.zeros(inicio) ## Agrega ceros al inicio del sistema.
        c_desplazado = np.concatenate([desplazamiento, c_signal])[:i+1] ## Ajusta la longitud del sistema en cada iteración. concatenando los valores de la señal con los ceros, lo que quiere decir que se va desplazando agregando ceros a la izquierda
        plt.stem(np.arange(i+1), c_desplazado, linefmt='r-', markerfmt='ro', basefmt="black") ## ayuda a gráficar la señal desplazada 
        plt.title(f"{titulo} - Sistema c[n] desplazado (Paso {i+1})") ## titulo del sub gráfico
        plt.xlabel("n")
        plt.grid() ## añade una rejilla para la figura 

        # Graficar y[n] acumulado correctamente
        plt.subplot(3, 1, 3) ## tercer subgráfico
        plt.stem(np.arange(i + 1), y_signal[:i + 1], linefmt='g-', markerfmt='go', basefmt="black") ## se muestra la señal acomulando valores por cada vez
        plt.title(f"{titulo} - Salida y[n] acumulada")
        plt.xlabel("n")
        plt.grid()

        plt.tight_layout()
        
        # Mostrar la animación correctamente
        clear_output(wait=True)  # Borra la gráfica anterior
        display(plt.gcf())  # Muestra la nueva gráfica
        time.sleep(0.3)  # Pausa breve para animación fluida

    # Limpiar la última iteración
    clear_output(wait=True)

# -------------------- ANIMACIÓN PARA DANIEL --------------------
animar_convolucion(h, x, y, "Convolución Daniel")  ## envia los parametros a la función 

# -------------------- ANIMACIÓN PARA ISABEL --------------------
animar_convolucion(p, i, yy, "Convolución Isabel")

```
A continuación mostraremos algunas de las imagenes mostradas por la secuencia gráfica generada, por cuestón de extención del repositorio no las enunciaremos todas, ya que son bastantes, al compilar el código se podra observar de forma más clara.Para ambas convoluciones se relizó el procedimiento pero  aquí expondremos solo fragmentos del primer resultado:

#### primera imagen de la secuencia gráfica:

![image](https://github.com/user-attachments/assets/5576c1c5-784a-42a6-8239-66c7d223feb7)



#### Avance de la secuencia


![image](https://github.com/user-attachments/assets/af481f50-bca8-4595-b144-24d85e919b1a)



![image](https://github.com/user-attachments/assets/220ca855-6d86-4319-98b0-7e876aa08b2e)




![image](https://github.com/user-attachments/assets/dd2a58dc-bc26-49eb-bfc6-8c95dcc139dd)



#### Final de la secuencia


![image](https://github.com/user-attachments/assets/a3a71928-9aed-4f40-b2d5-e21be0165457)

## Correlación

La correlación entre dos señales mide el grado de similitud o relación entre ellas en diferentes desplazamientos en el tiempo. Es una herramienta fundamental en el procesamiento de señales para encontrar patrones, alineaciones o detectar señales en presencia de ruido.

En marco a lo propuesto en la práctica se realizo una correlación cruzada la cual es la correlación entre dos señales diferentes y Se usa para medir cuánto se parecen dos señales en diferentes instantes de tiempo.

Lo anterior se realizó con el sigueinte código en phyton:

```bash
# Definimos parámetros
Fs = 1 / (1.25e-3)  # Frecuencia de muestreo = 1 / Ts de finido por la guía 
Ts = 1 / Fs         # Periodo de muestreo
f = 100             # Frecuencia de la señal
n = np.arange(0, 9) # Valores de n

# Definimos las señales estipuladas en la guía entre ambas presentan un desface de pi/2
x1 = np.cos(2 * np.pi * f * n * Ts) 
x2 = np.sin(2 * np.pi * f * n * Ts)

# Calculamos la correlación cruzada
correlacion = np.correlate(x1, x2, mode="full") ## mediante una función de numpy se cálcula la correlación , se usa full para que se devuelvan todos las posibles alineaciones de x1 y x2 
lags = np.arange(-len(x1) + 1, len(x1)) ## Crea los valores de desplazamiento (lags) correspondientes a la correlación, representa los distintos desplazamientos con los que x1 y x2 se comparan en la correlación.

# GRAFICAMOS LAS SEÑALES 
plt.figure(figsize=(12, 6)) 
# Gráfico de x1[n]
plt.subplot(3, 1, 1) ## primer subgráfico
plt.stem(n, x1, linefmt='b-', markerfmt='bo', basefmt="black", label="x1[n] = cos(2π100nTs)") ## se gráfica la primera señal
plt.xlabel("n")
plt.ylabel("Amplitud")
plt.title("Señal x1[n]")
plt.grid()
plt.legend()

# Gráfico de x2[n]
plt.subplot(3, 1, 2) ## segundo subgráfico
plt.stem(n, x2, linefmt='r-', markerfmt='ro', basefmt="black", label="x2[n] = sin(2π100nTs)") ## se gráfica la segunda señal
plt.xlabel("n")
plt.ylabel("Amplitud")
plt.title("Señal x2[n]")
plt.grid()
plt.legend()

# Gráfico de la correlación
plt.subplot(3, 1, 3) ## tercer subgráfico
plt.stem(lags, correlacion, linefmt='g-', markerfmt='go', basefmt="black", label="Correlación x1[n] y x2[n]") ## se gráfica la correlación
plt.xlabel("Desplazamiento (lags)")
plt.ylabel("Amplitud")
plt.title("Correlación Cruzada entre x1[n] y x2[n]")
plt.grid()
plt.legend()

plt.tight_layout()
plt.show()

# Imprimir resultados
print("Valores de la correlación cruzada:") ## imprime valor a valor de la correlación 
print(correlacion)
```

![image](https://github.com/user-attachments/assets/91fbd1ef-a42c-4fcd-8997-957fc3c13038)

El análisis de correlación entre x1 [n] y x2 [n] muestra que son ondas sinusoidales ortogonales, es decir, están desfasadas 90° (π/2 radianes). Cuando no hay desplazamiento (lag=0), la correlación es cercana a cero, lo que confirma que están desfasadas. Sin embargo, al mover una de las señales en el tiempo, su similitud aumenta, alcanzando valores altos y bajos en ciertos desplazamientos.

## Señal electromiográfica de Physionet
Se eligió la señal EMG "emg_healthym" con duración de 10segundos en  PhysioNet, y se descargaron los archivos .info y .mat para su análisis. La electromiografía se tomó de un paciente masculino de 44 años sin antecedentes de enfermedad neuromuscular siendo así una EMG de electrodo de aguja concéntrico de 25 mm colocado en el músculo tibial anterior
El paciente dorsiflexionó el pie suavemente contra resistencia y luego lo relajó, todo esto se sabe gracias a la información que nos proporciona la pagina de Physionet.

- A continuación se muestran las librerias y el código implementado para la adecuación de la señal basado en los parametros descritos en el archivo .info descargado:

```bash
import matplotlib.pyplot as plt ## Crear gráficos y visualizaciones
import numpy as np  ## Manejo de arreglos y cálculos numéricos
from scipy.io import loadmat  ## Cargar archivos .mat 
from scipy.interpolate import make_interp_spline ## Interpolación y suavización de curvas
from scipy.signal import welch # Permite calcular y gráficar la densidad espectral

x=loadmat('emg_healthym.mat')  # ajuste de los valores segun el archivo .info
emg =np.transpose(emg) # transpone el vector de columnas a filas
emg = emg.squeeze() # Arregla las dimensiones en tamaño de la señal
fs =4000 # frecuencia de muestreo
tm =1/fs # tiempo entre muestras

````

- Así se calcularon los estadisticos descriptivos de la señal:

```bash
# Calcular la media aritmética manualmente
n = emg.size

if n > 1:
    suma = 0.0
    for x in emg:
        suma += x
    media = suma / n

# Calcular la desviación estándar manualmente
    suma1 = 0.0
    for x in emg:
        suma1 += (x - media) ** 2
    desvi = (suma1 / (n - 1)) ** 0.5  
else:
    media = float('error al calcular')
    desvi = float('error al calcular')

# Estadísticos calculados por medio de funciones
mediac = np.mean(emg)
desviacionc = np.std(emg, ddof=1) 

## coeficiente de variación calculado

coefi= desvi/media 

## coeficiente de variación con los valores de las funciones

coefi1= desviacionc/mediac

print(f"\nMedia calculada: {media}\n")
print(f"Desviación estándar calculada: {desvi}\n")
print(f"coeficiente de variación calculado: {coefi}\n")
print(f"Media por funciones: {mediac}\n")
print(f"Desviación estándar por funciones: {desviacionc}\n")
print(f"coeficiente de variación con valores de las funciones: {coefi1}\n")
```
- Así se graficó la señal EMG en función del tiempo:
  
```bash
#Graficamos la señal con respecto al tiempo:
tiempo=np.linspace(0,desviacionc,len(emg))
plt.figure(figsize=(10,4),facecolor='linen')
plt.plot(tiempo, emg, label="Señal en el tiempo",color='indianred')
plt.xlabel("Tiempo (s)", color='darkslategray')
plt.ylabel("Amplitud" , color='darkslategray')
plt.title("Señal en el Dominio del Tiempo", color='darkslategray')
plt.legend()
plt.grid()
plt.show()
```
- Gráfica señal Electromiográfica:

![image](https://github.com/user-attachments/assets/59ef6c41-4334-4a81-a468-ddda7aca18d7)



## Transformada de Fourier: 
La Transformada de Fourier descompone una señal en sus componentes de frecuencia, permitiendo su análisis en el dominio de la frecuencia y así se analizó con la señal EMG.

```bash
#Se cre la transformada de Fourier
N = len(emg) # Donde N es la cantidad de muestras de la señal.
frecuencias = np.fft.fftfreq(N, d=1/fs)  # a partir de la funcion ftt se calculan las frecuencias asociadas
trs_magnitud = np.abs(np.fft.fft(emg)) # np.fft.fft es una función que calcula la FFT de la señal EMG, obteniendo un arreglo complejo con información de amplitud y fase y np.abs decarta la oarte imaginaria.

#Se grafica la transformada de Fourier con respecto a la señal EMG
plt.figure(figsize=(10, 4),facecolor='linen')
plt.plot(frecuencias, trs_magnitud, label="Magnitud de la Transformada de fourier",color='indianred')
plt.xlabel("Frecuencia [Hz]", color='darkslategray')
plt.ylabel("Magnitud" , color='darkslategray')
plt.title("Transformada de Fourier de la Señal", color='darkslategray')
plt.grid()
plt.legend()
plt.show()
```

- Gráfica de la transformada de Fourier:

![image](https://github.com/user-attachments/assets/be47a9f8-5493-4b0b-af09-462cb59381f0)

## Densidad espectral:

La densidad espectral se puede definir cómo  se distribuye la potencia o energía de una señal en el dominio de la frecuencia, aplicando en Python se realizó de la siguiente manera.
```bash
frecuen_psd, psd= welch(emg, fs, nperseg=(4000)) # la función  nperseg=4000 define el numero de puntos en cada segmento de la señal antes de calcular la tff.
plt.figure(figsize=(10, 4),facecolor='linen')
plt.semilogy(frecuen_psd, psd,label="Densidad Espectral",color='indianred' ) #eta linea graficas la desnidad espectral en escala logarítmica en el eje y para que se aprecie con amyor "nitidez"
plt.xlabel("Frecuencia [Hz]", color='darkslategray')
plt.ylabel("Densidad de potencia" , color='darkslategray')
plt.title("Densidad Espectral de la señal", color='darkslategray')
plt.legend()
plt.show()
```
- Gráfica densidad espectral:

  ![image](https://github.com/user-attachments/assets/3baf40d8-9243-4bf7-bd9e-38ada01d31e3)


## Estadisticos en función de la frecuencia:
En el dominio de la frecuencia los estadisticos tales como la media, la mediana y la desviación estandar se calcularon de la siguiente manera:

```bash
especpot= trs_magnitud **2  # Calcula la potencia espectral
ptotal= np.sum(especpot) # 2Calcula la potencia total del espectro

medfreq= np.sum(frecuencias * especpot) / ptotal  # Esta línea calcula la frecuencia media que representa el centro de masa del espectro de potencia
medianafreq= frecuencias[np.searchsorted(np.cumsum(especpot), ptotal/2)] # la funciónnp.cumsum Calcula la suma acumulativa de la potencia espectral y la función np.searchsorted encuentra el índice donde la suma acumulada alcanza el 50% de la potencia total.              
desvifreq= np.sqrt(np.sum((frecuencias - medfreq)**2*especpot)/ptotal) # esta  parte calcula la desviación estándar espectral.  a partir de raíz cuadrada            

print("Estadísticos con Frecuencia:")
print(f"Media: {medfreq}")
print(f"Mediana: {medianafreq}")
print(f"Desvación estándar: {desvifreq}")

```

- Estadisticos de frecuencia:

  ![image](https://github.com/user-attachments/assets/2fe4101a-5f95-4488-a977-8de9e557dbae)


  ## Histograma de frecuencias

Para la construcción del histograma se realizó mediante funciones, como se muestra a continuación:

  ```bash 
plt.figure(figsize=(10, 4), facecolor='beige') ## se crea una figura de tamaño y color deseado
plt.hist(frecuencias[:N//2], bins=50, weights=trs_magnitud[:N//2], color='coral', alpha=0.7, edgecolor='maroon') ## dibuja un histograma a partir de los datos a partir de las frecuencias positivas generadas por la transformada, weights=trs_magnitud[:N//2]=Pondera el histograma con los valores de magnitud de la FFT, para que cada barra refleje cuánta energía hay en cada frecuencia.
plt.xlabel("Frecuencia [Hz]", color='red')
plt.ylabel("Magnitud", color='red')
plt.title("Histograma de Frecuencias de la Transformada de Fourier", color='red')
plt.grid()
plt.show()
  ```
A continuación se muestra el resultado del histograma:



