<template>
  <FormGenerator ref="FormGenerator" :model="form" :formOption="formOption" />
</template>

<script>
import { FormGenerator,GeneratorUtils } from 'element-ui-generator'

export default {
  components: {
    FormGenerator
  },
  data: () => {
    const staticOptions = [
      {
        value: 'Option1',
        label: 'Option1',
      },
      {
        value: 'Option2',
        label: 'Option2',
      },
      {
        value: 'Option3',
        label: 'Option3',
      },
      {
        value: 'Option4',
        label: 'Option4',
      },
      {
        value: 'Option5',
        label: 'Option5',
      },
    ]
    return {
      form: {},
      formOption: [
        {
          type: 'select',
          formItem: {
            prop: 'key1',
            label: '基础用法',
          },
          control: {
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key2',
            label: '禁用选项',
          },
          control: {
            option: [
              {
                value: 'Option1',
                label: 'Option1',
                disabled: true,
              },
              {
                value: 'Option2',
                label: 'Option2',
              },
            ]
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key3',
            label: '禁用状态',
          },
          control: {
            disabled: true,
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key4',
            label: '清空单选',
          },
          control: {
            clearable: true,
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key5',
            label: '基础多选',
          },
          control: {
            multiple: true,
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key6',
            label: '自定义',
          },
          control: {
            option: [
              {
                value: 'Option1',
                slot: {
                  default: () => (<span><i class="el-input__icon el-icon-date"></i> Option1</span>),
                }
              },
              {
                value: 'Option2',
                slot: {
                  default: () => (<span><i class="el-input__icon el-icon-search"></i> Option2</span>),
                }
              },
            ]
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key7',
            label: '筛选选项',
          },
          control: {
            filterable: true,
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key8',
            label: '新建选项',
          },
          control: {
            multiple: true,
            filterable: true,
            allowCreate: true,
            defaultFirstOption: true,
            reserveKeyword: "false",
            option: staticOptions
          },
        },
        {
          type: 'select',
          formItem: {
            prop: 'key9',
            label: '异步加载',
          },
          control: {
            option: []
          },
        },
      ],
    }
  },
  mounted() {
    const data = [
      {
        id: '1',
        name: 'Option1'
      }
    ]
    GeneratorUtils.getLabel(this.formOption, 'key9').control.option = GeneratorUtils.getOption(data, 'name', 'id') // [{label:'Option1',value:'1'}]
  },
}

</script>