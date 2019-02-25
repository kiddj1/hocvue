<template>
  <div>
    <div class="hello">
      <div>
        <div class="text-left">Thêm công việc vào danh sách</div>
        <b-row>
          <b-col cols="2" class="text-left mt-2">Tiêu đề</b-col>
          <b-col cols="9">
            <b-form-input v-model="text1" type="text" placeholder="Enter your name" />
          </b-col>
        </b-row>
          <b-row class="mt-2">
          <b-col cols="2" class="text-left mt-3">Chi tiết công việc</b-col>
          <b-col cols="9">
            <b-form-textarea
              id="textarea1"
              v-model="text"
              placeholder="Enter something"
              rows="4"
              max-rows="6"
            />
          </b-col>
        </b-row>
        <b-row class="mt-2">
          <b-col cols="2" class="text-left mt-2">Độ ưu tiên</b-col>
          <b-col cols="8" class="text-left">
            <b-dropdown id="ddown-dropright" dropright text="Drop-Right" variant="success" >
              <b-dropdown-item href="#">Action</b-dropdown-item>
              <b-dropdown-item href="#">Another action</b-dropdown-item>
              <b-dropdown-item href="#">Something else here</b-dropdown-item>
            </b-dropdown>
          </b-col>
        </b-row>
        <b-row class="mt-2" align-self="end">
          <b-col class="text-right" cols="11">
            <b-button variant="danger">+ Thêm</b-button>
            <b-button variant="success">x Xóa</b-button>
          </b-col>
        </b-row>

      </div>
    </div>
    <div class="hello mt-2">
      <div class="text-left">Danh sách công việc</div>
      <div class="text-left mt-2">2 công việc</div>
      <b-row align-self="end">
        <b-col class="text-right" cols="11">
          <b-dropdown class="mlr" id="ddown1" size="sm" split text="Tất Cả" variant="outline-primary">
            <b-dropdown-item href="#">Action</b-dropdown-item>
            <b-dropdown-item href="#">Another action</b-dropdown-item>
            <b-dropdown-item href="#">Something else here</b-dropdown-item>
          </b-dropdown>
           <b-dropdown id="ddown1" size="sm" split text="Tất Cả" variant="outline-primary">
            <b-dropdown-item href="#">Action</b-dropdown-item>
            <b-dropdown-item href="#">Another action</b-dropdown-item>
            <b-dropdown-item href="#">Something else here</b-dropdown-item>
          </b-dropdown>
        </b-col>
      </b-row>
      <b-table striped hover :items="items" class="mt-2">
        <template slot="#" slot-scope="data">
          {{ data.value[0] }}
        </template>
        <template slot="Action" slot-scope="data">
          <b-button variant="outline-secondary" size="sm">Hoàn thành</b-button>
          <b-button variant="outline-secondary" size="sm">Chỉnh sửa</b-button>
          <b-button variant="outline-secondary" size="sm">Xóa</b-button>
        </template>
      </b-table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      items: [
        {"#": '1', 'Tiêu đề': 'Hoàn thiện hành trình lên cao thủ', "Trạng Thái": 'Chưa hoàn thành', 'Độ ưu tiên': '0', 'Action': null }
      ]

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
.hello {
  border: 1px solid;
  margin-left: 5px;
  margin-right: 5px;
}
.mla {
  margin-left: 20px;
}
.mlr {
  margin-right: 60px;
}
.testbg {
  background-color: green;
}
</style>
