# Base de datos de ejemplo con medicamentos
medicamentos_db = {
    "12345": {"nombre": "Paracetamol", "uso": "Analgésico", "dosis": "500mg", "efectos_secundarios": "Náuseas, mareo"},
    "54321": {"nombre": "Ibuprofeno", "uso": "Antiinflamatorio", "dosis": "200mg", "efectos_secundarios": "Dolor de cabeza, mareo"},
    "67890": {"nombre": "Amoxicilina", "uso": "Antibiótico", "dosis": "500mg", "efectos_secundarios": "Reacciones alérgicas, diarrea"},
}

# Función para buscar medicamento por código o nombre
def buscar_medicamento(entrada):
    for codigo, info in medicamentos_db.items():
        if entrada == codigo or entrada.lower() == info["nombre"].lower():
            return f"Medicamento encontrado:\nCódigo: {codigo}\nNombre: {info['nombre']}\nUso: {info['uso']}\nDosis: {info['dosis']}\nEfectos secundarios: {info['efectos_secundarios']}"
    
    return "Medicamento no encontrado."

# Ejemplo de uso
entrada = input("Ingresa el código o nombre del medicamento: ")
resultado = buscar_medicamento(entrada)
print(resultado)



# Definir los colores principales
colores = {
    "primario": "#3498db",  # Azul
    "secundario": "#2ecc71",  # Verde
    "terciario": "#e74c3c",  # Rojo
    "fondo": "#f4f4f4",  # Gris claro
    "texto_principal": "#2c3e50",  # Gris oscuro
    "texto_secundario": "#95a5a6"  # Gris claro
}

# Función para generar el archivo CSS
def generar_css(colores):
    css = f"""
    /* Estilos generados automáticamente */
    :root {{
        --color-primario: {colores['primario']};
        --color-secundario: {colores['secundario']};
        --color-terciario: {colores['terciario']};
        --color-fondo: {colores['fondo']};
        --color-texto-principal: {colores['texto_principal']};
        --color-texto-secundario: {colores['texto_secundario']};
    }}

    body {{
        background-color: var(--color-fondo);
        color: var(--color-texto-principal);
        font-family: Arial, sans-serif;
    }}

    h1, h2, h3 {{
        color: var(--color-primario);
    }}

    p {{
        color: var(--color-texto-secundario);
    }}

    a {{
        color: var(--color-secundario);
    }}

    .btn {{
        background-color: var(--color-primario);
        color: white;
        padding: 10px 20px;
        border: none;
        cursor: pointer;
    }}

    .btn:hover {{
        background-color: var(--color-secundario);
    }}
    """
    
    # Escribir el archivo CSS
    with open("estilos.css", "w") as archivo_css:
        archivo_css.write(css)
    print("Archivo 'estilos.css' generado con éxito.")

# Ejecutar la función para generar el archivo CSS
generar_css(colores)



# Función para calcular la dosis según el peso, la edad y la condición de salud del paciente
def calcular_dosificacion(peso, edad, condicion_salud, dosis_base):
    """
    Esta función calcula la dosificación recomendada de un medicamento
    basado en el peso, la edad y la condición de salud del paciente.

    Parámetros:
    - peso: el peso del paciente en kilogramos.
    - edad: la edad del paciente en años.
    - condicion_salud: puede ser 'normal', 'leve', o 'grave'.
    - dosis_base: la dosis recomendada en mg por cada kg de peso.

    Retorna:
    - La dosis total recomendada en miligramos (mg).
    """
    
    # Ajustar la dosis según la edad
    if edad < 12:
        factor_edad = 0.75  # Menores de 12 años reciben el 75% de la dosis
    elif edad >= 60:
        factor_edad = 0.85  # Adultos mayores reciben el 85% de la dosis
    else:
        factor_edad = 1.0  # Adultos reciben el 100% de la dosis

    # Ajustar la dosis según la condición de salud
    if condicion_salud == "leve":
        factor_condicion = 0.9  # En condiciones leves, se reduce la dosis un 10%
    elif condicion_salud == "grave":
        factor_condicion = 1.2  # En condiciones graves, se aumenta la dosis un 20%
    else:
        factor_condicion = 1.0  # En condiciones normales, la dosis no cambia

    # Calcular la dosis total
    dosis_total = dosis_base * peso * factor_edad * factor_condicion
    return dosis_total

