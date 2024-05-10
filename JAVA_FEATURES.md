# JAVA Versions And Features
## Java 7 New Features

Java 7 was officially released by Oracle Corporation on July 28, 2011, introduced several new features and enhancements. Here are some of the key features:

1. **String in Switch Statements:**
  - Prior to Java 7, switch statements only supported integral types (byte, short, int, long) and enumerated types. Java 7 introduced the ability to use strings in switch statements.
  **Example**
    ```java
    String day = "Monday";
    switch (day) {
      case "Monday":
         System.out.println("It's Monday!");
         break;
      case "Tuesday":
         System.out.println("It's Tuesday!");
         break;
      // ...
      default:
         System.out.println("It's another day!");
    }
    ```

2. **Diamond Operator:**
  - The diamond operator (`<>`) allows you to omit the type arguments when creating an instance of a generic class, as long as the compiler can infer the type arguments from the context.
  **Example**
    ```java
    List<String> names = new ArrayList<>();
    ```

3. **Try-with-Resources:**
  - The try-with-resources statement simplifies the handling of resources that need to be closed after use, such as streams or database connections.
  **Example**
    ```java
    try (FileInputStream fis = new FileInputStream("file.txt");
       InputStreamReader isr = new InputStreamReader(fis);
       BufferedReader br = new BufferedReader(isr)) {
      String line;
      while ((line = br.readLine()) != null) {
         System.out.println(line);
      }
    } catch (IOException e) {
      e.printStackTrace();
    }
    ```

4. **Improved Exception Handling:**
  - Java 7 introduced multi-catch, which allows you to catch multiple exceptions in a single catch block.
  **Example**
    ```java
    try {
      // Code that may throw exceptions
    } catch (IOException | SQLException e) {
      e.printStackTrace();
    }
    ```
## Java 8 New Features

Java 8 was officially released by Oracle Corporation on March 18, 2014, and introduced several new features and enhancements. Here are some of the key features:

1. **Lambda Expressions:**
  - Lambda expressions allow you to treat functionality as a method argument or code as data. They enable you to write more concise and expressive code.
  **Example**
    ```java
    List<String> names = Arrays.asList("John", "Jane", "Alice");
    names.forEach(name -> System.out.println(name));
    ```

2. **Stream API:**
  - The Stream API provides a functional programming approach to process collections of data. It allows you to perform operations such as filtering, mapping, and reducing on collections easily.
  **Example**
    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
    int sum = numbers.stream()
                    .filter(n -> n % 2 == 0)
                    .mapToInt(n -> n)
                    .sum();
    ```

3. **Default Methods:**
  - Default methods allow you to add new methods to an interface without breaking the existing implementations of that interface. It provides a way to extend interfaces without requiring all implementing classes to implement the new methods.
  **Example**
    ```java
    interface Vehicle {
      void start();
      void stop();

      default void honk() {
        System.out.println("Honk honk!");
      }
    }
    ```

4. **Date and Time API:**
  - Java 8 introduced a new Date and Time API that provides a more comprehensive and flexible way to work with dates and times. It includes classes such as LocalDate, LocalTime, LocalDateTime, and DateTimeFormatter.
  **Example**
    ```java
    LocalDate currentDate = LocalDate.now();
    System.out.println("Current date: " + currentDate);
    ```

5. **Optional Class:**
  - The Optional class is a container object that may or may not contain a non-null value. It provides methods to handle the presence or absence of a value, reducing the need for null checks.
  **Example**
    ```java
    Optional<String> name = Optional.ofNullable(getName());
    if (name.isPresent()) {
      System.out.println("Name: " + name.get());
    } else {
      System.out.println("Name not available");
    }

    private String getName() {
      // Code to retrieve name
    }
    ```

6. **Method References:**
  - Method references allow you to refer to methods or constructors without invoking them. They provide a shorthand syntax for lambda expressions when the lambda expression simply calls an existing method or constructor.
  **Example**
    ```java
    List<String> names = Arrays.asList("John", "Jane", "Alice");
    names.forEach(System.out::println);
    ```

7. **Parallel Streams:**
  - Parallel streams allow you to process collections of data in parallel, taking advantage of multi-core processors and potentially improving performance for computationally intensive tasks.
  **Example**
    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
    int sum = numbers.parallelStream()
                    .filter(n -> n % 2 == 0)
                    .mapToInt(n -> n)
                    .sum();
    ```

