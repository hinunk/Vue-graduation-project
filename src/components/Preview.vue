<template>
  <div id="preview">
    <h1>{{resume.formLabelAlign.name || '请填写姓名'}}</h1>
    <p>出生: {{resume.formLabelAlign.location}}</p>
    <p>所在地: {{resume.formLabelAlign.birth}}</p>
    <section v-if="filter(resume.workExperience).length > 0">
      <h2>工作经历</h2>
      <ul>
        <li v-for="workExperience in filter(resume.workExperience)">
          公司 :{{workExperience.company}} 工作内容: {{workExperience.jobContent}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.workExperience).length > 0">
      <h2>学习经历</h2>
      <ul>
        <li v-for="schoolExperience in filter(resume.schoolExperience)">
          学校: {{schoolExperience.school}} 学位: {{schoolExperience.degree}} 时间: {{schoolExperience.time}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.projects).length > 0">
      <h2>项目</h2>
      <ul>
        <li v-for="project in filter(resume.projects)">
          项目名称: {{project.name}} 工作内容: {{project.content}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.awards).length > 0">
      <h2>获奖情况</h2>
      <ul>
        <li v-for="awards in filter(resume.awards)">
          我的奖项: {{awards.name}}
        </li>
      </ul>
    </section>
    <section>
      <h2>联系方式</h2>
      <p>QQ: {{resume.contacts.qq}}</p>
      <p>微信: {{resume.contacts.wechat}}</p>
      <p>邮箱: {{resume.contacts.phone}}</p>
      <p>手机: {{resume.contacts.email}}</p>
    </section>
  </div>
</template>

<script>
export default {
  props: ['resume'],
  name: 'preview',
  methods: {
    filter(array) { // 找出非空对象
      return array.filter(item => !this.isEmpty(item))
    },
    isEmpty(object) { // 只要有一个 value 不是 falsy，就返回 flase
      let empty = true
      for (let key in object) {
        if (object[key]) {
          empty = false
          break
        }
      }
      return empty
    }
  }
}
</script>


<style lang="scss">
#preview {
  border: 1px solid black;
  min-height: 100px;
  font-size: 24px;
  overflow: auto;
  width: 829px;
  white-space: normal;
  div,
  h1,
  p,
  section {
    white-space: normal;
    text-align: center;
    border-bottom: none;
    padding-top: 16px;
  }
}
</style>
