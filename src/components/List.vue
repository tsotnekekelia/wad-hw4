<template>
    <div class="container">
        <div v-if="sortedList.length">
            <div v-for="(item, index) in sortedList" :key="index" :class="{done: item.done}" class="list-item">
                <div class="title">{{item.title}}</div>
                <div>
                    <span @click="() => { toggle(item) }"></span>
                </div>
            </div>
        </div>
        <div v-else>
            <h3>Add your first Todo task</h3>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'List',
        methods: {
            toggle: item => {
                item.done = !item.done;
            }
        },
        computed: {
            sortedList: function () {
                let list = this.list;
                return list.sort(function (x, y) {
                    return (x.done === y.done) ? 0 : x.done ? 1 : -1;
                })
            }
        },
        props: {
            list: {
                type: Array,
                default : () => []
            }
        }
    }
</script>
<style scoped>
    .container {
      overflow-y: auto;
      width: 100%;
      height: calc(100% - 100px);
    }

    h3 {
        text-align: center;
    }

    .list-item {
        display: flex;
        justify-content: space-between;
        padding: 15px 0;
    }

    .list-item span {
        width: 20px;
        height: 20px;
        display: block;
        border-radius: 100%;
        border: 3px solid #e4e4e4;
        cursor: pointer;
    }

    .list-item span:hover {
        border: 3px solid #c2c2c2;
        cursor: pointer;
    }

    .list-item.done .title {
        color: #e4e4e4;
        text-decoration: line-through;
    }

    .list-item.done span {
        color: #ffffff;
        background-color: #42b983;
        border: 3px solid #42b983;
        text-align: center;
        line-height: 15px;
    }

    .list-item.done span:hover {
        opacity: 0.8;
    }

    .list-item.done span::after {
        content: '\2713';
    }

</style>
