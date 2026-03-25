# Java I/O & NIO Basics

## File Input/Output Basics
- Java provides the `java.io` package for reading and writing files.
- Common classes:
  - `FileReader` / `FileWriter` for character streams.
  - `FileInputStream` / `FileOutputStream` for byte streams.
- Example:
```java
try (FileWriter writer = new FileWriter("output.txt")) {
    writer.write("Hello, Java I/O!");
}
```
-----

### Stream-Based I/O
Streams represent a sequence of data (input or output).

Types:

- Byte Streams: InputStream, OutputStream.

- Character Streams: Reader, Writer.

- Streams can be chained (e.g., BufferedReader wrapping FileReader)

### NIO Overview (Path, Files)
- Java NIO (java.nio.file) provides modern APIs for file handling.

- Path: Represents a file path.

- Files: Utility class for file operations.

```
import java.nio.file.*;

Path path = Paths.get("data.txt");
if (Files.exists(path)) {
    String content = Files.readString(path);
    System.out.println(content);
}
```

------------

### Stream vs Channel (Concept)
- Stream: One-way flow of data, blocking I/O.

- Channel: Bi-directional, supports non-blocking I/O, often used with buffers.

- Channels are part of NIO and allow faster, scalable data transfer.
--------

## Summary
- Java I/O uses streams for reading/writing files, while NIO introduces Path, Files, and channels for modern, efficient operations.