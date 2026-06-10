def calcular_ecuacion(p1, p2):
    """Calcula m y b dados dos puntos (x1, y1) y (x2, y2)."""
    x1, y1 = p1
    x2, y2 = p2

    m = (y2 - y1) / (x2 - x1)
    b = y1 - m * x1

    return m, b


m, b = calcular_ecuacion((1, 2), (3, 6))
print(f"La ecuación es: y = {m}x + {b}")
# Imprime: La ecuación es: y = 2.0x + 0.0

