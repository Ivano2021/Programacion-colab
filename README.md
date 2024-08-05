import pandas as pd
import matplotlib.pyplot as plt

# Creamos una lista vacía para almacenar los datos
lista_datos = []

# Definimos la función para ingresar los datos
def ingresar_datos():
    while True:
        try:
            dia = int(input("Ingrese el día de la medición: "))
            abundancia = float(input("Ingrese la abundancia de cianobacterias: "))
            biomasa = float(input("Ingrese la biomasa de cianobacterias: "))
            absorbancia = float(input("Ingrese la densidad óptica (absorbancia): "))
            break
        except ValueError:
            print("Error: Por favor, ingrese un número válido.")

    return dia, abundancia, biomasa, absorbancia

# Definimos la función para actualizar los datos y graficar
def actualizar_datos(dia, abundancia, biomasa, absorbancia):
    global lista_datos
    lista_datos.append({'Día': dia, 'Abundancia': abundancia, 'Biomasa': biomasa, 'Absorbancia': absorbancia})

    # Convertimos la lista de datos en un DataFrame
    datos = pd.DataFrame(lista_datos)

    # Graficamos la curva de crecimiento de abundancia
    plt.figure(figsize=(10, 6))
    plt.subplot(2, 2, 1)
    plt.plot(datos['Día'], datos['Abundancia'], marker='o', color='blue')
    plt.xlabel('Día')
    plt.ylabel('Abundancia de cianobacterias')
    plt.title('Curva de Crecimiento de Abundancia')

    # Graficamos la curva de crecimiento de biomasa
    plt.subplot(2, 2, 2)
    plt.plot(datos['Día'], datos['Biomasa'], marker='o', color='green')
    plt.xlabel('Día')
    plt.ylabel('Biomasa de cianobacterias')
    plt.title('Curva de Crecimiento de Biomasa')

    # Graficamos la curva de absorbancia
    plt.subplot(2, 2, 3)
    plt.plot(datos['Día'], datos['Absorbancia'], marker='o', color='red')
    plt.xlabel('Día')
    plt.ylabel('Absorbancia')
    plt.title('Curva de Absorbancia')

    plt.tight_layout()
    plt.show()

# Simulamos el ingreso de datos durante un periodo de 30 días
for dia in range(1, 31):
    print(f"\n--- Día {dia} ---")
    dia, abundancia, biomasa, absorbancia = ingresar_datos()
    actualizar_datos(dia, abundancia, biomasa, absorbancia)
