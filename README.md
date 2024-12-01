/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package lalal.p2;

import java.util.*;

class Person {
    private String idNumber;

    public Person(String idNumber) {
        this.idNumber = idNumber;
    }

    @Override
    public String toString() {
        return "ID: " + idNumber;
    }
}

class Student extends Person {
    private String universityID;
    private int level;

    public Student(String idNumber, String universityID, int level) {
        super(idNumber);
        this.universityID = universityID;
        this.level = level;
    }

    public int getLevel() {
        return level;
    }

    @Override
    public String toString() {
        return super.toString() + ", University ID: " + universityID + ", Level: " + level;
    }
}

class Teacher extends Person {
    private String email;

    public Teacher(String idNumber, String email) {
        super(idNumber);
        this.email = email;
    }

    public String getEmail() {
        return email;
    }
}

class CourseResource {
    private List<String> videos = new ArrayList<>();
    private List<String> texts = new ArrayList<>();

    public void addResource(String type, String link) {
        if (type.equals("Video")) {
            videos.add(link);
        } else if (type.equals("Text")) {
            texts.add(link);
        }
    }

    public void removeResource(String type, int index) {
        if (type.equals("Video") && index >= 0 && index < videos.size()) {
            videos.remove(index);
        } else if (type.equals("Text") && index >= 0 && index < texts.size()) {
            texts.remove(index);
        }
    }

    public List<String> getResources(String type) {
        return type.equals("Video") ? videos : texts;
    }
}

class Course {
    private String name;
    private CourseResource resources = new CourseResource();

    public Course(String name) {
        this.name = name;
        initializeResources();
    }

    private void initializeResources() {
        switch (name) {
            case "AI":
                resources.addResource("Text", "https://drive.google.com/file/d/11bPP-ftKjhPCbcObAbGP1g8KqKRvnoYP/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1ChuJSMypR7sSX9zOYcXsGMFDRbaGTrPn/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/NdJtQDlUegs?si=s6Hi14ydH2irrH9K");
                resources.addResource("Video", "https://youtu.be/1iba4Sb3qtk?si=Ksz7YAtRSgoKNxN9");
                break;
            case "Cyber Security":
                resources.addResource("Text", "https://drive.google.com/file/d/1jTXxoFKfYiJPn1CDC0jK9e2xSQnqZ7Bn/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1TMRIsfsYZ9vN8XmA-20TQjOeKuR-ypYU/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/Fh9LE4-YlNI?si=raqMCr6H0Qcf29zd");
                resources.addResource("Video", "https://youtu.be/oeQn42dNi24?si=a0zc5oMcgtLPKp4I");
                break;
            case "Calculus":
                resources.addResource("Text", "https://drive.google.com/file/d/1cu9Go_gn5zmRJyIZqEULdU8gNr2E1Txx/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1w2TDXifs2yMakFjTcWhXTSe_fSgA9Vlv/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/IHLBbSTFxRA?si=pwxDlIusIHxs1nsb");
                resources.addResource("Video", "https://youtu.be/NpIrlfJ9550?si=rbNrhxI5glJebvb8");
                break;
            case "OOP":
                resources.addResource("Text", "https://drive.google.com/file/d/1u88JAD7O0SAoAcuoQNEps5LBB1Zf13pH/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1kSMZrVMQ8kWGFWRbk6YF5Lg17WGIg7G7/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/M3Na5luSx50?si=mweExiEqXVuv72Dm");
                resources.addResource("Video", "https://youtu.be/QEcGBVPjGio?si=jt7kusxbm04-NGm_");
                break;
            case "Statistics":
                resources.addResource("Text", "https://drive.google.com/file/d/1_rXqe4tWRAEPGGwbLtih9U7OY7iWxR36/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1d-vq3ALSe7ehUA-BNkY4PhO3dYM3yZ4o/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/kHP_CYmVuEE?si=FFhWnvtRqGgNJcem");
                resources.addResource("Video", "https://youtu.be/7YCG1vcn0EE?si=OOx5tu5bDQYdYU5H");
                break;
            case "Network":
                resources.addResource("Text", "https://drive.google.com/file/d/1bKKD3iuZmHttkcsbeTa05PE2MpEdib2M/view?usp=drivesdk");
                resources.addResource("Text", "https://drive.google.com/file/d/1kx_YcxRPFT9D4c3fWf8g7W1R7uxq0Rhe/view?usp=drivesdk");
                resources.addResource("Video", "https://youtu.be/9aOWD34RIVo?si=BwgZVubgvBXSagZo");
                resources.addResource("Video", "https://youtu.be/gUSR72Sbz_I?si=88rQKttvH84fq1z6");
                break;
        }
    }

    public String getName() {
        return name;
    }

    public CourseResource getResources() {
        return resources;
    }
}

class ResourceManager {
    private Map<Integer, List<Course>> courses = new HashMap<>();

    public ResourceManager() {
        initializeCourses();
    }

    private void initializeCourses() {
        courses.put(1, Arrays.asList(new Course("AI"), new Course("Cyber Security"), new Course("Calculus")));
        courses.put(2, Arrays.asList(new Course("OOP"), new Course("Statistics"), new Course("Network")));
    }

    public List<Course> getCourses(int level) {
        return courses.get(level);
    }
}

