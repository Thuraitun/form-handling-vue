<template>
  <div>
    <pre>
      {{ JSON.stringify(formValue, null, 2) }}
    </pre>
  </div>
  <form @submit="submitForm">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model.trim.lazy="formValue.name">
    </div>

    <div>
      <label for="profile">Profile Summary</label>
      <textarea type="text" v-model="formValue.profileSummary" />
    </div>
    
    <div>
      <label for="country">Country</label>
      <select id="country" v-model="formValue.country">
        <option value="">Choose Country</option>
        <option value="Myanmar">Myanmar</option>
        <option value="Thailand">Thailand</option>
        <option value="Singapore">Singapore</option>
        <option value="Malaysia">Malaysia</option>
      </select>
    </div>

    <div>
      <label for="job-location">Job Location</label>
      <select id="job-location" multiple v-model="formValue.jobLocation">
        <option value="Myanmar">Myanmar</option>
        <option value="Thailand">Thailand</option>
        <option value="Singapore">Singapore</option>
        <option value="Malaysia">Malaysia</option>
      </select>
    </div>

    <div>
      <input type="checkbox" id="remotework" v-model="formValue.remoteWork" true-value="yes" false-value="no"/>
      <label for="remotework">Open to remote work?</label>
    </div>

    <div>
      <label for="">Skills Set</label>
      <input type="checkbox" id="html" value="HTML" v-model="formValue.skillSet">
      <label for="html">HTML</label>
      <input type="checkbox" id="css" value="CSS" v-model="formValue.skillSet">
      <label for="css">CSS</label>
      <input type="checkbox" id="javascript" value="Javascript" v-model="formValue.skillSet">
      <label for="javascript">Javascript</label>
    </div>

    <div>
      <label for="">Years of Experience</label>
      <input 
        type="radio"
        id="0-2"
        value="0-2"
        v-model="formValue.yearsOfExperience" 
      />
      <label for="0-2">0-2</label>
      <input 
        type="radio"
        id="3-5"
        value="3-5"
        v-model="formValue.yearsOfExperience" 
      />
      <label for="3-5">3-5</label>
      <input 
        type="radio"
        id="6-10"
        value="6-10"
        v-model="formValue.yearsOfExperience" 
      />
      <label for="6-10">6-10</label>
      <input 
        type="radio"
        id="10+"
        value="10+"
        v-model="formValue.yearsOfExperience" 
      />
      <label for="10+">10+</label>
    </div>
    
    <div>
      <label for="age">Age</label>
      <input @keyup.enter="submit" type="number" id="age" v-model.number="formValue.age" />
    </div>

    <div>
      <button>Submit</button>
    </div>
  </form>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
         formValue: {
          name: '',
          profileSummary: '',
          country: '',
          jobLocation: [],
          remoteWork: 'no',
          skillSet: [],  
          yearsOfExperience: '',
          age: null,   
        },
      }
    },
    methods: {
      submitForm(event) {
        event.preventDefault()
        console.log('Form Values', this.formValue)
      },
    },
  };
</script>

<style>
  #app{
    margin-top: 60px;
  }
  label {
    font-weight: bold;
    display: flex;
    margin-bottom: 5px;
  }
  
  input + label {
    font-weight: bold;
    display: inline-flex;
    margin-right: 20px;
  }

  input[type='text'],
  textarea,
  select {
    display: block;
    padding: 6px 12px;
    width: 400px;
    font-size: 14px;
    line-height: 1.42857143;
    color: #555;
    background-color: #fff;
    background-image: none;
  }
</style>