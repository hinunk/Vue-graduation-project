<template>
    <div>
        工作经历
        <el-form class="el-form el-form--label-top">
            <div v-for="(i, index) in workExperience">
                <i class="el-icon-circle-cross" @click="removeWorkExperience(index)"></i>
                <el-form-item label="公司名称">
                    <el-input v-model="i.company"></el-input>
                </el-form-item>
                <el-form-item label="工作内容">
                    <el-input v-model="i.jobContent"></el-input>
                </el-form-item>
            </div>
            <el-button @click="addWorkExperience()">添加</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['workExperience'],
    methods: {
        addWorkExperience() {
            this.workExperience.push({
                company: '',
                jobContent: ''
            })
        },
        removeWorkExperience(index) {
            this.workExperience.splice(index, 1)

        }
    }
}
</script>

