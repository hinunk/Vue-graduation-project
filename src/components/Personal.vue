<template>
    <div>
        <h1>{{title}}</h1>
        <el-form class="el-form el-form--label-top">
            <el-form-item label="姓名">
                <el-input v-model="formLabelAlign.name"></el-input>
            </el-form-item>
            <el-form-item label="所在地">
                <el-input v-model="formLabelAlign.location"></el-input>
            </el-form-item>
            <el-form-item label="出生年月">
                <el-input v-model="formLabelAlign.birth"></el-input>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
    props: ['formLabelAlign','title']
}
</script>
