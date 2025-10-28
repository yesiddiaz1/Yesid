[import java.util.java](https://github.com/user-attachments/files/23193938/import.java.util.java)
import java.util.ArrayList;

class Producto {
    protected String nombre;
    protected double precio;

    public Producto(String nombre, double precio) {
        this.nombre = nombre;
        this.precio = precio;
    }

    public void mostrarInfo() {
        System.out.println("Producto: " + nombre + ", Precio: $" + precio);
    }
}

class Libro extends Producto {
    private String autor;
    private String isbn;
    private int cantidad;

    public Libro(String nombre, String autor, double precio, int cantidad, String isbn) {
        super(nombre, precio);
        this.autor = autor;
        this.cantidad = cantidad;
        this.isbn = isbn;
    }

    @Override
    public void mostrarInfo() {
        System.out.println("Libro: " + nombre + ", Autor: " + autor +
                           ", Precio: $" + precio + ", Cantidad: " + cantidad + 
                           ", ISBN: " + isbn);
    }

    public double valorTotal() {
        return precio * cantidad;
    }

    public int getCantidad() {
        return cantidad;
    }
}

public class Inventario {
    public static void main(String[] args) {
        ArrayList<Libro> libros = new ArrayList<>();

        libros.add(new Libro("Java Básico", "Juan Pérez", 25.50, 10, "123-ABC"));
        libros.add(new Libro("Estructuras de Datos", "Ana Gómez", 30.00, 3, "456-DEF"));
        libros.add(new Libro("Algoritmos Avanzados", "Luis Martínez", 40.00, 0, "789-GHI"));

        double valorInventario = 0;
        System.out.println("Listado de libros en inventario:");
        for (Libro libro : libros) {
            libro.mostrarInfo();  // Polimorfismo
            valorInventario += libro.valorTotal();  // Operación
            if (libro.getCantidad() < 5) {
                System.out.println("  -> Atención: Stock bajo!");
            }
        }

        System.out.println("\nValor total del inventario: $" + valorInventario);
    }
}
