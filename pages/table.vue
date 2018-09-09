<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template slot="headerCell" slot-scope="props">
        <v-tooltip bottom>
          <span slot="activator">
            {{ props.header.text }}
          </span>
          <span>
            {{ props.header.text }}
          </span>
        </v-tooltip>
      </template>
      <template slot="items" slot-scope="props">
        <td>{{ props.item.s_code }}</td>
        <td class="text-xs-lelt">{{ props.item.s_cord }}</td>
        <td class="text-xs-lelt">{{ props.item.s_name }}</td>
        <td class="text-xs-lelt">{{ props.item.s_class }}</td>
        <td class="text-xs-lelt">{{ props.item.s_goup }}</td>
        <td class="text-xs-lelt">{{ props.item.s_iron }}</td>
      </template>
    </v-data-table>
    <div>
      <v-btn color="success">เพิ่มข้อมูล</v-btn>
      <v-btn color="error">ลบข้อมูล</v-btn>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'รหัสอาหาร',
          align: 'left',
          sortable: false,
          value: 'name',
        },
        { text: '', value: '' },
        { text: 'ชื่ออาหาร', value: 'fat' },
        { text: 'ประเภท', value: 'carbs' },
        { text: 'ราคา', value: 'protein' },
        { text: '', value: 'iron' },
      ],
      desserts: [],
    }
  },
async created() {
    this.getstudent()
  }, 
methods: {
    async getstudent() {
      let res = await this.$http.get('http://127.0.0.1/php-api/list-student.php')
      this.desserts = res.data.student
    },
}
}
</script>