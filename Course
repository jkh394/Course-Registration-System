import java.io.*;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;
import java.util.StringTokenizer;

public class Course implements java.io.Serializable {
	String courseName;
	String courseID;
	int maxStudents;
	int currentStudents;
	ArrayList<Student> studentList;
	String instructorName;
	int courseSection;
	String courseLocation;
	static ArrayList<Course> courseList = new ArrayList<Course>();

	Course() {

	}

	Course(String courseName, String courseID, int maxStudents, int currentStudents, String instructorName,
			int courseSection, String courseLocation) {
		this.courseName = courseName;
		this.courseID = courseID;
		this.maxStudents = maxStudents;
		this.currentStudents = currentStudents;
		this.studentList = new ArrayList<Student>();
		this.instructorName = instructorName;
		this.courseSection = courseSection;
		this.courseLocation = courseLocation;
	}

	public String print() {
		String names = "";

		if (studentList != null) {
			for (int i = 0; i < studentList.size(); i++) {
				String addFirst = studentList.get(i).getFirstName();
				String addLast = studentList.get(i).getLastName();
				names = names + addFirst + " " + addLast + ", ";
			}
			System.out.println("Course: " + courseName + "\n" + "Course ID: " + courseID + "\n"
					+ "Maximum # of Students: " + maxStudents + "\n" + "Current # of Students: " + currentStudents
					+ "\n" + "Registered Students: " + names + "\n" + "Instructor: " + instructorName + "\n"
					+ "Section: " + courseSection + "\n" + "Location: " + courseLocation);
			System.out.println("==========");
			String text1 = "Course: " + courseName + "\n" + "Course ID: " + courseID + "\n" + "Maximum # of Students: "
					+ maxStudents + "\n" + "Current # of Students: " + currentStudents + "\n" + "Registered Students: "
					+ names + "\n" + "Instructor: " + instructorName + "\n" + "Section: " + courseSection + "\n"
					+ "Location: " + courseLocation;
			return (text1);
		} else {
			System.out.println("Course: " + courseName + "\n" + "Course ID: " + courseID + "\n"
					+ "Maximum # of Students: " + maxStudents + "\n" + "Current # of Students: " + currentStudents
					+ "\n" + "Registered Students: " + studentList + "\n" + "Instructor: " + instructorName + "\n"
					+ "Section: " + courseSection + "\n" + "Location: " + courseLocation);
			System.out.println("==========");
			String text2 = "Course: " + courseName + "\n" + "Course ID: " + courseID + "\n" + "Maximum # of Students: "
					+ maxStudents + "\n" + "Current # of Students: " + currentStudents + "\n" + "Registered Students: "
					+ studentList + "\n" + "Instructor: " + instructorName + "\n" + "Section: " + courseSection + "\n"
					+ "Location: " + courseLocation;
			return (text2);
		}
	}

	public String studentPrint() {
		System.out.println("Course: " + courseName + "\n" + "Course ID: " + courseID + "\n" + "Maximum # of Students: "
				+ maxStudents + "\n" + "Current # of Students: " + currentStudents + "\n" + "Registered Students: "
				+ "\n" + "Instructor: " + instructorName + "\n" + "Section: " + courseSection + "\n" + "Location: "
				+ courseLocation);
		System.out.println("==========");
		String text = "Course: " + courseName + "\n" + "Course ID: " + courseID + "\n" + "Maximum # of Students: "
				+ maxStudents + "\n" + "Current # of Students: " + currentStudents + "\n" + "Registered Students: "
				+ "\n" + "Instructor: " + instructorName + "\n" + "Section: " + courseSection + "\n" + "Location: "
				+ courseLocation;
		return (text);
	}

	//Getters and Setters

	public String getCourseName() {
		return courseName;
	}

	public void setCourseName(String courseName) {
		this.courseName = courseName;
	}

	public String getCourseID() {
		return courseID;
	}

	public void setCourseID(String courseID) {
		this.courseID = courseID;
	}

	public int getMaxStudents() {
		return maxStudents;
	}

	public void setMaxStudents(int maxStudents) {
		this.maxStudents = maxStudents;
	}

	public int getCurrentStudents() {
		return currentStudents;
	}

	public void setCurrentStudents(int currentStudents) {
		this.currentStudents = currentStudents;
	}

