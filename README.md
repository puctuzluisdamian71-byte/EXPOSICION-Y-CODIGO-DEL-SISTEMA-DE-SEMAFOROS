import random

def main():
    # Simulación del conteo de vehículos en 3 semáforos por 15 minutos
    semaforos = [0, 0, 0]  # Norte, Este, Oeste
    total_general = 0
    
    print("=== EXPERIMENTO ESTOCÁSTICO - SANTA LUCÍA ===")
    print("Minuto  Sem1  Sem2  Sem3  Total")
    print("------  ----  ----  ----  -----")
    
    for minuto in range(1, 16):
        # Determina semáforo activo según ciclo de 72 segundos
        semaforo_activo = (minuto - 1) % 3
        
        # Genera vehículos aleatorios (2-12 basado en observaciones)
        vehiculos = 2 + random.randint(0, 10)
        semaforos[semaforo_activo] += vehiculos
        total_general += vehiculos
        
        # Muestra resultados por minuto con formato fijo
        print(f"{minuto:6d}  "
              f"{(vehiculos if semaforo_activo == 0 else 0):4d}  "
              f"{(vehiculos if semaforo_activo == 1 else 0):4d}  "
              f"{(vehiculos if semaforo_activo == 2 else 0):4d}  "
              f"{vehiculos:5d}")
    
    # Resultados finales
    print("\n=== RESULTADOS ===")
    print(f"Semáforo 1 (Norte): {semaforos[0]} vehículos")
    print(f"Semáforo 2 (Este): {semaforos[1]} vehículos")
    print(f"Semáforo 3 (Oeste): {semaforos[2]} vehículos")
    print(f"TOTAL: {total_general} vehículos")
    print(f"Promedio: {total_general/15.0:.2f} veh/min")

if __name__ == "__main__":
    main()
