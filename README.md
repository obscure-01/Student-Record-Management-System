🚀 Project Overview

This small console application loads student records from students.txt at startup, lets you add/view/search/delete/sort students, demonstrates random access reads, and saves updated records back to the same file on exit.

Features:

Load & save student records (CSV format)

Add / view all / search by name / delete by name

Sort by marks (desc) and by name (asc)

Display using Iterator

Demonstrate RandomAccessFile with recorded byte offsets

Simple persistent storage via students.txt

📁 File structure /project-folder ├─ StudentRecordApp.java // main single-file Java program ├─ students.txt // data file (CSV) └─ Lab Assignment 4.pdf // assignment spec (referenced locally)

🧾 students.txt format (CSV)

Each line is a record in the format:

roll,name,email,course,marks

Example:

101,Ankit,ankit@mail.com,B.Tech,85.5 102,Riya,riya@mail.com,M.Tech,91.0 103,Karan,karan@mail.com,BCA,76.2

💻 How to compile & run

Open a terminal/command prompt in the project folder and run:

compile
javac StudentRecordApp.java

run
java StudentRecordApp

The program will create students.txt if it does not exist.

🧭 Menu options (in-app)

Add Student

View All Students

Search by Name

Delete by Name

Sort by Marks (descending)

Sort by Name (ascending)

Demo Random Read (RandomAccessFile)

Save and Exit

🧩 Implementation details

Data model: Student inner class with roll, name, email, course, marks. Methods: fromCSV(String), toCSV(), and toString() for display.

Storage: students.txt (plain CSV). File handling via BufferedWriter/RandomAccessFile.

Collection: ArrayList is used with generics for type safety.

Sorting:

Marks — students.sort((a,b) -> Double.compare(b.marks, a.marks)); (descending)

Name — students.sort(Comparator.comparing(s -> s.name.toLowerCase())); (ascending)

Display: Iteration uses Iterator to demonstrate Iterator use.

RandomAccessFile demo:

On load the program records the byte offset of each line (via RandomAccessFile).

The demo allows the user to enter a record index and the program seeks to the stored offset and reads that single record.

File update strategy:

append() for adding a single student (keeps file write cost low).

saveAll() (rewrite) after deletions to ensure file consistency.

⚠️ Assumptions & notes

CSV is simple and does not handle escaped commas or quoted fields. Keep names/emails/courses without commas.

RandomAccessFile.readLine() uses ISO-8859-1 decoding; for typical ASCII/UTF-8 content this works but be aware of encoding caveats for non-ASCII characters.

The program records offsets on load; if you edit students.txt externally while running, offsets may be inconsistent—restart the app after external edits.

The application is intentionally single-file for easy submission; it can be refactored to multiple classes/files for better organization.

✅ Improvements you can add (optional)

Use CSV library or JSON for robust serialization.

Add validation for emails / unique roll numbers.

Add unit tests (JUnit) for parsing, sorting, and file operations.

Convert to multi-file project (Student.java, FileUtil.java, StudentManager.java, Main.java).

Add a simple GUI (Swing / JavaFX) or export to CSV/Excel.
