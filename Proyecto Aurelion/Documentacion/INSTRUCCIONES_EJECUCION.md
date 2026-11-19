# 📋 Instrucciones de Ejecución - Proyecto Aurelion

> **Sistema de Análisis de Ventas con Python**  
> **Autor:** Sofia Suppia  
> **Fecha:** Octubre 2025

---

## 🎯 Descripción del Proyecto

Este sistema analiza datos de ventas para identificar:
- 🏆 Clientes más valiosos (Análisis Pareto 80/20)
- 📉 Productos menos rentables
- 🌍 Distribución geográfica de ingresos
- 💰 Cálculo de ganancia bruta con margen del 30%

---

## 📋 Requisitos Previos

### **1. Python Instalado**
```bash
python --version
```
*Debe mostrar Python 3.8 o superior*

### **2. Librerías Requeridas**
```bash
pip install pandas numpy openpyxl
```

### **3. Archivos de Datos (Excel)**
- `Clientes.xlsx`
- `Productos.xlsx` 
- `Ventas.xlsx`
- `Detalle_ventas.xlsx`

---


## 🚀 Ejecución del Programa

### **Opción 1: Ejecución Directa (Recomendada)**

1. **Abrir PowerShell o Terminal**
2. **Navegar al directorio del proyecto:**
   ```powershell
   cd "C:\ruta\a\tu\proyecto"
   ```
3. **Ejecutar el programa:**
   ```powershell
   python main.py
   ```

### **Opción 2: Con Ruta Completa de Python**
```powershell
"C:/Users/TuUsuario/AppData/Local/Programs/Python/Python313/python.exe" main.py
```

---

## 📁 Configuración de Base de Datos

### **🔧 Cambiar Ruta de Acceso a la Base de Datos**

El programa busca automáticamente los archivos Excel en estas ubicaciones **en orden de prioridad**:

1. **Directorio actual** (donde está `main.py`)
2. **Carpeta `./BaseDatos`** 
3. **Carpeta `../BaseDatos`**
4. **Carpeta `BaseDatos` ubicada junto a `Proceso_Datos.py`**

### **Método 1: Editar el Código (Avanzado)**

Si necesitas cambiar las rutas, edita el archivo `Proceso_Datos.py`:

```python
# Líneas 12-18 en Proceso_Datos.py
RUTAS_POSIBLES = [
    '.',  # Directorio actual
    './BaseDatos',  # Subdirectorio BaseDatos
    '../BaseDatos',  # BaseDatos en directorio padre
    './MiCarpetaPersonalizada',  # ← AGREGA TU RUTA AQUÍ
    'C:/MiRutaCompleta/Datos',   # ← O UNA RUTA ABSOLUTA
]
```

### **Método 2: Organización de Archivos (Recomendado)**

**Opción A - Misma Carpeta:**
```
📁 Tu Proyecto/
├── main.py
├── Proceso_Datos.py
├── Analisis_Datos.py
├── Analisis_Recurrente.py
├── Clientes.xlsx      ← Archivos Excel aquí
├── Productos.xlsx
├── Ventas.xlsx
└── Detalle_ventas.xlsx
```

**Opción B - Carpeta BaseDatos:**
```
📁 Tu Proyecto/
├── main.py
├── Proceso_Datos.py
├── Analisis_Datos.py
├── Analisis_Recurrente.py
└── 📁 BaseDatos/
    ├── Clientes.xlsx
    ├── Productos.xlsx
    ├── Ventas.xlsx
    └── Detalle_ventas.xlsx
```

---

## ✅ Verificación de Funcionamiento

### **Resultado Esperado:**
```
--- INICIO DEL ANÁLISIS DE VENTAS ---
Iniciando carga y limpieza inicial de datos...
📁 Directorio actual: C:\tu\ruta\proyecto
✅ Archivos encontrados en: ./BaseDatos
📋 Archivos encontrados:
   ✅ clientes: ./BaseDatos\Clientes.xlsx
   ✅ productos: ./BaseDatos\Productos.xlsx
   ✅ ventas: ./BaseDatos\Ventas.xlsx
   ✅ detalle: ./BaseDatos\Detalle_ventas.xlsx
📖 Cargando ./BaseDatos\Clientes.xlsx...
   ✅ Clientes.xlsx cargado exitosamente (100 filas, 5 columnas)
...
=======================================================
               RESULTADOS DEL ANÁLISIS
=======================================================

--- 1. Clientes Pareto (Top 80% de Ingresos) ---
--- 2. 10 Productos Menos Rentables (Ganancia Bruta) ---
--- 3. Distribución de Ingresos por Ciudad ---

--- ANÁLISIS COMPLETADO EXITOSAMENTE ---
```

