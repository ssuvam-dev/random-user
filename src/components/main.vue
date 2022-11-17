<script>
    export default{
        name:'mainContent',
        data(){
            return {
                
                title:"Mr.",
                firstName:"Subham",
                lastName:"Sharma",
                email:"abc@gmail.com",
                age:10,
                city:"Gulariya",
                zip:100,
                picture:"https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-profiles/avatar-1.webp"
            }
        },
        methods:{
            async getUser(){  
                 const data=await fetch('https://randomuser.me/api/');
                 const { results }=await data.json();
                 console.log(results);
                 this.title=results[0].name.title;
                 this.firstName=results[0].name.first;
                 this.lastName=results[0].name.last; 
                 this.picture=results[0].picture.large;
                 this.email=results[0].email;
                 this.age=results[0].dob.age;
                 this.city=results[0].location.city;
                 this.zip=results[0].location.street.number;
            }
        }
    }
</script>
<template>
   <section class="vh-100" style="background-color: #9de2ff;">
  <div class="container py-5 h-100">
    <div class="row d-flex justify-content-center align-items-center h-100">
      <div class="col col-md-9 col-lg-7 col-xl-5">
        <div class="card" style="border-radius: 15px;">
          <div class="card-body p-4">
            <div class="d-flex text-black">
              <div class="flex-shrink-0">
                <img :src="picture"
                  :alt="firstName" class="img-fluid"
                  style="width: 180px; border-radius: 10px;">
              </div>
              <div class="flex-grow-1 ms-3">
                <h5 class="mb-1">{{title}}. {{firstName}} {{lastName}}</h5>
                <p class="mb-2 pb-1" style="color: #2b2a2a;">{{email}}</p>
                <div class="d-flex justify-content-start rounded-3 p-2 mb-2"
                  style="background-color: #efefef;">
                  <div>
                    <p class="small text-muted mb-1">Age</p>
                    <p class="mb-0">{{age}}</p>
                  </div>
                  <div class="px-3">
                    <p class="small text-muted mb-1">City</p>
                    <p class="mb-0">{{city}}</p>
                  </div>
                  <div>
                    <p class="small text-muted mb-1">Zip</p>
                    <p class="mb-0">{{zip}}</p>
                  </div>
                </div>
                <div class="d-flex pt-1">
                  <button  @click="getUser()" class="btn btn-primary flex-grow-1">Next</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

</template>