8. **Functional Interfaces:**
  - Functional interfaces are interfaces that have exactly one abstract method. They are used to enable lambda expressions and method references.
  **Example**
    ```java
    @FunctionalInterface
    interface Calculator {
      int calculate(int a, int b);
    }
    ```

9. **CompletableFuture:**
  - CompletableFuture is a class that represents a future result of an asynchronous computation. It provides a way to perform asynchronous operations and handle their results using callbacks.
  **Example**
    ```java
    CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
      // Code to perform asynchronous computation
      return "Result";
    });

    future.thenAccept(result -> System.out.println("Result: " + result));
    ```

10. **Nashorn JavaScript Engine:**
  - Java 8 includes a new JavaScript engine called Nashorn, which allows you to execute JavaScript code from within Java applications. It provides improved performance compared to the previous JavaScript engine.
  **Example**
    ```java
    ScriptEngineManager manager = new ScriptEngineManager();
    ScriptEngine engine = manager.getEngineByName("nashorn");
    engine.eval("print('Hello, World!')");
    ```

These are just a few of the new features introduced in Java 8. There are many more features and enhancements available in the Java 8 release.

## Java 9 New Features

Java 9 was officially released by Oracle Corporation on September 21, 2017, and introduced several new features and enhancements. Here are some of the key features:

1. **Module System:**
  - Java 9 introduced the Java Platform Module System (JPMS), which provides a way to create modular applications. It allows you to encapsulate code into modules and define dependencies between modules.
  **Example**
    ```java
    module com.example.myapp {
      requires java.base;
      requires java.sql;
      requires org.apache.commons.lang3;
    }
    ```

2. **JShell:**
  - JShell is an interactive Read-Eval-Print Loop (REPL) tool that allows you to evaluate Java code snippets and see the results immediately. It provides a convenient way to experiment with Java code.
  **Example**
    ```java
    jshell> int sum = 0;
    jshell> for (int i = 1; i <= 10; i++) {
    ...>     sum += i;
    ...> }
    jshell> sum
    $3 ==> 55
    ```

3. **Private Methods in Interfaces:**
  - Java 9 allows you to define private methods in interfaces. These methods can be used to share common code between default methods or to improve code readability.
  **Example**
    ```java
    interface MyInterface {
      default void publicMethod() {
        privateMethod();
      }

      private void privateMethod() {
        // Code here
      }
    }
    ```