public class P2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ResourceManager resourceManager = new ResourceManager();

        while (true) {
            System.out.println("\nWelcome! Please choose an option:");
            System.out.println("1. Student");
            System.out.println("2. Teacher");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            if (choice == 1) {
                System.out.println("\nWelcome, dear student!");
                System.out.print("Enter your University ID: ");
                String universityID = scanner.nextLine();
               
                System.out.print("Choose your level (1 or 2): ");
                int level = scanner.nextInt();
                scanner.nextLine();

                List<Course> availableCourses = resourceManager.getCourses(level);
                if (availableCourses != null) {
                    System.out.println("\nAvailable courses:");
                    for (int i = 0; i < availableCourses.size(); i++) {
                        System.out.println((i + 1) + ". " + availableCourses.get(i).getName());
                    }

                    System.out.print("\nChoose a course by number: ");
                    int courseChoice = scanner.nextInt();
                    scanner.nextLine();

                    if (courseChoice > 0 && courseChoice <= availableCourses.size()) {
                        Course selectedCourse = availableCourses.get(courseChoice - 1);
                        System.out.println("\nYou selected: " + selectedCourse.getName());
                        System.out.println("Choose resource type:");
                        System.out.println("1. Video");
                        System.out.println("2. Text");
                        System.out.print("Enter your choice: ");
                        int resourceType = scanner.nextInt();
                        scanner.nextLine();

                        String type = resourceType == 1 ? "Video" : "Text";
                        List<String> resources = selectedCourse.getResources().getResources(type);

                        System.out.println("\n" + type + " resources for " + selectedCourse.getName() + ":");
                        for (String resource : resources) {
                            System.out.println("- " + resource);
                        }
                    } else {
                        System.out.println("Invalid course choice!");
                    }
                } else {
                    System.out.println("Invalid level!");
                }
            } else if (choice == 2) {
                System.out.println("\nWelcome, dear teacher!");
                System.out.print("Enter your email: ");
                String email;
                while (true) {
                    email = scanner.nextLine();
                    if (email.endsWith("@iau.edu.sa")) {
                        break;
                    } else {
                        System.out.print("Invalid email! Please enter an email ending with '@iau.edu.sa': ");
                    }
                }

                Teacher teacher = new Teacher("DefaultID", email);
                System.out.println("Welcome, Teacher! Your email is verified: " + teacher.getEmail());

                System.out.print("Choose your level (1 or 2): ");
                int level = scanner.nextInt();
                scanner.nextLine();

                List<Course> availableCourses = resourceManager.getCourses(level);
                if (availableCourses != null) {
                    System.out.println("\nAvailable courses:");
                    for (int i = 0; i < availableCourses.size(); i++) {
                        System.out.println((i + 1) + ". " + availableCourses.get(i).getName());
                    }

                    System.out.print("\nChoose a course by number: ");
                    int courseChoice = scanner.nextInt();
                    scanner.nextLine();

                    if (courseChoice > 0 && courseChoice <= availableCourses.size()) {
                        Course selectedCourse = availableCourses.get(courseChoice - 1);
                        System.out.println("\nYou selected: " + selectedCourse.getName());
                        System.out.println("Choose resource type:");
                        System.out.println("1. Video");
                        System.out.println("2. Text");
                        System.out.print("Enter your choice: ");
                        int resourceType = scanner.nextInt();
                        scanner.nextLine();

                        String type = resourceType == 1 ? "Video" : "Text";
                        CourseResource resources = selectedCourse.getResources();

                        while (true) {
                            System.out.println("\nTeacher options:");
                            System.out.println("1. Add resource");
                            System.out.println("2. Remove resource");
                            System.out.println("3. View resources");
                            System.out.println("4. Back to main menu");
                            System.out.print("Enter your choice: ");
                            int teacherChoice = scanner.nextInt();
                            scanner.nextLine();

                            if (teacherChoice == 1) {
                                System.out.print("Enter the resource link to add: ");
                                String resourceLink = scanner.nextLine();
                                resources.addResource(type, resourceLink);
                                System.out.println("Resource added successfully!");
                            } else if (teacherChoice == 2) {
                                List<String> resourceList = resources.getResources(type);
                                for (int i = 0; i < resourceList.size(); i++) {
                                    System.out.println((i + 1) + ". " + resourceList.get(i));
                                }
                                System.out.print("Enter the number of the resource to remove: ");
                                int resourceIndex = scanner.nextInt() - 1;
                                scanner.nextLine();
                                resources.removeResource(type, resourceIndex);
                                System.out.println("Resource removed successfully!");
                            } else if (teacherChoice == 3) {
                                System.out.println("\n" + type + " resources:");
                                for (String resource : resources.getResources(type)) {
                                    System.out.println("- " + resource);
                                }
                            } else if (teacherChoice == 4) {
                                break;
                            } else {
                                System.out.println("Invalid choice! Try again.");
                            }
                        }
                    } 
                        else  {
                        System.out.println("Invalid course choice!");
                    } 
                } else {
                    System.out.println("Invalid level!");
                }
            } else if (choice == 3) {
                System.out.println("\nThank you for using the application. Goodbye!");
                break;
            } else {
                System.out.println("Invalid choice! Please try again.");
            }
        }
        scanner.close();
    }
    }
