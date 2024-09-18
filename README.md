# lab1shpringer
import java.util.Scanner;
import java.io.FileWriter;
import java.io.IOException;

/**
 * Клас для генерації зубчастого масиву згідно заданих параметрів.
 *
 * @author Шпрінгер Соломія
 * 
 */
public class lab1shpringer302 {

    public static void main(String[] args) throws IOException {
        Scanner scanner = new Scanner(System.in);

        // Отримання розміру матриці та символу-заповнювача від користувача
        System.out.print("Введіть розмір квадратної матриці: ");
        int size = scanner.nextInt();

        if (size <= 0) {
            System.err.println("Розмір матриці має бути додатним числом.");
            return;
        }

        System.out.print("Введіть символ-заповнювач: ");
        String fillString = scanner.next();

        if (fillString.length() != 1) {
            System.err.println("Введіть лише один символ-заповнювач.");
            return;
        }
        char fillChar = fillString.charAt(0);

        // Генерація зубчастого масиву
        char[][] matrix = generateMatrix(size, fillChar);

        // Виведення матриці на екран
        printMatrix(matrix);

        // Запис матриці у файл
        writeMatrixToFile(matrix, "output.txt");
    }

    /**
     * Генерує зубчастий масив з заданими параметрами.
     *
     * @param size Розмір квадратної матриці.
     * @param fillChar Символ для заповнення.
     * @return Згенерований зубчастий масив.
     */
    	
    	 private static char[][] generateMatrix(int size, char fillChar) {
    	        char[][] matrix = new char[size][size];
    	        for (int i = 0; i < size; i++) {
    	            for (int j = 0; j < size; j++) {
    	                // Логіка для створення двох перевернутих трикутників
    	                if ( (i + j >= size - 1 && i <= j||i + j <= size - 1 && i >= j)) {
    	                    matrix[j][i] = fillChar;
    	                } else {
    	                    matrix[j][i] = ' ';
    	                }
    	            }
    	        }
    	        return matrix;
    	    }

    	    private static void printMatrix(char[][] matrix) {
    	        for (char[] row : matrix) {
    	            for (char c : row) {
    	                System.out.print(c);
    	            }
    	            System.out.println();
    	        }
    	    }

    	    private static void writeMatrixToFile(char[][] matrix, String fileName) throws IOException {
    	        try (FileWriter writer = new FileWriter(fileName)) {
    	            for (char[] row : matrix) {
    	                for (char c : row) {
    	                    writer.write(c);
    	                }
    	                writer.write(System.lineSeparator());
    	                
    	            }
    	        }
    	    }
    	}
      