4. **Stream API Enhancements:**
  - Java 9 introduced several enhancements to the Stream API, including new methods and improvements to existing methods. These enhancements make it easier to work with streams and perform common operations.
  **Example**
    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
    List<Integer> squaredNumbers = numbers.stream()
                                          .map(n -> n * n)
                                          .collect(Collectors.toList());
    ```

5. **Reactive Streams:**
  - Java 9 includes support for Reactive Streams, which is a specification for asynchronous stream processing with non-blocking back pressure. It provides a standard way to handle streams of data in a reactive manner.
  **Example**
    ```java
    Publisher<Integer> publisher = new Publisher<Integer>() {
      // Implementation here
    };

    Subscriber<Integer> subscriber = new Subscriber<Integer>() {
      // Implementation here
    };

    publisher.subscribe(subscriber);
    ```

6. **Process API Updates:**
  - Java 9 introduced updates to the Process API, which allows you to interact with operating system processes. These updates provide more control over process management and improve the handling of process streams.
  **Example**
    ```java
    ProcessBuilder pb = new ProcessBuilder("my-command", "arg1", "arg2");
    Process process = pb.start();

    InputStream inputStream = process.getInputStream();
    BufferedReader reader = new BufferedReader(new InputStreamReader(inputStream));

    String line;
    while ((line = reader.readLine()) != null) {
      System.out.println(line);
    }
    ```

7. HTTP/2 Client:
  - Java 9 includes a new HTTP/2 client API, which provides a more modern and efficient way to send HTTP requests and handle responses. It supports features such as multiplexing, server push, and request/response streaming.
  **Example**
    ```java
    HttpClient client = HttpClient.newHttpClient();
    HttpRequest request = HttpRequest.newBuilder()
                                    .uri(URI.create("https://example.com"))
                                    .build();
    HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
    ```

## Java 10 New Features

Java 10 was officially released by Oracle Corporation on March 20, 2018, and introduced several new features and enhancements. Here are some of the key features:

1. **Local Variable Type Inference:**
  - Java 10 introduced the ability to declare local variables with the `var` keyword, allowing the type of the variable to be inferred by the compiler.
  **Example**
    ```java
    var message = "Hello, World!";
    var numbers = List.of(1, 2, 3, 4, 5);
    ```

2. Application Class-Data Sharing:
  - Java 10 introduced the concept of Application Class-Data Sharing (AppCDS), which allows classes to be shared between different Java processes to reduce startup time and memory footprint.
  **Example**
    ```java
    java -Xshare:dump
    java -Xshare:on -jar myapp.jar
    ```

3. **Parallel Full GC for G1:**
  - Java 10 improved the Garbage-First (G1) garbage collector by introducing parallel full garbage collection, which can improve the performance of applications with large heaps.
  **Example**
    No code example needed.

4. Experimental Java-Based JIT Compiler:
  - Java 10 introduced an experimental Just-In-Time (JIT) compiler called Graal, which is written in Java itself. It provides an alternative to the existing JIT compilers and allows for better performance optimization.
  **Example**
    No code example needed.

5. Time-Based Release Versioning:
  - Java 10 introduced a new versioning scheme based on time, where a new feature release is planned every six months. This allows for more frequent updates and faster delivery of new features.
  **Example**
    No code example needed.

## Java 11 New Features

Java 11 was officially released by Oracle Corporation on September 25, 2018, and introduced several new features and enhancements. Here are some of the key features:

1. Local-Variable Syntax for Lambda Parameters:
  - Java 11 introduced the ability to use the `var` keyword for lambda parameters, allowing the type of the parameter to be inferred by the compiler.
  **Example**
    ```java
    (var x, var y) -> x + y
    ```

2. **HTTP Client:**
  - Java 11 includes a new HTTP client API that provides a more modern and efficient way to send HTTP requests and handle responses. It supports features such as asynchronous requests, HTTP/2, and WebSocket.
  **Example**
    ```java
    HttpClient client = HttpClient.newHttpClient();
    HttpRequest request = HttpRequest.newBuilder()
                                    .uri(URI.create("https://example.com"))
                                    .build();
    HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
    ```

3. Nest-Based Access Control:
  - Java 11 introduced nest-based access control, which allows classes that are logically part of the same nest to access each other's private members without the need for reflection.
  **Example**
    ```java
    class Outer {
      private int x;

      class Inner {
        private int y;

        void accessOuterPrivateMember() {
          x = 10; // Accessing private member of outer class
        }
      }
    }
    ```

4. **Epsilon:** A No-Op Garbage Collector:
  - Java 11 introduced a new experimental garbage collector called Epsilon, which is a no-op garbage collector that does not perform any garbage collection. It is useful for performance testing and memory pressure analysis.
  **Example**
    No code example needed.

5. Launch Single-File Source-Code Programs:
  - Java 11 introduced the ability to directly execute a single-file source-code program without the need for explicit compilation. This makes it easier to run simple Java programs without the need for a separate compilation step.
  **Example**
    ```java
    // Hello.java
    public class Hello {
      public static void main(String[] args) {
        System.out.println("Hello, World!");
      }
    }

    // Run the program
    java Hello.java
    ```
## Java 12 New Features

Java 12 was officially released by Oracle Corporation on March 19, 2019, and introduced several new features and enhancements. Here are some of the key features:

1. Switch Expressions (Preview):
  - Java 12 introduced a preview feature called switch expressions, which allows the use of switch as an expression instead of a statement. It simplifies the syntax and enables more concise code.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1 -> "Monday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

2. **Compact Number Formatting:**
  - Java 12 introduced a new compact number formatting feature, which allows you to format numbers in a more concise and readable way. It provides options for formatting large numbers with abbreviations.
  **Example**
    ```java
    NumberFormat numberFormat = NumberFormat.getCompactNumberInstance(Locale.US, NumberFormat.Style.SHORT);
    String formattedNumber = numberFormat.format(1000000);
    System.out.println("Formatted number: " + formattedNumber);
    ```

3. **Teeing Collector:**
  - Java 12 introduced a new collector called teeing collector, which allows you to perform two separate operations on the same stream and combine the results. It simplifies the code when you need to perform multiple operations on a stream.
  **Example**
    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
    IntSummaryStatistics statistics = numbers.stream()
                                            .collect(Collectors.teeing(
                                                Collectors.summarizingInt(Integer::intValue),
                                                Collectors.counting(),
                                                (summary, count) -> new IntSummaryStatistics(
                                                    summary.getCount(),
                                                    summary.getSum(),
                                                    summary.getMin(),
                                                    summary.getMax(),
                                                    count
                                                )
                                            ));
    System.out.println("Statistics: " + statistics);
    ```

