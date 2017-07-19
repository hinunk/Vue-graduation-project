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
                <Personal v-bind:formLabelAlign="formLabelAlign" title="个人信息" />
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <ArrayEditor v-bind:items="workExperience" v-bind:labels="{company: '公司',jobContent: '工作内容'}" title="工作经历" />
            </li>
            <li v-bind:class="{active: currentTab === 2}">
                <ArrayEditor v-bind:items="schoolExperience" v-bind:labels="{school: '学校', time: '时间', degree: '学位'}" title="学习经历" />
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <ArrayEditor v-bind:items="projects" title="项目经历" v-bind:labels="{name:'项目名称', content:'工作内容'}" />
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <ArrayEditor v-bind:items="awards" title="获奖情况" v-bind:labels="{name:'奖励详情'}" />
            </li>
            <li v-bind:class="{active: currentTab === 5}">
                <h2>联系方式</h2>
                <el-form>
                    <el-form-item label="QQ">
                        <el-input v-model="contacts.qq"></el-input>
                    </el-form-item>
                    <el-form-item label="微信">
                        <el-input v-model="contacts.wechat"></el-input>
                    </el-form-item>
                    <el-form-item label="邮箱">
                        <el-input v-model="contacts.email"></el-input>
                    </el-form-item>
                    <el-form-item label="手机">
                        <el-input v-model="contacts.phone"></el-input>
                    </el-form-item>
                </el-form>
            </li>
        </ol>
    </div>
</template>

<script>
import Personal from './Personal'
import ArrayEditor from './ArrayEditor'
export default {
    components: {
        Personal,
        ArrayEditor
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
            schoolExperience: [{
                school: '', degree: '', time: ''
            }
            ],
            projects: [{ name: '', content: '' }],
            awards: [{ name: '' }],
            contacts: { qq: '', wechat: '', phone: '', email: '' }
        }
    },
    methods: {
        addSchoolExperience() {
            this.schoolExperience.push({
                school: '',
                degree: '',
                time: ''
            })
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
