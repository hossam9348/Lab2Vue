<template>
   <div>
        <!-- <ul>
            <li v-for="book in books" :title="book.author">{{book.Name}}</li>
        </ul> -->
        <div v-if="isVisible==false" class="text-center">
        <div class="row justify-content-center my-1 text-center">
        <div class="card m-1" style="width: 28rem;" v-for="book in books" :key="book.iSBN">
            <img :src="book.imgUrl" style="height: 20rem;" class="card-img-top">
            <div :class="[book.PageNumbers>50?'more':'', book.PageNumbers<=50?'less':'',]">
            <div class="card-body row">
                <div class="row" style="width: 14rem;">
                    <div class="card-item bg-light" style="width: 10rem;">Category: {{book.Category}}</div>
                    <div class="card-item bg-light" style="width: 10rem;">PageNumbers: {{book.PageNumbers}}</div>
                    <div class="card-item bg-light" style="width: 10rem;">ISBN: {{book.iSBN}}</div>
                </div>
                <div class="row" style="width: 14rem;">
                    <div class="card-item bg-light" style="width: 10rem;">Author: {{book.author}}</div>
                    <div class="card-item bg-light" style="width: 10rem;">Price: {{currencyFormatter(book.price)}}</div>
                    <button class="btn btn-primary" style="width: 10rem;" :disabled:="flag"  @click="addToList(book)">Add to List</button>
                </div>
            </div>
            </div>
          </div>
        </div>
        <button class="btn btn-primary" style="width: 20rem;" @click="isVisible=true">Display Wish List</button>
    </div>
    <div class="text-center" v-else>
    <table class="table text-center">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Category</th>
            <th scope="col">PageNumbers</th>
            <th scope="col">ISBN</th>
            <th scope="col">Author</th>
            <th scope="col">Price</th>
            <th scope="col">Remove</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="wishList in wishList.items" :key="wishList.iSBN">
            <td>{{wishList.Name}}</td>
            <td>{{wishList.Category}}</td>
            <td>{{wishList.PageNumbers}}</td>
            <td>{{wishList.iSBN}}</td>
            <td>{{wishList.author}}</td>
            <td>{{wishList.price}}</td>
            <td>
                <button class="btn btn-primary" style="width: 5rem;" @click="removeFromList(wishList)">Remove</button>
            </td>
          </tr>
        </tbody>
      </table>
      <button class="btn btn-primary" style="width: 5rem;" @click="isVisible=false">Back to books</button>
    </div>
    </div>
</template>

<script>
import books from '../books'
export default {
            data:()=>({
            books:books,
            flag: false,
            wishList:{
                items:[]
            },
            isVisible:false
        }),
        methods:{
            currencyFormatter(value){
                return Intl.NumberFormat('ar-SA', {
                    style: 'currency',
                    currency: 'SAR',
                    minimumFractionDigits:0
                }).format(value)
            },
            addToList(book){
                this.wishList.items.push(book)
                if (this.wishList.items.filter((wish_) =>  wish_.iSBN == book.iSBN).length !=0){this.flag = true;} 
                 else {
                  this.flag = false;
                 } 
            },
            removeFromList(wish){
                this.wishList.items = this.wishList.items.filter((wish_)=>  wish_.iSBN != wish.iSBN )
            },
        }
}

</script>

<style>
    .less{
        background: orange;  
    }
    .more{
        background: green;  
    }
</style>