4. JVM Constants API (Preview):
  - Java 12 introduced a preview feature called JVM Constants API, which provides a standard way to define and use constants in the Java Virtual Machine (JVM). It simplifies the code and improves performance by allowing the JVM to optimize constant values.
  **Example**
    ```java
    import static java.lang.invoke.MethodHandles.constant;

    class Constants {
      static final int MAX_VALUE = 100;
      static final int MIN_VALUE = 0;

      static final int DEFAULT_VALUE = constant(int.class, 42);
    }

    public class Main {
      public static void main(String[] args) {
        System.out.println("Max value: " + Constants.MAX_VALUE);
        System.out.println("Min value: " + Constants.MIN_VALUE);
        System.out.println("Default value: " + Constants.DEFAULT_VALUE);
      }
    }
    ```

5. Switch Expressions (Standard):
  - Java 12 made the switch expressions feature a standard feature, removing the preview status. It allows the use of switch as an expression instead of a statement, simplifying the syntax and enabling more concise code.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1 -> "Monday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

6. Compact Number Formatting (Standard):
  - Java 12 made the compact number formatting feature a standard feature, removing the preview status. It allows you to format numbers in a more concise and readable way, providing options for formatting large numbers with abbreviations.
  **Example**
    ```java
    NumberFormat numberFormat = NumberFormat.getCompactNumberInstance(Locale.US, NumberFormat.Style.SHORT);
    String formattedNumber = numberFormat.format(1000000);
    System.out.println("Formatted number: " + formattedNumber);
    ```
## Java 13 New Features

Java 13 was officially released by Oracle Corporation on September 17, 2019, and introduced several new features and enhancements. Here are some of the key features:

1. **Text Blocks:**
  - Java 13 introduced text blocks, which are a new way to write multi-line strings in Java. Text blocks make it easier to write and read strings that span multiple lines, without the need for escape characters or concatenation.
  **Example**
    ```java
    String message = """
                      Hello,
                      World!
                      """;
    System.out.println(message);
    ```

2. Switch Expressions (Preview):
  - Java 13 enhanced switch expressions, which were introduced in Java 12 as a preview feature. Switch expressions now support multiple labels and yield statements, making them more powerful and expressive.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1, 8 -> "Monday or Sunday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

3. **Dynamic CDS Archives:**
  - Java 13 introduced dynamic Class-Data Sharing (CDS) archives, which allow you to create CDS archives at runtime. Dynamic CDS archives provide improved startup performance by preloading classes and reducing class loading time.
  **Example**
    ```java
    ArchiveBuilder builder = ArchiveBuilder.create();
    builder.addClass(MyClass.class);
    builder.addClass(MyOtherClass.class);
    Archive archive = builder.build();
    archive.save("myapp.cds");
    ```

4. **Reimplement the Legacy Socket API:**
  - Java 13 reimplemented the legacy Socket API using the new NIO.2 APIs. This improves the performance and scalability of socket operations, especially in high-concurrency scenarios.
  **Example**
    ```java
    SocketChannel channel = SocketChannel.open();
    channel.connect(new InetSocketAddress("example.com", 80));
    ByteBuffer buffer = ByteBuffer.allocate(1024);
    channel.read(buffer);
    ```

5. **ZGC:** A Scalable Low-Latency Garbage Collector:
  - Java 13 introduced ZGC, a new garbage collector designed for low-latency applications. ZGC provides consistent pause times regardless of the heap size and is suitable for applications that require high throughput and low latency.
  **Example**
    No code example needed.

6. Text Blocks (Preview):
  - Java 13 introduced text blocks as a preview feature. Text blocks make it easier to write and read multi-line strings in Java, improving the readability and maintainability of code.
  **Example**
    ```java
    String message = """
                      Hello,
                      World!
                      """;
    System.out.println(message);
    ```

