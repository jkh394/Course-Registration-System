class Student extends User implements StudentInterface, java.io.Serializable {

	public Student(String firstName, String lastName) {
		super(firstName, lastName);
	}

	@Override
	public void studentViewAllCourses() {
		for (int i = 0; i < courseList.size(); i++) {
			// prints out the courses within the course list
			courseList.get(i).studentPrint();
		}
	}

	@Override
	public void viewAvailableCourses() {
		for (int i = 0; i < courseList.size(); i++) {
			if (courseList.get(i).getCurrentStudents() != courseList.get(i).getMaxStudents()) {
				courseList.get(i).studentPrint();
			}
		}
	}

	@Override
	// In this case the student must enter the course name, section, and student
	// full name, the name will be added to the appropriate course.
	public void registerToCourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course name: ");
		String courseName = in.readLine();
		System.out.println("Enter the course section ID: ");
		String courseID = in.readLine();
		System.out.println("Enter your first name: ");
		String firstName = in.readLine();
		System.out.println("Enter your last name: ");
		String lastName = in.readLine();

		for (int i = 0; i < courseList.size(); i++) {
			if (courseList.get(i).getCourseName() == courseName && courseList.get(i).getCourseID() == courseID) {
				Student student = new Student(firstName, lastName);
				courseList.get(i).studentList.add(student);
				System.out.println("You have been successfully added to the course!");
			}
		}
	}

	@Override
	// In this case the student will be asked to enter name and the course name,
	// then the name of student will be taken off from given course's list.
	public void withdrawFromCourse() throws IOException {
		BufferedReader in = new BufferedReader(new InputStreamReader(System.in));

		System.out.println("Enter the course name: ");
		String courseName = in.readLine();
		System.out.println("Enter your first name: ");
		String firstName = in.readLine();
		System.out.println("Enter your last name: ");
		String lastName = in.readLine();

		for (int i = 0; i < courseList.size(); i++) {
			if (courseList.get(i).getCourseName() == courseName) {
				Student student = new Student(firstName, lastName);
				courseList.get(i).studentList.remove(student);
				System.out.println("You have been successfully removed from the course!");
			}
		}
	}

	@Override
	public void viewAllRegisteredCourses() {
  
	}
}
