<template>
  <form @submit.prevent="submitForm">
    <div class="form-control">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model="userName" />
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model.number="userAge" ref="ageInput" />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <!-- Value akan disimpan ke referrer -->
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <!-- Tanamkan v-model dam value ke setiap checkbox -->
      <div>
        <input id="interest-news" name="interest" type="checkbox" value="news" v-model="interest" />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" name="interest" type="checkbox" value="tutorials" v-model="interest" />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" name="interest" type="checkbox" value="nothing" v-model="interest" />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <!-- Tanamkan v-model dan value ke setiap radiobutton -->
      <div>
        <input id="how-video" name="how" type="radio" value="video" v-model="how" />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" name="how" type="radio" value="blog" v-model="how" />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" value="other" v-model="how" />
        <label for="how-other">Other</label>
      </div>
    </div>
    <!-- Kalau hanya ada satu checkbox maka tipe datanya boolean dan tidak perlu diberikan value -->
    <div class="form-control">
      <input type="checkbox" name="confirm-terms" id="confirm-terms" v-model="confirm">
      <label for="confirm-terms"> Agree to terms of use?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
export default {
  data(){
    return {
      userName:'',
      userAge:null,
      referrer:'wom', //wom sebagai element default yang dipilih
      interest:[], // interest bertipe array karena mengambil data dari checkboxes
      how:null,
      confirm:false,
    }
  },
  methods:{
    submitForm(){
      console.log('Username: '+this.userName);
      this.userName='';
      console.log('User Age: ');
      console.log(this.userAge + 5);
      console.log(this.$refs.ageInput.value + 5);
      console.log(31);
      this.userAge=null;
      console.log('Referrer: '+this.referrer);
      this.referrer='wom'; // setelah disubmit, kembali ke pilih wom
      console.log('Checkboxes');
      console.log(this.interest);
      console.log('Radio buttons');
      console.log(this.how);
      this.interest=[];
      this.how=null;
      console.log('Confirm?');
      console.log(this.confirm);
      this.confirm=false;
    }
  }
}
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>