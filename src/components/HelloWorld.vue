<template>
  <div class="hello">
    <div id="copy-txt">
      <div>
        近日，福建省政府正式批复省水投集团整合重组方案，标志着福建省水投集团步入新的发展阶段。
      </div>
      <p>
        根据批复精神，福建省水投集团升格为省管企业，并同步开展水务板块整合重组。整合重组后，由省国资委履行出资人职责实施全面监管。
      </p>
      <div>
        福建省水利投资开发集团有限公司成立于2011年12月，注册资本46亿元，主要负责引领拉动全省重大水利项目建设，主导推进全省城乡供水一体化。
        成立以来，公司坚持以项目建设带动产业发展，以产业发展促进项目建设，加快全省水资源市场的战略布局，涉水项目实现全省全覆盖，逐步形成以水资源开发、水工程建筑、水生态投资等三大板块，已经发展成为贯彻省委省政府决策部署、拉动重大水利项目投资和服务社会民生的重要力量。
      </div>
      <div>
        <img src="../assets/demo.png" alt="">
      </div>
    </div>
    <el-button type="primary" @click="copyTXT">复制</el-button>

    <div class="quill-box">
      <template>
        <quill-editor v-model="content" ref="content"> </quill-editor>
      </template>
    </div>
    <div>
      <el-button type="primary" @click="fwb">富文本</el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      content: "",
    };
  },
  methods: {
    copyTXT() {
      var copyDOM = document.querySelector("#copy-txt"); //指定的DOM元素
      var range = document.createRange(); // 创建容器
      range.selectNode(copyDOM); // 选中需要复制的节点
      window.getSelection().addRange(range); // 执行选中元素
      var successful = document.execCommand("copy"); // 执行 copy 操作
      try {
        var msg = successful ? "successful" : "unsuccessful";
        console.log("Copy was " + msg);
      } catch (err) {
        console.log("unable to copy");
      }
      window.getSelection().removeAllRanges(); // 移除选中的元素
    },
    fwb() {
      console.log("content", this.content);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
