<template>
  <div>
    <div class="hello">
      <div>
        <div class="text-left">Thêm công việc vào danh sách</div>
        <b-row>
          <b-col cols="2" class="text-left mt-2">Tiêu đề</b-col>
          <b-col cols="9">
            <b-form-input v-model="txt_title" type="text" placeholder="Enter your title you want" />
          </b-col>
        </b-row>
          <b-row class="mt-2">
          <b-col cols="2" class="text-left mt-3">Chi tiết công việc</b-col>
          <b-col cols="9">
            <b-form-textarea
              id="textarea1"
              v-model="txt_description"
              placeholder="Enter something"
              rows="4"
              max-rows="6"
            />
          </b-col>
        </b-row>
        <b-row class="mt-2">
          <b-col cols="2" class="text-left mt-2">Độ ưu tiên</b-col>
          <b-col cols="8" class="text-left">
            <b-dropdown id="ddown-dropright" dropright v-bind:text="dropDownPicked" variant="success" >
              <div v-for="(lvl, index) in levels" v-bind:key="index">
                <b-dropdown-item href="#" @click="dropDownPickedFunc(index)" >{{lvl.nameLvl}}</b-dropdown-item>
              </div>
              <!-- <b-dropdown-item href="#">2 - Trung Binh</b-dropdown-item>
              <b-dropdown-item href="#">3- Thap</b-dropdown-item> -->
            </b-dropdown>
          </b-col>
        </b-row>
        <b-row class="mt-2" align-self="end">
          <b-col class="text-right" cols="11">
            <b-button variant="danger" @click="addWork">+ Thêm</b-button>
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
          {{ data.index }}
        </template>
        <template slot="Action" slot-scope="data">
          <b-button variant="outline-secondary" size="sm" @click="changeStatus(data.index, 'Hoàn Thành')">Hoàn thành</b-button>
          <b-button variant="outline-secondary" size="sm">Chỉnh sửa</b-button>
          <b-button variant="outline-secondary" size="sm" @click="removeItem(data.index)">Xóa</b-button>
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
        {"#": '1', 'Tiêu đề': 'Hoàn thiện hành trình lên cao thủ', "Trạng Thái": 'Chưa hoàn thành', 'Độ ưu tiên': '1', 'Action': null }
      ],
      txt_title: '',
      txt_description: '',
      levels: [
        {index: 1, nameLvl: '1 - Cao'},
        {index: 2, nameLvl: '2 - Trung Bình'},
        {index: 3, nameLvl: '3 - Thấp'},
      ],
      dropDownPicked: '1 - Cao',
      dropDownPicked_data: 1,


    }
  },
  methods : {
    addWork: function() {
      let instance = this;
      let items = {
        "#": `${this.items.length + 1}`, 'Tiêu đề': this.txt_title, "Trạng Thái": 'Chưa hoàn thành', 'Độ ưu tiên': this.dropDownPicked_data , 'Action': null ,
      };
      this.items.push(items);
      // console.log(this.items[0]['Trạng Thái'] = 'AAA')
    },
    dropDownPickedFunc: function(a) {
      this.dropDownPicked = `${this.levels[a].nameLvl}`;
      this.dropDownPicked_data = a > 0 ? ++a : a;
    },
    removeItem: function(a){
      this.items.splice(a, 1);
    },
    changeStatus: function(a, stt){
      this.items[a]['Trạng Thái'] = stt;
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
