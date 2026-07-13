# FernandoSilvaFPY1101_002D_ET
# Examen


peliculas = {
    #------------------------------------------------------
    # Titulo, genero, duracion, clasificación, idioma y 3d
    #------------------------------------------------------
    "P101": ['Luz de Otoño', 'drama', 110, 'B', 'Español', False],
    "P102": ['Noche Neón', 'acción', 125, 'C', 'Ingles', True],
    'P103': ['Planeta Agua', 'documental', 90, 'A', 'Español', False],
    'P104': ['Risa Total', 'comedia', 105, 'A', 'Español', True],
    'P105': ['Código Zero', 'thriller', 118, 'C', 'Ingles', True],
    'P106': ['Viaje Lunar', 'ciencia ficción', 132, 'B', 'Ingles', False]
}
cartelera = {
    #---------------
    # Precio y Stock
    #---------------
    'P101': [5990, 40],
    'P102': [7990, 0],
    'P103': [4990, 25],
    'P104': [6990, 12],
    'P105': [8990, 8],
    'P106': [7490, 3]
}

#------------------------------------------------------------
# Busca el codigo y return True si lo encuentra, False sino.
#------------------------------------------------------------

def buscar_codigo():
    buscar_code=input("Escriba antes el CODIGO: ")
    for buscar_code in peliculas:
        if buscar_code == peliculas[0]:
            return True
    return False

#------------------------------------------------------
# Def para buscar el tipo de genero en el diccionario.
#------------------------------------------------------

def cupos_generos(genero,peliculas):
    for genero in peliculas:
        if genero.upper in peliculas:
            print("Si hay")
        else:
            print("No se encontró")

#--------------------
# Buscar y mostrar.
#--------------------

def buscar_(codigo,peliculas):
    if codigo.upper() in peliculas:
        print (peliculas[codigo.upper()])
    else:
        print ("No se encontró")

#---------------------------------------------
# Otro buscar por si el de más arriba me falla
#----------------------------------------------

def buscar(codigo, peliculas):
    if codigo.upper() in peliculas:
        return True
    return False

#--------------------------------
# Busqueda por rango de precios
#--------------------------------

def busqueda_precio(minimo, maximo, peliculas, cartelera):
    for codigo in cartelera:
        precio = cartelera [codigo][0]
        stock = cartelera [codigo][1]
        if minimo <= precio <= maximo and stock >0 and minimo and minimo >0 and maximo >0:
            print (codigo)
            print ("Las peliculas encontradas son:\n")
            print (peliculas[codigo])
            print (precio)
        else:

            #--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
            # Repite el ciclo for la cantidad de veces que se repite el else, pero no es lo que pide el enunciado, no especifica cuantas veces, solo que muestre el mensaje asi que se ignora.
            #----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

            print("No hay peliculas en ese rango de precios.")

#-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Funcion creada para actualizar algun precio del diccionario "cartelera", el enunciado pide solo codigo y nuevo_precio pero le añadi cartelera porque también trabajaré con las key dentro de ese diccionario, me refiero a "cartelera".
#-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

def actualizar_precio (codigo, nuevo_precio, cartelera):
    if codigo in cartelera:
        cartelera[codigo[0]] = nuevo_precio
        print("Precio actualizado")
        return True
    return False

#-----------------------------------------------------------
# Funcion creada para agregar peliculas en los 2 diccionarios
#-----------------------------------------------------------

def agregar_pelicula (codigo, titulo, genero,duracion, clasificacion,idioma, es_3d, precio, cupos, peliculas, cartelera, stock):
    if codigo in peliculas:
        return False
    
    titulo = input("Titulo de la pelicula: ")
    genero = input("Genero de la pelicula: ")
    duracion = float(input("Duración de la pelicula: "))
    clasificacion = input("Clasificación de la película: ")
    idioma = input ("Idioma de la pelicula: ")
    es_3d = input("¿ Es 3D ? \n[S] para SI o [N] para NO")
    precio = float(input("Precio: "))
    
    peliculas [codigo] = 
    cartelera[codigo] = [precio, stock]
    
    return True

#----------------------------------------------------------------------------------------------------------------------------------------
# El enunciado pide trabajar  con codigo solamente pero tengo que  añadir a mi funcion el diccionario cartelera y el diccionario peliculas
#----------------------------------------------------------------------------------------------------------------------------------------

def eliminar_pelicula (codigo, peliculas, cartelera):
    if codigo in peliculas:
        del peliculas[codigo]
        del cartelera[codigo]
        return True
    return False

#-------------------------------------------------------------
# Def para modificar algun dato si lo necesito mas adelante...
#-------------------------------------------------------------

def modificar_dato(codigo, indice, nuevo_dato,peliculas):
    if codigo in peliculas:
        peliculas[codigo][indice]=nuevo_dato
        return True
    return False

#----------------------------------
# Otra funcion creada para tratar de buscar código
#----------------------------------

def encontrar_codigo (codigo, peliculas):
    codigo = codigo.upper()
    for ver in peliculas:
        if ver.lower() == codigo.lower():
            print(ver)
            return ver
    return None



while True:

    try:

        opcion_menu=int(input("========== MENÚ CINE MAX ==========\n1. Cupos por género\n2. Búsqueda de películas por rango de precio\n3. Actualizar precio de película\n4. Agregar película\n5. Eliminar película\n6. Salir\n=====================================\n"))
        if opcion_menu == 1:
            codigo = input("Escriba el codigo: ")
            buscar_codigo()

        elif opcion_menu ==2:

            try:

                minimo = int(input("Precio minimo"))
                maximo = int(input("Precio máximo"))
                busqueda_precio(minimo,maximo,peliculas, cartelera)
                continue

            except ValueError:

                print ("Debe ingresar valores enteros")

        elif opcion_menu ==3:

            nuevo_precio = float(input("A qué precio desea actualizar?"))
            actualizar_precio(codigo, nuevo_precio, cartelera)
            continue

        elif opcion_menu ==4:
            codigo = input("Código de la pelicula a agregar: ")
            agregar_pelicula(codigo, peliculas)
            continue

        elif opcion_menu ==5:
            codigo = input("Codigo de la pelicula a eliminar")
            eliminar_pelicula(codigo,peliculas)
            continue

        elif opcion_menu ==6:
            #----------------------------------------------------------------------------------------------------------------------------------------------------------------
            # Para implementar esta opción no requiere función adicional, el programa principal es responsable de detener el ciclo (con Break) y mostrar el mensaje de cierre.
            #----------------------------------------------------------------------------------------------------------------------------------------------------------------
            print("Programa finalizado")
            break

    except ValueError:

        print ("Debe seleccionar una opción válida")



# Tuve problemas buscando el código de los diccionarios y me tome mucho tiempo buscando un def adecuado, haciendo que los pasos después tal vez me aparezcan como errores aunque los def esten bien utilizados nunca se encontrará el codigo porque fue el último paso que hice, primero hice el ==2 que era la parte más dificil encuentro yo.
# Hay algunos def que no alcancé a terminar por temas de tiempo...
# Trate de utilizar las excepciones donde correspondan y se me hizo enorme mis lineas de código... Me demoraba mucho en subir y ver algun error... por querer hacer los def antes de los enunciados que estaban pidiendo...
