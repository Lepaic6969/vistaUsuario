<template>
  <div id="UserBalance">
     <h2>{{username}}</h2>
     <h2>Nombre: <span> {{name}}  </span><br>Apellido:<span> {{last_name}}</span><br>Departamento:<span> {{department}}</span><br>Id: <span>{{clearance}}</span><br></h2>
     
  </div>
</template>

   <script>
   import axios from 'axios';
   export default {
      name: 'UserBalance',
      data: function (){
       return {
                
                name:"",
                last_name:"",
                department:"",
                clearance : 666,
              
                
             }
       },

created: function(){
   this.username = this.$route.params.username
   let self = this
   axios.get("https://dokimanback.herokuapp.com/user/balance/" + this.username) 
              
   //        
      .then((result) => {
          self.name = result.data.name
          self.last_name=result.data.last_name
          self.department=result.data.department
          self.clearance=result.data.clearance

      })
      .catch((error) => {
             alert("ERROR Servidor");
       });
  }
}
</script>

<style>
    #UserBalance{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        }

    #UserBalance h2{
        font-size: 50px;
        color: #283747;
        }
    #UserBalance span{
        color: crimson;
        font-weight: bold;
        }
</style>
