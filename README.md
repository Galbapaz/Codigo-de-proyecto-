# Codigo-de-proyecto-
#include <iostream>
using namespace std;

int main() {
    string dueño, seguridad, gerente;
    cin >> dueño >> seguridad >> gerente; // Creamos los tres usuarios

    string contra_dueño, contra_seguridad, contra_gerente;
    cin >> contra_dueño >> contra_seguridad >> contra_gerente; // Creamos las tres contraseñas

    cout << "Iniciar sesión" << endl;
    cout << "Usuario" << endl;

    string usuario;
    cin >> usuario; //Introduce el usuario

    if (usuario != dueño && usuario != seguridad && usuario != gerente) {
        cout << "Error: Usuario incorrecto" << endl; //Si no introduces uno de los tres usuarios te saldra error
        return 0;
    }

    cout << "Contraseña" << endl;

    string contraseña;
    cin >> contraseña;

    if ((usuario == dueño && contraseña == contra_dueño) ||
        (usuario == seguridad && contraseña == contra_seguridad) ||
        (usuario == gerente && contraseña == contra_gerente)) {
        
        cout << "Sesión iniciada como " << usuario << endl;
        cout << "Tambien se registrara quien inicio sesion y cuando lo hizo."  << endl;

        string camaras;
        cin >> camaras; //Activacion de las camaras

        if (camaras == "activar") {
            cout << "Se monitorearán en tiempo real." << endl;
            cout << "Todo será guardado y almacenado para poder revisar y analizar en caso de que pase algo." << endl;
            cout << "Se mostrara la fecha y hora" << endl;
            cout << "También aquellos con permiso podrán acceder a las cámaras desde un dispositivo conectado a internet." << endl;
        } else {
            cout << "Avisar al dueño, jefe de seguridad y gerente que las cámaras no funcionan." << endl;
            cout << "Si solo esta fallando una camara se notificara cual es." << endl;
        }
    } else {
        cout << "Error: Contraseña incorrecta" << endl;
    }

    return 0;
}
