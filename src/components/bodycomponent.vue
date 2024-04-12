<template>
    <div class="col-md-9 m-2">
      <!-- Child component to add new students -->
      <addcomponent @onaddstudent="addNewStudentFromBody" />
  
      <!-- Table to display list of students -->
      <table class="table table-striped table-bordered">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>City</th>
            <th>Actions</th> <!-- Column for update and delete buttons -->
          </tr>
        </thead>
        <tbody>
          <!-- Loop through 'students' array and display each student -->
          <tr v-for="student in students" :key="student.id">
            <td>{{ student.id }}</td>
            <td>{{ student.name }}</td>
            <td>{{ student.city }}</td>
            <td>
              <!-- Button to update student -->
              <button class="btn btn-primary" @click="editStudent(student)" data-bs-toggle="modal" data-bs-target="#editModal">Edit</button>
              <!-- Button to delete student -->
              <button class="btn btn-danger" @click="deleteStudent(student.id)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
  
      <!-- Edit Modal -->
      <div class="modal fade" id="editModal" tabindex="-1" aria-labelledby="editModalLabel" aria-hidden="true">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="editModalLabel">Edit Student</h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
              <input type="text" v-model="editedStudent.name" class="form-control my-2" placeholder="Name" />
              <input type="text" v-model="editedStudent.city" class="form-control my-2" placeholder="City" />
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
              <button type="button" class="btn btn-primary" @click="saveChanges">Save Changes</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import students from '../students'; // Assuming 'students' is an array of student data
  import addcomponent from './addcomponent.vue'; // Import child component with corrected naming convention
  
  export default {
    data() {
      return {
        students: students,
        editedStudent: {} // Data object to hold currently edited student
      };
    },
    methods: {
      // Method to add new student from child component
      addNewStudentFromBody(studentInfo) {
        this.students.push(studentInfo);
      },
      // Method to edit student
      editStudent(student) {
        // Set 'editedStudent' to a copy of 'student' for editing in the modal
        this.editedStudent = { ...student };
      },
      // Method to save changes after editing student
      saveChanges() {
        // Find the index of 'editedStudent' in 'students' array
        const index = this.students.findIndex(student => student.id === this.editedStudent.id);
        if (index !== -1) {
          // Update the student data with edited values
          this.students[index].name = this.editedStudent.name;
          this.students[index].city = this.editedStudent.city;
          // Close the modal
          $('#editModal').modal('hide');
        }
      },
      // Method to delete student by ID
      deleteStudent(studentId) {
        const index = this.students.findIndex(student => student.id === studentId);
        if (index !== -1) {
          this.students.splice(index, 1); // Remove student from array
        }
      }
    },
    components: {
      addcomponent
    }
  };
  </script>
  
  <style>
  /* Add your custom styles here */
  </style>
  