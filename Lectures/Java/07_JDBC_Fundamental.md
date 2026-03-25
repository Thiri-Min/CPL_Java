# JDBC Fundamentals

## JDBC Architecture & Flow
JDBC (Java Database Connectivity) is an API that enables Java applications to interact with relational databases.  
The typical flow is:
1. Load the JDBC driver.
2. Establish a connection to the database.
3. Create a statement object.
4. Execute SQL queries or updates.
5. Process the results.
6. Close resources.

---

## Driver, Connection, Statement
- **Driver**: A JDBC driver is required to connect Java applications with a specific database (e.g., MySQL, PostgreSQL).
- **Connection**: Represents a session with the database. Created using `DriverManager.getConnection()`.
- **Statement**: Used to execute SQL queries (e.g., `SELECT`, `INSERT`, `UPDATE`, `DELETE`).

**Example:**
```java
import java.sql.*;

public class JdbcExample {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:yourportnumber/yourdatabasename";
        String user = "yourusername";
        String password = "password";

        try (Connection conn = DriverManager.getConnection(url, user, password);
             Statement stmt = conn.createStatement()) {

            ResultSet rs = stmt.executeQuery("SELECT * FROM employee");
            while (rs.next()) {
                System.out.println(rs.getInt("id") + " - " + rs.getString("name"));
            }

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```
---------

## PreparedStatement Usage
PreparedStatement is used for executing parameterized queries, which helps prevent SQL injection and improves performance.
```
String sql = "INSERT INTO employee (id, name, department) VALUES (?, ?, ?)";
try (PreparedStatement pstmt = conn.prepareStatement(sql)) {
    pstmt.setInt(1, 101);
    pstmt.setString(2, "Alice");
    pstmt.setString(3, "HR");
    pstmt.executeUpdate();
}
```
-----
## ResultSet Mapping
ResultSet represents the result of a query. You can map database columns to Java objects.

```
ResultSet rs = stmt.executeQuery("SELECT id, name, department FROM employee");
while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
    String dept = rs.getString("department");
    System.out.println(id + " | " + name + " | " + dept);
}
```

## Transaction Basics (Commit/Rollback)
Transactions ensure data consistency. By default, JDBC auto-commits after each statement. You can disable auto-commit and manage transactions manually.

```
conn.setAutoCommit(false);
try {
    stmt.executeUpdate("UPDATE employee SET department='Finance' WHERE id=101");
    stmt.executeUpdate("UPDATE employee SET department='Finance' WHERE id=102");
    conn.commit(); // commit both updates
} catch (SQLException e) {
    conn.rollback(); // rollback if any error occurs
}
```

## Resource Management (try-with-resources)
Always close JDBC resources (Connection, Statement, ResultSet) to avoid memory leaks.
Use try-with-resources for automatic closing.
```
try (Connection conn = DriverManager.getConnection(url, user, password);
     PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM employee");
     ResultSet rs = pstmt.executeQuery()) {

    while (rs.next()) {
        System.out.println(rs.getInt("id") + " - " + rs.getString("name"));
    }

} catch (SQLException e) {
    e.printStackTrace();
}
```
## Summary
JDBC provides a standard way to connect Java applications with databases.

Key components: Driver, Connection, Statement, PreparedStatement, ResultSet.

Transactions allow commit/rollback for consistency.

Use try-with-resources for safe resource management.
