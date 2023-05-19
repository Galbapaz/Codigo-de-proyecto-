#include <iostream>
using namespace std;     //cambiar las ñ para que funcione

int main() { 
    string correo_dueño, correo_seguridad, correo_gerente;
    cout << "introduzca los correos" << endl; //ingresar los correos de los usuarios
    cin >> correo_dueño >> correo_seguridad >> correo_gerente;
    int number_dueño, number_seguridad, number_gerente;
    cout << "introduzca los numeros de celular" << endl;
    cin >> number_dueño >> number_seguridad >> number_gerente; //ingresar los numeros de celular de los usuarios 
    string dueño, seguridad, gerente;
    cout << "Introduzca los nombres de usuario" << endl;
    cin >> dueño >> seguridad >> gerente; //Se crean los usuarios
string contra_dueño, contra_seguridad, contra_gerente;
    cout << "Introduzca las contraseñas" << endl;
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
    cout << "Activar o Desactivar sistema" << endl;
    cin >> camaras; //Activacion de las camaras

    if (camaras == "activar") { //Indicamos lo que pasa mientras estan activas
        cout << "Se monitorearán en tiempo real." << endl;
        cout << "Todo será guardado y almacenado para poder revisar y analizar en caso de que pase algo." << endl;
        cout << "Se mostrara la fecha y hora" << endl;
        cout << "También aquellos con permiso podrán acceder a las cámaras desde un dispositivo conectado a internet." << endl;
        cout << "Despues de las 10:30pm se activaran unos sensores." << endl;
        cout << "Si un sensor detecta algo, se llamara a las 3 personas con acceso a las camaras" << endl;
    } else { //Indicamos lo que pasa si las desactivan o alguna camara tiene problemas
         cout << "Avisar al dueño, jefe de seguridad y gerente que las cámaras fueron desactivadas." << endl;
        cout << "Avisar al dueño, jefe de seguridad y gerente que las cámaras no funcionan." << endl;
        cout << "Si solo esta fallando una camara se notificara cual es." << endl;
    }
} else { 
    cout << "Error: Contraseña incorrecta" << endl;
}

return 0;
}

