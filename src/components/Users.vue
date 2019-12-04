<template>
    <div>
        <select @change="onChange($event.target.value)">
            <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
        </select>
    </div>
</template>

<script>
    export default {
        name: "Users",
        props: {
            users: Array,
            onChange: Function
        }
    }
</script>