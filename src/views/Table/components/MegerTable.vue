<template>
  <div>
    <TableGenerator :data="tableData" :tableOption="tableOption" :span-method="arraySpanMethod" />
    <TableGenerator :data="tableData" :tableOption="tableOption" :span-method="objectSpanMethod" />
  </div>
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
        prop: 'id',
        label: 'Id',
      }, {
        prop: 'name',
        label: 'Name',
      }, {
        prop: 'amount1',
        label: 'amount1',
      }, {
        prop: 'amount2',
        label: 'amount2',
      }, {
        prop: 'amount3',
        label: 'amount3',
      },
    ],
    tableData: [
      {
        id: '12987122',
        name: 'Tom',
        amount1: '234',
        amount2: '3.2',
        amount3: 10,
      },
      {
        id: '12987123',
        name: 'Tom',
        amount1: '165',
        amount2: '4.43',
        amount3: 12,
      },
      {
        id: '12987124',
        name: 'Tom',
        amount1: '324',
        amount2: '1.9',
        amount3: 9,
      },
      {
        id: '12987125',
        name: 'Tom',
        amount1: '621',
        amount2: '2.2',
        amount3: 17,
      },
      {
        id: '12987126',
        name: 'Tom',
        amount1: '539',
        amount2: '4.1',
        amount3: 15,
      },
    ],
  }),
  methods: {
    arraySpanMethod({ row, column, rowIndex, columnIndex }) {
      if (rowIndex % 2 === 0) {
        if (columnIndex === 0) {
          return [1, 2]
        } else if (columnIndex === 1) {
          return [0, 0]
        }
      }
    },
    objectSpanMethod({ row, column, rowIndex, columnIndex }) {
      if (columnIndex === 0) {
        if (rowIndex % 2 === 0) {
          return {
            rowspan: 2,
            colspan: 1,
          }
        } else {
          return {
            rowspan: 0,
            colspan: 0,
          }
        }
      }
    }
  },
}
</script>