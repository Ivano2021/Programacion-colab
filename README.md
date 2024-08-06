import pandas as pd
import matplotlib.pyplot as plt
from google.colab import files

# Pedir al usuario que cargue el archivo Excel
print("Por favor, carga tu archivo Excel:")
uploaded = files.upload()

# Obtener el nombre del archivo cargado
file_name = list(uploaded.keys())[0]

# Cargar el archivo Excel en un DataFrame
df = pd.read_excel(file_name)

# Convertir la columna 'FECHA' a tipo datetime
df['FECHA'] = pd.to_datetime(df['FECHA'])

# Ordenar el DataFrame por la columna 'FECHA'
df = df.sort_values(by='FECHA')

# Gráficos
plt.figure(figsize=(12, 6))

# Gráfico de DO
plt.subplot(3, 1, 1)
plt.plot(df['FECHA'], df['DO'], marker='o', linestyle='-')
plt.title('DO')
plt.xlabel('Fecha')
plt.ylabel('ABS')

# Gráfico de Abundancia
plt.subplot(3, 1, 2)
plt.plot(df['FECHA'], df['ABUNDANCIA'], marker='o', linestyle='-')
plt.title('Abundancia')
plt.xlabel('Fecha')
plt.ylabel('CELS/ML')

# Gráfico de Fosfato
plt.subplot(3, 1, 3)
plt.plot(df['FECHA'], df['FOSFATO'], marker='o', linestyle='-')
plt.title('Fosfato')
plt.xlabel('Fecha')
plt.ylabel('PO4')

# Ajustes de diseño
plt.tight_layout()
plt.show()
