# Calculo-de-RFC
crear un software donde al ingresar los datos correspondientes te arroje el RFC sin homoclave


#include <iostream>
#include <string>
using namespace std;


//Funsion para obtener la primer vocalinterna de una cadena de texto
char obtenerPrimerVocalInterna(const std::string& str) {
    for (size_t i = 1; i < str.length(); ++i) {
        char c = str[i];
        if (c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U')
            return c;
    }
    return 'X'; // Si no se encuentra ninguna vocal interna, entonces se utiliza X
}

// Funcion principal para realizar el calculo de RFC 

    string calcularRFC(const std::string& nombre, const std::string& apellidoPaterno, const std::string& apellidoMaterno, const std::string& fechaNacimiento) {
    std::string rfc;

    // Se obtiene la letra inicial y la primer vocal interna del apellido apellidoPaterno 
    char letraInicial = apellidoPaterno[0];
    char primeraVocalInterna = obtenerPrimerVocalInterna(apellidoPaterno);

    // Se obtiene la letra inicial del apellido materno o se usa un 'X' si no cuenta con apellido materno 
    char inicialApellidoMaterno = (apellidoMaterno.empty()) ? 'X' : apellidoMaterno[0];


    // Se obtiene la letra inicial del primer nombre o se sustituye por una 'X' si no tiene 
    char inicialNombre = nombre[0];

    // Se obtiene los dos ultimos digitos del año de nacimiento 
    std::string anio = fechaNacimiento.substr(2, 2);

    // Se obtiene el mes y el dia de nacimiento
    std::string mes = fechaNacimiento.substr(5, 2);
    std::string dia = fechaNacimiento.substr(8, 2);

    // se crea el rfc 
    rfc = letraInicial;
    rfc += primeraVocalInterna;
    rfc += inicialApellidoMaterno;
    rfc += inicialNombre;
    rfc += anio;
    rfc += mes;
    rfc += dia;

    return rfc;
}

int main() {
    std::string nombre, apellidoPaterno, apellidoMaterno, fechaNacimiento;

    std::cout << "FAVOR DE INGRESAR SOLO MAYUSCULAS " << std::endl;
    std::cout << "Ingresa el nombre(s): ";
    std::getline(std::cin, nombre);

    std::cout << "Ingresa el apellido paterno: ";
    std::getline(std::cin, apellidoPaterno);

    std::cout << "Ingresa el apellido materno (si no tiene, precione <Enter>: ";
    std::getline(std::cin, apellidoMaterno);

    std::cout << "Ingresa la fecha de nacimiento (YYYY-MM-DD): ";
    std::getline(std::cin, fechaNacimiento);

    std::string rfc = calcularRFC(nombre, apellidoPaterno, apellidoMaterno, fechaNacimiento);
    std::cout << "RFC: " << rfc  <<  std::endl; 

    return 0;
}
    
