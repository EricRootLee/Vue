<template>
  <section>
    <li>
      <h2>{{ name }} {{ fav === true ? 'Fav' : 'Not fav' }}</h2>
      <button @click="showdetails">Show Details</button> <button @click="toogleFav">Fav</button>
      <ul v-if="detailsAreAvailable">
        <li><strong>Phone</strong>{{ phone }}</li>
        <li><strong>Email</strong>{{ email }}</li>
      </ul>
    </li>
  </section>
</template>

<script>
export default {
  // props:[
  //     'email',
  //     'phone',
  //     'name',
  //     'isFav'
  // ],
  props: {
    ///adding
    name: {
      type: String,
      required: true
    },
    phone: String,
    email: String,
    isFav: {
      type: Boolean,
      required: false,
      default: false,

    }

  },
  data() {
    return {
      detailsAreAvailable: false,
   fav:this.isFav,
    };
  },
  methods: {
    showdetails() {
      this.detailsAreAvailable = !this.detailsAreAvailable;
    },
    toogleFav(){
      this.$emit('favorite',this.phone)
      console.log('Muli')
      //this.fav = !this.fav;
    }
  },
};
</script>
