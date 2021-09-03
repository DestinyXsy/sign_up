<template>
  <div id="signUp">
    <h1>报名表单</h1>
    <form name="input" method="post">
      <div class="box">
        <div class="items">
          <span>姓名：</span>
          <input v-model="datas.name" type="text" />
        </div>
        <div class="items">
          <span>学院：</span>
          <select
            v-model="datas.faculty"
            name="faculties"
            @change="showFaculty"
          >
            <option v-for="option in options" :key="option" :value="option">
              {{ option }}<span v-if="option != '体育'">学院</span
              ><span v-else>系</span>
            </option>
          </select>
          <br />
        </div>
        <div class="items">
          <span>球衣号码：</span>
          <input v-model="datas.number" type="nubmer" />
        </div>
        <div class="items">
          <span>场上位置：</span>
          <select v-model="datas.work" name="works">
            <option v-for="work in works" :key="work" :value="work">
              {{ work }}
            </option>
          </select>
        </div>
        <input type="submit" id="submit" value="提交" @click="submit" />
      </div>
    </form>
  </div>
</template>

<script>
import md5 from 'js-md5'
export default {
  name: "HelloWorld",
  data() {
    return {
      options: [
        "公路",
        "汽车",
        "工程机械",
        "经济与管理",
        "电子与控制工程",
        "信息工程",
        "地质工程与测绘",
        "地球科学与资源",
        "建筑工程",
        "水利与环境",
        "建筑",
        "材料科学与工程",
        "马克思主义",
        "人文",
        "运输工程",
        "土地工程",
        "理",
        "外国语",
        "体育",
        "未来交通",
        "长安都柏林国际交通",
      ],
      works: ["大前锋", "小前锋", "中锋", "得分后卫", "控球后卫"],
      datas: {
        name: "",
        faculty: "",
        number: "",
        work: "",
        verify: "",
      },
    };
  },
  methods: {
    submit: function () {
      this.datas.verify=md5(this.datas.name+" "+this.datas.faculty+" "+this.datas.number+" "+this.datas.work+" ").slice(7,20);
      alert("您的身份码为"+this.datas.verify+",这个身份码将用于长大篮协微信小程序球员身份认证,请务必妥善保存。")
    },
  },
};
</script>

<style scoped>
#signUp {
  background: #d9e7f6;
  width: 500px;
  height: 500px;
  padding: 20px 0;
  border: 3px solid white;
  outline: 5px solid #d9e7f6;
  margin: auto;
}
h1 {
  margin-bottom: 60px;
}
a {
  color: #42b983;
}
select {
  width: 180px;
  height: 30px;
  float: right;
}
span {
  float: left;
}
input {
  float: right;
  width: 172px;
  height: 24px;
}
.items {
  margin: 40px auto;
  width: 300px;
  height: 30px;
  font-size: 22px;
}
#submit {
  width: 194px;
  height: 50px;
  margin: 30px auto;
  float: none;
  background: #f9e29f;
  border: none;
  font-size: 22px;
}
</style>