# Pedir datos al usuario
peso = float(input("Ingresa el peso del paciente (kg): "))
edad = int(input("Ingresa la edad del paciente (años): "))
condicion_salud = input("Ingresa la condición de salud (normal, leve, grave): ").lower()

# Definir una dosis base estándar (mg por cada kg de peso)
dosis_base = 10  # Por ejemplo, 10 mg/kg

# Calcular la dosis recomendada usando los datos ingresados
dosis_recomendada = calcular_dosificacion(peso, edad, condicion_salud, dosis_base)

# Mostrar el resultado
print(f"\nLa dosis recomendada para el paciente es: {dosis_recomendada:.2f} mg.")


# Función para generar el archivo CSS con la tipografía seleccionada
def generar_css_tipografia(tipografia):
    """
    Genera un archivo CSS con la tipografía seleccionada.

    Parámetros:
    - tipografia: nombre de la tipografía seleccionada.
    """
    
    # Definimos el contenido del CSS
    css = f"""
    /* Estilos generados para la selección de tipografía */
    body {{
        font-family: '{tipografia}', sans-serif;
        margin: 0;
        padding: 0;
        color: #333;
    }}

    h1, h2, h3 {{
        font-family: '{tipografia}', sans-serif;
        font-weight: bold;
    }}

    p {{
        font-family: '{tipografia}', sans-serif;
        font-size: 16px;
    }}
    """
    
    # Guardar el CSS en un archivo
    with open("tipografia.css", "w") as archivo_css:
        archivo_css.write(css)
    print("Archivo 'tipografia.css' generado con éxito.")

# Mostrar opciones de tipografía al usuario
print("Selecciona la tipografía que quieres usar en tu página web:")
print("1. Arial")
print("2. Helvetica")
print("3. Times New Roman")
print("4. Verdana")
print("5. Courier New")

# Obtener la selección del usuario
opcion = int(input("\nIngresa el número de la tipografía elegida: "))

# Diccionario para mapear la opción con la tipografía
tipografias = {
    1: "Arial",
    2: "Helvetica",
    3: "Times New Roman",
    4: "Verdana",
    5: "Courier New"
}

# Validar la opción ingresada
if opcion in tipografias:
    tipografia_seleccionada = tipografias[opcion]
    print(f"\nHas seleccionado: {tipografia_seleccionada}")
    
    # Generar el archivo CSS con la tipografía seleccionada
    generar_css_tipografia(tipografia_seleccionada)
else:
    print("Opción no válida. Intenta de nuevo.")


    # Función para generar el HTML y CSS para el logo
def generar_logo_web(ruta_logo):
    """
    Genera el archivo HTML y CSS para mostrar un logo en la página web.
    
    Parámetros:
    - ruta_logo: la ubicación (ruta) del archivo de imagen del logo.
    """
    
    # Contenido del archivo HTML
    html = f"""
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Página con Logo</title>
        <link rel="stylesheet" href="estilos.css">
    </head>
    <body>
        <header>
            <img src="{ruta_logo}" alt="Logo de la página" class="logo">
            <h1>Bienvenido a Mi Página Web</h1>
        </header>
        <main>
            <p>Este es un ejemplo de cómo integrar un logo en una página web.</p>
        </main>
    </body>
    </html>
    """
    
    # Contenido del archivo CSS
    css = """
    /* Estilos para la página con logo */
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        text-align: center;
        background-color: #f4f4f4;
    }

    header {
        background-color: #333;
        color: white;
        padding: 20px;
    }

    .logo {
        width: 150px;
        height: auto;
        display: block;
        margin: 0 auto;
    }

    h1 {
        font-size: 24px;
        margin-top: 10px;
    }

    main {
        margin: 20px;
    }
    """
    
    # Guardar los archivos HTML y CSS
    with open("index.html", "w") as archivo_html:
        archivo_html.write(html)
    
    with open("estilos.css", "w") as archivo_css:
        archivo_css.write(css)
    
    print("Archivos 'index.html' y 'estilos.css' generados con éxito.")

# Pedir al usuario la ruta del logo
ruta_logo = input("Ingresa la ruta del archivo del logo (ej. logo.png): ")

