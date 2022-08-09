<template>

  <form @submit.prevent="handleSubmit">
    <label>email</label>
    <input type="email" required v-model="email">

    <label>password</label>
    <input type="password" required v-model="password">
    <div class="error" v-if="passwordError">{{passwordError}}</div>

    <label>Role</label>
    <select v-model="role">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Designer</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">

    <div class="best">
        <div v-for="skill in skills" :key="skill" class="pill" >
            <div @click="removeSkill(skill)">{{ skill }}</div>
        </div>
    </div>


    <div class="terms" >
        <input type="checkbox" required v-model="terms">
        <label> Accept terms and conditions.</label>
    </div>

    <button class="submit">
        Create Account
    </button>
    <!-- <div>
        <input type="checkbox" value="Trevor" v-model="names">
        <label > Trevor</label>
    </div>
    <div>
        <input type="checkbox" value="Arapu" v-model="names">
        <label > Arapu</label>
    </div>
    <div>
        <input type="checkbox" value="Morris" v-model="names">
        <label > Morris</label>
    </div> -->
  </form>

    <!-- <h4>Email: {{email}}</h4>
    <h4>Password: {{password}}</h4>
    <h4>Role: {{role}}</h4>
    <h4>Terms Accepted: {{terms}}</h4>
    <h4>Names: {{names}}</h4> -->
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            passwordError: '',
            role: '',
            terms: false,
            tempSkill: '',
            skills: []
            // names: []
        }
    },
    methods: {
        addSkill(e) {

            if(e.key === "," && this.tempSkill) {
                if(!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = ''
            }
        },
        removeSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return skill !== item
            })
        },
        handleSubmit() {
            //validate password
            this.passwordError = this.password.length > 5 ? '': 'Password Must be 6 characters long'
            if(!this.passwordError) {
                console.log('email:', this.email)
                console.log('password:', this.password)
                console.log('role:', this.role)
                console.log('skills:', this.skills)
                console.log('terms accepted:', this.terms)
            }
        }
    }

}
</script>

<style>
    form {
        width: 600px;
        display: flex;
        flex-direction: column;
        padding: 20px;
        margin: 10px auto;
        background: #ffffff;
        border-radius: 7px;
        text-align: left;
    }
    label {
        color: rgb(125, 125, 125);
        display: inline-block;
        margin: 25px 0 15px;
        font-weight: bold;
        letter-spacing: 2px;
        text-transform: lowercase;
    }
    form input {
        background: #e9e9e9;
        padding: 10px 15px;
        border-radius: 7px;
        border: none;
    }
    select {
        background: #e9e9e9;
        padding: 10px 15px;
        border-radius: 7px;
        border: none;
    }
    input[type="checkbox"] {
        margin-right: 10px;
        cursor: pointer;
    }
    .best {
        display: flex;
        flex-direction: row;
    }
    .pill {
        padding:10px 15px;
        background: #e9e9e9;
        margin: 10px;
        border-radius: 13px;
        max-width: 100px;
        cursor: pointer; 
    }
    button {
        padding: 10px 20px;
        margin: 10px;
        border: none;
        background: #0f197e;
        color: #ffffff;
        border-radius: 5px;
        width: 150px;
        cursor: pointer;
    }
    .error {
        padding:10px 15px;
        background: #ff0000;
        margin: 10px;
        margin-left: 0;
        border-radius: 5px;
        max-width: 400px;
        cursor: not-allowed; 
        color: #ffffff;
    }
</style>