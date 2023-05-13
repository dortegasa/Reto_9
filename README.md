# Reto_9
## 1. De los retos anteriores seleciones 3 funciones y escribalas en forma de lambdas.

### Primero:
```python
# Definimos funciones lambda para verificar si el número es positivo, negativo o cero
positivo = lambda x: print(f"El número {x} es positivo") if x > 0 else None
negativo = lambda x: print(f"El número {x} es negativo") if x < 0 else None
cero = lambda x: print(f"El número {x} es el neutro para la suma") if x == 0 else None
# Pedimos al usuario que ingrese un número real
x = float(input("Ingrese un número real: "))
# Llamamos a las funciones lambda para determinar si el número es positivo, negativo o cero
positivo(x)
negativo(x)
cero(x)
```
### Segundo:
```python
# Definimos una función lambda para calcular la distancia entre dos puntos en un plano
distancia = lambda x1, y1, x2, y2: ((x2 - x1)**2 + (y2 - y1)**2)**0.5
# Pedimos al usuario que ingrese las coordenadas del centro del círculo y el radio
xCentro= float(input("Ingrese la coordenada x del centro del círculo: "))
yCentro = float(input("Ingrese la coordenada y del centro del círculo: "))
radio = float(input("Ingrese el radio del círculo: "))
# Pedimos al usuario que ingrese las coordenadas del punto a verificar
xPunto = float(input("Ingrese la coordenada x del punto: "))
yPunto = float(input("Ingrese la coordenada y del punto: "))
# Calculamos la distancia entre el centro del círculo y el punto utilizando la función lambda
d = distancia(xCentro, yCentro, xPunto, yPunto)
# Verificamos si el punto pertenece al interior del círculo
if d < radio:
    print("El punto pertenece al interior del círculo")
else:
    print("El punto no pertenece al interior del círculo")
```

### Tercero:
```python
# Definimos una función lambda para verificar si se pueden construir un triángulo
triangulo = lambda a, b, c: a + b > c and a + c > b and b + c > a
# Solicitamos al usuario ingresar las tres longitudes
a = float(input("Ingrese la longitud del primer lado: "))
b = float(input("Ingrese la longitud del segundo lado: "))
c = float(input("Ingrese la longitud del tercer lado: "))
# Verificamos si se pueden construir un triángulo con las longitudes dadas utilizando la función lambda
if triangulo(a, b, c):
    print("Se puede construir un triángulo con las longitudes dadas")
else:
    print("No se puede construir un triángulo con las longitudes dadas")
```

## 2. De los retos anteriores seleciones 3 funciones y escribalas con argumentos no definidos (*args).

### Primero:
```python
def contagios_covid(*args):
    C = args[0]
    D = args[1:]
    # Calculamos la cantidad de personas contagiadas en cada día
    P = [C * (2 ** d) for d in D]   
    # Mostramos los resultados
    for i in range(len(D)):
        print(f"La cantidad de personas contagiadas en el día {D[i]} es: {P[i]}")
# Solicitamos al usuario que ingrese los valores de C y D
C = int(input("Ingrese el número de contagiados actuales: "))
D = [int(d) for d in input("Ingrese los días transcurridos separados por espacios: ").split()]
# Llamamos a la función con los valores ingresados por el usuario
contagios_covid(C, *D)
```

### Segundo:
```python
def CantidadCarne(*args):
    # Definimos los pesos de cada tipo de ave
    PesoGallina = 6
    PesoGallo = 7
    # Solicitamos al usuario la cantidad de cada tipo de ave
    N = int(input("Ingrese la cantidad de gallinas: "))
    M = int(input("Ingrese la cantidad de gallos: "))
    K = int(input("Ingrese la cantidad depollitos: "))
    # Calculamos la cantidad total de carne de aves en kilos
    TotalCarne = (N * PesoGallina) + (M * PesoGallo) + K
    # Devolvemos el resultado
    return TotalCarne
# Ejemplo de uso
print("Hay en total", CantidadCarne(), "kilos de carne.") 
```

### Tercero:
```python
def calcular_vueltas(*args):
    # Definimos los precios de cada producto
    precio_pan = 300
    precio_leche = 3300
    precio_huevo = 350
    # Solicitamos al usuario la cantidad de cada producto
    P = int(input("Ingrese la cantidad de panes: "))
    M = int(input("Ingrese la cantidad de bolsas de leche: "))
    H = int(input("Ingrese la cantidad de huevos: "))
    # Calculamos el total de la compra
    total = (P * precio_pan) + (M * precio_leche) + (H * precio_huevo)
    # Solicitamos al usuario el valor del billete
    B = int(input("Ingrese el valor del billete: "))
    # Calculamos las vueltas o la deuda
    vueltas = B - total
    # Devolvemos el resultado
    return vueltas
# Ejemplo de uso
print("Queda con un total de", calcular_vueltas())
```

## 3. Escriba una función recursiva para calcular la operación de la potencia.

```python
def PotenciaRecursiva(BaseNum: float, ExponenteNum: int):
    if ExponenteNum == 0:
        return 1
    elif ExponenteNum == 1:
        return BaseNum
    else:
        return BaseNum * PotenciaRecursiva(BaseNum, ExponenteNum - 1)
if __name__ == '__main__':
    base = float(input("Ingresa la base: "))
    exponente = int(input("Ingresa el exponente: "))
    resultado = PotenciaRecursiva(base, exponente)
    print(f"La potencia de {base} elevado a {exponente} es igual a {resultado}")
```

## 4. Utilice la siguiente plantilla de code para contar el tiempo:
```python
import time

start_time = time.time()
# instrucciones sobre las cuales se quiere medir tiempo de ejecución
end_time = time.time()

timer = end_time - start_time
print(timer)
```

### Codigo:

```python
import time

def fibonacci_iterative(n):
    if n < 2:
        return n
    a, b = 0, 1
    for i in range(2, n+1):
        a, b = b, a + b
    return b

def fibonacci_recursive(n):
    if n < 2:
        return n
    return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)

n = int(input("Ingrese un número para calcular la serie de Fibonacci: "))

start_time = time.time()
fib_iter = fibonacci_iterative(n)
end_time = time.time()

iter_timer = end_time - start_time

start_time = time.time()
fib_rec = fibonacci_recursive(n)
end_time = time.time()

rec_timer = end_time - start_time

print("El {}-ésimo número de Fibonacci con iteración es: {}".format(n, fib_iter))
print("El tiempo de ejecución con iteración es: {:.10f} segundos".format(iter_timer))

print("El {}-ésimo número de Fibonacci con recursión es: {}".format(n, fib_rec))
print("El tiempo de ejecución con recursión es: {:.10f} segundos".format(rec_timer))

if iter_timer > rec_timer:
    print("La función recursiva es más rápida para calcular la serie de Fibonacci a partir del {}-ésimo término.".format(n))
else:
    print("La función iterativa es más rápida para calcular la serie de Fibonacci a partir del {}-ésimo término.".format(n))
```

## 5. Cuenta en stackoverflow

[![stack.png](https://i.postimg.cc/59rKyGbD/stack.png)](https://postimg.cc/NL1kPdyx)

## 6. Cuenta de Linkedin

Enlace del perfil de Linkedin: [Perfil linkedin]([https://www.linkedin.com/in/david-alejandro-dortegasa-b67b10273/])
