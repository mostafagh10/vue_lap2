<template>
    <div>
      <button class="btn btn-success w-100 my-1" data-bs-toggle="modal" data-bs-target="#exampleModal">
        Add
      </button>
  
      <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel">Add New Student</h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
              <input type="text" placeholder="ID" v-model="stdId" class="form-control my-2" />
              <input type="text" placeholder="Name" v-model="stdname" class="form-control my-2" />
              <input type="text" placeholder="City" v-model="stdcity" class="form-control my-2" />
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
              <button type="button" class="btn btn-success" @click="addNewStudent">Save Changes</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        stdId: 0,
        stdname: "",
        stdcity: ""
      };
    },
    methods: {
      addNewStudent() {
        let stdInfo = {
          id: this.stdId,
          name: this.stdname,
          city: this.stdcity
        };
        console.log(stdInfo);
        this.$emit("onaddstudent", stdInfo);
      }
    }
  };
  </script>
  
  <style>
  /* Add your custom styles here */
  </style>
  