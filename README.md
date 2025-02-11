# JAVA-DATABASE
## 1. Load and Register the Driver Class
`Class.forName("com.mysql.cj.jdbc.Driver");`


## 2. Establish Connection Between Java Application and Database
'DriverManager.getConnection()'

`import java.sql.Connection;
 import java.sql.DriverManager;
 import java.sql.SQLException;
 
 
 public class DBConnection {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String user = "your_username";
        String password = "your_password";
   
        tyr(Connection conn = DriverManager.getConnection(url, user, passwordl)) {
           System.out.println("Database connected successfully!");
        } catch (SQLException e) {
            e.printStackTrace();
          }
    }
 }`

## 3.Create a Statement Object
'Statement'

`import java.sql.Connection;
 import java.sql.DriverManager;
 import java.sql.SQLException;

 import java.sql.Statement;
 
 
 public class DBConnection {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String user = "your_username";
        String password = "your_password";
   
        tyr(Connection conn = DriverManager.getConnection(url, user, passwordl); Statement stmt = conn.createStatement()) {
           System.out.println("Database object created!");
        } catch (SQLException e) {
            e.printStackTrace();
          }
    }
 }`

## 4. Prepare, Send, and Execute SQL Queries

Use executeUpdate() for INSERT, UPDATE, and DELETE queries.
Use executeQuery() for SELECT queries.

Example: Insert Data
`String sql = "INSERT INTO users (name, email) VALUES ('Umugisha', 'umugisha@gmail.com')";
 stmt.executeUpdate(sql);
 System.out.println("Data inserted successfully!");`

Example: Retrieve Data
`String sql = "SELECT * FROM users";
ResultSet rs = stmt.executeQuery(sql);`

## 5. Process Results from ResultSet
If executing a SELECT query, process results using ResultSet.

`import java.sql.*;

public class RetrieveData {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String user = "your_username";
        String password = "your_password";

        try (Connection conn = DriverManager.getConnection(url, user, password);
             Statement stmt = conn.createStatement();
             ResultSet rs = stmt.executeQuery("SELECT * FROM users")) {

            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                String email = rs.getString("email");
                System.out.println("ID: " + id + ", Name: " + name + ", Email: " + email);
            }

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}`

## 6. Close Connection

. Using try-with-resources (best practice, auto-closes resources):
`try (Connection conn = DriverManager.getConnection(url, user, password);
     Statement stmt = conn.createStatement();
     ResultSet rs = stmt.executeQuery("SELECT * FROM users")) {`
. Manually closing resources:
`rs.close();
stmt.close();
conn.close();`

# Summary of Steps
✅ Load Driver (Not always required in modern JDBC)
✅ Establish Connection
✅ Create Statement Object
✅ Prepare, Send, and Execute SQL Queries
✅ Process Results
✅ Close Connection
