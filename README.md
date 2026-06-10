import os
import matplotlib.pyplot as plt


def limpiar_pantalla():
    # RF-11: Limpia la pantalla dependiendo del sistema operativo
    os.system('cls' if os.name == 'nt' else 'clear')


def calcular_funcion_lineal():
    limpiar_pantalla()
    print("=========================================")
    print("      CÁLCULO DE FUNCIÓN LINEAL          ")
    print("=========================================\n")

    # RF-06: Solicitar coeficientes
    try:
        m = float(input("Escriba el coeficiente de X de grado 1 (m): "))
        b = float(input("Escriba el término independiente (b): "))
    except ValueError:
        print("\n❌ Error: Ambos valores deben ser numéricos.")
        input("\nPresione Enter para volver al menú...")
        limpiar_pantalla()
        return

    # RF-07: Valores de X fijos
    valores_x = [-2, -1, 0, 1, 2]
    valores_y = []

    # RF-08: Mostrar pares de coordenadas (X, Y)
    print("\n-----------------------------------------")
    print(" Coordenadas calculadas (X, Y):")
    print("-----------------------------------------")
    for x in valores_x:
        y = m * x + b
        valores_y.append(y)
        print(f"  📌 Para X = {x:2} -> Y = {y:4}  |  Par: ({x}, {y})")
    print("-----------------------------------------")

    # RF-09: Preguntar por la gráfica
    respuesta = input("\n¿Desea la gráfica de la función? (SI/NO): ").strip().lower()

    # RF-10: Dibujar la gráfica
    if respuesta in ["si", "s", "sí"]:
        print("\nGenerando gráfica... Cierre la ventana de la gráfica para continuar.")

        plt.figure(figsize=(8, 5))
        plt.plot(valores_x, valores_y, marker='o', color='crimson', linewidth=2, label=f"f(x) = {m}x + {b}")

        # Líneas de los ejes cartesianos (X=0, Y=0)
        plt.axhline(0, color='black', linewidth=1, linestyle='-')
        plt.axvline(0, color='black', linewidth=1, linestyle='-')

        # Configuración estética
        plt.title(f"Gráfica de la Función: f(x) = {m}x + {b}", fontsize=14)
        plt.xlabel("Eje X", fontsize=11)
        plt.ylabel("Eje Y", fontsize=11)
        plt.grid(True, linestyle='--', alpha=0.6)
        plt.legend(loc="upper left")

        plt.show()

        # Una vez cerrada la gráfica, limpia y regresa
        input("\nPresione Enter para volver al menú principal...")
        limpiar_pantalla()
    else:
        # RF-11: Si responde NO (o cualquier otra cosa), limpia y vuelve al menú
        limpiar_pantalla()


def menu_principal():
    while True:
        print("=========================================")
        print("            MENÚ PRINCIPAL               ")
        print("=========================================")
        print("1. Calcular Función Lineal")
        print("2. Salir del programa")
        print("=========================================")

        opcion = input("Seleccione una opción: ").strip()

        if opcion == "1":
            calcular_funcion_lineal()
        elif opcion == "2":
            print("\n¡Gracias por usar el programa! Saliendo...")
            break
        else:
            print("\n❌ Opción no válida. Intente de nuevo.")
            input("\nPresione Enter para continuar...")
            limpiar_pantalla()


# Punto de entrada del programa
if __name__ == "__main__":
    limpiar_pantalla()
    menu_principal()
