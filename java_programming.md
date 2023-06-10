# Java Programming Library

## I have a list of Employee object.I want to sort the list based on the employee age. Use the Stream API and code for it

<br>


Sure! Here's an example code that uses the Stream API to sort a list of Employee objects based on their age:

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // Create a list of Employee objects
        List<Employee> employees = new ArrayList<>();
        employees.add(new Employee("John", 25));
        employees.add(new Employee("Alice", 30));
        employees.add(new Employee("Bob", 22));
        employees.add(new Employee("Jane", 28));

        // Sort the list based on employee age
        List<Employee> sortedList = employees.stream()
                .sorted(Comparator.comparingInt(Employee::getAge))
                .toList();

        // Print the sorted list
        for (Employee employee : sortedList) {
            System.out.println(employee.getName() + " - " + employee.getAge());
        }
    }
}

class Employee {
    private String name;
    private int age;

    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```
<br>
In the above code, we have a list of Employee objects. We use the <code>stream()</code> method on the list to obtain a stream of Employee objects. Then, we use the <code>sorted()</code> method along with a <code>Comparator</code> to specify the sorting order based on the employee's age. The <code>Comparator.comparingInt()</code> method is used to create a comparator based on the employee's age. Finally, we collect the sorted stream back into a list using the <code>toList()</code> method.

The resulting sorted list is then printed to the console, showing the employees sorted by their age in ascending order.

<br>


## What if I want to sort on both age and name. Code for it

<br>


If you want to sort the list of Employee objects based on both age and name, you can modify the comparator used in the <code>sorted()</code> method to include multiple sorting criteria. Here's an example code that sorts the list based on age and then name:

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // Create a list of Employee objects
        List<Employee> employees = new ArrayList<>();
        employees.add(new Employee("John", 25));
        employees.add(new Employee("Alice", 30));
        employees.add(new Employee("Bob", 22));
        employees.add(new Employee("Jane", 28));

        // Sort the list based on employee age and then name
        List<Employee> sortedList = employees.stream()
                .sorted(Comparator.comparingInt(Employee::getAge)
                        .thenComparing(Employee::getName))
                .toList();

        // Print the sorted list
        for (Employee employee : sortedList) {
            System.out.println(employee.getName() + " - " + employee.getAge());
        }
    }
}

class Employee {
    private String name;
    private int age;

    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```
<br>
In the above code, the <code>sorted()</code> method is modified to use <code>Comparator.comparingInt()</code> for sorting based on age, and then <code>thenComparing()</code> is used to specify the secondary sorting criteria based on the employee's name. The <code>thenComparing()</code> method allows us to chain multiple comparators together to define a combined sorting order.

The resulting sorted list will be first sorted by age, and for employees with the same age, it will further sort them based on their names in ascending order.

<br>


## Consider I have a list of Employees. I want to find the Employee who gets second largest salary. Use Stream API to write the code

<br>


To find the Employee with the second-largest salary in a list of Employees using the Stream API, you can follow this example code:

```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // Create a list of Employee objects
        List<Employee> employees = new ArrayList<>();
        employees.add(new Employee("John", 2500));
        employees.add(new Employee("Alice", 3000));
        employees.add(new Employee("Bob", 2200));
        employees.add(new Employee("Jane", 2800));

        // Find the Employee with the second-largest salary
        Employee secondLargestSalaryEmployee = employees.stream()
                .sorted(Comparator.comparingInt(Employee::getSalary).reversed())
                .skip(1) // Skip the first Employee with the largest salary
                .findFirst()
                .orElse(null);

        // Print the Employee with the second-largest salary
        if (secondLargestSalaryEmployee != null) {
            System.out.println("Employee with second-largest salary: " + secondLargestSalaryEmployee.getName());
        } else {
            System.out.println("No Employee found.");
        }
    }
}

class Employee {
    private String name;
    private int salary;

    public Employee(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }

    public String getName() {
        return name;
    }

    public int getSalary() {
        return salary;
    }
}
```

In the above code, we have a list of Employee objects with their respective salaries. We use the <code>stream()</code> method on the list to obtain a stream of Employee objects. Then, we use the <code>sorted()</code> method with a <code>Comparator</code> to sort the Employees based on their salaries in descending order. The <code>reversed()</code> method is used to sort in descending order.

Next, we use the <code>skip(1)</code> method to skip the first Employee in the sorted stream, which corresponds to the Employee with the largest salary. Finally, we call the <code>findFirst()</code> method to get the first Employee in the remaining stream, which corresponds to the Employee with the second-largest salary.
The resulting Employee with the second-largest salary is then printed to the console.

<br>

## Consider I have list of String. I want to take out only those Strings which starts with 1. Use Stream API to code

To filter out only the Strings from a list that start with "1" using the Stream API, you can use the filter() method along with a lambda expression. Here's an example code:

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // Create a list of String objects
        List<String> strings = new ArrayList<>();
        strings.add("123");
        strings.add("456");
        strings.add("178");
        strings.add("234");
        strings.add("12345");

        // Filter out strings starting with "1"
        List<String> filteredStrings = strings.stream()
                .filter(s -> s.startsWith("1"))
                .toList();

