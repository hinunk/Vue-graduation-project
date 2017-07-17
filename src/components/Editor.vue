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
                <Personal v-bind:formLabelAlign="formLabelAlign" />
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <WorkExperience v-bind:workExperience="workExperience" />
            </li>
            <li v-bind:class="{active: currentTab === 2}">
                学校经历
                <el-form class="el-form el-form--label-top">
                    <div v-for="(i, index) in schoolExperience">
                        <i class="el-icon-circle-cross" @click="removeSchoolExperience(index)"></i>
                        <el-form-item label="学校">
                            <el-input v-model="i.school"></el-input>
                        </el-form-item>
                        <el-form-item label="学位">
                            <el-input v-model="i.degree"></el-input>
                        </el-form-item>
                        <el-form-item label="时间">
                            <el-input v-model="i.time"></el-input>
                        </el-form-item>
                    </div>
                </el-form>
                <el-button @click="addSchoolExperience()">添加</el-button>
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
import Personal from './Personal'
import WorkExperience from './WorkExperience'
export default {
    components: {
        Personal,
        WorkExperience
    },
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
            ],
            schoolExperience: [
                {
                    school: '',
                    degree: '',
                    time: ''
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
        addSchoolExperience() {
            this.schoolExperience.push({
                school: '',
                degree: '',
                time: ''
            })
        },
        removeWorkExperience(index) {
            this.workExperience.splice(index, 1)

        },
        removeSchoolExperience(index) {
            this.schoolExperience.splice(index, 1)
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
