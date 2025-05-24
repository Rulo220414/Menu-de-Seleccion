def es_anagrama(palabra1, palabra2):
    if len(palabra1) != len(palabra2):
        return False
    return sorted(palabra1.lower()) == sorted(palabra2.lower())

def invertir_cadena(cadena):
    return cadena[::-1]

def fibonacci(n):
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n-1) + fibonacci(n-2)

def eliminar_duplicados(lista):
    return list(set(lista))

def es_palindromo(cadena):
    cadena = cadena.lower().replace(" ", "")
    return cadena == cadena[::-1]

def contar_palabras(texto):
    palabras = texto.lower().split()
    conteo = {}
    for palabra in palabras:
        if palabra in conteo:
            conteo[palabra] += 1
        else:
            conteo[palabra] = 1
    return conteo

def encontrar_mayor(lista):
    return max(lista)

def invertir_lista(lista):
    return lista[::-1]

def filtrar_pares(lista):
    return [num for num in lista if num % 2 == 0]

def encontrar_segundo_mayor(lista):
    if len(lista) < 2:
        return None
    lista_ordenada = sorted(lista, reverse=True)
    return lista_ordenada[1]

def contar_vocales(texto):
    vocales = "aeiouáéíóú"
    cuenta = 0
    for letra in texto.lower():
        if letra in vocales:
            cuenta += 1
    return cuenta

def ordenar_tuplas(lista_tuplas):
    return sorted(lista_tuplas, key=lambda x: x[1])

def contar_unicos(cadena):
    return len(set(cadena))

def palabras_mas_largas(texto, n):
    palabras = texto.split()
    palabras.sort(key=len, reverse=True)
    return palabras[:n]

