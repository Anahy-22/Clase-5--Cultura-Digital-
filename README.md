# Clase-5--Cultura-Digital-
Tercero A- Anahy Cóndor

    #include <iostream>
    #include <vector>
    #include <string>
    using namespace std;

    struct Tarea {
    string nombre;
    bool completada;
    };

    void mostrarMenu() {
    cout << "\n===== MENU DE TAREAS =====\n";
    cout << "1. Agregar tarea\n";
    cout << "2. Ver tareas\n";
    cout << "3. Completar tarea\n";
    cout << "4. Salir\n";
    cout << "Elige una opción: ";
    }

    int main() {
    vector<Tarea> tareas;
    int opcion;

    do {
        mostrarMenu();
        cin >> opcion;

        switch (opcion) {

        case 1: {
            cin.ignore();
            Tarea t;
            cout << "Escribe el nombre de la tarea: ";
            getline(cin, t.nombre);
            t.completada = false;
            tareas.push_back(t);
            cout << "Tarea agregada correctamente.\n";
            break;
        }

        case 2: {
            cout << "\n--- Lista de tareas ---\n";
            if (tareas.empty()) {
                cout << "No hay tareas registradas.\n";
            } else {
                for (int i = 0; i < tareas.size(); i++) {
                    cout << i + 1 << ". " << tareas[i].nombre
                         << (tareas[i].completada ? " [Completada]\n" : " [Pendiente]\n");
                }
            }
            break;
        }

        case 3: {
            int num;
            cout << "Número de la tarea a completar: ";
            cin >> num;

            if (num > 0 && num <= tareas.size()) {
                tareas[num - 1].completada = true;
                cout << "Tarea marcada como completada.\n";
            } else {
                cout << "Número inválido.\n";
            }
            break;
        }

        case 4:
            cout << "Saliendo...\n";
            break;

        default:
            cout << "Opción no válida. Inténtalo de nuevo.\n";
        }

    } while (opcion != 4);

    return 0;
}
