import java.util.*;

class Person {
    protected String name;
    protected String surname;
    protected int age;
    protected boolean gender;

    public Person(String name, String surname, int age, boolean gender) {
        this.name = name;
        this.surname = surname;
        this.age = age;
        this.gender = gender;
    }

    public String toString() {
        String genderString = gender ? "Male" : "Female";
        return "Hi, I am " + name + " " + surname + ", a " + age + "-year-old " + genderString + ".";
    }
}

class Student extends Person {
    private static int idCounter = 1;
    private int studentID;
    private List<Integer> grades;

    public Student(String name, String surname, int age, boolean gender) {
        super(name, surname, age, gender);
        this.studentID = idCounter++;
        this.grades = new ArrayList<>();
    }

    public void addGrade(int grade) {
        if (grade >= 0 && grade <= 100) {
            grades.add(grade);
        }
    }

    public double calculateGPA() {
        if (grades.isEmpty()) return 0.0;
        int total = 0;
        for (int grade : grades) {
            total += grade;
        }
        return total / (double) grades.size();
    }

    @Override
    public String toString() {
        return super.toString() + " I am a student with ID " + studentID + ".";
    }
}

class Teacher extends Person {
    private String subject;
    private int yearsOfExperience;
    private int salary;

    public Teacher(String name, String surname, int age, boolean gender, String subject, int yearsOfExperience, int salary) {
        super(name, surname, age, gender);
        this.subject = subject;
        this.yearsOfExperience = yearsOfExperience;
        this.salary = salary;
    }

    public void giveRaise(double percentage) {
        salary += salary * percentage / 100;
    }

    @Override
    public String toString() {
        return super.toString() + " I teach " + subject + ".";
    }

    public int getYearsOfExperience() {
        return yearsOfExperience;
    }

    public int getSalary() {
        return salary;
    }
}

class School {
    private List<Person> members;

    public School() {
        members = new ArrayList<>();
    }

    public void addMember(Person person) {
        members.add(person);
    }

    @Override
    public String toString() {
        StringBuilder result = new StringBuilder();
        for (Person member : members) {
            result.append(member.toString()).append("\n");
        }
        return result.toString();
    }
}

public class Main {
    public static void main(String[] args) {
        School school = new School();

        Student student1 = new Student("Alice", "Smith", 20, false);
        student1.addGrade(85);
        student1.addGrade(90);
        student1.addGrade(78);

        Student student2 = new Student("Bob", "Johnson", 22, true);
        student2.addGrade(88);
        student2.addGrade(92);
        student2.addGrade(95);

        Teacher teacher1 = new Teacher("Dr. Emily", "Brown", 45, false, "Mathematics", 15, 50000);
        Teacher teacher2 = new Teacher("Mr. John", "Doe", 35, true, "History", 8, 40000);

        school.addMember(student1);
        school.addMember(student2);
        school.addMember(teacher1);
        school.addMember(teacher2);

        System.out.println("Student 1 GPA: " + student1.calculateGPA());
        System.out.println("Student 2 GPA: " + student2.calculateGPA());

        if (teacher1.getYearsOfExperience() > 10) {
            teacher1.giveRaise(10);
            System.out.println(teacher1.surname + "'s new salary: " + teacher1.getSalary());
        }

        System.out.println("\nSchool Members:\n" + school);
    }
}
