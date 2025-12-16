# Build in codespace

To build the Lanterna project using the provided `pom.xml`, you will need to use Apache Maven, which is the build tool specified in the POM file. Below are the steps to build the project:

---

### **Steps to Build the Lanterna Project:**

1. **Install Apache Maven**
   - Ensure Maven is installed on your machine.
   - Verify Maven installation by running:
     ```bash
     mvn -version
     ```
   - If Maven isn't installed, download it from [Maven's website](https://maven.apache.org/download.cgi) and follow the installation instructions.

2. **Clone the Repository**
   - Clone the Lanterna repository from GitHub:
     ```bash
     git clone https://github.com/mabe02/lanterna.git
     cd lanterna
     ```

3. **Execute the Maven Build Command**
   - Run the following command from the project's root directory to compile the project:
     ```bash
     mvn clean install
     ```
   - The `clean` phase ensures that any previously compiled files are removed before building.
   - The `install` goal compiles the project, runs tests, generates jars, and installs the package into your local Maven repository.

4. **Build Artifacts**
   - After running the command, the build artifacts (e.g., the compiled JAR file) will be located in the `target` directory.
   - Look for the Lanterna JAR file here:
     ```
     target/lanterna-3.2.0-SNAPSHOT.jar
     ```

5. **Optional: Skip Tests**
   - If you would like to skip running the tests during the build, add the `-DskipTests` flag:
     ```bash
     mvn clean install -DskipTests
     ```

6. **Profiles for Releases**
   - The POM file defines a Maven profile named `release` for creating release builds. To activate this profile, use the `-P` option:
     ```bash
     mvn clean install -P release
     ```

7. **Generated JAR**
   - The built project generates two JAR files:
     - Main JAR: `lanterna-3.2.0-SNAPSHOT.jar`
     - Test JAR: `lanterna-3.2.0-SNAPSHOT-tests.jar` (if `test-jar` is configured).

8. **Build Requirements**
   - The project specifies Java 1.8 (`<maven.compiler.source>` and `<maven.compiler.target>` are set to `1.8`).
   - Ensure you have Java 8 or later installed on your system, as the Java compiler will target that version.
   - Verify your Java version by running:
     ```bash
     java -version
     ```

---

### **Summary**
- Use Maven commands:
  ```bash
  mvn clean install
  # Optional: Skip tests
  mvn clean install -DskipTests
  # Optional: Build with the 'release' profile
  mvn clean install -P release
  ```
- Check the `target` folder for the compiled JAR files after a successful build.

## Build Dependency sequence

```bash
jdeps -verbose:class --multi-release 9 target/lanterna-3.2.0-SNAPSHOT.jar > jdeps.txt
```