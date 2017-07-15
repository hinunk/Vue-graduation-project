<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active: currentTab === i}" v-on:click="currentTab = i">
                    <svg class="icon" aria-hidden="true">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li v-bind:class="{active: currentTab === 0}">
                个人信息
                <div style="margin: 20px;"></div>
                <el-form class="el-form el-form--label-top" :label-position="labelPosition" :model="formLabelAlign">
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
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                工作经历
                <el-form class="el-form el-form--label-top" :label-position="labelPosition" :model="formLabelAlign">
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
            </li>
            <li v-bind:class="{active: currentTab === 2}">
    
            </li>
            <li v-bind:class="{active: currentTab === 3}">
    
            </li>
            <li v-bind:class="{active: currentTab === 4}">
    
            </li>
            <li v-bind:class="{active: currentTab === 5}">
    
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentTab: 0,
            icons: ['identity', 'work', 'book', 'project', 'trophy', '3-copy'],
            labelPosition: 'right',
            formLabelAlign: {
                name: '',
                location: '',
                birth: ''
            },
            workExperience: [
                {
                    company: '',
                    jobContent: ''
                }
            ]
        }
    },
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


<style lang="scss">
#editor {
    border: 1px solid black;
    min-height: 100px;
    display: flex;
    >nav {
        background: black;
        width: 5em;
        >ol>li {
            padding: 8px 0;
            text-align: center;
            >.icon {
                fill: white;
            }
            &.active {
                background: white;
                >.icon {
                    fill: black;
                }
            }
        }
    }
    .panes {
        overflow: auto;
        flex: 1;
        padding: 2em;
        >li {
            display: none;
            &.active {
                display: block;
            }
        }
    }
}
</style>
