<template>
    <div>
        <h1> {{ heading }}</h1>
        <p> No: {{countNo}}</p>
        <p>1 way binding: <input type="number" @input="onChangeinput($event)"></p>
        <p>1 way binding: <input type="number" v-bind:value="countNo" v-on:input="onChangeinput($event)"></p>
        <P>2-way binding: <input type="number" v-model="countNo"></P>
        <button type="Button" @click="minus()">-</button>
        <button type="Button" @click="plus()">+</button>
        <hr>
        <ul>
            <li v-for="(item , key) in listItems" :key="`ul_${key}`">{{item}}</li>
        </ul>
        <ol>
            <li v-for="(item , key) in listItems" :key="`ol_${key}`" class="item" :class="{
                strong:key==0,
                hello:key==1,
            }">{{item}}</li>
        </ol>
        {{listItems}}
        <p>Insert: <input type="text" v-model="itemValues"></p>
        <p><button type="button" @click="addItem(itemValues)">Add Item</button></p>
    </div>
</template>

<script>
    export default {
        name: 'my-form',
        data(){
            return {
                heading : 'Counter',
                countNo : 0,
                listItems: [],
                itemValues: '',
            }
        },
        components: {
            
        },
        methods: {
            
            appendSurname(){
                //this.myName = this.myName + ' ' + this.surname;    <- Old Style
                this.myName = `${this.myName} ${this.surname}`; // <- New Style
            },
            plus(){
                this.countNo += 1;
            },
            minus(){
                this.countNo -= 1;
            },
            onChangeinput(event){
                const value = event.target.value;
                console.log(value);
                this.countNo = value;
            },
            addItem(item){
                if (item){
                    this.listItems.push(item);
                }
                else{
                    console.log("error");
                }
                this.itemValues = '';
                
            }
        },
    }
</script>

<style lang="less" scoped>
.strong{
    color: green;
}
.hello{
    color: yellow;
}
ul{
    border-bottom: 3px dashed red;
    li{
        border-bottom: 1px dashed blue;
    }
}
</style>
