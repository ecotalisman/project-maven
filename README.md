# Module 3
# Project Topic: Maven [JavaRush University]

## Module 3. Java Professional
### Level 2, Lecture 6

**Task**: Create a JAR file with a JavaFX game using the JavaRush graphics engine. 
To do this, follow the steps:

1. Fork from the repository: [project-maven](https://github.com/vasylmalik/project-maven.git).
2. Download your version of the project to your computer. We will work with the `pom.xml` file next.
3. Add dependencies:
   - `org.apache.commons: commons-lang3: 3.12.0`
   - `org.openjfx: javafx-controls: 18.0.1`
   - `com.javarush: desktop-game-engine:1.0` (separate task regarding this dependency)
   - `org.junit.jupiter: junit-jupiter-engine: 5.8.2` (with scope test)
4. Add plugins for:
   - Installing the dependency `com.javarush: desktop-game-engine:1.0` from the `lib` library to the local repository (additional information is recommended to be searched via Google);
   - Leave the `maven-compiler-plugin` unchanged;
   - Plugin that will gather all dependencies (with scope compile) and place them in a directory during compilation;
   - `maven-jar-plugin` that creates a jar file containing the game code and dependencies. This plugin needs to configure the `MANIFEST.MF` file to contain sections: `Class-Path`, `Main-Class`, and `Rsrc-Main-Class`.
       - `Class-Path` should list all our JAR dependencies.
       - `Main-Class` should mention the class `org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader`, which can use the classpath from JAR files and can also start a JavaFX program.
       - `Rsrc-Main-Class` should specify the game's starting class (`com.javarush.games.racer.RacerGame`).
   - In the `maven-surefire-plugin`, create a configuration so that the `StrangeTest` does not run during assembly. Other tests should be executed.
5. Add a “resources” section indicating that the collected JAR dependencies are a resource, so the `maven-jar-plugin` places them inside the JAR file in the `lib/` folder.
6. Push changes to your GitHub repository and send the link to the instructor.

**Tips**:

- Build with the command: `mvn clean install`.
- Start the game (via Maven) for viewing with: `mvn javafx: run`.
- Some plugins need to redefine the phase.
- The project uses JDK version 18.0.1. It should be installed on your computer.
- There will initially be errors in the Maven build. Read them carefully, and you will simplify your life.
- Don't change anything in the package `org.eclipse.jdt.internal.jarinjarloader`. It contains a custom class loader (honestly copied from StackOverflow), where the `main` method launch has been replaced with starting a JavaFX program. Use it only for educational purposes.
- If you complete all the steps, as a result of the assembly, you will get a fat-JAR-file. To launch and check that everything is done correctly, use the command:
    ```bash
    <path to java 18> -jar <name of the resulting jar file>
    ```
    **Example**: 
    ```bash
    "C:\Users\leo12\.jdks\openjdk-18.0.1.1\bin\java.exe" -jar "E:\temp\project-maven-1.0.jar"
    ```
    You should see:
  ![2023-10-23_19h03_29](https://github.com/ecotalisman/project-maven/assets/67708040/dfe575a4-42d5-4352-9583-d43ef55872c3)

    Builds depend on your operating system. Thus, if the JAR file is assembled on Windows, it can be executed on any computer with Windows and Java 18 but cannot be executed on Mac and Linux.

---
### 🇺🇦 Ukrainian version:
---
# Модуль 3
# Проєкт на тему: Maven [JavaRush University]

**Модуль 3. Java Professional**  
Рівень 2, Лекція 6

## Завдання
Зробити JAR-файл із грою на JavaFX за допомогою графічного рушія JavaRush. Для цього потрібно:

1. Зробити fork із репозиторію [https://github.com/vasylmalik/project-maven.git](https://github.com/vasylmalik/project-maven.git).
2. Завантажити свою версію проєкту на комп'ютер. Далі будемо працювати з файлом pom.xml.
3. Додати залежності:
   - `org.apache.commons: commons-lang3: 3.12.0`
   - `org.openjfx: javafx-controls: 18.0.1`
   - `com.javarush: desktop-game-engine:1.0` (стосовно цієї залежності буде окреме завдання)
   - `org.junit.jupiter: junit-jupiter-engine: 5.8.2` (зі scope test)
4. Додати плагіни для:
   - установлення залежності `com.javarush: desktop-game-engine:1.0` з бібліотеки lib до локального репозиторію (додаткову інформацію радимо пошукати через Google);
   - плагін maven-compiler-plugin залишити без змін;
   - плагін, який збере всі залежності (зі scope compile) та розмістить в якусь директорію при складанні;
   - плагін maven-jar-plugin, який зробить jar файл, що містить код гри та залежності.
     - У Class-Path мають бути прописані всі наші JAR-залежності.
     - У Main-Class має бути прописаний клас `org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader`.
     - У Rsrc-Main-Class має бути прописаний стартовий клас гри (`com.javarush.games.racer.RacerGame`).
5. У плагіні maven-surefire-plugin створити конфігурацію, щоб тест StrangeTest не запускався при складанні.
6. Додати секцію “resources”, у якій вказати, що зібрані JAR-залежності – це ресурс.
7. Залити зміни до свого GitHub-репозиторію, надіслати посилання на нього викладачеві.

## Корисне
- Білд потрібно виконувати командою `mvn clean install`.
- Запуск гри (через Maven) для перегляду можна виконати командою `mvn javafx: run`.
- Деяким плагінам потрібно перевизначити phase.
- У проєкті використовується версія JDK 18.0.1.
- У білді через Maven спершу будуть помилки. Читай їх уважно!
- У пакеті `org.eclipse.jdt.internal.jarinjarloader` нічого не змінюй. У ньому кастомний клас-лоадер.
- Якщо виконати всі пункти, в результаті складання проєкту ти отримаєш fat-JAR-файл. Запустити та перевірити, що все зроблено правильно, можна командою:
    ```bash
    <шлях до java 18> -jar <ім'я результуючого jar файла>
    ```
    **Приклад**: 
    ```bash
    "C:\Users\leo12\.jdks\openjdk-18.0.1.1\bin\java.exe" -jar "E:\temp\project-maven-1.0.jar"
    ```