	public ArrayList<Student> getStudentList() {
		return studentList;
	}

	public void setStudentList(ArrayList<Student> studentList) {
		this.studentList = studentList;
	}

	public String getInstructorName() {
		return instructorName;
	}

	public void setInstructorName(String instructorName) {
		this.instructorName = instructorName;
	}

	public int getCourseSection() {
		return courseSection;
	}

	public void setCourseSection() {
		this.courseSection = courseSection;
	}

	public String getCourseLocation() {
		return courseLocation;
	}

	public void setCourseLocation(String courseLocation) {
		this.courseLocation = courseLocation;
	}

	public static void deSerialization() {
		try {
			FileInputStream fis = new FileInputStream("CRSData.ser");
			ObjectInputStream ois = new ObjectInputStream(fis);

			courseList = (ArrayList<Course>) ois.readObject();
			ois.close();
			fis.close();
			System.out.println("Deserialization complete");
		} catch (IOException ioe) {
			ioe.printStackTrace();
		} catch (ClassNotFoundException c) {
			System.out.println("Class not found");
			c.printStackTrace();
		}
	}

	public static void serialization() {
		try {
			FileOutputStream fos = new FileOutputStream("CRSData.ser");
			ObjectOutputStream oos = new ObjectOutputStream(fos);

			oos.writeObject(courseList);
			oos.close();
			fos.close();
			System.out.println("Serialization complete");
		} catch (IOException ioe) {
			ioe.printStackTrace();
		}
	}

