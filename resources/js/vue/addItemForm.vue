<template>
    <div class="add-item">
        <input type="text" placeholder="type your todo" v-model="item.name">
            <button 
            type="submit" 
            :class="[ item.name ? 'active' : 'inactive', 'plus' ]"
            @click="addItem()"
            >
            Add
            </button>
    </div>
</template>

<script>
export default {
    data: function () { 
        return{
            item: {
                name: ""
            }
        }
    },
    methods: {
        addItem(){
            if (this.item.name == "") {
                return;
            }
            axios.post('/api/item/store', {
                item: this.item
            })
            .then( res => {
                if (res.status == "201") {
                    this.item.name == "";
                }
            })
            .catch(err => {
                alert(err);
            })
        }
    }
}
</script>

<style scoped>
.add-item {
    display: flex;
    align-items: center;
    justify-content: center;
}

input {
    background: #e7e7e7;
    border: 0px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
}

.plus {
    font-size: 20px;
}

.active {
    background: #00ce25;
    color: #fff;
}

.inactive {
    color: #999999;
}
</style>