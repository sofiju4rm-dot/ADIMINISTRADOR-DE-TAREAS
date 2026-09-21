# ADIMINISTRADOR-DE-TAREAS
public partial class Program
{
    private static void EjecutarAdministrador(string[] args)
    {
        List<string> tareas = [];
        List<int> IDS = [];
        List<string> estados = [];
        int siguienteID = 1;
        int opción = 0;

        do
        {
            Console.WriteLine("___ADMINISTRADOR DE TAREAS___");
            Console.WriteLine("1.Agregar tarea");
            Console.WriteLine("2.Ver tareas");
            Console.WriteLine("3.Cambiar estado de tarea");
            Console.WriteLine("4.Eliminar tarea");
            Console.WriteLine("5.Salir");
            Console.Write("Selecciona una opción: ");
            opción = int.TryParse(Console.ReadLine(), out opción) ? opción : 0;

            if (opción == 1)
            {
                Console.Write("Escribe la tarea: ");
                string? tarea = Console.ReadLine();

                if (string.IsNullOrWhiteSpace(tarea))
                {
                    Console.WriteLine("La tarea no puede estar vacía.");
                }
                else
                {
                    tareas.Add(tarea.Trim());
                    IDS.Add(siguienteID);
                    estados.Add("Pendiente");

                    Console.WriteLine("Tarea agregada correctamente.");
                    Console.WriteLine("ID de la tarea: " + siguienteID);
                    siguienteID++;
                }

                Console.WriteLine("Presiona cualquier tecla para continuar...");
                Console.ReadKey();
                Console.Clear();
            }
            else if (opción == 2)
            {
                if (tareas.Count == 0)
                {
                    Console.WriteLine("No hay tareas registradas.");
                }
                else
                {
                    Console.WriteLine("\n___TAREAS___");

                    for (int i = 0; i < tareas.Count; i++)
                    {
                        Console.WriteLine(
                            "ID: " + IDS[i] +
                            " | Tarea: " + tareas[i] +
                            " | Estado: " + estados[i]
                        );
                    }
                }

                Console.WriteLine("\nPresiona cualquier tecla para continuar...");
                Console.ReadKey();
                Console.Clear();
            }
            else if (opción == 3)
            {
                if (tareas.Count == 0)
                {
                    Console.WriteLine("No hay tareas registradas.");
                }
                else
                {
                    Console.WriteLine("\n___TAREAS___");

                    for (int i = 0; i < tareas.Count; i++)
                    {
                        Console.WriteLine(
                            "ID: " + IDS[i] +
                            " | Tarea: " + tareas[i] +
                            " | Estado: " + estados[i]
                        );
                    }

                    Console.Write("\nEscribe el ID de la tarea: ");
                    int id;
                    if (!int.TryParse(Console.ReadLine(), out id))
                    {
                        Console.WriteLine("ID inválido.");
                    }
                    else
                    {
                        int posicionEncontrada = -1;

                        for (int i = 0; i < IDS.Count; i++)
                        {
                            if (IDS[i] == id)
                            {
                                posicionEncontrada = i;
                                break;
                            }
                        }

                        if (posicionEncontrada == -1)
                        {
                            Console.WriteLine("No existe una tarea con ese ID.");
                        }
                        else
                        {
                            Console.WriteLine("\nSelecciona el nuevo estado:");
                            Console.WriteLine("1. Pendiente");
                            Console.WriteLine("2. En proceso");
                            Console.WriteLine("3. Finalizada");
                            Console.Write("Selecciona una opción: ");

                            int nuevoEstado;
                            if (!int.TryParse(Console.ReadLine(), out nuevoEstado))
                            {
                                Console.WriteLine("Estado inválido.");
                            }
                            else if (nuevoEstado == 1)
                            {
                                estados[posicionEncontrada] = "Pendiente";
                                Console.WriteLine("Estado cambiado correctamente.");
                            }
                            else if (nuevoEstado == 2)
                            {
                                estados[posicionEncontrada] = "En proceso";
                                Console.WriteLine("Estado cambiado correctamente.");
                            }
                            else if (nuevoEstado == 3)
                            {
                                estados[posicionEncontrada] = "Finalizada";
                                Console.WriteLine("Estado cambiado correctamente.");
                            }
                            else
                            {
                                Console.WriteLine("Estado inválido.");
                            }
                        }
                    }
                }

                Console.WriteLine("\nPresiona cualquier tecla para continuar...");
                Console.ReadKey();
                Console.Clear();
            }
            else if (opción == 4)
            {
                if (tareas.Count == 0)
                {
                    Console.WriteLine("No hay tareas registradas.");
                }
                else
                {
                    Console.WriteLine("\n___TAREAS___");

                    for (int i = 0; i < tareas.Count; i++)
                    {
                        Console.WriteLine(
                            "ID: " + IDS[i] +
                            " | Tarea: " + tareas[i] +
                            " | Estado: " + estados[i]
                        );
                    }

                    Console.Write("\nEscribe el ID de la tarea que quieres eliminar: ");
                    int id;
                    if (!int.TryParse(Console.ReadLine(), out id))
                    {
                        Console.WriteLine("ID inválido.");
                    }
                    else
                    {
                        int posicionEncontrada = -1;

                        for (int i = 0; i < IDS.Count; i++)
                        {
                            if (IDS[i] == id)
                            {
                                posicionEncontrada = i;
                                break;
                            }
                        }

                        if (posicionEncontrada == -1)
                        {
                            Console.WriteLine("No existe una tarea con ese ID.");
                        }
                        else
                        {
                            tareas.RemoveAt(posicionEncontrada);
                            IDS.RemoveAt(posicionEncontrada);
                            estados.RemoveAt(posicionEncontrada);
                            Console.WriteLine("Tarea eliminada correctamente.");
                        }
                    }
                }

                Console.WriteLine("\nPresiona cualquier tecla para continuar...");
                Console.ReadKey();
                Console.Clear();
            }
            else if (opción == 5)
            {
                Console.WriteLine("Saliendo del programa...");
            }
            else
            {
                Console.WriteLine("Opción inválida.");
                Console.WriteLine("Presiona cualquier tecla para continuar...");
                Console.ReadKey();
                Console.Clear();
            }
        } while (opción != 5);
    }
}
