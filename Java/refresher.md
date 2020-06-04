# Reading from stdin 

* SystemIn + Scanner 

  * ```java
    Scanner scanner = new Scanner(System.in);
    String nameSurname = scanner.nextLine();
    String gender = scanner.next();
    int age = scanner.nextInt();
    
    while (scanner.hasNextInt()) {
        int nmbr = scanner.nextInt();
        //...
    }
    ```

* SystemIn + InputReader + BufferedReader 

  * ```java
    BufferedReader buffReader = new BufferedReader(new InputStreamReader(System.in));
    int i = Integer.parseInt(buffReader.readLine());
    ```

