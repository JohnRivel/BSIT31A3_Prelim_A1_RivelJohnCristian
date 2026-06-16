using System;
using System.Collections.Generic;

class Program
{
    static List<Student> students = new List<Student>();

    static void Main()
    {
        int choice;
        do
        {
            Console.WriteLine("\n--- Student Management System ---");
            Console.WriteLine("1. Add Student");
            Console.WriteLine("2. View Students");
            Console.WriteLine("3. Search Student");
            Console.WriteLine("4. Delete Student");
            Console.WriteLine("5. Exit");
            Console.Write("Enter choice: ");
            
            choice = int.Parse(Console.ReadLine());

            switch (choice)
            {
                case 1: AddStudent(); break;
                case 2: ViewStudents(); break;
                case 3: SearchStudent(); break;
                case 4: DeleteStudent(); break;
                case 5: Console.WriteLine("Exiting..."); break;
                default: Console.WriteLine("Invalid choice."); break;
            }
        } while (choice != 5);
    }

    static void AddStudent()
    {
        Console.Write("Enter name: ");
        string name = Console.ReadLine();
        Console.Write("Enter ID: ");
        string id = Console.ReadLine();
        students.Add(new Student { Name = name, ID = id });
        Console.WriteLine("Student added successfully!");
    }

    static void ViewStudents()
    {
        Console.WriteLine("\n--- Student List ---");
        foreach (var s in students)
            Console.WriteLine($"ID: {s.ID}, Name: {s.Name}");
    }

    static void SearchStudent()
    {
        Console.Write("Enter ID to search: ");
        string id = Console.ReadLine();
        var student = students.Find(s => s.ID == id);
        if (student != null)
            Console.WriteLine($"Found: {student.Name} (ID: {student.ID})");
        else
            Console.WriteLine("Student not found.");
    }

    static void DeleteStudent()
    {
        Console.Write("Enter ID to delete: ");
        string id = Console.ReadLine();
        var student = students.Find(s => s.ID == id);
        if (student != null)
        {
            students.Remove(student);
            Console.WriteLine("Student deleted.");
        }
        else
            Console.WriteLine("Student not found.");
    }
}

class Student
{
    public string Name { get; set; }
    public string ID { get; set; }
}
