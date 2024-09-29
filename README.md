# Tasks-2

//*1.	Создайте метод, который принимает 2 строки и возвращает строку,
// состоящую из символов, входящих в 1 строку, но не входящих во 2.


public class duplicateChars {
    public static String findduplicateChars(String str1, String str2) {
        StringBuilder result = new StringBuilder();
        for (char c : str1.toCharArray()) {
            if (!str2.contains(String.valueOf(c))) {
                result.append(c);
            }
        }
        return result.toString();
    }

    public static void main(String[] args) {
        String str1 = "HI";
        String str2 = "hi";

        String duplicateChars = findduplicateChars(str1, str2);
        System.out.println("Символы, которые есть в первой строке, но нет во второй: " + duplicateChars);
    }
}



//*2.	Создайте метод, который принимает целочисленный массив
// и возвращает количество нечетных чисел, кратных 3.

public class dividedByThree {
    public static int countdividedByThree(int[] arr) {
        int count = 0; // Объявляем count внутри метода
        for (int num : arr) {
            if (num % 3 == 0) { // Проверка на кратность 3
                count++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        int[] numbers = {3, 12, 7, 81, 52};
        int count = countdividedByThree(numbers);
        System.out.println("Количество чисел, кратных 3: " + count); // Вывод: 5
    }
}


//*3.	Создайте метод, который принимает строку с ФИО и преобразует в библиографическое форматирование

public class getInitials {
    public static String getInitials(String fullName) {
        String[] parts  = fullName.split(" ");
        if (parts.length>=3) {
            return
                    parts[1].substring(0,1).toUpperCase()+"." +
                            parts[2].substring(0,1).toUpperCase()+"." +
                            parts[0] + " ";
        }else  {
            return fullName;
        }
    }

    public static void main (String[] args) {

        String fullName1 = "Максимова Мария Алексеевна";
        String fullName2= "Малицкий Алексей Семёнович";


        System.out.println (getInitials(fullName1));
        System.out.println (getInitials(fullName2));
    }
}

//*4.4.	Создайте функцию, которая принимает массив вещественных чисел и возвращает новый массив,
// в котором все элементы нормализованы. Нормализация массива — это процесс преобразования всех элементов
// таким образом, чтобы их значения находились в диапазоне от 0 до 1, причём минимальное значение становится 0,
// а максимальное — 1.
//Для нормализации используйте формулу: x’ = (x - min) / (max - min), где x – исходное значение элемента,
// min – минимальное значение в массиве, max – максимальное значение в массиве.*/

import java.util.Arrays;

public class Normalizator {

    public static double[] normalizator(double[] arr) {
        if (arr.length == 0) {
            return new double[0];
        }

        double min = arr[0];
        double max = arr[0];

        for (double num : arr) {
            if (num < min) {
                min = num;
            }
            if (num > max) {
                max = num;
            }
        }

        double[] normalizedArray = new double[arr.length];
        if (max - min == 0) { // Check for equal elements
            Arrays.fill(normalizedArray, 0); // Set all to 0
        } else {
            for (int i = 0; i < arr.length; i++) {
                normalizedArray[i] = (arr[i] - min) / (max - min);
            }
        }

        return normalizedArray;
    }

    public static void main(String[] args) {
        double[] arr1 = {3.5, 7.0, 1.5, 9.0, 5.5};
        double[] normalizedArr1 = normalizator(arr1);
        System.out.println("Нормализованный массив: " + Arrays.toString(normalizedArr1));

        double[] arr2 = {10.0, 10.0, 10.0, 10.0};
        double[] normalizedArr2 = normalizator(arr2);
        System.out.println("Нормализованный массив: " + Arrays.toString(normalizedArr2));
    }
}


//5.	Создайте метод, который берет массив вещественных чисел и возвращает «сжатую» версию массива,
// чьи элементы упорядочены по возрастанию и не содержат нулей.

import java.util.Arrays;

public class CompressedNums {

    public static double[] compressedNums(double[] arr) {
        if (arr.length == 0) {
            return new double[0]; // Возвращаем пустой массив, если исходный пустой
        }

        // Удаляем нули из массива
        double[] nonZeroArray = Arrays.stream(arr)
                .filter(num -> num != 0)
                .toArray();

        // Сортируем массив по возрастанию
        Arrays.sort(nonZeroArray);

        return nonZeroArray;
    }

    public static void main(String[] args) {
        double[] arr1 = {1.6, 0, 212.3, 34.8, 0, 27.5};
        double[] compressedArr1 = compressedNums(arr1);
        System.out.println("Сжатый массив: " + Arrays.toString(compressedArr1));

        double[] arr2 = {1, 27, 34, 212};
        double[] compressedArr2 = compressedNums(arr2);
        System.out.println("Сжатый массив: " + Arrays.toString(compressedArr2));
    }
}

//6.	Создайте метод, который принимает строку в формате CamelCase и преобразует ее в формате SnakeCase.

public class camelToSnake {
    public static String camelToSnake(String camelCase) {
        StringBuilder snakeCase = new StringBuilder();
        for (int i = 0; i < camelCase.length(); i++) {
            char c = camelCase.charAt(i);
            if (Character.isUpperCase(c)) {
                snakeCase.append('_');
                snakeCase.append(Character.toLowerCase(c));
            } else {
                snakeCase.append(c);
            }
        }
        return snakeCase.toString();
    }

    public static void main(String[] args) {
        String camelCase = "helloWorld";
        String snakeCase = camelToSnake(camelCase);
        System.out.println(snakeCase); // Вывод: hello_world
    }
}

//7.	Создайте метод, который принимает массив целых чисел и возвращает второй по величине элемент.

import java.util.Arrays;

public class SecondBiggest {

    public static int secondBiggest(int[] arr) {
        if (arr.length < 2) {
            throw new IllegalArgumentException("Массив должен содержать не менее двух элементов.");
        }

        // Сортируем массив по возрастанию
        Arrays.sort(arr);

        // Возвращаем второй с конца элемент (второй по величине)
        return arr[arr.length - 2];
    }

    public static void main(String[] args) {
        int[] numbers = {3, 5, 8, 1, 2, 4};
        int secondBiggestNumber = secondBiggest(numbers);
        System.out.println("Второй по величине элемент: " + secondBiggestNumber); // Вывод: 5
    }
}

//8.Создайте метод, принимающий строку и маркерный символ. Верните строку, в которой символы,
// находящиеся между парой маркерных символов, развернуты в обратном порядке.

public class LocalReverse {

    public static String localReverse(String str, char marker) {
        StringBuilder result = new StringBuilder();
        int startIndex = -1;
        int endIndex = -1;

        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == marker) {
                if (startIndex == -1) {
                    startIndex = i;
                } else {
                    endIndex = i;
                    result.append(str.substring(0, startIndex));
                    result.append(new StringBuilder(str.substring(startIndex + 1, endIndex)).reverse().toString());
                    result.append(str.substring(endIndex));
                    startIndex = -1; // Сброс для следующей пары маркеров
                }
            }
        }

        // Если остались необработанные символы
        if (startIndex != -1) {
            result.append(str.substring(0, startIndex));
            result.append(new StringBuilder(str.substring(startIndex + 1)).reverse().toString());
        } else {
            result.append(str); // Если нет маркеров, возвращаем исходную строку
        }

        return result.toString();
    }
    public static void main(String[] args) {
        String str1 = "bbabab";
        char marker1 = 'a';
        System.out.println(localReverse(str1, marker1)); // Вывод: baboab

        String str2 = "hello world";
        char marker2 = 'l';
        System.out.println(localReverse(str2, marker2)); // Вывод: hellow orld
    }
}

