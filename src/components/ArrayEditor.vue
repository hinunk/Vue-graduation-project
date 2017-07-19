<template>
    <div>
        <h1>{{title}}</h1>
        <el-form class="el-form el-form--label-top">
            <div v-for="(i, index) in items">
                <i class="el-icon-circle-cross" @click="removeitems(index)"></i>
                <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" v-bind:key="key">
                    <el-input v-model="i[key]"></el-input>
                </el-form-item>
            </div>
            <el-button @click="additems()">添加</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['items', 'labels','title'],
    computed: {
        keys() {
            return Object.keys(this.items[0])
        }
    },
    methods: {
        additems() {
            const empty = {}
            this.keys.map((key) => {
                empty[key] = ''
            })
            this.items.push(empty)
        },
        removeitems(index) {
            this.items.splice(index, 1)

        }
    }
}
</script>

