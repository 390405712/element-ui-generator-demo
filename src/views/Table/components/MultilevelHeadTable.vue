<template>
  <TableGenerator :data="tableData" :tableOption="tableOption" />
</template>

<script>
import { TableGenerator } from 'element-ui-generator'


export default {
  components: {
    TableGenerator
  },
  data: () => ({
    tableOption: [
      {
        prop: 'date',
        label: 'Date',
      },
      {
        label: 'Delivery Info',
        children: [
          {
            prop: 'name',
            label: 'Name',
          },
          {
            label: 'Address Info',
            children: [
              {
                prop: 'address',
                label: 'Address',
              }, {
                prop: 'city',
                label: 'City',
              },
            ]
          },
        ]
      },
    ],
    tableData: [
      {
        date: '2016-05-03',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles',
        city: 'Los Angeles',
      },
      {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles',
        city: 'Los Angeles',
      },
      {
        date: '2016-05-04',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles',
        city: 'Los Angeles',
      },
      {
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles',
        city: 'Los Angeles',
      },
    ],
  }),
}
</script>