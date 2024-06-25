# FileGenerator
Console application for generating large text files.
## Overview
This Java project provides a simple utility for generating large text files with random alphanumeric content. The generated files can be useful for testing applications that handle large amounts of data or for benchmarking file processing algorithms.

## Usage
To generate a large text file, run the following command:
```
java Main <output_file_name>
```
Replace <output_file_name> with the desired name for the output file.

## Details
The `FileGenerator` class contains the `generateLargeTextFile` method, which takes an output file name as an argument. This method generates random alphanumeric strings of varying lengths and writes them to the specified file.

The `Main` class serves as the entry point for the program. It accepts the output file name as a command-line argument and invokes the `generateLargeTextFile` method to create the file.

## Customization
You can customize the generated content by modifying the `alphabet` string in the `FileGenerator` class. This string defines the characters that can be used in the random strings. You can add or remove characters to suit your specific requirements.

Additionally, you can adjust the range of string lengths by modifying the `r.nextInt(46) + 5` expression. This expression generates random lengths between 5 and 50 characters (inclusive) for each string. You can change the upper and lower bounds to control the length of the generated strings.

## Code Snippet
Here's a code snippet from the FileGenerator class:
```
public class FileGenerator {
    public static void generateLargeTextFile(String outputFileName) {
        Random r = new Random();
        String alphabet = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";

        try (PrintWriter writer = new PrintWriter(outputFileName)) {
            for (int j = 0; j < 1_000_000_000; j++) {
                StringBuilder sb = new StringBuilder();
                for (int i = 0; i < r.nextInt(46) + 5; i++) {
                    sb.append(alphabet.charAt(r.nextInt(alphabet.length())));
                }
                writer.println(sb);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
