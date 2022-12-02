<template>
  <form action="" method="" @submit.prevent = "submit">
    <label for="email">Email</label>
    <input type="email" required v-model="email">

    <label for="password">Password</label>
    <input type="password" required v-model="password">
    <p v-if="errormsg" class="error">{{errormsg}}</p>

    <label for="role">Role</label>
    <select name="" id="" v-model="role">
        <option value="" selected disabled>Choose your role</option>
        <option value="developer">Web Developer</option>
        <option value="net enginner">Network Engineer</option>
        <option value="HR">Human Resource Manager</option>
        <option value="designer">UI/UX Designer</option>
    </select>

    <div class="box">
        <input type="checkbox" class="check" v-model="accept">
        <label for="title" class="title">Accept terms and conditions</label>
    </div>
    
    <label for="names">Check Names</label>
<div class="box2">

        <input type="checkbox" class="check1" v-model="name" value="Richard">
        <label for="title" class="title" >Richard</label>

        <input type="checkbox" class="check2" value="James" v-model="name">
        <label for="title" class="title" >James</label>
        
        <input type="checkbox" class="check3"  value="Yokko" v-model="name">
        <label for="title" class="title">Yokko</label>  
</div>

<label for="skills">Skills</label>
<input type="text" @keyup.alt= "addSkill" required v-model="skill">

<div v-for="skill in skills" :key="skill"  class="box3">

    <p class="skill">{{skill}}</p> <span class="cross" @click="deleteSkill(skill)">X</span>

</div>

<div class="align">
    <button @click="submit">Create Account</button>
</div>



    
  </form>
<div class="answer">

  <div>Email - {{email}}</div>
  <div>Password - {{password}}</div>
  <div>Role - {{role}}</div>
  <div>Accept - {{accept}}</div>
  <div>Names - {{name}}</div>
  <div>Skills - {{skills}}</div>
</div>
</template>

<script>
export default {

    data() {
        return{
            email: "",
            password:"",
            role: "",
            accept: false,
            name:[],
            skills:[],
            skill:"",
            errormsg: ""

        }
    },

    methods:{
      addSkill(e) {
        if(e.key === ",") {
            this.skills.push(this.skill);
            this.skill = ""
        }
      },

      deleteSkill(skill) {
        // console.log(skill)
        this.skills = this.skills.filter(loopskill => {
            console.log(loopskill)

            return skill != loopskill
        })
      },

      submit() {
        // console.log("submitted")
        if(this.password.length < 8) {
            this.errormsg = "Password must be at leat 8 characters!"
        }
      }

        
    }

}


</script>

<style>


form{
    border: 1px solid grey;
    padding: 20px 25px;
    background-color: rgba(240, 168, 160,0.4);
    max-width: 500px;
    max-height: 1500px;
    
    margin: 20px auto;
}

form label{
    margin-top: 40px;
    text-align: left;
    display: block;
    font-weight: bold;
    font-family: sans-serif;
    font-size: 20px;
    padding-top: 10px;
}

form input{
    display: block;
    margin: 0;
    margin-top: 30px;
    
    border-radius: 15px;
    width: 80%;
    border: 1px solid grey;
    padding: 10px 15px;
    font-size: 18px;
 
}

form input:focus{
     border: none;
    outline: none;
   
}

form select{
    margin-top: 10px;
    width: 100%;
    padding: 15px;
    font-family: Arial;
    font-size: 18px;
}

select option{
    padding: 10px;
}

.box{
    padding-bottom: 20px;
    position: relative;
}

.check{
    position: absolute;
    left: -38%;
    top: -30%;
}

.box .title{
    margin-left: 30px;
}

.answer div{
    margin: 20px;
}

.box2{
    position: relative;
}

.title{
    margin-left: 30px;
}

.check1{
    position: absolute;

    left: -38%;
    top: -9%;
}

.check2{
    position: absolute;
    left: -38%;

    top: 32%;
}

.check3{
    position: absolute;
    left: -38%;

    top: 73%;
}

.box3{
    text-align: left;
}

.skill{
    display: inline-block;
    font-size: 25px;
    font-weight: bold;
    margin-right: 10%;
   
}

.cross{
    font-size: 30px;
    color: red;
    font-weight: bold;
    /* margin-left: 30px; */
}

.align{
    
    margin: 20px;
   
}

button{
    width: 80%;
    padding: 10px 15px;
    border-radius: 15px;
    background-color: salmon;
    border:none;
    font-size: 18px;
}

.error{
    color: red;
    margin-top: 5px;
    padding-top: 5px;
    text-align: left;
}
</style>