        // Print the filtered strings
        for (String string : filteredStrings) {
            System.out.println(string);
        }
    }
}
```

In the above code, we have a list of String objects. We use the stream() method on the list to obtain a stream of String objects. Then, we use the filter() method along with a lambda expression s -> s.startsWith("1") to specify the filtering criteria. The lambda expression checks if each string starts with "1".

The filter() method retains only the elements that satisfy the given condition, in this case, the strings starting with "1". The resulting filtered strings are then collected into a new list using the toList() method.

Finally, we iterate over the filtered list and print each string to the console. In this example, the output will be:

```text
123
178
12345
```

These are the strings from the original list that start with "1".


<br>

## Write a java program to find duplicate elements in an array?

<br>

To find duplicate elements in an array, you can use various approaches in Java. Here's a traditional solution that uses nested loops:
Traditional Solution:

```java
import java.util.ArrayList;
import java.util.List;

public class DuplicateElements {
    public static List<Integer> findDuplicates(int[] arr) {
        List<Integer> duplicates = new ArrayList<>();
        
        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] == arr[j] && !duplicates.contains(arr[i])) {
                    duplicates.add(arr[i]);
                    break;
                }
            }
        }
        
        return duplicates;
    }

    public static void main(String[] args) {
        int[] array = { 1, 2, 3, 4, 2, 5, 6, 7, 8, 1, 3 };
        List<Integer> duplicateElements = findDuplicates(array);

        System.out.println("Duplicate elements in the array: " + duplicateElements);
    }
}
```
Time Complexity: The time complexity of this solution is O(n^2) because of the nested loops.
Now, let's see a solution using Java 8 Stream API and Set:

Stream API Solution:

```java
import java.util.Arrays;
import java.util.HashSet;
import java.util.Set;
import java.util.stream.Collectors;

public class DuplicateElements {
    public static Set<Integer> findDuplicates(int[] arr) {
        Set<Integer> uniqueElements = new HashSet<>();
        return Arrays.stream(arr)
                .filter(e -> !uniqueElements.add(e))
                .boxed()
                .collect(Collectors.toSet());
    }

    public static void main(String[] args) {
        int[] array = { 1, 2, 3, 4, 2, 5, 6, 7, 8, 1, 3 };
        Set<Integer> duplicateElements = findDuplicates(array);

        System.out.println("Duplicate elements in the array: " + duplicateElements);
    }
}
```
Time Complexity: The time complexity of this solution is O(n) because it uses a Set to keep track of unique elements, which has an average constant time complexity for insertion and lookup.
Both solutions will output the duplicate elements in the given array. Feel free to run the code and verify the results.

<br>

## Write a java program to find second largest element in an array
of integers?

<br>


To find the second largest element in an array of integers, you can use the following Java program:

```java
public class SecondLargestElement {
    public static int findSecondLargest(int[] arr) {
        if (arr.length < 2) {
            throw new IllegalArgumentException("Array must have at least two elements");
        }

        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > largest) {
                secondLargest = largest;
                largest = arr[i];
            } else if (arr[i] > secondLargest && arr[i] != largest) {
                secondLargest = arr[i];
            }
        }

        if (secondLargest == Integer.MIN_VALUE) {
            throw new IllegalArgumentException("There is no second largest element in the array");
        }

        return secondLargest;
    }

    public static void main(String[] args) {
        int[] array = { 5, 2, 8, 9, 1, 3, 6 };
        int secondLargest = findSecondLargest(array);

        System.out.println("The second largest element in the array is: " + secondLargest);
    }
}
```
Time Complexity: The time complexity of this solution is O(n) because we iterate through the array once.
This program will output the second largest element in the given array of integers. Please note that the program assumes the array has at least two elements. Feel free to modify the array in the <code>main</code> method to test different cases.

<br>

## You have not provided the solution using Stream API

<br>


Apologies for missing out on the Stream API solution. Here's an alternative solution using Java 8 Stream API to find the second largest element in an array:

```java
import java.util.Arrays;

public class SecondLargestElement {
    public static int findSecondLargest(int[] arr) {
        if (arr.length < 2) {
            throw new IllegalArgumentException("Array must have at least two elements");
        }

        return Arrays.stream(arr)
                .distinct()
                .sorted()
                .skip(arr.length - 2)
                .findFirst()
                .orElseThrow(() -> new IllegalArgumentException("There is no second largest element in the array"));
    }

