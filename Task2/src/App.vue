<template>
<div class="container">
  <div class="select">
     <select v-model="filter">
          <option value="Admin">Admin</option>
          <option value="User">User</option>
      </select> 
  </div>
  <div v-if="filter !== ''" class="greeting"><h2>Welcome {{filter}}!</h2></div>
  <div class="user" v-if="filter!== '' ">
      <div>
         <div class="imgholder">
          <img :src="user.src" alt="" class="img"> 
          </div> 
        <h3 class="imgholder">{{user.fullname}}</h3>
        <span class="imgchangebutton" v-on:click="change()">Change</span>
        <div v-if="isTrue" class="change">
          <h3>Input your src:</h3>
          <input type="text" v-model="newsrc">
          <div class="submitButton" @click="submit()">Submit</div>
        </div>
      </div>
      <div class="user__information">
          <h2 class="title">{{user.fullname}}</h2>
           <span><span class="inf">Email:</span> {{user.email}}</span>
           <br>
           <span><span class="inf">City:</span> {{user.city}}</span>
            <br>
           <span><span class="inf">BirthDate:</span> {{user.birthdate}}</span>
           <br>
           <span><span class="inf">Age:</span> {{getAge}}</span>
      </div>
  </div>
 

</div>

</template>

<script>
    export default{
      data(){
        return{
          filter: '',
          user:{
            src: '',
            fullname: 'Batyrkhan Syrym',
            email: 'syrymbatyrkhan@gmail.com',
            city: 'Aktau',
            birthdate: '2005-01-11'
          },
          isTrue: false,
          newsrc: ''
        }
      },
      computed:{
        getAge(){
           const birthdate = new Date(this.user.birthdate);
           const today = new Date();
            const age = today.getFullYear() - birthdate.getFullYear();
            return age;
        }
      },
      methods:{
        change(){
          this.isTrue = !this.isTrue;
        },
        submit(){
            try{
               if(this.newsrc.length ===0){
              console.log('asdads');
            return;
          }else{
            this.user.src = this.newsrc;
            this.isTrue = !this.isTrue;
          }

            }catch(exception){
              alert('exception');
            }
            
         
         
        }
      }
    }
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container{
  width: 60%;
  margin: 100px auto;
}
.select{
  display: flex;
  justify-content: center;
}
.greeting{
  display: flex;
  justify-content: center;
  margin-top: 5px;
}
.img{
  border-radius: 50%;
  width: 150px;
}
.imgholder{
  margin-bottom: 5px;
}
.user{
  display: flex;
  justify-content: space-between;
  width: 70%;
  margin: 30px auto;
}
.user__information{
  line-height: 1.65;
  border: 1px solid #d9e1cc;
  padding: 10px 20px ;
}
.inf{
  font-weight: bold;
  font-size: 18px;
}
.title{
  border-bottom: 1px solid #d9e1cc;
}
.imgchangebutton{
  background-color: gray;
  opacity: 0.8;
  padding: 5px 10px ;
  border-radius: 7px;
  display: flex;
  justify-content: center;
  width: 80%;
  margin: 0 auto;
}
.change{
  margin-top: 10px; 
}
.submitButton{
    background-color:green;
    opacity: 0.7;
    color: #d9e1cc;
    text-align: center;
    margin-top: 10px;
    padding: 5px 0px;
    border-radius: 10px;
}
</style>
