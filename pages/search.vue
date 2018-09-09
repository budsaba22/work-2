<template>
  <v-form v-model="valid">
    <v-text-field
      v-model="member"
      :rules="memberRules"
      label="กรอกรหัสนักศึกษาที่ต้องการค้นหา"
      requiredr
    ></v-text-field>
    <center>
     <v-btn color="primary" dark @click="Dosearch">ค้นหา
        <v-icon dark right>label</v-icon>
      </v-btn>
      </center>
      <div>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.s_id }}</td>
      <td class="text-xs-lelt">{{ props.item.s_code }}</td>
      <td class="text-xs-lelt">{{ props.item.s_name }}</td>
      <td class="text-xs-lelt">{{ props.item.s_class }}</td>
      <td class="text-xs-lelt">{{ props.item.s_group }}</td>
      
    </template>
    
    <template slot="pageText" slot-scope="props">
      Lignes {{ props.pageStart }} - {{ props.pageStop }} de {{ props.itemsLength }}
    
    </template>
  </v-data-table>
   <div>
    </div>
  </div>
  </v-form>
</template>

<script>
export default {
  data () {
  return {
      headers: [
        {
          text: "ID",
          align: "left",
          sortable: false,
          value: "name"
        },
        { text: "รหัสอาหาร ", value: "Code" },
        { text: "ชื่ออาหาร ", value: "Name" },
        { text: "ประเภท ", value: "Class" },
        { text: "ราคา ", value: "protein" }
      ],
      desserts: []
    };
  },
  async created() {
   
   this.getstudent()
  
      
  },
  methods: {
    async Dosearch() {
      console.log(this.member);
      let res = await this.$http.post("http://127.0.0.1/php-api/seaech.php", {
        member: this.member
      })
      if (res.data.ok) {
        this.desserts = res.data.admin
      }
    },
    Dosave() {
      this.member = "";
    }
  }
  
}
</script>