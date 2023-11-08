SEM_13POO


import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        List<Alumno> alumnos = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Agregar alumno");
            System.out.println("2. Ver y modificar alumno");
            System.out.println("3. Eliminar alumno");
            System.out.println("4. Buscar alumno por identificación");
            System.out.println("5. Mostrar todos los alumnos");
            System.out.println("6. Salir");
            System.out.print("Ingrese una opción: ");
            int opcion = scanner.nextInt();
            scanner.nextLine(); // Consumir el salto de línea después de leer la opción

            switch (opcion) {
                case 1:
                    System.out.print("Ingrese el nombre del alumno: ");
                    String nombre = scanner.nextLine();
                    System.out.print("Ingrese el apellido del alumno: ");
                    String apellido = scanner.nextLine();
                    System.out.print("Ingrese el número de identificación del alumno: ");
                    String identificacion = scanner.nextLine();
                    System.out.print("Ingrese la fecha de nacimiento del alumno: ");
                    String fechaNacimiento = scanner.nextLine();
                    System.out.print("Ingrese la dirección del alumno: ");
                    String direccion = scanner.nextLine();

                    Alumno alumno = new Alumno(nombre, apellido, identificacion, fechaNacimiento, direccion);
                    alumnos.add(alumno);
                    System.out.println("Alumno agregado correctamente.");
                    break;
                case 2:
                    System.out.print("Ingrese el número de identificación del alumno a modificar: ");
                    String identificacionModificar = scanner.nextLine();
                    Alumno alumnoModificar = buscarAlumnoPorIdentificacion(alumnos, identificacionModificar);
                    if (alumnoModificar != null) {
                        System.out.println("Información del alumno:");
                        System.out.println("Nombre: " + alumnoModificar.getNombre());
                        System.out.println("Apellido: " + alumnoModificar.getApellido());
                        System.out.println("Número de identificación: " + alumnoModificar.getIdentificacion());
                        System.out.println("Fecha de nacimiento: " + alumnoModificar.getFechaNacimiento());
                        System.out.println("Dirección: " + alumnoModificar.getDireccion());

                        System.out.println("Ingrese los nuevos datos del alumno:");
                        System.out.print("Nombre: ");
                        alumnoModificar.setNombre(scanner.nextLine());
                        System.out.print("Apellido: ");
                        alumnoModificar.setApellido(scanner.nextLine());
                        System.out.print("Número de identificación: ");
                        alumnoModificar.setIdentificacion(scanner.nextLine());
                        System.out.print("Fecha de nacimiento: ");
                        alumnoModificar.setFechaNacimiento(scanner.nextLine());
                        System.out.print("Dirección: ");
                        alumnoModificar.setDireccion(scanner.nextLine());

                        System.out.println("Alumno modificado correctamente.");
                    } else {
                        System.out.println("No se encontró ningún alumno con ese número de identificación.");
                    }
                    break;
                case 3:
                    System.out.print("Ingrese el número de identificación del alumno a eliminar: ");
                    String identificacionEliminar = scanner.nextLine();
                    Alumno alumnoEliminar = buscarAlumnoPorIdentificacion(alumnos, identificacionEliminar);
                    if (alumnoEliminar != null) {
                        alumnos.remove(alumnoEliminar);
                        System.out.println("Alumno eliminado correctamente.");
                    } else {
                        System.out.println("No se encontró ningún alumno con ese número de identificación.");
                    }
                    break;
                case 4:
                    System.out.print("Ingrese el número de identificación del alumno a buscar: ");
                    String identificacionBuscar = scanner.nextLine();
                    Alumno alumnoBuscar = buscarAlumnoPorIdentificacion(alumnos, identificacionBuscar);
                    if (alumnoBuscar != null) {
                        System.out.println("Información del alumno:");
                        System.out.println("Nombre: " + alumnoBuscar.getNombre());
                        System.out.println("Apellido: " + alumnoBuscar.getApellido());
                        System.out.println("Número de identificación: " + alumnoBuscar.getIdentificacion());
                        System.out.println("Fecha de nacimiento: " + alumnoBuscar.getFechaNacimiento());
                        System.out.println("Dirección: " + alumnoBuscar.getDireccion());
                    } else {
                        System.out.println("No se encontró ningún alumno con ese número de identificación.");
                    }
                    break;
                case 5:
                    System.out.println("Lista de alumnos:");
                    for (Alumno a : alumnos) {
                        System.out.println("Nombre: " + a.getNombre());
                        System.out.println("Apellido: " + a.getApellido());
                        System.out.println("Número de identificación: " + a.getIdentificacion());
                        System.out.println("Fecha de nacimiento: " + a.getFechaNacimiento());
                        System.out.println("Dirección: " + a.getDireccion());
                        System.out.println("-------------------------");
                    }
                    break;
                case 6:
                    System.out.println("¡Hasta luego!");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Opción inválida. Por favor, ingrese una opción válida.");
                    break;
            }
        }
    }

    public static Alumno buscarAlumnoPorIdentificacion(List<Alumno> alumnos, String identificacion) {
        for (Alumno alumno : alumnos) {
            if (alumno.getIdentificacion().equals(identificacion)) {
                return alumno;
            }
        }
        return null;
    }
}

class Alumno {
    private String nombre;
    private String apellido;
    private String identificacion;
    private String fechaNacimiento;
    private String direccion;

    public Alumno(String nombre, String apellido, String identificacion, String fechaNacimiento, String direccion) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.identificacion = identificacion;
        this.fechaNacimiento = fechaNacimiento;
        this.direccion = direccion;
    }

    // Getters y setters

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getApellido() {
        return apellido;
    }

    public void setApellido(String apellido) {
        this.apellido = apellido;
    }

    public String getIdentificacion() {
        return identificacion;
    }

    public void setIdentificacion(String identificacion) {
        this.identificacion = identificacion;
    }

    public String getFechaNacimiento() {
        return fechaNacimiento;
    }

    public void setFechaNacimiento(String fechaNacimiento) {
        this.fechaNacimiento = fechaNacimiento;
    }

    public String getDireccion() {
        return direccion;
    }

    public void setDireccion(String direccion) {
        this.direccion = direccion;
    }
}