7. Switch Expressions (Standard):
  - Java 13 made switch expressions a standard feature, removing the preview status. Switch expressions now support multiple labels and yield statements, making them more powerful and expressive.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1, 8 -> "Monday or Sunday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

8. Text Blocks (Second Preview):
  - Java 13 introduced text blocks as a second preview feature. Text blocks make it easier to write and read multi-line strings in Java, improving the readability and maintainability of code.
  **Example**
    ```java
    String message = """
                      Hello,
                      World!
                      """;
    System.out.println(message);
    ```

9. Reimplement the Legacy Socket API (Second Preview):
  - Java 13 reimplemented the legacy Socket API using the new NIO.2 APIs as a second preview feature. This improves the performance and scalability of socket operations, especially in high-concurrency scenarios.
  **Example**
    ```java
    SocketChannel channel = SocketChannel.open();
    channel.connect(new InetSocketAddress("example.com", 80));
    ByteBuffer buffer = ByteBuffer.allocate(1024);
    channel.read(buffer);
    ```
## Java 14 New Features

Java 14 was officially released by Oracle Corporation on March 17, 2020, and introduced several new features and enhancements. Here are some of the key features:

1. **Records:**
  - Records are a new type of class introduced in Java 14 that provide a concise way to declare classes that are primarily used to store data. They automatically generate useful methods such as equals(), hashCode(), and toString().
  **Example**
    ```java
    public record Person(String name, int age) {
      // Record body
    }
    ```

2. Switch Expressions (Preview):
  - Switch expressions were introduced as a preview feature in Java 12 and became a standard feature in Java 14. They allow you to use switch statements as expressions, which can simplify code and make it more readable.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1, 8 -> "Monday or Sunday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

3. Text Blocks (Second Preview):
  - Text blocks were introduced as a preview feature in Java 13 and continued as a second preview feature in Java 14. They make it easier to write and read multi-line strings in Java, improving the readability and maintainability of code.
  **Example**
    ```java
    String message = """
                      This is a multi-line
                      text block in Java 14.
                      """;
    System.out.println(message);
    ```

4. Pattern Matching for instanceof (Preview):
  - Pattern matching for instanceof is a preview feature introduced in Java 14 that simplifies the common pattern of checking the type of an object and then casting it. It allows you to combine the instanceof check and the cast into a single operation.
  **Example**
    ```java
    if (obj instanceof String str) {
      // Use str as a String
      System.out.println(str.length());
    }
    ```

5. **Helpful NullPointerExceptions:**
  - Java 14 introduced improvements to NullPointerExceptions by providing more detailed information about the null reference that caused the exception. This can help developers quickly identify and fix null-related issues.
  **Example**
    ```java
    String name = null;
    System.out.println(name.length());
    ```

6. Records (Preview):
  - Records were introduced as a preview feature in Java 14. They provide a concise way to declare classes that are primarily used to store data. Records automatically generate useful methods such as equals(), hashCode(), and toString().
  **Example**
    ```java
    public record Person(String name, int age) {
      // Record body
    }
    ```

7. Switch Expressions (Standard):
  - Switch expressions were introduced as a preview feature in Java 12 and became a standard feature in Java 14. They allow you to use switch statements as expressions, which can simplify code and make it more readable.
  **Example**
    ```java
    int dayOfWeek = 1;
    String dayName = switch (dayOfWeek) {
      case 1, 8 -> "Monday or Sunday";
      case 2 -> "Tuesday";
      case 3 -> "Wednesday";
      case 4 -> "Thursday";
      case 5 -> "Friday";
      default -> "Weekend";
    };
    System.out.println("Today is " + dayName);
    ```

8. Text Blocks (Standard):
  - Text blocks were introduced as a preview feature in Java 13 and became a standard feature in Java 14. They make it easier to write and read multi-line strings in Java, improving the readability and maintainability of code.
  **Example**
    ```java
    String message = """
                      This is a multi-line
                      text block in Java 14.
                      """;
    System.out.println(message);
    ```

9. Foreign-Memory Access API (Incubator):
  - Java 14 introduced the Foreign-Memory Access API as an incubator feature. It provides a safe and efficient way to access native memory directly from Java, enabling better integration with native libraries and improved performance.
  **Example**
    ```java
    try (MemorySegment segment = MemorySegment.allocateNative(1024)) {
      segment.asByteBuffer().putInt(0, 42);
      int value = segment.asByteBuffer().getInt(0);
      System.out.println("Value: " + value);
    }
    ```

