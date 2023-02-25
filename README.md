# Prueba
Repositorio de prueba
# Definimos una lista con los días disponibles para reservar
dias_disponibles = ['martes', 'miércoles', 'jueves', 'viernes', 'sábado', 'domingo']

# Creamos un diccionario para almacenar las horas reservadas
horas_reservadas = {}

# Creamos un bucle que permita al usuario hacer varias reservas
while True:
    # Pedimos al usuario que seleccione una opción
    opcion = input("¿Desea hacer una reserva (1) o salir (2)? ")

    # Verificamos la opción seleccionada por el usuario
    if opcion == '1':
        # Pedimos al usuario que seleccione el día en que desea reservar
        dia = input("Ingrese el día en que desea reservar (martes, miércoles, jueves, viernes, sábado o domingo): ")
        # Verificamos si el día ingresado es válido
        while dia not in dias_disponibles:
            print("Error: El día ingresado no es válido.")
            dia = input("Ingrese el día en que desea reservar (martes, miércoles, jueves, viernes, sábado o domingo): ")

        # Pedimos al usuario que ingrese la cantidad de horas que desea reservar
        horas = input("Ingrese la cantidad de horas que desea reservar (mínimo 1 hora): ")
        # Validamos la entrada del usuario
        while not horas.isdigit() or int(horas) < 1:
            print("Error: Debe ingresar un número entero mayor o igual a 1.")
            horas = input("Ingrese la cantidad de horas que desea reservar (mínimo 1 hora): ")

        # Convertimos las horas ingresadas a un entero
        horas_reserva = int(horas)

        # Verificamos si el día ya tiene reservas
        if dia in horas_reservadas:
            # Verificamos si la cantidad de horas a reservar no excede las disponibles
            if horas_reserva <= (9 - horas_reservadas[dia]):
                horas_reservadas[dia] += horas_reserva
                print(f"Se han reservado {horas_reserva} horas para el día {dia}.")
            else:
                print(f"Error: Solo hay {9 - horas_reservadas[dia]} horas disponibles para el día {dia}.")
        else:
            # Verificamos si la cantidad de horas a reservar no excede las disponibles
            if horas_reserva <= 9:
                horas_reservadas[dia] = horas_reserva
                print(f"Se han reservado {horas_reserva} horas para el día {dia}.")
            else:
                print(f"Error: Solo se pueden reservar hasta 9 horas para el día {dia}.")

        # Imprimimos el estado actual de las reservas
        print("Reservas actuales:")
        for dia in horas_reservadas:
            print(f"{dia}: {horas_reservadas[dia]} horas")

    elif opcion == '2':
        # Salimos del bucle
        print("¡Gracias por utilizar nuestro sistema de reservas!")
        break

    else:
        # Opción inválida
        print("Error: Opción inválida. Por favor seleccione 1 o 2.")
