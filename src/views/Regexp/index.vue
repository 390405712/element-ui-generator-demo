<template>
  <div class="container">
    <FormGenerator label-position="top" ref="formRef" :model="form" :formOption="formOption" >
      <template v-for="(item, index) in formOption" #[item.formItem.prop]="scope">
        <el-input v-model="scope.form[item.formItem.prop]" :key="item.formItem.prop"></el-input>
        <div class="examples">
          <div v-if="item.control?.key" class="tag-container no-wrap">
            <div>key</div>
            <el-tag @click="copy(item.control.key)">{{ item.control.key }}</el-tag>
          </div>
          <div v-if="item.control?.rule" class="tag-container no-wrap">
            <div>正则</div>
            <el-tag @click="copy(item.control.rule)">{{ item.control.rule }}</el-tag>
          </div>
          <div v-if="item.control?.examples" class="tag-container">
            <div>例子</div>
            <el-tag type="success" @click="copy(i, item.formItem.prop)" v-for="(i, itemIndex) in item.control.examples"
              :key="itemIndex">{{ i }}</el-tag>
          </div>
          <div v-if="item.control?.counterExamples" class="tag-container">
            <div>反例</div>
            <el-tag type="danger" @click="copy(i, item.formItem.prop)"
              v-for="(i, itemIndex) in item.control.counterExamples" :key="itemIndex">{{ i }}</el-tag>
          </div>
        </div>
      </template>
    </FormGenerator>
  </div>
</template>

<script>

import { FormGenerator, GeneratorUtils } from 'element-ui-generator'
import Regexps from 'element-ui-generator/dist/regexpToArr'
import { Message as ElMessage } from 'element-ui'

export default {
  name: 'regexp',
  components: { FormGenerator },
  data: () => ({
    form: {},
    formOption: [],
  }),
  created() {
    Regexps.forEach((item, index) => {
      this.formOption.push({
        type: 'slot',
        formItem: {
          prop: item.key,
          label: item.title,
          rules: {
            require: true,
            trigger: 'change',
            validator: item.rule
          }
        },
        control: {
          ...item
        }
      })
    })
    GeneratorUtils.setRequired(this.formOption)
  },
  methods: {
    copy(val, key) {
      if (key) {
        this.form[key] = val
      } else {
        navigator.clipboard.writeText(val)
        ElMessage.success(`已复制:${val}`)
      }
    },
    regexpListGen() {
      let str = ''
      Regexps.forEach((item, index) => {
        str += `
    /**
     * ${item.title}
     *
     * @example
     * ${item.examples.join(',')}
     */
     export const ${item.key} = ${item.rule}
    `
      })
      console.log(str);
    }

  }
}



</script>
<style lang="scss" scoped>
.container {
  // padding: 20px;
  // box-sizing: border-box;

  .examples {
    margin-top: 10px;
    display: flex;
    flex-direction: column;
    overflow: auto;

    .no-wrap {
      flex-wrap: nowrap !important;
      ;
    }

    .tag-container {
      display: flex;
      // flex-wrap: wrap;
      align-items: center;
      gap: 10px;

      >div {
        flex-shrink: 0;
      }

      .el-tag {
        cursor: pointer;
      }
    }
  }

  ::v-deep(.el-form-item) {
    padding: 15px 15px 30px;
    border-radius: 4px;
    margin-bottom: 15px;
    border-color: #eee;
    border-width: 1px;
    border-style: solid;
    -webkit-box-shadow: 1px 2px 5px 1px rgb(0 0 0 / 10%);
    box-shadow: 1px 2px 5px 1px rgb(0 0 0 / 10%);
    overflow: hidden;
  }
}
</style>