10. Packaging Tool (Incubator):
  - Java 14 introduced the Packaging Tool as an incubator feature. It allows you to package your Java applications as platform-specific installers, such as MSI or DEB, making it easier to distribute and install your applications.
  **Example**
    No code example needed.

Please note that some features mentioned above are preview or incubator features, which means they are still under development and subject to change in future Java versions.
## Java 15 New Features

Java 15 was officially released by Oracle Corporation on September 15, 2020, and introduced several new features and enhancements. Here are some of the key features:

1. **Sealed Classes:**
  - Sealed classes restrict the subclasses that can extend or implement them. This provides more control over the inheritance hierarchy and improves code maintainability.
  **Example**
    ```java
    public sealed class Shape permits Circle, Rectangle {
      // Class body
    }

    final class Circle extends Shape {
      // Class body
    }

    final class Rectangle extends Shape {
      // Class body
    }
    ```

2. **Hidden Classes:**
  - Hidden classes are classes that are not discoverable by normal class loading mechanisms. They are useful for implementing frameworks and libraries that need to generate classes dynamically at runtime without polluting the class namespace.
  **Example**
    ```java
    MethodHandles.Lookup lookup = MethodHandles.lookup();
    Class<?> hiddenClass = lookup.defineHiddenClass(bytecode, true);
    ```

3. Text Blocks (Standard):
  - Text blocks were introduced as a preview feature in Java 13 and became a standard feature in Java 15. They make it easier to write and read multi-line strings in Java, improving the readability and maintainability of code.
  **Example**
    ```java
    String message = """
                      This is a multi-line
                      text block in Java 15.
                      """;
    System.out.println(message);
    ```

4. **Records (Standard):**
  - Records were introduced as a preview feature in Java 14 and became a standard feature in Java 15. They provide a concise way to declare classes that are primarily used to store data. Records automatically generate useful methods such as equals(), hashCode(), and toString().
  **Example**
    ```java
    public record Person(String name, int age) {
      // Record body
    }
    ```

5. **Pattern Matching for instanceof (Standard):**
  - Pattern matching for instanceof is a feature introduced as a preview feature in Java 14 and became a standard feature in Java 15. It simplifies the common pattern of checking the type of an object and then casting it. It allows you to combine the instanceof check and the cast into a single operation.
  **Example**
    ```java
    if (obj instanceof String str) {
      // Use str as a String
      System.out.println(str.length());
    }
    ```

Please note that the features mentioned above are standard features in Java 15.
## Java 16 New Features

Java 16 was officially released by Oracle Corporation on March 16, 2021, and introduced several new features and enhancements. Here are some of the key features:

1. **Records:**
  - Records are a new type of class introduced in Java 16 that provide a concise way to declare classes that are solely used to store data. They automatically generate constructors, accessors, and other useful methods.
  **Example**
    ```java
    public record Person(String name, int age) {
      // Record body
    }
    ```

2. **Pattern Matching for instanceof (Standard):**
  - Pattern matching for instanceof, which was introduced as a preview feature in Java 14 and became a standard feature in Java 15, has been further enhanced in Java 16. It allows you to simplify the common pattern of checking the type of an object and then casting it.
  **Example**
    ```java
    if (obj instanceof String str) {
      // Use str as a String
      System.out.println(str.length());
    }
    ```

3. **Sealed Classes (Second Preview):**
  - Sealed classes, which were introduced as a preview feature in Java 15, have been further enhanced in Java 16. Sealed classes restrict the subclasses that can extend or implement them, providing more control over the inheritance hierarchy.
  **Example**
    ```java
    public sealed class Shape permits Circle, Rectangle {
      // Class body
    }

    final class Circle extends Shape {
      // Class body
    }

    final class Rectangle extends Shape {
      // Class body
    }
    ```

4. **Unix Domain Socket Channels:**
  - Java 16 introduces Unix domain socket channels, which allow Java applications to communicate with other processes on the same machine using Unix domain sockets. This feature is particularly useful for inter-process communication in Unix-like operating systems.
  **Example**
    ```java
    UnixDomainSocketAddress address = UnixDomainSocketAddress.of("/path/to/socket");
    UnixDomainSocketChannel channel = UnixDomainSocketChannel.open(address);
    ```

