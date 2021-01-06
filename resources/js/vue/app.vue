<template>
    <div class="todolistContainer">
        <div class="heading">
            <h2 class="title">Todo List</h2>
            <add-item-form />
        </div>
        <list-item :items="items" />
    </div>
</template>

<script>
import addItemForm from './addItemForm';
import AddItemForm from './addItemForm.vue';
import ListItem from './listItem.vue';
import listView from './listView';


export default {
    components: {
        addItemForm,
        AddItemForm,
        ListItem,
        listView
    },
    data: function () { 
        return {
            items: []
        }
    },
    methods: {
        getList() {
            axios.get('/api/items')
            .then( res => {
                this.items = res.data
            })
            .catch(err => {
                alert(err);
            })
        }
    },
    created() {
        this.getList();
    }
}
</script>

<style scoped>
    .todolistContainer {
        width: 350px;
        margin: auto;
    }

    .heading {
        background: #e6e6e6;
        padding: 10px;
    }

    .title {
        text-align: center;
    }
</style>