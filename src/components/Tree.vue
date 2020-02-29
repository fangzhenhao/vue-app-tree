<template>
  <div>
    <div v-for="item1 in dataList">
      <input type="checkbox"><span>{{item1.name}}</span>
      <input v-show="item1.children" @click="subordinate(item1)" type="button" value="下级">
      <!--<div v-for="item2 in item1.children">
        <input type="checkbox"><span>{{item2.name}}</span>
        <div v-for="item3 in item2.children">
          <input type="checkbox"><span>{{item3.name}}</span>
        </div>
      </div>-->
    </div>
  </div>
</template>

<script>
  export default {
    name: "Tree",
    data() {
      return {
        dataList: [
          {
            "children": [
              {
                "children": [
                  {
                    "children": [],
                    "name": "教师1",
                    "pid": "1133184954990067712",
                    "id": "1133186086739116032"
                  },
                  {
                    "children": [],
                    "name": "教师2",
                    "pid": "1133184954990067712",
                    "id": "1133186086739116032"
                  }
                ],
                "name": "在编教师",
                "pid": "1133184954990067712",
                "id": "1133186086739116032"
              },
              {
                "children": [],
                "name": "部门自聘人员",
                "pid": "1133184954990067712",
                "id": "1133187313757585408"
              }
            ],
            "name": "教师",
            "pid": "-1",
            "id": "1133184954990067712"
          },
          {
            "children": [
              {
                "children": [
                  {
                    "children": [],
                    "name": "本科生1",
                    "pid": "1133184954990067712",
                    "id": "1133186086739116032"
                  },
                  {
                    "children": [],
                    "name": "本科生2",
                    "pid": "1133184954990067712",
                    "id": "1133186086739116032"
                  }
                ],
                "name": "本科生",
                "pid": "1133185731036971008",
                "id": "1133187654939049984"
              },
              {
                "children": [],
                "name": "研究生",
                "pid": "1133185731036971008",
                "id": "1133189438256447488"
              }
            ],
            "name": "学生",
            "pid": "-1",
            "id": "1133185731036971008"
          }
        ],
      }
    },
    methods:{
      subordinate(data){
        this.dataList = data.children;
      },
      exportAll(){
        this.changeSekectListToFinal();
        this.customerBillService.exportExcel(this.selectedListFinam).then(res =>{
          console.info(res)
        },
        error => {
          console.info(error)
        })
      }
    }
  }
</script>

<style scoped>

</style>
