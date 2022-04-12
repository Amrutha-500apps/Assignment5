<template>
<div>
<b-form-input v-model="value" placeholder="enter your country" required></b-form-input><br>
<b-button variant="primary" @click="getData">Get Data</b-button>
<table border="1px">
<tr>
<td>country</td>
<td>name</td>
<td>domains</td>
<td>website</td>
</tr>
<tr v-for="item in list" v-bind:key="item.id">
<td>{{ item.country }}</td>
<td>{{ item.name }}</td>
<td>{{ item.domains}}</td>
<td>{{ item.web_pages}}</td>
</tr>
</table>
<button @click="redirect()">click</button>
</div>
</template>
<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
name: "HompDG",
data() {
return { list: undefined };
},
mounted() {
Vue.axios
.get("http://universities.hipolabs.com/search?")
//.get("http://dummy.restapiexample.com/api/v1/employees")
.then((resp) => {
this.list = resp.data;
console.log(resp.data);
});
},
methods:{
redirect()
{
Vue.axios

.get("http://localhost:8080/#/call")

.then((resp) => {

this.list = resp.data;

document.write(resp.data);

});

}

}

};


</script>




