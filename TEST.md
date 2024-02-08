La compilación se ha realizado online, usando: https://www.mycompiler.io/es/new/java
(se puede introducir entradas, solo necesario en Test 1)

----------- Test 1 -------------

import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int numero = scanner.nextInt();
        boolean isPar = numero % 2 == 0;
        
        if (isPar) { 
            System.out.println("Número par");

            for (int i = numero; i >= 0; i -= 2) {
                System.out.println(i);
            }
        } else { 
            System.out.println("Número impar");

            for (int i = numero; i >= 1; i -= 2) {
                System.out.println(i);
            }
        }

        scanner.close();
    }
}


----------- Test 2 -------------

import java.util.ArrayList;
import java.util.List;

class Persona {
    String sexo;
    int edad;

    public Persona(String sexo, int edad) {
        this.sexo = sexo;
        this.edad = edad;
    }
}

class Main {
    public static void main(String[] args) {
        List<Persona> personas = leerPersonas();

        int mayoresDeEdad = 0;
        int menoresDeEdad = 0;
        int hombresMayoresDeEdad = 0;
        int mujeresMenoresDeEdad = 0;

        for (Persona p : personas) {
            if (p.edad >= 18) {
                mayoresDeEdad++;
                if ("masculino".equals(p.sexo)) {
                    hombresMayoresDeEdad++;
                }
            } else {
                menoresDeEdad++;
                if ("femenino".equals(p.sexo)) {
                    mujeresMenoresDeEdad++;
                }
            }
        }

        int totalPersonas = personas.size();
        int totalMujeres = (int) personas.stream().filter(p -> "femenino".equals(p.sexo)).count();
        double porcentajeMayoresDeEdad = (mayoresDeEdad * 100.0) / totalPersonas;
        double porcentajeMujeres = (totalMujeres * 100.0) / totalPersonas;

        System.out.println("Personas mayores de edad: " + mayoresDeEdad);
        System.out.println("Personas menores de edad: " + menoresDeEdad);
        System.out.println("Personas masculinas mayores de edad: " + hombresMayoresDeEdad);
        System.out.println("Personas femeninas menores de edad: " + mujeresMenoresDeEdad);
        System.out.println("% personas mayores de edad: " + porcentajeMayoresDeEdad + "%");
        System.out.println("% de mujeres: " + porcentajeMujeres + "%");
    }

    private static List<Persona> leerPersonas() {
        List<Persona> personas = new ArrayList<>();
        int menorEdad = 17;
        int mayorEdad = 20;
        
        for (int i = 0; i < 50; i++) {
            String sexo = (i % 2 == 0) ? "masculino" : "femenino";
            int edad = (i % 3 == 0) ? menorEdad : mayorEdad; 
            personas.add(new Persona(sexo, edad));
        }
        return personas;
    }
}


----------- Test 3 -------------

import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        int HORAS_TRABAJADAS = 40;
        double TARIFA = 12;

        double salario = calcularSalario(HORAS_TRABAJADAS, TARIFA);

        System.out.println("El salario del trabajador es: " + salario + "€");
    }

    private static double calcularSalario(int horasTrabajadas, double tarifa) {
        int horasBase = 40;
        double incremento = 1.5; // Incremento del 50%
        double salario;

        if (horasTrabajadas > horasBase) {
            int horasExtras = horasTrabajadas - horasBase;
            salario = (horasBase * tarifa) + (horasExtras * tarifa * incremento);
        } else {
            salario = horasTrabajadas * tarifa;
        }

        return salario;
    }
}