def es_primo(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

def primos_hasta(n):
    primos = []
    i = 2
    while len(primos) < n:
        if es_primo(i):
            primos.append(i)
        i += 1
    return primos

def mostrar_titulo(titulo):
    print("\n" + "="*50)
    print(f"{titulo:^50}")
    print("="*50)

def mostrar_ejemplo(funcion, ejemplo, resultado):
    print("\nEjemplo de uso:")
    print(f"Función: {funcion.__name__}")
    print(f"Entrada: {ejemplo}")
    print(f"Resultado: {resultado}")

def obtener_lista_numeros():
    while True:
        entrada = input("Ingrese números separados por comas: ")
        try:
            return [float(x.strip()) for x in entrada.split(",") if x.strip()]
        except ValueError:
            print("Error: Ingrese solo números separados por comas. Intente nuevamente.")

def obtener_lista_general():
    while True:
        entrada = input("Ingrese elementos separados por comas: ")
        if entrada.strip():
            return [x.strip() for x in entrada.split(",") if x.strip()]
        print("Error: No ingresó ningún elemento. Intente nuevamente.")

def menu_principal():
    mostrar_titulo("MENÚ PRINCIPAL")
    print("Seleccione una operación:")
    print(" 1. Verificar si dos palabras son anagramas")
    print(" 2. Invertir una cadena")
    print(" 3. Generar secuencia Fibonacci")
    print(" 4. Eliminar elementos duplicados de una lista")
    print(" 5. Verificar si una cadena es palíndromo")
    print(" 6. Contar frecuencia de palabras en un texto")
    print(" 7. Encontrar el número mayor en una lista")
    print(" 8. Invertir una lista")
    print(" 9. Filtrar números pares de una lista")
    print("10. Encontrar el segundo número mayor en una lista")
    print("11. Contar vocales en un texto")
    print("12. Ordenar lista de tuplas por segundo elemento")
    print("13. Contar caracteres únicos en una cadena")
    print("14. Encontrar las N palabras más largas en un texto")
    print("15. Generar los primeros N números primos")
    print(" 0. Salir")
    
    while True:
        opcion = input("\nIngrese el número de opción (0-15): ")
        if opcion.isdigit() and 0 <= int(opcion) <= 15:
            return int(opcion)
        print("Opción inválida. Intente nuevamente.")

def ejecutar_opcion(opcion):
    funciones = {
        1: (es_anagrama, ["Ingrese primera palabra: ", "Ingrese segunda palabra: "]),
        2: (invertir_cadena, ["Ingrese la cadena a invertir: "]),
        3: (fibonacci, ["Ingrese cantidad de términos Fibonacci a generar: "]),
        4: (eliminar_duplicados, ["Ingrese lista de elementos (separados por comas): "]),
        5: (es_palindromo, ["Ingrese texto para verificar si es palíndromo: "]),
        6: (contar_palabras, ["Ingrese texto para contar palabras: "]),
        7: (encontrar_mayor, ["Ingrese lista de números (separados por comas): "]),
        8: (invertir_lista, ["Ingrese lista de elementos (separados por comas): "]),
        9: (filtrar_pares, ["Ingrese lista de números (separados por comas): "]),
        10: (encontrar_segundo_mayor, ["Ingrese lista de números (separados por comas): "]),
        11: (contar_vocales, ["Ingrese texto para contar vocales: "]),
        12: (ordenar_tuplas, ["Ingrese lista de tuplas (ej. [(1,2),(3,1)]): "]),
        13: (contar_unicos, ["Ingrese cadena para contar caracteres únicos: "]),
        14: (palabras_mas_largas, ["Ingrese texto: ", "Ingrese cantidad de palabras más largas a mostrar: "]),
        15: (primos_hasta, ["Ingrese cantidad de números primos a generar: "])
    }
    
    funcion, prompts = funciones[opcion]
    
    mostrar_titulo(funcion.__name__.replace("_", " ").title())
    
    print("\n¿Cómo desea proceder?")
    print("1. Ingresar mis propios datos")
    print("2. Ver un ejemplo")
    print("3. Volver al menú principal")
    
    while True:
        modo = input("Seleccione una opción (1-3): ")
        if modo == "1":
            try:
                entradas = []
                for prompt in prompts:
                    if "lista de números" in prompt:
                        entradas.append(obtener_lista_numeros())
                    elif "lista de elementos" in prompt:
                        entradas.append(obtener_lista_general())
                    elif "lista de tuplas" in prompt:
                        while True:
                            try:
                                entrada = input(prompt)
                                entradas.append(eval(entrada))
                                break
                            except:
                                print("Formato inválido. Intente nuevamente.")
                    else:
                        entrada = input(prompt)
                        if prompt.endswith(": "):
                            if "cantidad" in prompt:
                                entradas.append(int(entrada))
                            else:
                                entradas.append(entrada)
                
                resultado = funcion(*entradas)
                print("\nResultado:")
                print(resultado)
            except Exception as e:
                print(f"\nError: {str(e)}")
            break
            
        elif modo == "2":
            ejemplos = {
                1: ('es_anagrama("amor", "roma")', True),
                2: ('invertir_cadena("Python")', 'nohtyP'),
                3: ('[fibonacci(i) for i in range(10)]', [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]),
                4: ('eliminar_duplicados([1, 2, 2, 3, 4, 4, 5])', [1, 2, 3, 4, 5]),
                5: ('es_palindromo("Anita lava la tina")', True),
                6: ('contar_palabras("hola hola mundo")', {'hola': 2, 'mundo': 1}),
                7: ('encontrar_mayor([7, 3, 9, 2, 5])', 9),
                8: ('invertir_lista(["a", "b", "c", "d"])', ['d', 'c', 'b', 'a']),
                9: ('filtrar_pares([1, 2, 3, 4, 5, 6])', [2, 4, 6]),
                10: ('encontrar_segundo_mayor([5, 2, 8, 1, 9])', 8),
                11: ('contar_vocales("Hola, ¿cómo estás?")', 5),
                12: ('ordenar_tuplas([(3, 2), (1, 3), (4, 1)])', [(4, 1), (3, 2), (1, 3)]),
                13: ('contar_unicos("hello")', 4),
                14: ('palabras_mas_largas("El perro persiguió al gato", 2)', ['persiguió', 'perro']),
                15: ('primos_hasta(5)', [2, 3, 5, 7, 11])
            }
            
            ejemplo, resultado = ejemplos[opcion]
            mostrar_ejemplo(funcion, ejemplo, resultado)
            break
            
        elif modo == "3":
            return
        else:
            print("Opción inválida. Intente nuevamente.")
    
    input("\nPresione Enter para continuar...")

def main():
    while True:
        opcion = menu_principal()
        if opcion == 0:
            mostrar_titulo("PROGRAMA FINALIZADO")
            break
        ejecutar_opcion(opcion)

if __name__ == "__main__":
    main()
