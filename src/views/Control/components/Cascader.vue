<template>
  <FormGenerator ref="FormGenerator" :model="form" :formOption="formOption" />
</template>

<script>
import { FormGenerator } from 'element-ui-generator'

export default {
  components: {
    FormGenerator
  },
  data: () => {
    const options = [
      {
        value: 'guide',
        label: 'Guide',
        children: [
          {
            value: 'disciplines',
            label: 'Disciplines',
            children: [
              {
                value: 'consistency',
                label: 'Consistency',
              },
              {
                value: 'feedback',
                label: 'Feedback',
              },
              {
                value: 'efficiency',
                label: 'Efficiency',
              },
              {
                value: 'controllability',
                label: 'Controllability',
              },
            ],
          },
          {
            value: 'navigation',
            label: 'Navigation',
            children: [
              {
                value: 'side nav',
                label: 'Side Navigation',
              },
              {
                value: 'top nav',
                label: 'Top Navigation',
              },
            ],
          },
        ],
      },
      {
        value: 'component',
        label: 'Component',
        children: [
          {
            value: 'basic',
            label: 'Basic',
            children: [
              {
                value: 'layout',
                label: 'Layout',
              },
              {
                value: 'color',
                label: 'Color',
              },
              {
                value: 'typography',
                label: 'Typography',
              },
              {
                value: 'icon',
                label: 'Icon',
              },
              {
                value: 'button',
                label: 'Button',
              },
            ],
          },
          {
            value: 'form',
            label: 'Form',
            children: [
              {
                value: 'radio',
                label: 'Radio',
              },
              {
                value: 'checkbox',
                label: 'Checkbox',
              },
              {
                value: 'input',
                label: 'Input',
              },
              {
                value: 'input-number',
                label: 'InputNumber',
              },
              {
                value: 'select',
                label: 'Select',
              },
              {
                value: 'cascader',
                label: 'Cascader',
              },
              {
                value: 'switch',
                label: 'Switch',
              },
              {
                value: 'slider',
                label: 'Slider',
              },
              {
                value: 'time-picker',
                label: 'TimePicker',
              },
              {
                value: 'date-picker',
                label: 'DatePicker',
              },
              {
                value: 'datetime-picker',
                label: 'DateTimePicker',
              },
              {
                value: 'upload',
                label: 'Upload',
              },
              {
                value: 'rate',
                label: 'Rate',
              },
              {
                value: 'form',
                label: 'Form',
              },
            ],
          },
          {
            value: 'data',
            label: 'Data',
            children: [
              {
                value: 'table',
                label: 'Table',
              },
              {
                value: 'tag',
                label: 'Tag',
              },
              {
                value: 'progress',
                label: 'Progress',
              },
              {
                value: 'tree',
                label: 'Tree',
              },
              {
                value: 'pagination',
                label: 'Pagination',
              },
              {
                value: 'badge',
                label: 'Badge',
              },
            ],
          },
          {
            value: 'notice',
            label: 'Notice',
            children: [
              {
                value: 'alert',
                label: 'Alert',
              },
              {
                value: 'loading',
                label: 'Loading',
              },
              {
                value: 'message',
                label: 'Message',
              },
              {
                value: 'message-box',
                label: 'MessageBox',
              },
              {
                value: 'notification',
                label: 'Notification',
              },
            ],
          },
          {
            value: 'navigation',
            label: 'Navigation',
            children: [
              {
                value: 'menu',
                label: 'Menu',
              },
              {
                value: 'tabs',
                label: 'Tabs',
              },
              {
                value: 'breadcrumb',
                label: 'Breadcrumb',
              },
              {
                value: 'dropdown',
                label: 'Dropdown',
              },
              {
                value: 'steps',
                label: 'Steps',
              },
            ],
          },
          {
            value: 'others',
            label: 'Others',
            children: [
              {
                value: 'dialog',
                label: 'Dialog',
              },
              {
                value: 'tooltip',
                label: 'Tooltip',
              },
              {
                value: 'popover',
                label: 'Popover',
              },
              {
                value: 'card',
                label: 'Card',
              },
              {
                value: 'carousel',
                label: 'Carousel',
              },
              {
                value: 'collapse',
                label: 'Collapse',
              },
            ],
          },
        ],
      },
      {
        value: 'resource',
        label: 'Resource',
        children: [
          {
            value: 'axure',
            label: 'Axure Components',
          },
          {
            value: 'sketch',
            label: 'Sketch Templates',
          },
          {
            value: 'docs',
            label: 'Design Documentation',
          },
        ],
      },
    ]
    return {
      form: {},
      formOption: [
        {
          type: 'cascader',
          formItem: {
            prop: 'key1',
            label: '基础用法',
          },
          control: {
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key2',
            label: '禁用选项',
          },
          control: {
            disabled: true,
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key3',
            label: '可清空',
          },
          control: {
            clearable: true,
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key4',
            label: '仅显示最后一级',
          },
          control: {
            showAllLevels: false,
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key5',
            label: '多选',
          },
          control: {
            props: {
              multiple: true,
            },
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key6',
            label: '选择任意一级选项',
          },
          control: {
            props: {
              checkStrictly: true,
            },
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key7',
            label: '动态加载',
          },
          control: {
            props: {
              lazy: true,
              lazyLoad(node, resolve) {
                let { level } = node
                setTimeout(() => {
                  const nodes = Array.from({ length: level + 1 }).map((item) => ({
                    value: ++level,
                    label: `Option - ${level}`,
                    leaf: level >= 2,
                  }))
                  // Invoke `resolve` callback to return the child nodes data and indicate the loading is finished.
                  resolve(nodes)
                }, 1000)
              },
            },
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key8',
            label: '可搜索',
          },
          control: {
            filterable: true,
            options: options
          },
        },
        {
          type: 'cascader',
          formItem: {
            prop: 'key9',
            label: '自定义节点内容',
          },
          control: {
            options: options,
            slot: {
              default: (scope) => (
                <div>
                  <span>{scope.data.label}</span>
                  {!scope.node.isLeaf ? <span> ({scope.data.children.length}) </span> : ''}
                </div>
              ),
            }
          },
        },
      ],
    }
  },
}

</script>