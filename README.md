import java.util.*;

class Estudiante {
    private String nombre;
    private int edad;
    private double nota;
    
    public Estudiante(String nombre, int edad, double nota) {
        this.nombre = nombre;
        this.edad = edad;
        this.nota = nota;
    }
    
    public String mostrarInfo() {
        return nombre + " - Edad: " + edad + " - Nota: " + nota;
    }
    
    public boolean estaAprobado() {
        return nota >= 6.0;
    }
}

public class SistemaEstudiantes {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        List<Estudiante> estudiantes = new ArrayList<>();
        int cantidad;
        
        do {
            System.out.print("Cantidad estudiantes: ");
            cantidad = sc.nextInt();
            sc.nextLine();
            if(cantidad <= 0) {
                System.out.println("Debe ser mayor que 0");
            }
        } while(cantidad <= 0);
        
        for(int i = 0; i < cantidad; i++) {
            System.out.println("Estudiante " + (i+1));
            System.out.print("Nombre: ");
            String nombre = sc.nextLine();
            System.out.print("Edad: ");
            int edad = sc.nextInt();
            System.out.print("Nota: ");
            double nota = sc.nextDouble();
            sc.nextLine();
            
            estudiantes.add(new Estudiante(nombre, edad, nota));
        }
        
        int opcion;
        do {
            System.out.println("1. Todos");
            System.out.println("2. Aprobados");
            System.out.println("0. Salir");
            System.out.print("Opcion: ");
            opcion = sc.nextInt();
            sc.nextLine();
            
            if(opcion == 1) {
                System.out.println("TODOS:");
                for(Estudiante e : estudiantes) {
                    System.out.println(e.mostrarInfo());
                }
            } else if(opcion == 2) {
                System.out.println("APROBADOS:");
                boolean hay = false;
                for(Estudiante e : estudiantes) {
                    if(e.estaAprobado()) {
                        System.out.println(e.mostrarInfo());
                        hay = true;
                    }
                }
                if(!hay) {
                    System.out.println("Ninguno aprobado");
                }
            }
        } while(opcion != 0);
        
        sc.close();
    }
}