5. **Foreign Function & Memory API (Incubator):**
  - Java 16 includes an incubator module called Foreign Function & Memory API, which provides a way to interact with native code and memory in a safe and controlled manner. This API allows Java programs to call native functions and access native memory directly.
  **Example**
    ```java
    try (MemorySegment segment = MemorySegment.allocateNative(1024)) {
      segment.asByteBuffer().putInt(0, 42);
      int result = LibC.printf("The answer is %d\n", segment.address());
      System.out.println("Printf returned: " + result);
    }
    ```

Please note that the features mentioned above are standard features in Java 16.
## Java 17 New Features
1. **Sealed Classes (Full Feature):**

These were a preview feature in Java 15 and became a full feature in Java 17. Sealed classes restrict which other classes can inherit from them, improving code safety and readability.

*Example:*
```java
    public sealed class Shape permits Circle, Rectangle {
      public double getArea() {
        return 0;
      }
    }

    public final class Circle extends Shape {
      private final double radius;

      public Circle(double radius) {
        this.radius = radius;
      }

      @Override
      public double getArea() {
        return Math.PI * radius * radius;
      }
    }

    public final class Rectangle extends Shape {
      private final double width;
      private final double height;

      public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
      }

      @Override
      public double getArea() {
        return width * height;
      }
    }
```
In this example, `Shape` is a sealed class. Only `Circle` and `Rectangle` can inherit from it, preventing unexpected subclasses.

2. **Pattern Matching for Switch (Preview Feature):**

Switch statements become more flexible with pattern matching. You can use patterns like `instanceof` to check types.
```java
public String getShapeDetails(Object obj) {
  return switch (obj) {
    case String s -> "It's a String";
    case Integer i -> "It's an Integer";
    case Double d -> "It's a Double";
    default -> "Unknown type";
  };
}
```
This code uses pattern matching to check the type of the `obj` argument and returns a corresponding message.

**Note:** Pattern matching for switch is still a preview feature in Java 17. Its syntax might change in future versions.

## Java 18 (Released March 2022)
1. **Project Loom (Preview Feature):**

Project Loom introduces lightweight virtual threads for improved concurrency. These threads are called "fibers" and offer better performance compared to traditional threads, especially for I/O-bound tasks.

Example: (Due to Loom being a preview feature, there is no widely adopted standard way to use it yet. Here's a glimpse of what the code might look like):

```java
// Imagine a library for Project Loom
ExecutorService executor = Executors.newVirtualThreadExecutor();
executor.submit(() -> {
  // Your code for the virtual thread
});
```
**Note:** Project Loom is under development and its API might change before it becomes a full feature.

## Java 19 (Released September 2022)
1. **Records (Preview Feature):**

Records, introduced in Java 14, gain new features in Java 19. One such feature is compact constructors that automatically initialize record components from their corresponding parameters.

Example:

```java
public record Point(int x, int y) { }  // Compact constructor
```
This record automatically creates a constructor with parameters `x` and `y` and initializes the corresponding components.

## Java 20 (Released March 2023)

1. **Garbage Collector: ZGC by Default (Preview Feature):**

The Z Garbage Collector, known for its low-latency approach, becomes the default on some platforms (experimental).

**Note:**  ZGC is still under development, and its usage as the default is subject to change. There's currently no example code for this feature as it's managed by the JVM.

## Java 21 (Released September 2023) (Current LTS Version)
Java 21 focuses on stability and performance improvements rather than introducing major new features.

## Java 22 (Released March 2024)
1. **Unnamed Variables & Patterns (Final Feature):**

Java 22 finalizes the use of unnamed _ variables in enhanced for loops and switch expressions to discard unused elements.

**Example:**
```java
for (_ : numbers) {
  // Process the elements without storing them in a variable
}
```

In this example, the `_` variable discards the actual values in the numbers array. The loop only executes the code in the body to process elements.

2. **Statements Before super(...) (Preview Feature):**

Java 22 allows code within a constructor before calling the superclass constructor using `super()`. This provides more flexibility for initialization logic, especially when interacting with fields or performing computations before relying on the parent class's initialization.
**Example:**
```java
public class Child extends Parent {
  private int value;

  public Child() {
    // Validate and set value before calling superclass constructor
    this.value = validateAndSetValue(10);
    super();  // Call superclass constructor after initialization
  }

  private int validateAndSetValue(int val) {
    // Perform validation or calculations on the value
    return val * 2;
  }
}
```

