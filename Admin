class Admin extends User implements AdminInterface, java.io.Serializable {
	static ArrayList<Student> masterRegistry = new ArrayList<Student>();

	public Admin() {
		super();
		this.user = "admin";
		this.pass = "admin001";
	}

	public ArrayList<Student> getMasterRegistry() {
		return masterRegistry;
	}

	public void setUsername(ArrayList<Student> masterRegistry) {
		this.masterRegistry = masterRegistry;
	}

	@Override // same name, same parameters or signature and same return type
	public void createCourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course name: ");
		this.courseName = in.readLine();

		System.out.println("Enter the course ID: ");
		this.courseID = in.readLine();

		System.out.println("Enter the maximum number of students that can register: ");
		String mS = in.readLine();
		int maxStudents = Integer.parseInt(mS);

		System.out.println("Enter the current number of students that are registered: ");
		String cS = in.readLine();
		int currentStudents = Integer.parseInt(cS);

		System.out.println("Enter the instructor's name: ");
		this.instructorName = in.readLine();

		System.out.println("Enter the course section number: ");
		String cSN = in.readLine();
		int courseSection = Integer.parseInt(cSN);

		System.out.println("Enter the course location: ");
		this.courseLocation = in.readLine();

		Course c = new Course(this.courseName, this.courseID, maxStudents, currentStudents, this.instructorName,
				courseSection, this.courseLocation);
		courseList.add(c);

		System.out.println("The new course " + courseName + " has been successfully added!");
	}

	@Override
	public void deleteCourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course name to be deleted: ");
		String courseName = in.readLine();

		for (int i = 0; i < courseList.size(); i++) {
			String j = courseList.get(i).getCourseName();
			System.out.println(courseList.get(i).getCourseName());
			if (j.contentEquals(courseName)) {
				courseList.remove(i);
				System.out.println("The course " + courseName + " has been successfully removed!");
				System.out.println(" ");
				break;
			} else if ((!j.contentEquals(courseName)) && (i == courseList.size() - 1)) {
				System.out.println("Oops! We are unable to find that course, let's try again!");
				Admin admin = new Admin();
				admin.deleteCourse();
			}
		}
	}

	@Override
	// This will allow the admin to edit any information on the course except for
	// course ID and name.)
	// Change course instructor and location.
	public void editCourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter '1' to change a course's instructor.");
		System.out.println("Enter '2' to change a course's location.");
		String option = in.readLine();
		System.out.println("Enter the name of the course you would like to edit: ");
		String courseName = in.readLine();

		if (option.contentEquals("1")) {
			System.out.println("Enter the new instructor's name: ");
			String instructorName = in.readLine();
			for (int i = 0; i < courseList.size(); i++) {
				String j = courseList.get(i).getCourseName();
				if (j.contentEquals(courseName)) {
					courseList.get(i).setInstructorName(instructorName);
					System.out.println("Course instructor name has been successfully edited to: " + instructorName);
					System.out.println("");
				}
			}
		} else if (option.contentEquals("2")) {
			System.out.println("Enter the course's new location: ");
			String courseLocation = in.readLine();
			for (int i = 0; i < courseList.size(); i++) {
				String j = courseList.get(i).getCourseName();
				if (j.contentEquals(courseName)) {
					courseList.get(i).setCourseLocation(courseLocation);
					System.out.println("Course location has been successfully edited to: " + courseLocation);
					System.out.println(" ");
				}
			}
		}
	}

	@Override
	// by course ID
	public void displayACourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course ID: ");
		String courseID = in.readLine();
		for (int i = 0; i < courseList.size(); i++) {
			String j = courseList.get(i).getCourseID();
			if (j.contentEquals(courseID)) {
				courseList.get(i).print();
			}
		}
	}

	@Override
	// This option will allow the admin to add a student without assigning to a
	// course.
	// Check Req 11 for student's information
	// Hint: You might need to have an ArrayList of Students where you store Student
	// objects.
	public void registerStudent() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the new student's first name: ");
		String firstName = in.readLine();
		System.out.println("Enter the new student's last name: ");
		String lastName = in.readLine();

		Student newStudent = new Student(firstName, lastName);
		masterRegistry.add(newStudent);
		System.out.println(masterRegistry.get(masterRegistry.size() - 1).getFirstName());
		System.out.println("New student has been successfully added!");
		System.out.println(" ");
	}

	@Override
	// For every course the admin should be able to see the list of enrolled
	// students' names, enrolled student ids, number of students registered, and the
	// maximum number of students allowed to be registered.
	public void adminViewAllCourses() {
		for (int i = 0; i < courseList.size(); i++) {
			// prints out the courses within the course list
			courseList.get(i).print();
		}
	}

	@Override
	// reached the maximum number of students
	public ArrayList<Course> viewFullCourses() {
		ArrayList<Course> returnCourses = new ArrayList<Course>();
		for (int i = 0; i < courseList.size(); i++) {
			if (courseList.get(i).getCurrentStudents() == courseList.get(i).getMaxStudents()) {
				courseList.get(i).print();
				returnCourses.add(courseList.get(i));
			}
		}
		return returnCourses;
	}

	@Override
	// View the names of the students that are registered in a specific course.
	public void viewRegisteredStudents() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course's name: ");
		String courseName = in.readLine();

		for (int i = 0; i < courseList.size(); i++) {
			if (courseList.get(i).getCourseName() == courseName) {
				for (int j = 0; j < studentList.size(); j++) {
					String firstName = courseList.get(i).getStudentList().get(j).getFirstName();
					String lastName = courseList.get(i).getStudentList().get(j).getLastName();
					System.out.println("Registered Students for " + courseName);
					System.out.print("* " + firstName + " " + lastName);
				}
			}
		}
	}

	@Override
	// Given a student first name and last name the system shall display all the
	// courses that student is registered in.
	public void viewAllStudentCourses() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the new student's first name: ");
		String firstName = in.readLine();
		System.out.println("Enter the new student's last name: ");
		String lastName = in.readLine();

		System.out.println(firstName + " " + lastName + "'s Classes:");
		for (int i = 0; i < courseList.size(); i++) {
			for (int j = 0; j < studentList.size(); j++) {
				if (courseList.get(i).getStudentList().get(j).getFirstName() == firstName
						&& courseList.get(i).getStudentList().get(j).getLastName() == lastName) {
					String courseName = courseList.get(i).getCourseName();
					System.out.println("* " + courseName);
				}
			}
		}
	}

	@Override
	// Sort the courses based on the current number of students registered.
	public void sortCourses() {
		for (int i = 0; i < courseList.size(); i++) {
			for (int j = courseList.size() - 1; j > i; j--) {
				if (courseList.get(i).getCurrentStudents() > courseList.get(j).getCurrentStudents()) {
					Course tmp = courseList.get(i);
					courseList.set(i, courseList.get(j));
					courseList.set(j, tmp);
				}

			}

		}

		for (int i = 0; i < courseList.size(); i++) {
			// prints out the courses within the course list
			courseList.get(i).print();
		}
	}

	@Override
	public void writeToFileFullCourses() {
		String fileName = "text.txt";
		Scanner scan = new Scanner(System.in);

		try {
			FileWriter fileWriter = new FileWriter(fileName);
			BufferedWriter bufferedWriter = new BufferedWriter(fileWriter);
			for (int i = 0; i < viewFullCourses().size(); i++) {
				String text = viewFullCourses().get(i).print();
				bufferedWriter.write(text);
				bufferedWriter.newLine();
			}
			// Always close writer
			bufferedWriter.close();
		}
		// Always close files

		catch (IOException exk) {
			System.out.println("Error writing file '" + fileName + "'");
			exk.printStackTrace();
		}
	}

}
