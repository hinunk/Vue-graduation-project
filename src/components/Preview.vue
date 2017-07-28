<template>
    <div id="preview">
        <h1>{{resume.formLabelAlign.name || '请填写姓名'}}</h1>
        <p>{{resume.formLabelAlign.location}}</p>
        <p>{{resume.formLabelAlign.birth}}</p>
    <section v-if="filter(resume.projects).length > 0">
      <h2>项目</h2>
      <ul>
        <li v-for="project in filter(resume.projects)">
          {{project.name}}
          {{project.content}}
        </li>
      </ul>
    </section>
    </div>

</template>

<script>
export default {
    props: ['resume'],
      methods:{
      filter(array){ // 找出非空对象
        return array.filter(item=> !this.isEmpty(item))
      },
      isEmpty(object){ // 只要有一个 value 不是 falsy，就返回 flase
        let empty = true
        for(let key in object){
          if(object[key]){
            empty = false
            break
          }
        }
        return empty
      }
    }
}
</script>


<style>
#preview {
    border: 1px solid black;
    min-height: 100px;
}
</style>
