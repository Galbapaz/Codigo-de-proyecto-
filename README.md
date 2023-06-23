#include <iostream>
#include <string>
#include <ctime>

using namespace std;

int main() {
    string usuario;
    string contrasena;

    // Registro de usuarios
    string duenoUsuario = "dueno";
    string duenoContrasena = "123456";
    string guardiaUsuario = "guardia";
    string guardiaContrasena = "abcdef";
    string gerenteUsuario = "gerente";
    string gerenteContrasena = "qwerty";

    // Autenticación de usuarios
    cout << "Inicio de Sesión" << endl;
    cout << "Usuario: ";
    cin >> usuario;
    cout << "Contraseña: ";
    cin >> contrasena;
    cout << endl;

    // Verificación de credenciales
    if (usuario == duenoUsuario && contrasena == duenoContrasena) {
        cout << "Bienvenido, dueño del edificio." << endl;
    } else if (usuario == guardiaUsuario && contrasena == guardiaContrasena) {
        cout << "Bienvenido, guardia de seguridad." << endl;
    } else if (usuario == gerenteUsuario && contrasena == gerenteContrasena) {
        cout << "Bienvenido, gerente." << endl;
    } else {
        cout << "Credenciales inválidas. Acceso denegado." << endl;
        return 0;
    }

    // Verificación de la hora actual
    time_t now = time(0);
    tm* tiempoActual = localtime(&now);
    int hora = tiempoActual->tm_hour;
    int minuto = tiempoActual->tm_min;

    bool activarCamaras = false;

    // Verificar si es hora de activar las cámaras
    if (hora > 22 || (hora == 22 && minuto >= 30) || hora < 6 || (hora == 6 && minuto <= 30)) {
        activarCamaras = true;
    }

    const int numCamaras = 16;
    string estadoCamaras[numCamaras];

    // Estado inicial de las cámaras
    for (int i = 0; i < numCamaras; i++) {
        estadoCamaras[i] = activarCamaras ? "activada" : "desactivada";
    }

    // Verificar si es hora de activar los sensores de movimiento
    bool activarSensores = false;

    if (hora > 22 || (hora == 22 && minuto >= 30) || hora < 6 || (hora == 6 && minuto <= 30)) {
        activarSensores = true;
    }

    const int numSensores = 16;
    bool estadoSensores[numSensores];

    // Estado inicial de los sensores de movimiento
    for (int i = 0; i < numSensores; i++) {
        estadoSensores[i] = activarSensores;
    }

    // Menú de opciones
    int opcion;
    do {
        cout << endl;
        cout << "Menú de opciones" << endl;
        cout << "1. Ver estado de las cámaras" << endl;
        cout << "2. Activar todas las cámaras" << endl;
        cout << "3. Desactivar todas las cámaras" << endl;
        cout << "4. Ver estado de los sensores de movimiento" << endl;
        cout << "5. Activar todos los sensores de movimiento" << endl;
        cout << "6. Desactivar todos los sensores de movimiento" << endl;
        cout << "7. Activar un sensor de movimiento" << endl;
        cout << "8. Desactivar un sensor de movimiento" << endl;
        cout << "9. Salir" << endl;
        cout << "Ingrese una opción: ";
        cin >> opcion;

        switch (opcion) {
            case 1: {
                cout << "Estado de las cámaras:" << endl;
                for (int i = 0; i < numCamaras; i++) {
                    cout << "Cámara " << (i + 1) << ": " << estadoCamaras[i] << endl;
                }
                break;
            }
            case 2: {
                for (int i = 0; i < numCamaras; i++) {
                    estadoCamaras[i] = "activada";
                }
                cout << "Todas las cámaras han sido activadas correctamente." << endl;
                break;
            }
            case 3: {
                for (int i = 0; i < numCamaras; i++) {
                    estadoCamaras[i] = "desactivada";
                }
                cout << "Todas las cámaras han sido desactivadas correctamente." << endl;
                break;
            }
            case 4: {
                cout << "Estado de los sensores de movimiento:" << endl;
                for (int i = 0; i < numSensores; i++) {
                    cout << "Sensor " << (i + 1) << ": " << (estadoSensores[i] ? "activado" : "desactivado") << endl;
                }
                break;
            }
            case 5: {
                for (int i = 0; i < numSensores; i++) {
                    estadoSensores[i] = true;
                }
                cout << "Todos los sensores de movimiento han sido activados correctamente." << endl;
                break;
            }
            case 6: {
                for (int i = 0; i < numSensores; i++) {
                    estadoSensores[i] = false;
                }
                cout << "Todos los sensores de movimiento han sido desactivados correctamente." << endl;
                break;
            }
            case 7: {
                int sensor;
                cout << "Ingrese el número de sensor a activar (1-" << numSensores << "): ";
                cin >> sensor;

                if (sensor >= 1 && sensor <= numSensores) {
                    estadoSensores[sensor - 1] = true;
                    cout << "Sensor " << sensor << " activado correctamente." << endl;
                } else {
                    cout << "Número de sensor inválido." << endl;
                }
                break;
            }
            case 8: {
                int sensor;
                cout << "Ingrese el número de sensor a desactivar (1-" << numSensores << "): ";
                cin >> sensor;

                if (sensor >= 1 && sensor <= numSensores) {
                    estadoSensores[sensor - 1] = false;
                    cout << "Sensor " << sensor << " desactivado correctamente." << endl;
                } else {
                    cout << "Número de sensor inválido." << endl;
                }
                break;
            }
            case 9: {
                cout << "Saliendo del programa..." << endl;
                break;
            }
            default:
                cout << "Opción inválida. Por favor, ingrese una opción válida." << endl;
                break;
        }
    } while (opcion != 9);

    return 0;
}