---

## 🚨 Solución de Problemas Comunes

### **Error: "No such file or directory"**

**Síntomas:**
```
¡ERROR! El programa no encuentra los archivos.
FileNotFoundError: [Errno 2] No such file or directory: 'Clientes.xlsx'
```

**Soluciones:**

1. **Verificar ubicación de archivos:**
   - Los 4 archivos Excel deben estar en la misma carpeta que `main.py`
   - O en una subcarpeta llamada `BaseDatos`

2. **Verificar directorio actual:**
   ```powershell
   pwd  # En PowerShell
   dir  # Para ver archivos en el directorio
   ```

3. **Copiar archivos al directorio correcto:**
   - Localiza tus archivos Excel
   - Cópialos a la carpeta del proyecto

### **Error: "ModuleNotFoundError"**

**Síntomas:**
```
ModuleNotFoundError: No module named 'pandas'
```

**Solución:**
```powershell
pip install pandas numpy openpyxl
```

### **Error: "ImportError"**

**Síntomas:**
```
ImportError: cannot import name 'analizar_clientes_pareto'
```

**Solución:**
- Asegúrate de que todos los archivos Python estén en la misma carpeta
- Verifica que no haya errores de sintaxis en los archivos

---

## 📊 Descripción de los Resultados

### **1. Análisis Pareto de Clientes**
- Identifica el 20% de clientes que generan el 80% de los ingresos
- Muestra nombre del cliente, monto total y porcentaje acumulado

### **2. Productos Menos Rentables**
- Lista los 10 productos con menor ganancia bruta
- Incluye categoría, ganancia total y unidades vendidas
- Usa la fórmula: `Ganancia = Importe - (Costo_Unitario × Cantidad)`

### **3. Distribución por Ciudad**
- Ranking de ciudades por ingresos totales
- Porcentaje de participación de cada ciudad

---

## 🔧 Metodología Implementada

### **Cálculo de Costo Unitario**
```
Costo_Unitario = Precio_Unitario / 1.30
```
*Asume un margen de ganancia bruta del 30%*

### **Cálculo de Ganancia Bruta**
```
Ganancia_Bruta = Importe - (Costo_Unitario × Cantidad)
```

### **Tecnologías Utilizadas**
- **Python 3.8+**: Lenguaje de programación
- **Pandas**: Manipulación de datos y análisis
- **NumPy**: Operaciones numéricas eficientes
- **OpenPyXL**: Lectura de archivos Excel

---

## 📞 Soporte Adicional

### **Para Desarrolladores:**
- Revisa `Documentacion_Completa.md` para detalles técnicos
- Consulta `pseudocodigo.md` para la lógica de algoritmos

### **Para Usuarios:**
- Asegúrate de tener los 4 archivos Excel correctos
- Verifica que Python y las librerías estén instalados
- Sigue las instrucciones paso a paso

### **Contacto:**
- **Autor:** Sofia Suppia
- **Proyecto:** Fundamentos de Inteligencia Artificial
- **Año:** 2025

---

*¡El análisis de ventas nunca fue tan fácil! 🚀*
dir
```
Deberías ver todos los archivos .xlsx listados.

### **4. Ejecutar el programa:**
```powershell
python main.py
```

## 📞 Si Sigues Teniendo Problemas:

El programa ahora muestra información de diagnóstico detallada:
- ✅ Archivos encontrados
- ❌ Archivos faltantes
- 📁 Directorio actual
- 💡 Soluciones específicas

**Copia y pega el mensaje completo de error para obtener ayuda específica.**

## 🎯 Resultado Esperado:

Si todo funciona correctamente, deberías ver:
```
--- INICIO DEL ANÁLISIS DE VENTAS ---
📁 Directorio actual: C:\tu\carpeta
📋 Archivos en el directorio:
   ✅ Clientes.xlsx
   ✅ Productos.xlsx
   ✅ Ventas.xlsx
   ✅ Detalle_ventas.xlsx
   ✅ ENCONTRADO: Clientes.xlsx
   ✅ ENCONTRADO: Productos.xlsx
   ✅ ENCONTRADO: Ventas.xlsx
   ✅ ENCONTRADO: Detalle_ventas.xlsx
✅ Todos los archivos están disponibles.
📖 Cargando Clientes.xlsx...
   ✅ Clientes.xlsx cargado exitosamente
...
=======================================================
               RESULTADOS DEL ANÁLISIS
=======================================================
```