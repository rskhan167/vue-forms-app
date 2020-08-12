<template>
    <div class="container">
        <form>
            <div class="row">
                <div>
                    <h1>File a Complaint</h1>
                    <hr>
                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                                type="text"
                                id="email"
                                class="form-control"
                                v-model="userData.email">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model="userData.password">
                    </div>
                    <div class="form-group">
                        <label for="age">Age</label>
                        <input
                                type="number"
                                id="age"
                                class="form-control"
                                v-model="userData.age">
                    </div>

                </div>
            </div>
            <div class="row">
                <div>
                    <label for="message">Message</label><br>
                    <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
                    <textarea
                            id="message"
                            rows="5"
                            class="form-control"
                            v-model="message"></textarea>
                </div>
            </div>
            <div class="row">
                <div>
                    <div class="form-group">
                        <label for="sendmail">
                            <input
                                    type="checkbox"
                                    id="sendmail"
                                    value="SendMail"
                                    v-model="sendMail"> Send Mail
                        </label>
                        <label for="sendInfomail">
                            <input
                                    type="checkbox"
                                    id="sendInfomail"
                                    value="SendInfoMail"
                                    v-model="sendMail"> Send Infomail
                        </label>
                    </div>

                </div>
            </div>
            <div class="row">
                <div>
                    <label for="male">
                        <input
                                type="radio"
                                id="male"
                                value="Male"
                                v-model="gender"> Male
                    </label>
                    <label for="female">
                        <input
                                type="radio"
                                id="female"
                                value="Female"
                                v-model="gender"> Female
                    </label>
                </div>
            </div>
            <div class="row">
                <div>
                    <label for="priority">Priority</label>
                    <select
                            id="priority"
                            class="form-control"
                            v-model="selectedPriority">
                        <option v-for="(priority, index) in priorities" :key="index">{{ priority }}</option>
                    </select>
                </div>
            </div>
            <div class="row">
              <div class="switch">
                <app-switch v-model="dataSwitch"></app-switch>
              </div>
            </div>
            <div class="row">
                <div>
                    <button
                            class="btn" @click.prevent="submitted">Submit!
                    </button>
                </div>
            </div>
        </form>
        <hr>
        <div class="data" v-if="isSubmitted">
            <div>
                <div class="panel">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Mail: {{ userData.email }} </p>
                        <p>Password: {{ userData.password }}</p>
                        <p>Age: {{ userData.age }}</p>
                        <p style="white-space: pre">Message: {{ message }}</p>
                        <p><strong>Send Mail?</strong></p>
                        <ul>
                            <li v-for="(item, index) in sendMail" :key="index">{{ item }}</li>
                        </ul>
                        <p>Gender: {{ gender }}</p>
                        <p>Priority: {{ selectedPriority }}</p>
                        <p>Switched: {{ dataSwitch }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>




<script>
import Switch from './components/Switch.vue';

    export default {
      data(){
        return{
          userData: {
            email: '',
            password: '',
            age: 27
          },
          message: 'Write something here!!!',
          sendMail: [],
          gender: 'Male',
          selectedPriority: 'High',
          priorities: ['High', 'Medium', 'Low'],
          dataSwitch: true,
          isSubmitted: false
        };
      },
      methods: {
        submitted(){
          this.isSubmitted = true;
        }
      },
      components: {
        appSwitch: Switch
      }
    }
</script>

<style scoped>
    h1{
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    form{
      text-align: center;
    }
    .form-group, label{
      padding: 10px;
    }
    button{
      margin: 20px;
    }
    .panel{
      border: 1.5px solid black;
      margin: 20px;
      margin-left: 350px;
      margin-right: 350px;
      
    }
    .panel-body{
      margin-left: 10px;
    }
    .panel-heading{
      font-size: 24px;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin-left: 10px;
    }
    input{
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
      resize: vertical;
    }
    label {
      padding: 12px 12px 12px 0;
      display: inline-block;
    }
    .btn{
      background-color: #4CAF50;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    .container {
      border-radius: 5px;
      background-color: #f2f2f2;
      padding: 20px;
    }
    textarea{
      width: 400px;
      height: 100px;
      border: 3px solid #cccccc;
      padding: 5px;
    }
</style>
