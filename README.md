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

    bool activarSensores = false;

    // Verificar si es hora de activar los sensores
    if (hora > 22 || (hora == 22 && minuto >= 30) || hora < 6 || (hora == 6 && minuto <= 30)) {
        activarSensores = true;
    }

    const int numCamaras = 16;
    string estadoCamaras[numCamaras];

    // Estado inicial de las cámaras
    for (int i = 0; i < numCamaras; i++) {
        estadoCamaras[i] = activarSensores ? "activada" : "desactivada";
    }

    // Menú de opciones
    int opcion;
do {
    cout << endl;
    cout << "Menú de opciones" << endl;
    cout << "1. Ver estado de las cámaras" << endl;
    cout << "2. Activar una cámara" << endl;
    cout << "3. Desactivar una cámara" << endl;
    cout << "4. Activar todas las cámaras" << endl;
    cout << "5. Desactivar todas las cámaras" << endl;
    cout << "6. Salir" << endl;
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
            int camara;
            cout << "Ingrese el número de cámara a activar (1-" << numCamaras << "): ";
            cin >> camara;

            if (camara >= 1 && camara <= numCamaras) {
                estadoCamaras[camara - 1] = "activada";
                cout << "Cámara " << camara << " activada correctamente." << endl;
            } else {
                cout << "Número de cámara inválido." << endl;
            }
            break;
        }
        case 3: {
            int camara;
            cout << "Ingrese el número de cámara a desactivar (1-" << numCamaras << "): ";
            cin >> camara;

            if (camara >= 1 && camara <= numCamaras) {
                estadoCamaras[camara - 1] = "desactivada";
                cout << "Cámara " << camara << " desactivada correctamente." << endl;
            } else {
                cout << "Número de cámara inválido." << endl;
            }
            break;
        }
        case 4: {
            for (int i = 0; i < numCamaras; i++) {
                estadoCamaras[i] = "activada";
            }
            cout << "Todas las cámaras han sido activadas correctamente." << endl;
            break;
        }
        case 5: {
            for (int i = 0; i < numCamaras; i++) {
                estadoCamaras[i] = "desactivada";
            }
            cout << "Todas las cámaras han sido desactivadas correctamente." << endl;
            break;
        }
        case 6: {
            cout << "Saliendo del programa..." << endl;
            break;
        }
        default:
            cout << "Opción inválida. Por favor, ingrese una opción válida." << endl;
            break;
    }
} while (opcion != 6);

return 0;
}