    public static void main(String[] args) {
        int[] array = { 5, 2, 8, 9, 1, 3, 6 };
        int secondLargest = findSecondLargest(array);

        System.out.println("The second largest element in the array is: " + secondLargest);
    }
}
```
Time Complexity: The time complexity of this solution is O(n log n) due to the sorting operation.
This program will also output the second largest element in the given array using the Stream API. As before, please ensure that the array has at least two elements when using this solution.

<br>

## Maximum consecutive one’s (or zeros) in a binary array?

<br>


To find the maximum consecutive ones or zeros in a binary array, you can use the following Java program:

```java
public class MaxConsecutiveOnesZeros {
    public static int findMaxConsecutive(int[] nums, int target) {
        int maxConsecutive = 0;
        int currentConsecutive = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                currentConsecutive++;
                maxConsecutive = Math.max(maxConsecutive, currentConsecutive);
            } else {
                currentConsecutive = 0;
            }
        }

        return maxConsecutive;
    }

    public static void main(String[] args) {
        int[] binaryArray = { 1, 1, 0, 1, 0, 0, 1, 1, 1, 0, 1, 1, 1 };
        int maxConsecutiveOnes = findMaxConsecutive(binaryArray, 1);
        int maxConsecutiveZeros = findMaxConsecutive(binaryArray, 0);

        System.out.println("Maximum consecutive ones: " + maxConsecutiveOnes);
        System.out.println("Maximum consecutive zeros: " + maxConsecutiveZeros);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the binary array.
This program will output the maximum consecutive ones and zeros in the given binary array. You can modify the binary array in the <code>main</code> method to test different cases.

<br>

## is there any other approach using Stream API, collections or in-built methods?

<br>


Yes, you can utilize the Stream API and in-built methods to find the maximum consecutive ones or zeros in a binary array. Here's an alternative solution:

```java
import java.util.Arrays;

public class MaxConsecutiveOnesZeros {
    public static int findMaxConsecutive(int[] nums, int target) {
        return Arrays.stream(nums)
                .reduce((count, num) -> num == target ? count + 1 : 0)
                .orElse(0);
    }

    public static void main(String[] args) {
        int[] binaryArray = { 1, 1, 0, 1, 0, 0, 1, 1, 1, 0, 1, 1, 1 };
        int maxConsecutiveOnes = findMaxConsecutive(binaryArray, 1);
        int maxConsecutiveZeros = findMaxConsecutive(binaryArray, 0);

        System.out.println("Maximum consecutive ones: " + maxConsecutiveOnes);
        System.out.println("Maximum consecutive zeros: " + maxConsecutiveZeros);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the binary array.
This program utilizes the <code>Arrays.stream(nums)</code> method to create a stream of elements from the binary array. Then, the <code>reduce</code> operation is used to calculate the maximum consecutive count based on the target element. The <code>orElse(0)</code> ensures that the result defaults to 0 if the array is empty.
Both traditional and Stream API solutions will give you the maximum consecutive ones and zeros in the binary array. Feel free to run the code and test it with different inputs.

<br>

## Write a java program to find all pairs of elements in an integer array whose sum is equal to a given number?

<br>


To find all pairs of elements in an integer array whose sum is equal to a given number, you can use the following Java program:

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class PairSum {
    public static List<List<Integer>> findPairs(int[] arr, int target) {
        List<List<Integer>> pairs = new ArrayList<>();
        Map<Integer, Integer> numFrequency = new HashMap<>();

        for (int num : arr) {
            int complement = target - num;
            if (numFrequency.containsKey(complement)) {
                int frequency = numFrequency.get(complement);
                for (int i = 0; i < frequency; i++) {
                    List<Integer> pair = new ArrayList<>();
                    pair.add(num);
                    pair.add(complement);
                    pairs.add(pair);
                }
            }
            numFrequency.put(num, numFrequency.getOrDefault(num, 0) + 1);
        }

        return pairs;
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 6, 3, 1, 7, 5, 9, 8, 2, 6 };
        int targetSum = 10;
        List<List<Integer>> pairs = findPairs(array, targetSum);

        System.out.println("Pairs with sum " + targetSum + ":");
        for (List<Integer> pair : pairs) {
            System.out.println(pair.get(0) + " + " + pair.get(1) + " = " + targetSum);
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program will find and output all pairs of elements in the given integer array that sum up to the target number. The program utilizes a HashMap to keep track of the frequency of numbers encountered while iterating through the array. By checking for the complement of each element, it identifies the pairs that fulfill the sum condition.
Feel free to modify the array and target sum in the <code>main</code> method to test different cases.

<br>

## is there any other approach using Stream API, collections or in-built methods?

<br>


Yes, you can use the Stream API and in-built methods to find all pairs of elements in an integer array whose sum is equal to a given number. Here's an alternative solution:

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class PairSum {
    public static List<List<Integer>> findPairs(int[] arr, int target) {
        List<List<Integer>> pairs = new ArrayList<>();

        Arrays.stream(arr)
                .distinct()
                .forEach(num -> {
                    int complement = target - num;
                    if (Arrays.stream(arr).filter(n -> n == complement).count() > 0) {
                        List<Integer> pair = new ArrayList<>();
                        pair.add(num);
                        pair.add(complement);
                        pairs.add(pair);
                    }
                });

        return pairs;
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 6, 3, 1, 7, 5, 9, 8, 2, 6 };
        int targetSum = 10;
        List<List<Integer>> pairs = findPairs(array, targetSum);

        System.out.println("Pairs with sum " + targetSum + ":");
        for (List<Integer> pair : pairs) {
            System.out.println(pair.get(0) + " + " + pair.get(1) + " = " + targetSum);
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the array.
This program utilizes the Stream API to iterate through the array and find pairs that sum up to the target number. It uses the <code>distinct()</code> method to ensure each number is considered only once. Then, for each number, it checks if the complement exists in the array using the <code>filter()</code> and <code>count()</code> methods.
Both the traditional and Stream API solutions will give you the pairs of elements that sum up to the target number. Feel free to run the code and test it with different inputs.

<br>

## Write a java program to find continuous sub array whose sum is equal to a given number?

<br>


To find a continuous subarray in an integer array whose sum is equal to a given number, you can use the following Java program:

```java
import java.util.ArrayList;
import java.util.List;

public class SubarraySum {
    public static List<Integer> findSubarray(int[] arr, int targetSum) {
        List<Integer> subarray = new ArrayList<>();
        int currentSum = 0;
        int start = 0;

        for (int i = 0; i < arr.length; i++) {
            currentSum += arr[i];

            while (currentSum > targetSum && start <= i) {
                currentSum -= arr[start];
                start++;
            }

            if (currentSum == targetSum) {
                for (int j = start; j <= i; j++) {
                    subarray.add(arr[j]);
                }
                break;
            }
        }

        return subarray;
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 6, 3, 1, 7, 5, 9, 8, 2, 6 };
        int targetSum = 14;
        List<Integer> subarray = findSubarray(array, targetSum);

        System.out.println("Continuous subarray with sum " + targetSum + ": " + subarray);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program will find and output the continuous subarray in the given integer array whose sum is equal to the target number. It uses two pointers, <code>start</code> and <code>i</code>, to track the current subarray. The program updates the <code>currentSum</code> by adding elements and adjusts the <code>start</code> pointer when the sum exceeds the target. If the sum becomes equal to the target, it adds the subarray elements to the result list and breaks the loop.
Feel free to modify the array and target sum in the <code>main</code> method to test different cases.

<br>

## Write a java program to find the intersection of two arrays?

<br>


To find the intersection of two arrays in Java, you can use the following program:

```java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class ArrayIntersection {
    public static int[] findIntersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> intersectionSet = new HashSet<>();

        for (int num : nums1) {
            set1.add(num);
        }

        for (int num : nums2) {
            if (set1.contains(num)) {
                intersectionSet.add(num);
            }
        }

        int[] intersection = new int[intersectionSet.size()];
        int index = 0;
        for (int num : intersectionSet) {
            intersection[index++] = num;
        }

        return intersection;
    }

    public static void main(String[] args) {
        int[] nums1 = { 2, 4, 6, 8, 10 };
        int[] nums2 = { 4, 8, 12, 16, 20 };

        int[] intersection = findIntersection(nums1, nums2);

        System.out.print("Intersection of the two arrays: ");
        for (int num : intersection) {
            System.out.print(num + " ");
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the larger array.
This program finds the intersection of two arrays by utilizing sets. It first creates a set (<code>set1</code>) and adds all elements from the first array to it. Then, it iterates over the second array and checks if each element exists in <code>set1</code>. If an element is found in both arrays, it is added to the <code>intersectionSet</code>. Finally, the <code>intersectionSet</code> is converted to an array and returned as the result.
You can modify the <code>nums1</code> and <code>nums2</code> arrays in the <code>main</code> method to test different cases.

<br>

## Write a java program to find a missing number in an integer array?

<br>


To find a missing number in an integer array in Java, you can use the following program:

```java
public class MissingNumber {
    public static int findMissingNumber(int[] nums) {
        int n = nums.length;
        int totalSum = (n + 1) * (n + 2) / 2; // Sum of numbers from 1 to n+1
        int arraySum = 0;

        for (int num : nums) {
            arraySum += num;
        }

        return totalSum - arraySum;
    }

    public static void main(String[] args) {
        int[] array = { 1, 2, 4, 6, 3, 7, 8, 5 };
        int missingNumber = findMissingNumber(array);

        System.out.println("Missing number in the array: " + missingNumber);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program calculates the missing number in the array by finding the difference between the sum of numbers from 1 to n+1 (where n is the length of the array) and the sum of the elements in the array. By using the formula for the sum of consecutive numbers, the total sum is calculated as <code>(n + 1) * (n + 2) / 2</code>. Then, the array sum is computed by iterating over the array and adding each element. Finally, the missing number is obtained by subtracting the array sum from the total sum.
Feel free to modify the array in the <code>main</code> method to test different cases.

<br>

## is there any other approach for using Stream API, collections or in-build methods?

<br>


Yes, you can use the Stream API and in-built methods to find the missing number in an integer array. Here's an alternative solution:

```java
import java.util.Arrays;

public class MissingNumber {
    public static int findMissingNumber(int[] nums) {
        int n = nums.length + 1;
        int totalSum = n * (n + 1) / 2;

        int arraySum = Arrays.stream(nums).sum();

        return totalSum - arraySum;
    }

    public static void main(String[] args) {
        int[] array = { 1, 2, 4, 6, 3, 7, 8, 5 };
        int missingNumber = findMissingNumber(array);

        System.out.println("Missing number in the array: " + missingNumber);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program uses the Stream API to sum the elements of the array using the <code>sum()</code> method of the <code>Arrays</code> class. It calculates the total sum of numbers from 1 to n+1 using the formula <code>(n + 1) * (n + 2) / 2</code>. Then, it subtracts the array sum from the total sum to find the missing number.
Both the traditional and Stream API solutions will give you the missing number in the array. Feel free to run the code and test it with different inputs.

<br>

## Write a java program to count occurrences of each element in an array?

<br>


To count the occurrences of each element in an integer array in Java, you can use the following program:

```java
import java.util.HashMap;
import java.util.Map;

public class ElementCount {
    public static Map<Integer, Integer> countOccurrences(int[] nums) {
        Map<Integer, Integer> occurrences = new HashMap<>();

        for (int num : nums) {
            occurrences.put(num, occurrences.getOrDefault(num, 0) + 1);
        }

        return occurrences;
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 6, 3, 2, 4, 7, 2, 6, 8, 2 };
        Map<Integer, Integer> occurrences = countOccurrences(array);

        System.out.println("Occurrences of each element:");
        for (Map.Entry<Integer, Integer> entry : occurrences.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program uses a HashMap to store the occurrences of each element in the array. It iterates over the array, and for each element, it retrieves the current count from the HashMap using <code>getOrDefault()</code>. Then, it updates the count by incrementing it and puts it back into the HashMap. Finally, it prints out the occurrences of each element using a for-each loop on the HashMap entries.
Feel free to modify the array in the <code>main</code> method to test different cases.

<br>

## Find a rotation with maximum hamming distance?

<br>


To find a rotation with the maximum hamming distance in an array, you can use the following Java program:

```java
public class MaximumHammingDistance {
    public static int findMaxHammingDistance(int[] arr) {
        int n = arr.length;
        int maxHammingDistance = 0;

        // Create a copy of the original array to rotate
        int[] rotatedArray = new int[n];
        System.arraycopy(arr, 0, rotatedArray, 0, n);

        // Iterate through all possible rotations
        for (int i = 0; i < n; i++) {
            int currentHammingDistance = 0;

            // Compare the elements of the original array with the rotated array
            for (int j = 0; j < n; j++) {
                if (arr[j] != rotatedArray[j]) {
                    currentHammingDistance++;
                }
            }

            // Update the maximum hamming distance if necessary
            maxHammingDistance = Math.max(maxHammingDistance, currentHammingDistance);

            // Rotate the array by one position to the left
            int temp = rotatedArray[0];
            System.arraycopy(rotatedArray, 1, rotatedArray, 0, n - 1);
            rotatedArray[n - 1] = temp;
        }

        return maxHammingDistance;
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 8, 0 };
        int maxHammingDistance = findMaxHammingDistance(array);

        System.out.println("Maximum Hamming Distance: " + maxHammingDistance);
    }
}
```
Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the array.
This program finds the rotation with the maximum hamming distance by comparing each element of the original array with the elements of the rotated array. It iterates through all possible rotations and computes the hamming distance by counting the number of elements that differ between the arrays. The maximum hamming distance is updated if a higher value is found. The array rotation is performed by shifting all elements to the left by one position in each iteration.
Feel free to modify the array in the <code>main</code> method to test different cases.

<br>

## Count Distinct element in every k size window

<br>


To count the distinct elements in every k-size window of an array in Java, you can use the following program:

```java
import java.util.HashMap;
import java.util.Map;

public class DistinctElementsInWindow {
    public static void countDistinctElements(int[] nums, int k) {
        int n = nums.length;

        // Create a HashMap to store the frequency of elements in the window
        Map<Integer, Integer> frequencyMap = new HashMap<>();

        // Initialize the frequency map for the first window
        for (int i = 0; i < k; i++) {
            frequencyMap.put(nums[i], frequencyMap.getOrDefault(nums[i], 0) + 1);
        }

        // Process the remaining windows
        for (int i = 0; i <= n - k; i++) {
            // Print the count of distinct elements in the current window
            System.out.println("Window [" + i + ", " + (i + k - 1) + "]: " + frequencyMap.size());

            // Update the frequency map for the next window
            int leftElement = nums[i];
            int rightElement = nums[i + k];

            frequencyMap.put(leftElement, frequencyMap.get(leftElement) - 1);
            if (frequencyMap.get(leftElement) == 0) {
                frequencyMap.remove(leftElement);
            }

            frequencyMap.put(rightElement, frequencyMap.getOrDefault(rightElement, 0) + 1);
        }
    }

    public static void main(String[] args) {
        int[] array = { 2, 4, 6, 2, 4, 3, 7, 8, 8, 5 };
        int k = 4;

        countDistinctElements(array, k);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the array.
This program counts the distinct elements in every k-size window of the array using a sliding window approach. It maintains a HashMap to store the frequency of elements within the current window. Initially, it initializes the frequency map for the first window. Then, it processes the remaining windows by sliding the window one element at a time. For each window, it prints the count of distinct elements based on the size of the frequency map. It updates the frequency map for the next window by removing the leftmost element and adding the rightmost element.
You can modify the array and the value of k in the <code>main</code> method to test different cases.

<br>

## Print duplicate characters from a string?

<br>


To print duplicate characters from a string in Java, you can use the following program:

```java
import java.util.HashMap;
import java.util.Map;

public class DuplicateCharacters {
    public static void printDuplicateCharacters(String str) {
        // Create a HashMap to store the frequency of characters
        Map<Character, Integer> charFrequency = new HashMap<>();

        // Iterate through each character in the string
        for (char c : str.toCharArray()) {
            charFrequency.put(c, charFrequency.getOrDefault(c, 0) + 1);
        }

        // Print the characters with frequency greater than 1
        System.out.println("Duplicate characters in the string: ");
        for (Map.Entry<Character, Integer> entry : charFrequency.entrySet()) {
            if (entry.getValue() > 1) {
                System.out.println(entry.getKey());
            }
        }
    }

    public static void main(String[] args) {
        String str = "Hello World";
        printDuplicateCharacters(str);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the string.
This program uses a HashMap to store the frequency of each character in the string. It iterates through each character in the string and updates the frequency in the HashMap. After that, it prints the characters that have a frequency greater than 1, indicating the duplicate characters.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Check if two strings are k-anagrams or not

<br>


To check if two strings are k-anagrams or not in Java, where k represents the number of allowed modifications (additions, deletions, or replacements) to make the two strings anagrams of each other, you can use the following program:

```java
import java.util.HashMap;
import java.util.Map;

public class KAnagrams {
    public static boolean areKAnagrams(String str1, String str2, int k) {
        if (str1.length() != str2.length()) {
            return false;
        }

        // Create frequency maps for both strings
        Map<Character, Integer> freqMap1 = new HashMap<>();
        Map<Character, Integer> freqMap2 = new HashMap<>();

        // Populate the frequency maps
        for (int i = 0; i < str1.length(); i++) {
            char ch1 = str1.charAt(i);
            char ch2 = str2.charAt(i);

            freqMap1.put(ch1, freqMap1.getOrDefault(ch1, 0) + 1);
            freqMap2.put(ch2, freqMap2.getOrDefault(ch2, 0) + 1);
        }

        // Count the number of modifications needed
        int modifications = 0;
        for (Map.Entry<Character, Integer> entry : freqMap1.entrySet()) {
            char ch = entry.getKey();
            int freq1 = entry.getValue();
            int freq2 = freqMap2.getOrDefault(ch, 0);

            if (freq1 > freq2) {
                modifications += freq1 - freq2;
            }
        }

        return modifications <= k;
    }

    public static void main(String[] args) {
        String str1 = "hello";
        String str2 = "holle";
        int k = 2;

        boolean result = areKAnagrams(str1, str2, k);

        if (result) {
            System.out.println("The strings are k-anagrams.");
        } else {
            System.out.println("The strings are not k-anagrams.");
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the strings.
This program checks if two strings are k-anagrams by comparing the frequency of characters in both strings. It first checks if the lengths of the strings are equal. Then, it creates frequency maps for both strings using HashMaps. After that, it compares the frequencies of characters in the two maps and counts the number of modifications needed to make the strings anagrams. If the number of modifications is less than or equal to k, it returns true; otherwise, it returns false.
You can modify the strings and the value of k in the <code>main</code> method to test different cases.

<br>

## Check for Balanced Brackets

<br>


To check if a string contains balanced brackets in Java, you can use a stack data structure. Here's an example program:

```java
import java.util.Stack;

public class BalancedBrackets {
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();

        for (char c : str.toCharArray()) {
            if (c == '(' || c == '[' || c == '{') {
                stack.push(c);
            } else if (c == ')' || c == ']' || c == '}') {
                if (stack.isEmpty()) {
                    return false;
                }

                char top = stack.pop();

                if ((c == ')' && top != '(') ||
                    (c == ']' && top != '[') ||
                    (c == '}' && top != '{')) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }

    public static void main(String[] args) {
        String str = "{[()]}";
        boolean isBalanced = isBalanced(str);

        if (isBalanced) {
            System.out.println("The brackets are balanced.");
        } else {
            System.out.println("The brackets are not balanced.");
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the string.
This program uses a stack to check if the brackets in the string are balanced. It iterates through each character in the string. If an opening bracket is encountered (i.e., '(', '[', or '{'), it is pushed onto the stack. If a closing bracket is encountered (i.e., ')', ']', or '}'), it is compared with the top of the stack. If they match, the opening bracket is popped from the stack. If they do not match or the stack is empty when encountering a closing bracket, it means the brackets are not balanced. Finally, it checks if the stack is empty after processing all the characters to ensure all opening brackets have matching closing brackets.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Count number of substrings

<br>


To count the number of substrings in a given string in Java, you can use the following program:

```java
public class SubstringCount {
    public static int countSubstrings(String str) {
        int count = 0;
        int n = str.length();

        // For each character in the string
        for (int i = 0; i < n; i++) {
            // For each possible substring starting from the current character
            for (int j = i; j < n; j++) {
                // Increment the count for each substring
                count++;
            }
        }

        return count;
    }

    public static void main(String[] args) {
        String str = "abc";
        int count = countSubstrings(str);

        System.out.println("Number of substrings: " + count);
    }
}
```
Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the string.
This program counts the number of substrings by iterating through each character in the string and considering each possible substring starting from that character. It uses two nested loops: the outer loop iterates through each character, and the inner loop iterates from the current character to the end of the string. For each substring, the count is incremented. Finally, it returns the total count of substrings.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Check if a string is a rotated palindrome or not

<br>


To check if a string is a rotated palindrome or not in Java, you can follow these steps:
<li>Create a helper method <code>isPalindrome</code> to check if a given string is a palindrome.</li><li>Create a method <code>isRotatedPalindrome</code> to check if a given string is a rotated palindrome.</li><li>In the <code>isRotatedPalindrome</code> method, concatenate the given string with itself to form a new string.</li><li>Iterate through each possible rotation point in the concatenated string.</li><li>Extract a substring starting from the rotation point with the same length as the original string.</li><li>Check if the extracted substring is a palindrome using the <code>isPalindrome</code> helper method.</li><li>If a palindrome is found, return <code>true</code>. If no palindromes are found after checking all rotation points, return <code>false</code>.</li>
Here's an example program that implements the above steps:

```java
public class RotatedPalindrome {
    public static boolean isPalindrome(String str) {
        int left = 0;
        int right = str.length() - 1;

        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }

    public static boolean isRotatedPalindrome(String str) {
        String concatenated = str + str;

        for (int i = 0; i < str.length(); i++) {
            String substring = concatenated.substring(i, i + str.length());
            if (isPalindrome(substring)) {
                return true;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        String str = "aab";
        boolean isRotatedPal = isRotatedPalindrome(str);

        if (isRotatedPal) {
            System.out.println("The string is a rotated palindrome.");
        } else {
            System.out.println("The string is not a rotated palindrome.");
        }
    }
}
```

Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the string.
This program checks if a string is a rotated palindrome by iterating through each rotation point in the concatenated string. It extracts substrings of the same length as the original string starting from each rotation point and checks if they are palindromes using the <code>isPalindrome</code> helper method. If a palindrome is found, it returns <code>true</code>, indicating that the string is a rotated palindrome. Otherwise, it returns <code>false</code>.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Find all possible palindromic substrings of a string

<br>


To find all possible palindromic substrings of a given string in Java, you can use the following program:

```java
import java.util.ArrayList;
import java.util.List;

public class PalindromicSubstrings {
    public static List<String> findAllPalindromicSubstrings(String str) {
        List<String> palindromes = new ArrayList<>();
        int n = str.length();

        // Consider each character as a potential center of a palindrome
        for (int i = 0; i < n; i++) {
            // For odd-length palindromes
            expandPalindrome(str, i, i, palindromes);

            // For even-length palindromes
            expandPalindrome(str, i, i + 1, palindromes);
        }

        return palindromes;
    }

    public static void expandPalindrome(String str, int left, int right, List<String> palindromes) {
        while (left >= 0 && right < str.length() && str.charAt(left) == str.charAt(right)) {
            // Add the palindromic substring to the list
            palindromes.add(str.substring(left, right + 1));

            // Expand the palindrome by moving the pointers
            left--;
            right++;
        }
    }

    public static void main(String[] args) {
        String str = "abba";
        List<String> palindromes = findAllPalindromicSubstrings(str);

        System.out.println("Palindromic substrings:");
        for (String palindrome : palindromes) {
            System.out.println(palindrome);
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the string.
This program finds all possible palindromic substrings by considering each character as a potential center of a palindrome. It uses the concept of expanding around the center to find palindromes. The <code>expandPalindrome</code> method takes a center position (or a center pair for even-length palindromes) and expands outwards as long as the characters on both sides are equal. It adds the palindromic substring to the list and continues expanding. The <code>findAllPalindromicSubstrings</code> method iterates through each character of the string and calls <code>expandPalindrome</code> for both odd-length and even-length palindromes. It collects all the palindromes in a list and returns it.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Find the longest substring of a string containing distinct characters

<br>


To find the longest substring of a string containing distinct characters in Java, you can use the following program:

```java
import java.util.HashMap;
import java.util.Map;

public class LongestSubstringDistinctCharacters {
    public static String findLongestSubstring(String str) {
        int n = str.length();
        int maxLength = 0;  // Length of the longest substring
        int start = 0;     // Start index of the longest substring

        // Map to store the last occurrence of each character
        Map<Character, Integer> lastIndexMap = new HashMap<>();

        int currLength = 0;     // Length of the current substring
        int currStart = 0;      // Start index of the current substring

        // Traverse the string
        for (int i = 0; i < n; i++) {
            char ch = str.charAt(i);

            // If the character is already seen in the current substring
            if (lastIndexMap.containsKey(ch) && lastIndexMap.get(ch) >= currStart) {
                // Update the current substring's start index
                currStart = lastIndexMap.get(ch) + 1;
                currLength = i - currStart;
            }

            // Update the current substring length
            currLength++;

            // Update the last occurrence of the character
            lastIndexMap.put(ch, i);

            // If the current substring is longer than the longest substring so far
            if (currLength > maxLength) {
                maxLength = currLength;
                start = currStart;
            }
        }

        // Return the longest substring
        return str.substring(start, start + maxLength);
    }

    public static void main(String[] args) {
        String str = "abcabcbb";
        String longestSubstring = findLongestSubstring(str);

        System.out.println("Longest substring with distinct characters: " + longestSubstring);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the string.
This program finds the longest substring of a string containing distinct characters by using a sliding window approach. It maintains a current substring starting from the <code>currStart</code> index. As it traverses the string, it updates the <code>currStart</code> index and <code>currLength</code> whenever it encounters a repeated character within the current substring. It also keeps track of the <code>maxLength</code> and <code>start</code> index of the longest substring seen so far. Finally, it returns the longest substring by using the <code>start</code> and <code>maxLength</code> values to extract the substring from the original string.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Determine whether a string is a palindrome or not

<br>


To determine whether a string is a palindrome or not in Java, you can use the following program:

```java
public class PalindromeChecker {
    public static boolean isPalindrome(String str) {
        int left = 0;
        int right = str.length() - 1;

        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }

    public static void main(String[] args) {
        String str = "madam";
        boolean isPal = isPalindrome(str);

        if (isPal) {
            System.out.println("The string is a palindrome.");
        } else {
            System.out.println("The string is not a palindrome.");
        }
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the string.
This program checks if a string is a palindrome by comparing characters from both ends of the string. It uses two pointers, <code>left</code> and <code>right</code>, starting from the beginning and the end of the string, respectively. It compares the characters at these positions and moves the pointers towards the center until they meet in the middle. If at any point the characters don't match, it returns <code>false</code>, indicating that the string is not a palindrome. If the pointers meet in the middle without any mismatches, it returns <code>true</code>, indicating that the string is a palindrome.
You can modify the string in the <code>main</code> method to test different cases.

<br>

## Find first k non-repeating characters in a string in a single traversal

<br>


To find the first k non-repeating characters in a string in a single traversal in Java, you can use the following program:

```java
import java.util.LinkedHashMap;
import java.util.Map;

public class FirstKNonRepeatingCharacters {
    public static String findFirstKNonRepeating(String str, int k) {
        Map<Character, Integer> charCountMap = new LinkedHashMap<>();

        // Build the character count map
        for (char ch : str.toCharArray()) {
            charCountMap.put(ch, charCountMap.getOrDefault(ch, 0) + 1);
        }

        // Find the first k non-repeating characters
        StringBuilder result = new StringBuilder();
        for (char ch : str.toCharArray()) {
            if (charCountMap.get(ch) == 1) {
                result.append(ch);
                if (result.length() == k) {
                    break;
                }
            }
        }

        return result.toString();
    }

    public static void main(String[] args) {
        String str = "aabbccddee";
        int k = 3;

        String firstKNonRepeating = findFirstKNonRepeating(str, k);

        System.out.println("First " + k + " non-repeating characters: " + firstKNonRepeating);
    }
}
```
Time Complexity: The time complexity of this solution is O(n), where n is the length of the string.
This program finds the first k non-repeating characters in a string by using a LinkedHashMap to maintain the order of character insertion. It iterates over each character in the string and builds a character count map. Then, it traverses the string again and checks the count of each character in the map. If a character has a count of 1, it is considered non-repeating and appended to the result string. The traversal stops when k non-repeating characters are found or the end of the string is reached. Finally, it returns the resulting string.
You can modify the string and the value of k in the <code>main</code> method to test different cases.

<br>

## Check if a repeated subsequence is present in a string or not

<br>


To check if a repeated subsequence is present in a string or not in Java, you can use the following program:

```java
public class RepeatedSubsequenceChecker {
    public static boolean isRepeatedSubsequencePresent(String str) {
        int n = str.length();

        // Create a 2D array to store the subsequence counts
        int[][] dp = new int[n + 1][n + 1];

        // Calculate the subsequence counts
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                // If characters match and indices are different
                if (str.charAt(i - 1) == str.charAt(j - 1) && i != j) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i][j - 1], dp[i - 1][j]);
                }
            }
        }

        // If a subsequence of length at least 2 is repeated
        return dp[n][n] >= 2;
    }

    public static void main(String[] args) {
        String str = "ABCDAB";
        boolean isRepeatedSubsequence = isRepeatedSubsequencePresent(str);

        if (isRepeatedSubsequence) {
            System.out.println("A repeated subsequence is present in the string.");
        } else {
            System.out.println("No repeated subsequence is present in the string.");
        }
    }
}
```

Time Complexity: The time complexity of this solution is O(n^2), where n is the length of the string.
This program checks if a repeated subsequence is present in a string by using dynamic programming. It uses a 2D array, <code>dp</code>, to store the counts of subsequences. The <code>dp[i][j]</code> value represents the count of the common subsequence of length <code>i</code> at the <code>i</code>th and <code>j</code>th positions in the string. It iterates through the string and updates the <code>dp</code> array based on whether the characters at <code>i</code> and <code>j</code> positions match or not. Finally, it checks if the count of a subsequence of length at least 2 is greater than or equal to 2, indicating the presence of a repeated subsequence.
You can modify the string in the <code>main</code> method to test different cases.