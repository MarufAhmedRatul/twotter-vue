<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
        <h1 class="user-profile__username">@{{ user.username }}</h1>
        <div class="user-profile__admin-badge" v-if="user.isAdmin">
            Admin
        </div><!-- admin badge end -->
        <div class="user-profile__follower-count">
            <strong>followers</strong> : {{ followers }}
        </div><!-- follower count end -->
    </div><!-- user panel end -->
  </div><!-- user profile end -->
</template>

<script>


export default {
  name: "UserProfile",
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_MarufAhmed',
        firstname: 'Maruf',
        lastname: 'Ahmed',
        email: 'ahmedratul217@gmail.com',
        isAdmin: true
      }
    }
  },
  watch:{
    followers(newFollowerCount, oldFollowerCount){
      if(oldFollowerCount < newFollowerCount){
        console.log(`${this.user.username} has gained a follwer!`)
      }
    }
  },
  computed:{
    fullname(){
      return `${this.user.firstname} ${this.user.lastname}`;
    }
  },
  methods:{
    followUser(){
      this.followers++
    }
  },
  mounted() {
    this.followUser();
  }
}
</script>

<style>
    .user-profile{
        display: grid;
        grid-template-columns: 1fr 3fr;
        padding: 50px 5%;
    }
    .user-profile__user-panel{
        display: flex;
        flex-direction: column;
        margin-right: 50px;
        padding: 20px;
        background: white;
        border: 1px solid #dfe3e8;
    }
    .user-profile__admin-badge{
        background: #760eff;
        color: #fff;
        border-radius: 5px;
        margin-right: auto;
        padding: 0 10px;
        font-weight: bold;
    }
    h1{
        margin: 0;
    }
</style>