//9.	Создайте метод, который принимает три целочисленных аргумента и возвращает количество целых чисел,
// имеющих одинаковое значение.


public class EqualNumbers {

    public static int countEqualPairs(int a, int b, int c) {
        int count = 0;
        if (a == b && a == c) { // Проверка всех трех чисел
            count = 3; // Все три числа равны
        } else if (a == b || a == c || b == c) { // Проверка пар
            count = 2; // Две пары равны
        }
        return count;
    }

    public static void main(String[] args) {
        System.out.println(countEqualPairs(1, 2, 3)); // Вывод: 0
        System.out.println(countEqualPairs(1, 1, 1)); // Вывод: 3
        System.out.println(countEqualPairs(1, 1, 2)); // Вывод: 2
        System.out.println(countEqualPairs(8, 1, 8)); // Вывод: 2
    }
}

//10. Создайте функцию, которая принимает две строки и определяет, являются ли они анаграммами.

import java.util.Arrays;

public class isAnagram {
    public static boolean isAnagram(String str1, String str2) {
        if (str1.length() != str2.length()) {
            return false; // Длины строк должны быть одинаковы
        }

        // Преобразуем строки в нижний регистр для игнорирования регистра
        str1 = str1.toLowerCase();
        str2 = str2.toLowerCase();

        // Сортируем символы в каждой строке
        char[] charArray1 = str1.toCharArray();
        Arrays.sort(charArray1);
        char[] charArray2 = str2.toCharArray();
        Arrays.sort(charArray2);

        // Сравниваем отсортированные массивы символов
        return Arrays.equals(charArray1, charArray2);
    }

    public static void main(String[] args) {
        System.out.println(isAnagram("LISTEN", "silent")); // Вывод: true
        System.out.println(isAnagram("Eleven plus two?", "Twelve plus one!"));
        System.out.println(isAnagram("hello", "world"));  // Вывод: false
    }
}



