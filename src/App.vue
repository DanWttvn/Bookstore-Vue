<template>
  <div id="app">

    <Header></Header>

    <form class="input-group" id="searchBox">
      <div class="gg-search"></div>
      <input v-on:keyup="searchBook" class="form-control" id="searchInput" type="text" placeholder="Search book...">
    </form>


    <div class="galleryBox">
      <div class="bookCard" v-for="book in booksToDisplay" v-bind:key="book.id">
        <EachBook v-bind:bookChild = "book"></EachBook> 
      </div>
    </div>



  </div>
</template>



<script>

import Header from "./components/Header.vue"
import EachBook from "./components/EachBook.vue"

export default {
  name: 'app',
  components: {
    Header,
    EachBook
  },
  data() {
		return {
			url: "https://api.myjson.com/bins/zyv02", 
			data: [],
			booksData: [],
			booksToDisplay: [],
		
			searchInput: "",
			searchTerm: "",
			titleDisplayed : ""
		}
	},
	methods: {
		loadData() {
			fetch(this.url , {
				method: "GET"
			}).then(function(response) {
				if (response.ok) {
					return response.json();
				}
			}).then((json) => {
				this.data = json;
				this.booksData = this.data.books;
				this.booksToDisplay = this.booksData.slice();
				console.log(this.booksToDisplay);
        
			});
		},
			
		searchBook: function(e) {
			this.booksToDisplay = [];
			
			this.searchTerm = e.target.value.toLowerCase();
			
			for (let i = 0; i < this.booksData.length; i++) {
				if (this.booksData[i].title.toLowerCase().indexOf(this.searchTerm) != -1) {
					this.booksToDisplay.push(this.booksData[i]);
				} 
			}
		}
	},
	created: function(){
		this.loadData()
	}
}
</script>



<style>
  @import "./assets/styles.css";
</style>