	public static void main(String[] args) throws FileNotFoundException, IOException {
		Admin admin = new Admin();
		File fileName = new File("CRSData.ser");
		if (!fileName.exists()) {
			fileName = new File("MyUniversityCourses.csv");

			// References one line at a time
			String line = null;

			try {
				// FileReader reads text files as characters as opposed to bytes (like
				// FileInputStream)
				// First, we instantiate the file reader class
				// It's parameter would be the name of the file to read (in this case, the
				// string variable which represents the file name);
				FileReader fileReader = new FileReader(fileName);

				// The BufferedReader class can wrap around Readers, like FileReader, to buffer
				// the input and improve efficiency.
				// ALWAYS wrap FileReader in BufferedReader
				BufferedReader bufferedReader = new BufferedReader(fileReader);

				// readLine() reads a line of text.
				// A line is considered to be terminated by a new line ('\n'). So Buffered
				// reader would literally read line by line.
				// While there are still lines to read, our program will print the file

				// Always close files
				bufferedReader.close();
			}
			// The catch block performs a specific action depending on the exception
			catch (FileNotFoundException ex) {
				System.out.println("Unable to open file '" + fileName + "'");
				// the printStackTrace method will print out an error output stream ("What went
				// wrong?" report);

				ex.printStackTrace();
			}

			catch (IOException ex) {
				System.out.println("Error reading file '" + fileName + "'");
				ex.printStackTrace();
			}

			// STEP 2: TOKENIZE CSV FILE
			// Array list of type User

			// input will represent the csv file as a string so that we may manipulate the
			// file
			String input = new Scanner(fileName).useDelimiter("\\A").next();

			// We remove any information we don't necessarily need in order to get the
			// necessary tokens
			// input=input.replace("Course_Name", " ").replace("Course_Id", "
			// ").replace("Maximum_Students", " ").replace("Current_Students", "
			// ").replace("List_Of_Names", " ").replace("Course_Instructor",
			// "").replace("Course_Section_Number", " ").replace("Course_Location", " ");

			// The tokenizer will look at each string token within the input
			StringTokenizer strTokens = new StringTokenizer(input, ",\n");

			int count = 0;
			// While there is still text to parse through within the file
			while (strTokens.hasMoreTokens()) {
				if (count > 7) {
					String courseName = strTokens.nextToken();
					String courseID = strTokens.nextToken();
					String test = strTokens.nextToken();
					String trimmedTest = test.replace(" ", "");
					int maxStudents = Integer.parseInt(trimmedTest);
					String test1 = strTokens.nextToken();
					String trimmedTest1 = test1.replace(" ", "");
					int currentStudents = Integer.parseInt(trimmedTest1);
					strTokens.nextToken();
					String instructorName = strTokens.nextToken();
					String test2 = strTokens.nextToken();
					String trimmedTest2 = test2.replace(" ", "");
					int courseSection = Integer.parseInt(trimmedTest2);
					String courseLocation = strTokens.nextToken();

					// creates a course list from the elements found
					Course c = new Course(courseName, courseID, maxStudents, currentStudents, instructorName,
							courseSection, courseLocation);
					courseList.add(c);
					count++;
				} else {
					strTokens.nextToken();
					count++;
				}
			}
		} else {
			deSerialization();

			String fileName2 = "newtext.txt";
			// References one line at a time
			String line = null;
			try {
				// FileReader reads text files as characters as opposed to bytes (like
				// FileInputStream)
				// First, we instantiate the file reader class
				// It's parameter would be the name of the file to read (in this case, the
				// string variable which represents the file name);

				FileReader fileReader = new FileReader(fileName2);

				// The BufferedReader class can wrap around Readers, like FileReader, to buffer
				// the input and improve efficiency.
				// ALWAYS wrap FileReader in BufferedReader

				BufferedReader bufferedReader = new BufferedReader(fileReader);

				// readLine() reads a line of text.
				// A line is considered to be terminated by a new line ('\n'). So Buffered
				// reader would literally read line by line.
				// While there are still lines to read, our program will print the file

				while ((line = bufferedReader.readLine()) != null) {
					//System.out.println(line);
					String[] animalsArray = line.split(",");
					String firstName = animalsArray[0];
					String lastName = animalsArray[1];
					Student student = new Student(firstName, lastName);
					Admin.masterRegistry.add(student);
					//System.out.println(Admin.masterRegistry.size());
				}

				// Always close files
				bufferedReader.close();
			}
			// The catch block performs a specific action depending on the exception
			catch (FileNotFoundException ex) {
				System.out.println("Unable to open file '" + fileName2 + "'");
				// the printStackTrace method will print out an error output stream ("What went
				// wrong?" report);

				ex.printStackTrace();
			}

			catch (IOException ex) {
				System.out.println("Error reading file '" + fileName2 + "'");
				ex.printStackTrace();
			}

		}

		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
		System.out.println("Welcome!");
		System.out.println("Enter '1' to login as Admin");
		System.out.println("Enter '2' to login as Student");
		System.out.println("Enter '3' to Exit");
		String option = in.readLine();

    // error message
		while (!option.contentEquals("1") && !option.contentEquals("2") && !option.contentEquals("3")) {
			System.out.println("Sorry, your input is not valid! Try again.");
			System.out.println("Enter '1' to login as Admin");
			System.out.println("Enter '2' to login as Student");
			System.out.println("Enter '3' to Exit");
			option = in.readLine();
		}

		if (option.contentEquals("1")) {

			System.out.println("Enter the Admin username:");
			String userInput = in.readLine();
			System.out.println("Enter the Admin password:");
			String passInput = in.readLine();

      // error message
			while (!userInput.contentEquals("admin") || !passInput.contentEquals("admin001")) {
				if (!userInput.contentEquals("admin")) {
					System.out.println("Sorry the username is not correct! Try again.");
					System.out.println("Enter the Admin username:");
					userInput = in.readLine();
					System.out.println("Enter the Admin password:");
					passInput = in.readLine();
				} else if (!passInput.contentEquals("admin001")) {
					System.out.println("Sorry the password is not correct! Try again.");
					System.out.println("Enter the Admin username:");
					userInput = in.readLine();
					System.out.println("Enter the Admin password:");
					passInput = in.readLine();
				}
			}

			System.out.println("Congrats! You have been successfully logged in as an admin!");
			boolean logout = false;
			while (!logout) {
				System.out.println("What would you like to do today?");
				System.out.println("Enter '1' to Manage Courses");
				System.out.println("Enter '2' to View Reports");
				System.out.println("Enter '3' to Exit");
				String option2 = in.readLine();
				if (option2.contentEquals("1")) {

					System.out.println("Course Management");
					System.out.println("Enter '1' to Create a New Course");
					System.out.println("Enter '2' to Delete a Course");
					System.out.println("Enter '3' to Edit a Course");
					System.out.println("Enter '4' to Display Information for a Given Course");
					System.out.println("Enter '5' to Register a Student");
					System.out.println("Enter '6' to Exit");
					String option3 = in.readLine();

					if (option3.contentEquals("1")) {
						admin.createCourse();
					} else if (option3.contentEquals("2")) {
						admin.deleteCourse();
					} else if (option3.contentEquals("3")) {
						admin.editCourse();
					} else if (option3.contentEquals("4")) {
						admin.displayACourse();
					} else if (option3.contentEquals("5")) {
						admin.registerStudent();
					} else {
						System.out.println("Thank you & come again! :D");
						logout = true;
						serialization();

						String fileName2 = "newtext.txt";
						Scanner scan = new Scanner(System.in);

						try {
							FileWriter fileWriter = new FileWriter(fileName2);
							BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

							for (int i = 0; i < Admin.masterRegistry.size(); i++) {
								String firstName = Admin.masterRegistry.get(i).getFirstName();
								String lastName = Admin.masterRegistry.get(i).getLastName();
								bufferedWriter.write(firstName + ",");
								bufferedWriter.write(lastName + "\n");
							}

							// Always close writer
							bufferedWriter.close();
							System.out.println("Master Registry recorded!");
						}

						// Always close files
						catch (IOException exk) {
							System.out.println("Error writing file '" + fileName2 + "'");
							exk.printStackTrace();
						}
					}

				} else if (option2.contentEquals("2")) {

					System.out.println("View Reports");
					System.out.println("Enter '1' to View All Courses");
					System.out.println("Enter '2' to View All Full Courses");
					System.out.println("Enter '3' to Write to File All Full Courses");
					System.out.println("Enter '4' to View Registered Students of Specific Course");
					System.out.println("Enter '5' to View All Registered Courses of Specific Student");
					System.out.println("Enter '6' to Sort Courses");
					System.out.println("Enter '7' to Exit");
					String option3 = in.readLine();

					if (option3.contentEquals("1")) {
						admin.adminViewAllCourses();
					} else if (option3.contentEquals("2")) {
						admin.viewFullCourses();
					} else if (option3.contentEquals("3")) {
						admin.writeToFileFullCourses();
					} else if (option3.contentEquals("4")) {
						admin.viewRegisteredStudents();
					} else if (option3.contentEquals("5")) {
						admin.viewAllStudentCourses();
					} else if (option3.contentEquals("6")) {
						admin.sortCourses();
					} else {
						System.out.println("Thank you & come again! :D");
						logout = true;
						serialization();

						String fileName2 = "newtext.txt";
						Scanner scan = new Scanner(System.in);

						try {
							FileWriter fileWriter = new FileWriter(fileName2);
							BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

							for (int i = 0; i < Admin.masterRegistry.size(); i++) {
								String firstName = Admin.masterRegistry.get(i).getFirstName();
								String lastName = Admin.masterRegistry.get(i).getLastName();
								bufferedWriter.write(firstName + ",");
								bufferedWriter.write(lastName + "\n");
							}

							// Always close writer
							bufferedWriter.close();
							System.out.println("Master Registry recorded!");
						}

						// Always close files
						catch (IOException exk) {
							System.out.println("Error writing file '" + fileName2 + "'");
							exk.printStackTrace();
						}
					}

				} else {
					System.out.println("Thank you & come again! :D");
					logout = true;
					serialization();

					String fileName2 = "newtext.txt";
					Scanner scan = new Scanner(System.in);

					try {
						FileWriter fileWriter = new FileWriter(fileName2);
						BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

						for (int i = 0; i < Admin.masterRegistry.size(); i++) {
							String firstName = Admin.masterRegistry.get(i).getFirstName();
							String lastName = Admin.masterRegistry.get(i).getLastName();
							bufferedWriter.write(firstName + ",");
							bufferedWriter.write(lastName + "\n");
						}

						// Always close writer
						bufferedWriter.close();
						System.out.println("Master Registry recorded!");
					}

					// Always close files
					catch (IOException exk) {
						System.out.println("Error writing file '" + fileName2 + "'");
						exk.printStackTrace();
					}
				}
			}

		} else if (option.contentEquals("2")) {

			System.out.println("Please enter your first name:");
			String firstName = in.readLine();
			System.out.println("Please enter your last name:");
			String lastName = in.readLine();

			Student searchStudent = new Student(firstName, lastName);

			for (int i = 0; i < Admin.masterRegistry.size(); i++) {
				if ((Admin.masterRegistry.get(i).getFirstName() != firstName)
						&& (i == Admin.masterRegistry.size() - 1)) {
					System.out.println("Oops! We don't have you in the Student List. Ask an admin to register you!");
					System.exit(0);
				} else {
					break;
				}
			}

			if ((searchStudent.getUsername() == null) || (searchStudent.getPassword() == null)) {
				System.out.println("Let's set up your username and password!");
				System.out.println("Please enter your desired username:");
				String setUser = in.readLine();
				System.out.println("Please enter your desired password:");
				String setPass = in.readLine();
				for (int i = 0; i < Admin.masterRegistry.size(); i++) {
					if ((Admin.masterRegistry.get(i).getFirstName() == firstName)
							&& (Admin.masterRegistry.get(i).getLastName() == lastName)) {
						Admin.masterRegistry.get(i).setUsername(setUser);
						Admin.masterRegistry.get(i).setPassword(setPass);
						System.out.println("Your username and password has been successfully set! Thanks!");
					}
				}
			}

			System.out.println("Enter your Student username:");
			String userInput = in.readLine();
			System.out.println("Enter your Student password:");
			String passInput = in.readLine();

			boolean valid = false;
			while (valid) {
				Student student = new Student("firstName", "lastName");
				student.setUsername(userInput);
				student.setPassword(passInput);
				if (Admin.masterRegistry.contains(student)) {
					valid = true;
				} else {
					System.out.println("Sorry the username is not correct! Try again.");
					continue;
				}
			}

			Student student = new Student(firstName, lastName);
			System.out.println("Congrats! You have been successfully logged in as " + firstName + " " + lastName + "!");
			System.out.println("What would you like to do today?");
			System.out.println("Enter '1' to View All Courses");
			System.out.println("Enter '2' to View All Available Courses");
			System.out.println("Enter '3' to Register to a Course");
			System.out.println("Enter '4' to Withdraw from a Course");
			System.out.println("Enter '5' to View All Registered Courses");
			System.out.println("Enter '6' to Exit");
			String option3 = in.readLine();

			if (option3.contentEquals("1")) {
				student.studentViewAllCourses();
			} else if (option3.contentEquals("2")) {
				student.viewAvailableCourses();
			} else if (option3.contentEquals("3")) {
				student.registerToCourse();
			} else if (option3.contentEquals("4")) {
				student.withdrawFromCourse();
			} else if (option3.contentEquals("5")) {
				student.viewAllRegisteredCourses();
			} else {
				System.out.println("Thank you & come again! :D");
				serialization();

				String fileName2 = "newtext.txt";
				Scanner scan = new Scanner(System.in);

				try {
					FileWriter fileWriter = new FileWriter(fileName2);
					BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

					for (int i = 0; i < Admin.masterRegistry.size(); i++) {
						String firstName1 = Admin.masterRegistry.get(i).getFirstName();
						String lastName1 = Admin.masterRegistry.get(i).getLastName();
						bufferedWriter.write(firstName1 + ",");
						bufferedWriter.write(lastName1 + "\n");
					}

					// Always close writer
					bufferedWriter.close();
					System.out.println("Master Registry recorded!");
				}

				// Always close files
				catch (IOException exk) {
					System.out.println("Error writing file '" + fileName2 + "'");
					exk.printStackTrace();
				}
			}

		} else {
			System.out.println("Thank you & come again! :D");
			serialization();

			String fileName2 = "newtext.txt";
			Scanner scan = new Scanner(System.in);

			try {
				FileWriter fileWriter = new FileWriter(fileName2);
				BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);

				for (int i = 0; i < Admin.masterRegistry.size(); i++) {
					String firstName = Admin.masterRegistry.get(i).getFirstName();
					String lastName = Admin.masterRegistry.get(i).getLastName();
					bufferedWriter.write(firstName + ",");
					bufferedWriter.write(lastName + "\n");
				}

				// Always close writer
				bufferedWriter.close();
				System.out.println("Master Registry recorded!");
			}

			// Always close files
			catch (IOException exk) {
				System.out.println("Error writing file '" + fileName2 + "'");
				exk.printStackTrace();
			}
		}

	}

}
