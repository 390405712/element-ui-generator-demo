<template>
  <FormGenerator ref="FormGenerator" :model="form" :formOption="formOption" @submit="submit" />
</template>

<script>
import { FormGenerator, GeneratorUtils } from 'element-ui-generator'

export default {
  components: {
    FormGenerator
  },
  data: (vm) => ({
    form: {},
    formOption: [
      {
        type: 'input',
        formItem: {
          prop: 'key1',
          label: '输入框',
        },
      },
      {
        type: 'select',
        formItem: {
          prop: 'key2',
          label: '选择器',
        },
        control: {
          option: [
            {
              value: 'Option1',
              label: 'Option1',
            },
            {
              value: 'Option2',
              label: 'Option2',
            },
          ]
        },
      },
    ],
  }),
  methods: {
    submit() {
      console.log(this.$refs.FormGenerator);
    }
  },
  created() {
    GeneratorUtils.setRequired(this.formOption)
  },
}
</script>