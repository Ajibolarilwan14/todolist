<template>
    <div class="item">
        <input type="checkbox" 
            @change="updateCheck()"
            v-model="items.completed"
        />
        <span :class="[items.completed ? 'completed' : '', 'inputText']">{{ items.name }}</span>
        <button 
        type="submit"
        @click="deleteItem()"
        class="trashcan"
        >
        Delete
        </button>
    </div>
</template>

<script>
export default {
    props: ['items']
}
</script>

<style scoped>
.completed {
    text-decoration: line-through;
    color: #999999;
}

.inputText {
    width: 100%;
    margin-left: 20px;
}

.item {
    display: flex;
    justify-content: center;
    align-items: center;
}

.trashcan {
    color: #fff;
    background: crimson;
    padding: 5px;
    outline: none;
    border: none;
}
</style>
