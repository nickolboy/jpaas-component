## 按钮
按钮用于开始一个即时操作

### 何时使用
标记了一个（或封装一组）操作命令，响应用户点击行为，触发相应的业务逻辑。

### 代码演示
#### 按钮类型
按钮有五种类型：主按钮、次按钮、虚线按钮、危险按钮和链接按钮。主按钮在同一个操作区域最多出现一次。

```vue
<template>
<div>
  <h-button type="primary">
    primary
  </h-button>
  <h-button>
    cancel
  </h-button>
  <h-button>
    Dashed
  </h-button>
  <h-button type="danger">
    Danger
  </h-button>
  <h-button type="link">
          Link
  </h-button>
</div>
</template>

<script>
import { HButton } from 'jpaas-component'
export default {
data(){
  return{
    
  }
},
components: {
  HButton
}
}
</script>

```
#### 加载中状态 
添加 loading 属性即可让按钮处于加载状态。

```vue
<template>
<div>
<h-button loading type="primary">
  加载中
</h-button>
</div>
</template>

<script>
import { HButton } from 'jpaas-component'

export default {
data(){
  return{
    
  }
},
components: {
  HButton
}
}
</script>

```
#### 带图标的按钮
当需要在 Button 内嵌入 Icon 时，需要设置 icon 属性。

```vue
<template>
<div>
<h-button :icon="IconEdit">编辑</h-button>
</div>
</template>
<script>
import { HButton } from "jpaas-component"
import IconEdit from "@ant-design/icons/svg/outline/edit.svg?inline"
export default {
componnet: {
    HButton
},
data () {
    return {
      IconEdit
    }
  }
}
</script>
      
```

#### 按钮组合 
可以将多个 Button 放入 Button.Group 的容器中。

```vue
<template>
<div>
<h-button :icon="IconEdit">编辑</h-button>
</div>
</template>
<script>
import { HButton } from "jpaas-component"
import IconEdit from "@ant-design/icons/svg/outline/edit.svg?inline"
export default {
componnet: {
    HButton
},
data () {
    return {
      IconEdit
    }
  }
}
</script>
      
```

### API
通过设置 Button 的属性来产生不同的按钮样式，推荐顺序为：`type` -> `shape` -> `size` -> `loading` -> `disabled`。

按钮的属性说明如下：

| 属性     | 说明                                                         | 类型                       | 默认值    | 版本 |
| -------- | ------------------------------------------------------------ | -------------------------- | --------- | ---- |
| disabled | 按钮失效状态                                                 | boolean                    | `false`   |      |
| ghost    | 幽灵属性，使按钮背景透明                                     | boolean                    | false     |      |
| htmlType | 设置 `button` 原生的 `type` 值，可选值请参考 [HTML 标准](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button#attr-type) | string                     | `button`  |      |
| icon     | 设置按钮的图标类型                                           | string                     | \-        |      |
| loading  | 设置按钮载入状态                                             | boolean\|{ delay: number } | `false`   |      |
| shape    | 设置按钮形状，可选值为 `circle`、 `round` 或者不设           | string                     | \-        |      |
| size     | 设置按钮大小，可选值为 `small` `large` 或者不设              | string                     | `default` |      |
| type     | 设置按钮类型，可选值为 `primary` `dashed` `danger` `link` 或者不设 | string                     | `default` |      |
| block    | 将按钮宽度调整为其父宽度的选项                               | boolean                    | `false`   |      |

#### 事件
| 事件名称 | 说明             | 回调参数        | 版本 |
| -------- | ---------------- | --------------- | ---- |
| click    | 点击按钮时的回调 | (event) => void |      |

支持原生 button 的其他所有属性。

## 侧边栏
协助进行页面级整体布局。

提示：作为页面布局使用时，将HSiderPanel作为根元素，能够自适应可视区高度

### 代码演示
#### 左侧面板 
需使用 #leftSiderContent插槽

```vue
<template>
<h-sider-panel style="height:200px">
<template #leftSiderTitle>左侧标题</template>
<template #leftSiderContent>
  <div>
    左侧区域
  </div>
</template>
<template #content>
  <div style="margin:30px">
    右侧内容
  </div>
</template>
</h-sider-panel>
</template>
<script>
import { HSiderPanel } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HSiderPanel
}
}
</script>
<style scoped>

</style>

```

#### 右侧面板
需使用 #rightSiderContent插槽

```vue
<template>
<h-sider-panel style="height:200px">
<template #leftSiderTitle>左侧标题</template>
<template #leftSiderContent>
  <div>
    左侧区域
  </div>
</template>
<template #content>
  <div style="margin:30px">
    右侧内容
  </div>
</template>
</h-sider-panel>
</template>
<script>
import { HSiderPanel } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HSiderPanel
}
}
</script>
<style scoped>

</style>

```

### Api
| 参数       | 说明                       | 类型   | 默认值 |
| :--------- | :------------------------- | :----- | :----- |
| leftWidth  | 右侧面板时左边内容区域宽度 | number | 240    |
| rightWidth | 左侧面板时右边内容区域宽度 | number | 240    |

## 导航菜单
为页面和功能提供导航的菜单列表。

### 何时使用
导航菜单是一个网站的灵魂，用户依赖导航在各个页面中进行跳转。一般分为顶部导航和侧边导航，顶部导航提供全局性的类目和功能，侧边导航提供多级结构来收纳和排列网站架构。

### 代码演示
#### 基本使用
基本使用。

```vue
<template>
<h-menu
:dataSource="orgTree"
:selectedKeys="selectedKeys"
mode="inline"
@click="clickMenu"
:matchSiderpanel="false"
>
</h-menu>
</template>
<script>
import { HMenu } from 'jpaas-component'
export default {
  data () {
    return {
      orgTree:[
        {
          params: { type: 0 },
          key: 'mingan',
          title: '敏感词'
        },
        {
          params: { type: 0 },
          key: 'tingyong',
          title: '停用词'
        },
        {
          params: { type: 0 },
          key: 'tongyi',
          title: '同义词'
        },
        {
          params: { type: 0 },
          key: 'yewu',
          title: '业务主词'
        },
        {
          params: { type: 0 },
          key: 'xiangguan',
          title: '相关词'
        },
        {
          params: { type: 0 },
          key: 'pinyin',
          title: '拼音词'
        },

        {
          params: { type: 0 },
          key: 'zidingyi',
          title: '自定义词'
        }
      ],
      selectedKeys:[],
    }
},
methods: {
  clickMenu (e) {
    this.selectedKeys = [e.key]
  }
}
components: {
  HMenu
}
}
</script>
<style scoped>

</style>

```

### API 
```html
<template>
  <h-menu>
    <h-menu-item>菜单项</h-menu-item>
    <h-sub-menu title="子菜单">
      <h-menu-item>子菜单项</h-menu-item>
    </h-sub-menu>
  </h-menu>
</template>
```

#### Menu 
| 参数                  | 说明                                         | 类型                                                      | 默认值             |
| :-------------------- | :------------------------------------------- | :-------------------------------------------------------- | :----------------- |
| defaultOpenKeys       | 初始展开的 SubMenu 菜单项 key 数组           |                                                           |                    |
| defaultSelectedKeys   | 初始选中的菜单项 key 数组                    | string[]                                                  |                    |
| forceSubMenuRender    | 在子菜单展示之前就渲染进 DOM                 | boolean                                                   | false              |
| inlineCollapsed       | inline 时菜单是否收起状态                    | boolean                                                   | -                  |
| inlineIndent          | inline 模式的菜单缩进宽度                    | number                                                    | 24                 |
| mode                  | 菜单类型，现在支持垂直、水平、和内嵌模式三种 | string: `vertical` `vertical-right` `horizontal` `inline` | `vertical`         |
| multiple              | 是否允许多选                                 | boolean                                                   | false              |
| openKeys(.sync)       | 当前展开的 SubMenu 菜单项 key 数组           | string[]                                                  |                    |
| selectable            | 是否允许选中                                 | boolean                                                   | true               |
| selectedKeys(v-model) | 当前选中的菜单项 key 数组                    | string[]                                                  |                    |
| subMenuCloseDelay     | 用户鼠标离开子菜单后关闭延时，单位：秒       | number                                                    | 0.1                |
| subMenuOpenDelay      | 用户鼠标进入子菜单后开启延时，单位：秒       | number                                                    | 0                  |
| theme                 | 主题颜色                                     | string: `light` `dark`                                    | `light`            |
| overflowedIndicator   | 自定义 Menu 折叠时的图标                     | DOM                                                       | `<span>···</span>` |

#### Menu 事件 
| 事件名称   | 说明                               | 回调参数                              |
| :--------- | :--------------------------------- | :------------------------------------ |
| click      | 点击 MenuItem 调用此函数           | function({ item, key, keyPath })      |
| deselect   | 取消选中时调用，仅在 multiple 生效 | function({ item, key, selectedKeys }) |
| openChange | SubMenu 展开/关闭的回调            | function(openKeys: string[])          |
| select     | 被选中时调用                       | function({ item, key, selectedKeys }) |

#### Menu.Item 
| 参数     | 说明                     | 类型    | 默认值 |
| :------- | :----------------------- | :------ | :----- |
| disabled | 是否禁用                 | boolean | false  |
| key      | item 的唯一标志          | string  |        |
| title    | 设置收缩时展示的悬浮标题 | string  |        |

#### Menu.SubMenu
| 参数           | 说明       | 类型         | 默认值 | 版本  |
| :------------- | :--------- | :----------- | :----- | :---- |
| popupClassName | 子菜单样式 | string       |        | 1.5.0 |
| disabled       | 是否禁用   | boolean      | false  |       |
| key            | 唯一标志   | string       |        |       |
| title          | 子菜单项值 | string\|slot |        |       |

Menu.SubMenu 的子元素必须是 `MenuItem` 或者 `SubMenu`.

#### SubMenu 事件
| 事件名称   | 说明           | 回调参数            |
| :--------- | :------------- | :------------------ |
| titleClick | 点击子菜单标题 | ({ key, domEvent }) |

#### Menu.ItemGroup 
| 参数  | 说明     | 类型                     | 默认值 |
| :---- | :------- | :----------------------- | :----- |
| title | 分组标题 | string\|\|function\|slot |        |

Menu.ItemGroup 的子元素必须是 `MenuItem`.

#### Menu.Divider 
菜单项分割线，只用在弹出菜单内。

## 元数据表单设计器
表单设计。

### 何时使用
1、表单结构复杂。
2、提供丰富类型的控件，自定义程度较高，支持预览功能，快速完成表单的设计

### 代码演示 
#### 表单设计
基本使用。

```vue
<template>
<a-card>
  <div style="margin-bottom: 16px;">
    <h-button type="primary" @click="handleSave" :style="{'marginRight': '16px'}">保存</h-button>
    <h-button type="primary" @click="handlePreview">预览</h-button>
  </div>

  <a-card style="margin: -10px;" :bodyStyle="{padding:0}">
    <h-meta-form-designer
      ref="hMetaFormDesigner"
      :fieldList="fieldList"
      :dimensionList="dimensionList"
      :importSource="importSource"
      :meta="formMeta"
      :template="formTemplate"
      :formConfig="formConfig"
      :associated="associated"
    />
  </a-card>
</a-card>
</template>
<script>
import HMetaFormDesigner from 'jpaas-component/lib/HMetaForm/design'
export default {
data () {
  return {
    associated:{},
    formMeta:{},
    formTemplate:[],
    formConfig:{},
    importSource:'meta',
    dimensionList:[
      {
        beInherit:0,
        creatorId:'bdf699cf97284db0a9524332f0648f22',
        delFlag:'0',
        dimensionCode:'nGvZdWCc7ByOoGgt',
        extend:null,
        iid:'7cc53e3e58394e4d9b4cbc259c9764bc',
        isDefault:1,
        name:'五公开',
        userName:null,
        utime:1651803224347
      },
      {
        beInherit:0,
        creatorId:'bdf699cf97284db0a9524332f0648f22',
        delFlag:'0',
        dimensionCode:'QJ1RV32QaV2S9VI3',
        extend:null,
        iid:'37050dfd2f854ffe91be93a56e63a336',
        isDefault:1,
        name:'服务对象',
        userName:null,
        utime:1634118331783
      }
    ], // 维度列表
    fieldList:[ // 字段列表
      {
        name:'年龄',
        fieldName:'age',
        fieldType:'Int'
      },
      {
        name:'性别',
        fieldName:'sex',
        fieldType:'Dimension'
      },
      {
        name:'得分',
        fieldName:'score',
        fieldType:'Number'
      },
      {
        name:'日期',
        fieldName:'date',
        fieldType:'Date'
      },
      {
        name:'时间',
        fieldName:'time',
        fieldType:'Time'
      },
      {
        name:'姓名',
        fieldName:'name',
        fieldType:'String'
      },
      {
        name:'描述',
        fieldName:'desc',
        fieldType:'Text'
      },
      {
        name:'图片',
        fieldName:'img',
        fieldType:'Picture'
      },
      {
        name:'视频',
        fieldName:'video',
        fieldType:'Video'
      },
      {
        name:'附件',
        fieldName:'attach',
        fieldType:'Attach'
      },
      {
        name:'定位',
        fieldName:'location',
        fieldType:'Location'
      },
      {
        name:'所属地区',
        fieldName:'address',
        fieldType:'Dimension'
      }
    ]
  }
},
components: {
  HMetaFormDesigner
},
methods:{
  handleSave () {
    this.$message.info('请查看控制台')
    this.$refs.hMetaFormDesigner.save()
    console.log('formMeta', this.formMeta)
    console.log('formTemplate', this.formTemplate)
    console.log('formConfig', this.formConfig)
    console.log('associated', this.associated)
  },
  handlePreview () {
    this.$refs.hMetaFormDesigner.preview()
  }
}
}
</script>
<style scoped>

</style>

```

### Api
元数据表单设计器的属性说明如下：

| 参数          | 说明                                                         | 类型   | 默认值 |
| :------------ | :----------------------------------------------------------- | :----- | :----- |
| fieldList     | 字段列表                                                     | Arrary | -      |
| dimensionList | 维度列表                                                     | Arrary | -      |
| importSource  |                                                              | string | meta   |
| meta          | 表单配置项[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaFormDesigner#FormMeta) | object | -      |
| template      | 表单列表项                                                   | Arrary | -      |
| formConfig    | 表单布局结构的配置项：[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaFormDesigner#formConfig) | object | -      |
| associated    | 表单设置项                                                   | object | -      |

#### FormMeta
表单设计的配置项：

| 参数      | 说明                                                         | 类型   | 默认值 |
| :-------- | :----------------------------------------------------------- | :----- | :----- |
| fieldName | 表单项绑定字段名                                             | string | -      |
| fieldType | 表单项绑定值类型                                             | string | -      |
| name      | 表单项名称                                                   | string | -      |
| pageNo    | 表单当前页（如果有分页的情况）                               | number | 1      |
| props     | 表单项初始化配置项，详见下面[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaFormDesigner#Props) | Object | -      |
| rules     | 表单项校验规则                                               | Array  | -      |
| type      | 表单项类型                                                   | string | -      |

#### FormConfig
表单布局结构的配置项：

| 参数            | 说明                     | 类型    | 默认值     |
| :-------------- | :----------------------- | :------ | :--------- |
| labelCol        | 表单项标签长度           | Object  | {span:4}   |
| labelAlign      | 表单项标签对齐方式       | string  | right      |
| layout          | 表单布局方式             | string  | "vertical" |
| pages           | 表单总页数（如果有分页） | number  | 1          |
| showePagination | 表单是否有分页           | Boolean | true       |

#### Props
表单项初始化的配置项：

| 参数        | 说明             | 类型    | 默认值 |
| :---------- | :--------------- | :------ | :----- |
| anchor      | 是否支持锚点定位 | Boolean | false  |
| disabled    | 是否禁用         | Boolean | false  |
| placeholder | 提示信息         | string  | -      |
| showTitle   | 是否显示标题     | Boolean | true   |
| flag        | 是否必填         | Boolean | false  |

## 元数据表单
表单使用。

### 何时使用
1、表单结构复杂。
2、可实现表单项定制

### 代码演示
#### 基本使用
使用设计好的表单。

```vue
<template>
  <div>
    <h-meta-form
      ref="metaForm"
      :layout="formConfig.layout"
      :labelCol="formConfig.labelCol"
      :wrapperCol="formConfig.wrapperCol"
      :labelAlign="formConfig.labelAlign"
      :associated="associated"
      :template="formTemplate"
      :meta="formMeta"
      :model="formModel"
      :pages="formConfig.pages"
      :componentMapping="componentMapping"
      :globalConfig="{
        imgUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-pic',
          accept: '.jpg,.jpeg,.png,.gif'
        },
        attachUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        },
        videoUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        }
      }"
    >
    </h-meta-form>
  </div>
</template>

<script>
import HMetaForm from 'jpaas-component/lib/HMetaForm'
import HMetaFormConfig from 'jpaas-component/lib/HMetaFormConfig'
export default {
  components: {
    HMetaForm

  },
  data () {
    return {
      // 工作流表单升级
      formDesign: {},
      formTemplate: ['Input_1653014542284', 'InputNumber_1653014805302', 'Switch_1653014811503'],
      formMeta: {
        'Input_1653014542284': {
          'name': '文本框',
          'type': 'Input',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'pcShow': true,
            'mobileShow': true,
            'flag': true,
            'placeholder': '请填写内容',
            'anchor': false
          },
          'rules': [{
            'required': true,
            'message': '请输入'
          }, {
            'min': 0,
            'max': 50,
            'message': '输入文字长度超出范围限制'
          }, {}],
          'pageNo': 1,
          'fieldType': 'String',
          'validator': true,
          'fieldName': 'eqwe',
          'visible': true
        },
        'InputNumber_1653014805302': {
          'name': '数字输入框',
          'type': 'InputNumber',
          'fieldType': 'Number',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'min': 0,
            'max': 100,
            'mobileShow': true,
            'pcShow': true,
            'placeholder': '请填写数字',
            'anchor': false
          },
          'rules': [{
            'required': false,
            'message': '请输入'
          }],
          'pageNo': 1,
          'fieldName': 'trte',
          'validator': true,
          'visible': true
        },
        'Switch_1653014811503': {
          'name': '开关',
          'type': 'Switch',
          'desensitizeRule': '',
          'props': {
            'isSwitch': true,
            'disabled': false,
            'mobileShow': true,
            'pcShow': true,
            'showTitle': true,
            'checked': true,
            'anchor': false,
            'checkedChildren': '开',
            'unCheckedChildren': '关',
            'defaultChecked': true
          },
          'pageNo': 1,
          'fieldType': 'String',
          'fieldName': 'wrwer',
          'validator': true,
          'visible': true
        }
      },
      formConfig: {
        'layout': 'vertical',
        'labelCol': null,
        'pages': 1,
        'showePagination': true,
        'mobileFormConfig': {
          'layout': 'vertical',
          'labelCol': null,
          'inputAlign': 'left',
          'pages': 1
        }
      },
      formModel: { eqwe: '测试',
      trte: 100,
      wrwer: true },
      associated: {},
      spinning: true,
      componentMapping: HMetaFormConfig
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
```
#### 表单配置
通过globalConfig可对上传、视频、音频等控件进行特定配置。

校验两种写法，一种统一写在HMetaForm上，一种写在组件的meta里（如：姓名的校验）

```vue
<template>
  <div>
    <h-meta-form
      ref="metaForm"
      :layout="formConfig.layout"
      :labelCol="formConfig.labelCol"
      :wrapperCol="formConfig.wrapperCol"
      :labelAlign="formConfig.labelAlign"
      :associated="associated"
      :template="formTemplate"
      :meta="formMeta"
      :model="formModel"
      :pages="formConfig.pages"
      :componentMapping="componentMapping"
      :globalConfig="{
        imgUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-pic',
          accept: '.jpg,.jpeg,.png,.gif'
        },
        attachUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        },
        videoUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        }
      }"
    >
    </h-meta-form>
  </div>
</template>

<script>
import HMetaForm from 'jpaas-component/lib/HMetaForm'
import HMetaFormConfig from 'jpaas-component/lib/HMetaFormConfig'
export default {
  components: {
    HMetaForm

  },
  data () {
    return {
      // 工作流表单升级
      formDesign: {},
      formTemplate: ['Input_1653014542284', 'InputNumber_1653014805302', 'Switch_1653014811503'],
      formMeta: {
        'Input_1653014542284': {
          'name': '文本框',
          'type': 'Input',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'pcShow': true,
            'mobileShow': true,
            'flag': true,
            'placeholder': '请填写内容',
            'anchor': false
          },
          'rules': [{
            'required': true,
            'message': '请输入'
          }, {
            'min': 0,
            'max': 50,
            'message': '输入文字长度超出范围限制'
          }, {}],
          'pageNo': 1,
          'fieldType': 'String',
          'validator': true,
          'fieldName': 'eqwe',
          'visible': true
        },
        'InputNumber_1653014805302': {
          'name': '数字输入框',
          'type': 'InputNumber',
          'fieldType': 'Number',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'min': 0,
            'max': 100,
            'mobileShow': true,
            'pcShow': true,
            'placeholder': '请填写数字',
            'anchor': false
          },
          'rules': [{
            'required': false,
            'message': '请输入'
          }],
          'pageNo': 1,
          'fieldName': 'trte',
          'validator': true,
          'visible': true
        },
        'Switch_1653014811503': {
          'name': '开关',
          'type': 'Switch',
          'desensitizeRule': '',
          'props': {
            'isSwitch': true,
            'disabled': false,
            'mobileShow': true,
            'pcShow': true,
            'showTitle': true,
            'checked': true,
            'anchor': false,
            'checkedChildren': '开',
            'unCheckedChildren': '关',
            'defaultChecked': true
          },
          'pageNo': 1,
          'fieldType': 'String',
          'fieldName': 'wrwer',
          'validator': true,
          'visible': true
        }
      },
      formConfig: {
        'layout': 'vertical',
        'labelCol': null,
        'pages': 1,
        'showePagination': true,
        'mobileFormConfig': {
          'layout': 'vertical',
          'labelCol': null,
          'inputAlign': 'left',
          'pages': 1
        }
      },
      formModel: { eqwe: '测试',
      trte: 100,
      wrwer: true },
      associated: {},
      spinning: true,
      componentMapping: HMetaFormConfig
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
```
#### 表单插槽和监听器
通过slots属性可指定注入到表单组件的插槽。

使用listeners属性可对表单组件进行实时监听

```vue
<template>
  <div>
    <h-meta-form
      ref="metaForm"
      :layout="formConfig.layout"
      :labelCol="formConfig.labelCol"
      :wrapperCol="formConfig.wrapperCol"
      :labelAlign="formConfig.labelAlign"
      :associated="associated"
      :template="formTemplate"
      :meta="formMeta"
      :model="formModel"
      :pages="formConfig.pages"
      :componentMapping="componentMapping"
      :globalConfig="{
        imgUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-pic',
          accept: '.jpg,.jpeg,.png,.gif'
        },
        attachUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        },
        videoUpload: {
          action: '/api-gateway/common-workflow-server/manager/business/upload-approve-file'
        }
      }"
    >
    </h-meta-form>
  </div>
</template>

<script>
import HMetaForm from 'jpaas-component/lib/HMetaForm'
import HMetaFormConfig from 'jpaas-component/lib/HMetaFormConfig'
export default {
  components: {
    HMetaForm

  },
  data () {
    return {
      // 工作流表单升级
      formDesign: {},
      formTemplate: ['Input_1653014542284', 'InputNumber_1653014805302', 'Switch_1653014811503'],
      formMeta: {
        'Input_1653014542284': {
          'name': '文本框',
          'type': 'Input',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'pcShow': true,
            'mobileShow': true,
            'flag': true,
            'placeholder': '请填写内容',
            'anchor': false
          },
          'rules': [{
            'required': true,
            'message': '请输入'
          }, {
            'min': 0,
            'max': 50,
            'message': '输入文字长度超出范围限制'
          }, {}],
          'pageNo': 1,
          'fieldType': 'String',
          'validator': true,
          'fieldName': 'eqwe',
          'visible': true
        },
        'InputNumber_1653014805302': {
          'name': '数字输入框',
          'type': 'InputNumber',
          'fieldType': 'Number',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'min': 0,
            'max': 100,
            'mobileShow': true,
            'pcShow': true,
            'placeholder': '请填写数字',
            'anchor': false
          },
          'rules': [{
            'required': false,
            'message': '请输入'
          }],
          'pageNo': 1,
          'fieldName': 'trte',
          'validator': true,
          'visible': true
        },
        'Switch_1653014811503': {
          'name': '开关',
          'type': 'Switch',
          'desensitizeRule': '',
          'props': {
            'isSwitch': true,
            'disabled': false,
            'mobileShow': true,
            'pcShow': true,
            'showTitle': true,
            'checked': true,
            'anchor': false,
            'checkedChildren': '开',
            'unCheckedChildren': '关',
            'defaultChecked': true
          },
          'pageNo': 1,
          'fieldType': 'String',
          'fieldName': 'wrwer',
          'validator': true,
          'visible': true
        }
      },
      formConfig: {
        'layout': 'vertical',
        'labelCol': null,
        'pages': 1,
        'showePagination': true,
        'mobileFormConfig': {
          'layout': 'vertical',
          'labelCol': null,
          'inputAlign': 'left',
          'pages': 1
        }
      },
      formModel: { eqwe: '测试',
      trte: 100,
      wrwer: true },
      associated: {},
      spinning: true,
      componentMapping: HMetaFormConfig
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
```
### Api
元数据表单的属性说明如下：

| 参数             | 说明                                                         | 类型   | 默认值                           |
| :--------------- | :----------------------------------------------------------- | :----- | :------------------------------- |
| model            | 表单绑定的数据源                                             | Object | -                                |
| meta             | 表单设计数据源，详见下面[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaForm#FormMeta) | Object | -                                |
| template         | 表单布局配置项                                               | Array  | -                                |
| pages            | 表单分页                                                     | Number | -                                |
| componentMapping | 表单项控件                                                   | Object | -                                |
| labelCol         | label 标签布局，同 <Col> 组件                                | object | -                                |
| layout           | 表单布局结构                                                 | string | horizontal \| vertical \| inline |
| labelAlign       | 标签对其方式                                                 | string | left \| right                    |
| wrapperCol       | 需要为输入控件设置布局样式时，使用该属性，用法同 labelCol    | object | -                                |

#### Meta
表单设计的配置项：

| 参数      | 说明                                                         | 类型   | 默认值 |
| :-------- | :----------------------------------------------------------- | :----- | :----- |
| fieldName | 表单项绑定字段名                                             | string | -      |
| fieldType | 表单项绑定值类型                                             | string | -      |
| name      | 表单项名称                                                   | string | -      |
| pageNo    | 表单当前页（如果有分页的情况）                               | number | 1      |
| props     | 表单项初始化配置项，详见下面[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaForm#Props) | Object | -      |
| rules     | 表单项校验规则                                               | Array  | -      |
| type      | 表单项类型                                                   | string | -      |

#### Props
表单项初始化的配置项：

| 参数        | 说明             | 类型    | 默认值 |
| :---------- | :--------------- | :------ | :----- |
| anchor      | 是否支持锚点定位 | Boolean | false  |
| disabled    | 是否禁用         | Boolean | false  |
| placeholder | 提示信息         | string  | -      |
| showTitle   | 是否显示标题     | Boolean | true   |
| flag        | 是否必填         | Boolean | false  |

## 元数据视图
通过鼠标或键盘输入内容，是最基础的表单域的包装。

### 何时使用
1、需要用户输入表单域内容时。

2、提供组合型输入框，带搜索的输入框，还可以进行大小选择
### 代码演示
#### 基本使用
基本使用。

```vue
<template>
<h-meta-view
:template="formTemplate"
:meta="formMeta"
:value="formData"
:borderShow="userBorder"
:layout="userLayout"
:labelAlign="userLabelAlign"
labelWidth="100px"
/>
</template>
<script>
import { HMetaView } from 'jpaas-component'
export default {
  data () {
    return {
      userLayout: 'horizontal',
      userBorder: true,
      userLabelAlign: 'right',
      formTemplate: ['eqwe', 'trte', 'wrwer'],
      formMeta: {
        'eqwe': {
          'name': '文本框',
          'type': 'Input',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'pcShow': true,
            'mobileShow': true,
            'flag': true,
            'placeholder': '请填写内容',
            'anchor': false
          },
          'rules': [{
            'required': true,
            'message': '请输入'
          }, {
            'min': 0,
            'max': 50,
            'message': '输入文字长度超出范围限制'
          }, {}],
          'pageNo': 1,
          'fieldType': 'String',
          'validator': true,
          'fieldName': 'eqwe',
          'visible': true
        },
        'trte': {
          'name': '数字输入框',
          'type': 'InputNumber',
          'fieldType': 'Number',
          'desensitizeRule': '',
          'props': {
            'disabled': false,
            'showTitle': true,
            'min': 0,
            'max': 100,
            'mobileShow': true,
            'pcShow': true,
            'placeholder': '请填写数字',
            'anchor': false,
            'value': 11
          },
          'rules': [{
            'required': false,
            'message': '请输入'
          }],
          'pageNo': 1,
          'fieldName': 'trte',
          'validator': true,
          'visible': true
        },
        'wrwer': {
          'name': '开关',
          'type': 'Switch',
          'desensitizeRule': '',
          'props': {
            'isSwitch': true,
            'disabled': false,
            'mobileShow': true,
            'pcShow': true,
            'showTitle': true,
            'checked': true,
            'anchor': false,
            'checkedChildren': '开',
            'unCheckedChildren': '关',
            'defaultChecked': true
          },
          'pageNo': 1,
          'fieldType': 'String',
          'fieldName': 'wrwer',
          'validator': true,
          'visible': true
        }
      },
      formData: {
        eqwe: '测试',
        trte: 100,
        wrwer: true
      }
    }
},
components: {
  HMetaView
}
}
</script>
<style scoped>

</style>

```

### Api
元数据视图的属性说明如下：

| 参数       | 说明                                                         | 类型    | 默认值                           |
| :--------- | :----------------------------------------------------------- | :------ | :------------------------------- |
| value      | 表单绑定的数据源                                             | Object  | -                                |
| meta       | 表单设计数据源，详见下面[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaView#FormMeta) | Object  | -                                |
| borderShow | 是否有边框线                                                 | boolean | true                             |
| layout     | 表单布局结构                                                 | string  | horizontal \| vertical \| inline |
| labelAlign | 标签对其方式                                                 | string  | left \| right                    |

#### FormMeta
表单设计的配置项：

| 参数      | 说明                                                         | 类型   | 默认值 |
| :-------- | :----------------------------------------------------------- | :----- | :----- |
| fieldName | 表单项绑定字段名                                             | string | -      |
| fieldType | 表单项绑定值类型                                             | string | -      |
| name      | 表单项名称                                                   | string | -      |
| pageNo    | 表单当前页（如果有分页的情况）                               | number | 1      |
| props     | 表单项初始化配置项，详见下面[配置项](https://jpaasdev2.hanweb.com/documentation/hMetaView#Props) | Object | -      |
| rules     | 表单项校验规则                                               | Array  | -      |
| type      | 表单项类型                                                   | string | -      |

#### Props
表单项初始化的配置项：

| 参数        | 说明             | 类型    | 默认值 |
| :---------- | :--------------- | :------ | :----- |
| anchor      | 是否支持锚点定位 | Boolean | false  |
| disabled    | 是否禁用         | Boolean | false  |
| placeholder | 提示信息         | string  | -      |
| showTitle   | 是否显示标题     | Boolean | true   |
| flag        | 是否必填         | Boolean | false  |

## 流程图
用图形来表示业务逻辑的一种极好的方法。

### 代码演示
#### 流程图设计
```vue
<template>
<div class="workflow-route-setting">
<flow
  ref="flowDesigner"
  :flowId="flowId"
/>
</div>
</template>
<script>
import Flow from 'jpaas-component/business/Flow'
export default {
  data () {
    return {
      flowId: 'b7a29ce08cba4cedbcbec18ac93b7451',
      flowData: [{
        'next': 1,
        'id': 0,
        'title': '发起节点',
        'type': 1
      }, {
        'title': '流程节点',
        'type': 3,
        'id': 1,
        'next': '3,4'
      }, {
        'id': 2,
        'branches': [{
          'type': 5,
          'children': [{
            'type': 3,
            'title': '流程节点',
            'id': 5,
            'next': -1
          }],
          'title': '条件节点',
          'id': 3,
          'next': 5
        }, {
          'type': 5,
          'children': [{
            'type': 3,
            'title': '流程节点',
            'id': 6,
            'next': -1
          }],
          'title': '条件节点',
          'id': 4,
          'next': 6
        }]
      }]
    }
},
mounted () {
  this.$refs.flowDesigner.setFlowDesign(this.flowData)
},
components: {
  Flow
}
}
</script>
<style scoped>

</style>

```

#### 流程图详情
```vue
<template>
<div class="workflow-route-setting">
<flow
  ref="flowDesigner"
  :flowId="flowId"
/>
</div>
</template>
<script>
import Flow from 'jpaas-component/business/Flow'
export default {
  data () {
    return {
      flowId: 'b7a29ce08cba4cedbcbec18ac93b7451',
      flowData: [{
        'next': 1,
        'id': 0,
        'title': '发起节点',
        'type': 1
      }, {
        'title': '流程节点',
        'type': 3,
        'id': 1,
        'next': '3,4'
      }, {
        'id': 2,
        'branches': [{
          'type': 5,
          'children': [{
            'type': 3,
            'title': '流程节点',
            'id': 5,
            'next': -1
          }],
          'title': '条件节点',
          'id': 3,
          'next': 5
        }, {
          'type': 5,
          'children': [{
            'type': 3,
            'title': '流程节点',
            'id': 6,
            'next': -1
          }],
          'title': '条件节点',
          'id': 4,
          'next': 6
        }]
      }]
    }
},
mounted () {
  this.$refs.flowDesigner.setFlowDesign(this.flowData)
},
components: {
  Flow
}
}
</script>
<style scoped>

</style>

```
### Api
| 属性   | 说明   | 类型   | 默认值 |
| :----- | :----- | :----- | :----- |
| flowId | 流程ID | string | -      |

## 输入框
通过鼠标或键盘输入内容，是最基础的表单域的包装。

### 何时使用
1、需要用户输入表单域内容时。

2、提供组合型输入框，带搜索的输入框，还可以进行大小选择

### 代码演示
#### 基本使用
基本使用。

```vue
<template>
  <h-input placeholder="请输入" />
</template>
<script>
import { HInput } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HInput
}
}
</script>
<style scoped>

</style>

```
#### 搜索框
用于对数据进行快速查找。

```vue
<template>
  <h-search placeholder="请输入" />
</template>
<script>
import { HSearch } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HSearch
}
}
</script>
<style scoped>

</style>

```
#### 文本域
用于多行输入。

```vue
<template>
  <h-textarea placeholder="请输入" :limit="50"/>
</template>
<script>
import { HTextarea } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HTextarea
}
}
</script>
<style scoped>

</style>

```

#### 密码强度检测。 需配合表单使用
用于检测输入内容安全强度。

```vue
<template>
  <h-textarea placeholder="请输入" :limit="50"/>
</template>
<script>
import { HTextarea } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HTextarea
}
}
</script>
<style scoped>

</style>

```

### Api
#### Input
| 参数           | 说明                                                         | 类型         | 默认值    | 版本  |
| :------------- | :----------------------------------------------------------- | :----------- | :-------- | :---- |
| addonAfter     | 带标签的 input，设置后置标签                                 | string\|slot |           |       |
| addonBefore    | 带标签的 input，设置前置标签                                 | string\|slot |           |       |
| defaultValue   | 输入框默认内容                                               | string       |           |       |
| disabled       | 是否禁用状态，默认为 false                                   | boolean      | false     |       |
| id             | 输入框的 id                                                  | string       |           |       |
| maxLength      | 最大长度                                                     | number       |           | 1.5.0 |
| prefix         | 带有前缀图标的 input                                         | string\|slot |           |       |
| size           | 控件大小。注：标准表单内的输入框大小限制为 `large`。可选 `large` `default` `small` | string       | `default` |       |
| suffix         | 带有后缀图标的 input                                         | string\|slot |           |       |
| type           | 声明 input 类型，同原生 input 标签的 type 属性，见：[MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#属性)(请直接使用 `Input.TextArea` 代替 `type="textarea"`)。 | string       | `text`    |       |
| value(v-model) | 输入框内容                                                   | string       |           |       |
| allowClear     | 可以点击清除图标删除内容                                     | boolean      |           |       |
| limit          | 适用于文本域，右下角显示限制长度                             | number       | -         |       |

#### Input 事件
| 事件名称   | 说明                   | 回调参数    |
| :--------- | :--------------------- | :---------- |
| change     | 输入框内容变化时的回调 | function(e) |
| pressEnter | 按下回车的回调         | function(e) |

> 如果 `Input` 在 `Form.Item` 内，并且 `Form.Item` 设置了 `id` 和 `options` 属性，则 `value` `defaultValue` 和 `id` 属性会被自动设置。

#### Input.TextArea 
| 参数           | 说明                                                         | 类型            | 默认值 | 版本  |
| :------------- | :----------------------------------------------------------- | :-------------- | :----- | :---- |
| autosize       | 自适应内容高度，可设置为 `true|false` 或对象：`{ minRows: 2, maxRows: 6 }` | boolean\|object | false  |       |
| defaultValue   | 输入框默认内容                                               | string          |        |       |
| value(v-model) | 输入框内容                                                   | string          |        |       |
| allowClear     | 可以点击清除图标删除内容                                     | boolean         |        | 1.5.0 |

#### Input.TextArea 事件 
| 事件名称   | 说明           | 回调参数    |
| :--------- | :------------- | :---------- |
| pressEnter | 按下回车的回调 | function(e) |

`Input.TextArea` 的其他属性和浏览器自带的 [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea) 一致。

##### Input.Search
| 参数        | 说明                                                    | 类型          | 默认值 | 版本  |
| :---------- | :------------------------------------------------------ | :------------ | :----- | :---- |
| enterButton | 是否有确认按钮，可设为按钮文字。该属性会与 addon 冲突。 | boolean\|slot | false  |       |
| loading     | 搜索 loading                                            | boolean       |        | 1.5.0 |

#### Input.Search 事件
| 事件名称 | 说明                         | 回调参数               |
| :------- | :--------------------------- | :--------------------- |
| search   | 点击搜索或按下回车键时的回调 | function(value, event) |

其余属性和 Input 一致。

##### Input.Group
| 参数    | 说明                                                         | 类型    | 默认值    |
| :------ | :----------------------------------------------------------- | :------ | :-------- |
| compact | 是否用紧凑模式                                               | boolean | false     |
| size    | `Input.Group` 中所有的 `Input` 的大小，可选 `large` `default` `small` | string  | `default` |

```html
<h-input-group>
  <h-input />
  <h-input />
</h-input-group>
```

##### Input.Password 
| 参数             | 说明             | 类型    | 默认值 |
| :--------------- | :--------------- | :------ | :----- |
| visibilityToggle | 是否显示切换按钮 | boolean | true   |

## 上传
上传是将信息（网页、文字、图片、视频等）通过网页或者上传工具发布到远程服务器上的过程。

### 何时使用
- 当需要上传一个或一些文件时。
- 当需要展现上传的进度时。

### 代码演示
#### 点击上传
经典款式，用户点击按钮弹出文件选择框。

```vue
<template>
<div>
<a-button type="primary" @click="$refs.uploader.excute()" style="margin-bottom:8px">上传文件</a-button>
<h-upload
    ref="uploader"
    :action="action"
    :accept="accept"
    :multiple="multiple"
    :fileNumLimit="fileNumLimit"
    :fileSizeLimit="fileSizeLimit"
    @ok="ok"
    />
    <div style="margin-bottom:8px;background:#f1f2f3;padding-left:8px" v-for="item in fileList" :key="item.uid">
    {{item.name}}
  </div>
</div>
</template>
<script>
import { HUpload } from 'jpaas-component'
export default {
  data () {
    return {
      action:'/api-gateway/common-workflow-server/manager/business/upload-approve-pic', // 上传文件的地址
      uploadedFiles:[],
      accept:'.jpg,.png,.gif',
      multiple:true,
      fileNumLimit:2,
      fileSizeLimit:'200M',
      fileList:[
        {
          name:'111',
          uid:'222'
        },
        {
          name:'2222',
          uid:'3333'
        }
      ]
    }
},
methods:{
  ok(val){
    console.log(val)
    this.fileList = val
  }
},
components: {
  HUpload
}
}
</script>
<style scoped>

</style>

```

### Api
| 属性          | 说明                               | 类型    | 默认值 |
| :------------ | :--------------------------------- | :------ | :----- |
| action        | 上传文件的接口地址                 | string  | -      |
| multiple      | 是否支持多文件上传                 | boolean | true   |
| accept        | 允许上传的文件格式，如： .jpg,.png | string  | -      |
| fileSizeLimit | 单个文件大小限制                   | string  | -      |
| fileNumLimit  | 上传文件数量限制                   | string  | -      |
| autoExcute    | 自动执行（用于编辑器加载并执行）   | true    | false  |

## 下载
下载是将远程服务器信息（网页、文字、图片、视频等）通过工具下载到本地的过程。

### 何时使用
当需要下载一个或一些文件时。

### 代码演示
#### 点击上传
经典款式，用户点击按钮弹出文件选择框。

```vue
<template>
<div>
<!-- 点击按钮触发下载事件 -->
<a-button type="primary" @click="download" class="button">
  下载
</a-button>
<h-download ref="hDownload" :hrefUrl="hrefUrl" :fileName="fileName"></h-download>
</div>
</template>
<script>
import { HDownload } from 'jpaas-component'
export default {
  data () {
    return {
      hrefUrl:'',
      iid:'',
      fileName:'下载文件名.doc'
    }
},
methods: {
  download (iid) {
    // 生成下载接口字符串地址,接口地址拼接后台需要的参数名，传递对应的参数，然后调用下载的方法即可
    this.hrefUrl = '/api-gateway/common-workflow-server/manager/business/file-download?attachId=' + this.iid
    this.$refs.hDownload.download()
  }
}
components: {
  HDownload
}
}
</script>
<style scoped>

</style>

```
### Api
| 属性     | 说明             | 类型   | 默认值 |
| :------- | :--------------- | :----- | :----- |
| hrefUrl  | 下载文件接口地址 | string | -      |
| fileName | 下载文件名       | string | -      |

## 颜色选择器
颜色选择面板

### 代码演示
#### 基本使用
```vue
<template>
  <div>
    <h-color-picker v-model="borderColor" ></h-color-picker>
  </div>
</template>

<script>

import { HColorPicker } from 'jpaas-component'
export default {
  data () {
    return {
      borderColor: 'red'
    }
  },
components: {
  HColorPicker
}
}
</script>
```

### Api
| 属性    | 说明   | 类型   | 默认值 |
| :------ | :----- | :----- | :----- |
| v-model | 绑定值 | string | -      |

## 文本编辑器
可设置字体的颜色、大小、样式等信息问题一个文本编辑器

### 代码演示
#### 基本使用
```vue
<template>
<h-editor
v-model="content"
:toolbars="
  [
    'removeformat', 'autotypeset',
    '|', 'bold', 'italic', 'underline', 'forecolor', 'link', 'unlink', 'fontfamily', 'fontsize',
    '|', 'indent', 'justifyleft', 'justifycenter', 'justifyright', 'justifyjustify',
    '|', 'insertorderedlist', 'insertunorderedlist',
    '|', 'insertimg', 'insertattach', 'template',
    '|', 'customplugin','inserttable',
    'source', 'fullscreen'
  ]
"
:shortcutMenu="
  [
    'indent',
    'dbc2sb',
    'todbc'
  ]
"
:imgShortcutMenu="imgShortcutMenu"
:plugins="[$BASE_URL + 'demo/ueditor/plugins/customplugin.js']"
:pluginComponents="pluginComponents"
:pluginConfig="{
  imgUpload:{
    action: '/api-gateway/common-workflow-server/manager/business/upload-approve-pic',
    accept: '.jpg,.jpeg,.png,.gif'
  },
  imgSelect:{
    dataUrl: 'demo/selectimages',
    params: params,
    uploadAction: 'api-gateway/common-workflow-server/manager/business/upload-approve-pic',
    uploadAccept:'.jpg,.png,.gif,.svg',
    fileNumLimit:5,
    slots: {
      toolbar: 'imgToolbar'
    }
  },
  attachUpload:{
    action: '/api-gateway/common-workflow-server/manager/business/upload-approve-pic',
    accept: '.jpg,.jpeg,.png,.gif'
  },
  attachSelect:{
    dataUrl: 'demo/selectimages',
    params: params,
    uploadAction: 'api-gateway/common-workflow-server/manager/business/upload-approve-pic',
    uploadAccept:'.jpg,.png,.gif,.svg',
    fileNumLimit:5,
    slots: {
      toolbar: 'attachToolbar'
    }
  }
}"
>
</h-editor>
</template>
<script>
import { HEditor } from 'jpaas-component'
export default {
  data () {
    return {
      pluginComponents: {
        CustomPlugin: () => import('@/views/demo/HEditor/testapp/plugins/CustomPlugin')
      },
      content: content,
      params: null,
      isShow: false,
      imgShortcutMenu: [
        {
          command: 'EditPic',
          title: '编辑'
        },
        {
          command: 'SetSize',
          title: '修改尺寸'
        },
        {
          command: 'ResetSize',
          title: '恢复尺寸'
        }
      ]
    }
},
methods: {
  reset () {
    this.$reset()
  },
  modify () {
    this.content = '大汉软件'
  },
  handleChange (value, plugin) {
    plugin.query({ dataType: value })
  },
  showModal () {
    this.isShow = true
  },
  handleCancel () {
    this.isShow = false
  }
}
components: {
  HEditor
}
}
</script>
<style lang="less" scoped>
.toolbar {
  margin-top: 10px;

  .ant-btn {
    margin-right: 10px;
  }
}
</style>

```
### Api
#### props
| 参数           | 说明       | 类型    | 默认值 |
| :------------- | :--------- | :------ | :----- |
| value(v-model) | 输入的内容 | stringt | -      |
| toolbars       | 工具栏配置 | array   | -      |
| shortcutMenu   | 快捷菜单   | array   | -      |
| pluginConfig   | 插件配置项 | object  | -      |

#### 工具栏配置
- 工具栏不配置则按照默认最简化配置，文件上传只有图片、附件上传，无文件选择，可通过toolbars属性自行配置
- 最后一个按钮是插件扩展示例
- 文件上传、选择的功能配置，参考“文件上传选择”的demo和配置。若文件选择的配置不写，则只会显示上传按钮
- 快捷菜单可使用shortcutMenu属性进行配置

**工具栏完整配置：**

[

 'removeformat', 'autotypeset', 'pasteplain',

 '|', 'bold', 'italic', 'underline', 'strikethrough', 'forecolor', 'backcolor', 'link', 'unlink', 'paragraph', 'fontfamily', 'fontsize',

 '|', 'indent', 'justifyleft', 'justifycenter', 'justifyright', 'justifyjustify',

 '|', 'rowspacingtop', 'rowspacingbottom', 'lineheight',

 '|', 'insertorderedlist', 'insertunorderedlist',

 '|', 'insertimg', 'insertattach', 'insertvideo', 'map', 'template',

 '|', 'inserttable', 'tableleft', 'tablecenter', 'tableright',

 '|', 'searchreplace', 'source', 'fullscreen',

 '-', 'quicktypeset', 'autoindent', 'removeemptyline', 'clearformat',

 '|', 'dbc2sb', 'todbc',

 '|', 'pagebreak'

]

**工具栏默认配置：**

[

 'removeformat', 'autotypeset',

 '|', 'bold', 'italic', 'underline', 'forecolor', 'link', 'unlink', 'fontfamily', 'fontsize',

 '|', 'indent', 'justifyleft', 'justifycenter', 'justifyright', 'justifyjustify',

 '|', 'insertorderedlist', 'insertunorderedlist',

 'source', 'fullscreen'

]

## 图片展示
用来代表用户或事物，支持图片、图标或字符展示。

### 代码演示
#### 基本使用
```vue
<template>
  <div>
    <h-img
    :src="url"
     mode="contain"
     :style="{
      width:'100px',
      height:'100px'
     }"
    :overLoadTime="1000"
     slot="cover"
    />
  </div>
</template>
<script>
import { HImg } from 'jpaas-component'
export default {
data () {
    return {
      url: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
    }
},
components: {
  HImg
}
}
</script>
```
### Api
| 属性         | 说明             | 类型                         | 默认值 |
| :----------- | :--------------- | :--------------------------- | :----- |
| src          | 图片地址         | string                       | -      |
| mode         | 显示模式         | cover \| contain \| fitwidth | false  |
| overLoadTime | 超时控制：毫秒数 | string                       | 60000  |

## 文件选择器
文件选择

### 代码演示
#### 基本使用
基本使用。

```vue
<template>
<div>
<a-button type="primary" @click="$refs.fileSelector.excute()">选择文件</a-button>
<a-textarea :value="selectedFiles" style="margin-top:10px;height:150px;"></a-textarea>
<h-file-selector
  ref="fileSelector"
  dataUrl="demo/selectimages"
  :params="params"
  uploadAction="/api-gateway/common-workflow-server/manager/business/upload-approve-pic"
  uploadAccept=".jpg,.png,.gif,.svg"
  :fileNumLimit="5"
  @ok="handleSelect">
  <template #toolbar>
    <a-select :defaultValue="1" style="width: 120px" @change="handleChange">
      <a-select-option key="1" :value="1">网站</a-select-option>
      <a-select-option key="2" :value="2">网盘</a-select-option>
    </a-select>
  </template>
</h-file-selector>
</div>
</template>
<script>
import { HFileSelector } from 'jpaas-component'
export default {
  data () {
    return {
      selectedFiles: '',
      params: {
        dataType: 1
      }
    }
},
methods: {
  handleSelect (fileList) {
    this.selectedFiles = fileList.map((file) => {
      return file.name + ': ' + file.url
    })
  },
  handleChange (value) {
    this.$refs.fileSelector.query({ dataType: value })
  }
},
components: {
  HFileSelector
}
}
</script>
<style scoped>

</style>

```

## 对象选择器
选择不同维度的对象

### 何时使用
需要快速的完成对象的选择功能

### 代码演示
#### 基本使用
```vue
<template>
<div>
<a-button @click="select('u', false)">用户非混选</a-button>
<a-button @click="select('u', true)">用户机构混选</a-button>
<a-button @click="select('u,t', false)">用户群组非混选</a-button><br/><br/>
<a-button @click="select('g')">机构</a-button>
<a-button @click="select('t')">群组</a-button>
<a-button @click="select('d')">地区</a-button>
<a-button @click="select('w')">网站</a-button>
<a-button @click="select('r')">角色</a-button>
<a-button @click="select('m')">维度</a-button>
<h-selector
  ref="modelSelector"
  :selectedLimit="1000"
  :mix="false"
  :orgType="type"
  :title="'选择器'"
  :urlConfig="urlConfig"
  @ok="ok"></h-selector>
<h-selector
  ref="modelSelectorMix"
  :selectedLimit="1000"
  :mix="true"
  :orgType="type"
  :title="'选择器'"
  :urlConfig="urlConfig"
  @ok="ok"></h-selector>
</div>
</template>
<script>
import { HSelector } from 'jpaas-component'
export default {
  data () {
    return {
      type: '',
      mix: false,
      urlConfig: {
        dimensionList: '/common-basesettings-server/manager/dimension/list',
        districtTree: '/common-ucenter-server/manager/district/find-by-pid-keyword',
        districtList: '/common-ucenter-server/manager/selector/find-by-pid-keyword',
        groupList: '/common-ucenter-server/manager/selector/find-gorups-by-pid',
        roleList: '/common-ucenter-server/manager/selector/find-apps-and-roles',
        teamList: '/common-ucenter-server/manager/selector/find-teams',
        userList: '/common-ucenter-server/manager/selector/find-members-by-gid-keyword',
        subUersList: '/common-ucenter-server/manager/selector/find-subusers-by-groupids',
        webSiteList: '/common-basesettings-server/manager/website/list'
      },
      data: [
        {
          iid: '797f20630bcb4c2eabfce29820be4b95',
          webname: '134',
          webalias: '1232',
          status: 0,
          districtid: '4719df358d324c57859f64b6f4539cf7',
          ctime: 1586929075218,
          onlinetime: null,
          groupname: '玩儿',
          groupid: '09c38ba888104c16b2432bc2dc603d71',
          managegroupid: '09c38ba888104c16b2432bc2dc603d71',
          key: '797f20630bcb4c2eabfce29820be4b95',
          id: '797f20630bcb4c2eabfce29820be4b95',
          name: '134',
          type: 'web',
          icon: 'file-word'
        }
      ]
    }
},
methods: {
  choose (type, mix) {
    this.type = type
    this.mix = mix
    this.$refs.modelSelector.open()
  },
  select (type, mix) {
    console.log(type,'type...')
    this.type = type
    if (mix) {
      this.$refs.modelSelectorMix.open()
    } else {
      this.$refs.modelSelector.open()
    }
  },
  handleOk () {

  },
  ok (data) {
    console.log('data', data)
  }
}
components: {
  HSelector
}
}
</script>
<style scoped>
::v-deep .content > .page-header-index-wide > .ant-card > .ant-card-body{
  background: #fff;
}
</style>
```

### Api
| 属性    | 说明                                                         | 类型    | 默认值 |
| :------ | :----------------------------------------------------------- | :------ | :----- |
| title   | 选择器标题                                                   | string  | -      |
| orgType | 选择器类型 u:用户选择 d:地区选择 w:网站选择 r：角色选择 t:群组选择 | string  | u      |
| mix     | 混选模式                                                     | Boolean | false  |

## 头像
展示头像。

### 代码演示
#### 基本
头像有三种尺寸，两种形状可选。

```vue
<template>
  <div>
    <div style="margin:30px">
      <h-avatar
        :size="64"
        :src="$BASE_URL + 'images/avator.png'"
        icon="user"
      />
      <h-avatar
      size="small"
      :src="$BASE_URL + 'images/avator.png'"
      icon="user"
    />
    <h-avatar
    shape="square" size="large"
    :src="$BASE_URL + 'images/avator.png'"
    icon="user"
  />
    </div>
  </div>
</template>
<script>
import { HAvatar } from 'jpaas-component'
export default {
data () {
    return {
    }
},
components: {
  HAvatar
}
}
</script>
```

### Api
| 参数      | 说明                                                         | 类型                                          | 默认值  |
| :-------- | :----------------------------------------------------------- | :-------------------------------------------- | :------ |
| icon      | 设置头像的图标类型，可设为 Icon 的 type 或 VNode             | string \| VNode \| slot                       | -       |
| shape     | 指定头像的形状                                               | Enum{ 'circle', 'square' }                    | circle  |
| size      | 设置头像的大小                                               | number \| Enum{ 'large', 'small', 'default' } | default |
| src       | 图片类头像的资源地址                                         | string                                        | -       |
| srcSet    | 设置图片类头像响应式资源地址                                 | string                                        | -       |
| alt       | 图像无法显示时的替代文本                                     | string                                        | -       |
| loadError | 图片加载失败的事件，返回 false 会关闭组件默认的 fallback 行为 | () => boolean                                 |         |

## 表格
展示行列数据。

### 何时使用
1、当有大量结构化的数据需要展现时
2、当需要对数据进行排序、搜索、分页、自定义操作等复杂行为时

### 代码演示
#### 基本使用
简单的表格,列选择项

```vue
<template>
<h-table
ref="table"
:columns="computedColumns"
:data="loadTableData"
:rowKey="record => record.iid"
:rowSelection="{ selectedRowKeys: selectedRowKeys, onChange: onSelectChange }"
class="region-list"
>
</h-table>
</template>
<script>
import { HTable } from 'jpaas-component'
export default {
  data () {
    return {
      rowKeys:[],
      selectedRowKeys:[],
      batchOps:false,
      queryParam: {
        systemCode: '', // 类型
        originCode: '', // 类型
        applyName: '', // 办件标题检索
        transactNo: '', // 办件编号
        applyUserName: '', // 提交人
        pendingState: 0, // 办件情况检索
        applyCurrentState: 5
      },
      loadTableData:(parameter) => {
        return this.axios({
          url:'/common-workflow-server/manager/business/pending/list',
          method:'post',
          data:Object.assign(parameter, this.queryParam)
        }).then(res => {        
          return res.data
        })
      },
      computedColumns:[{
        title:'标题',
        dataIndex:'applyName',
        key:'applyName',
        width:'23%',     
      },
      {
        title:'编号',
        dataIndex:'transactNo',
        key:'transactNo',
        width:'20%'
      },
      {
        title:'提交人',
        dataIndex:'applyUserName',
        key:'applyUserName',
        customRender:this.transformLevel
      },
      {
        title:'提交时间',
        dataIndex:'ctime',
        key:'ctime',
        scopedSlots:{ customRender: 'ctime' }
  
      },
      {
        title:'类型',
        dataIndex:'originName',
        key:'originName'
      },
      {
        title:'流程节点',
        dataIndex:'currentNodeName',
        key:'currentNodeName',
        scopedSlots:{ customRender: 'currentNodeName' }
      },
      {
        title:'流程状态',
        dataIndex:'applyCurrentState',
        key:'applyCurrentState',
        scopedSlots:{ customRender: 'applyCurrentState' }
      },
      {
        title: '节点截止时间',
        dataIndex: 'planEndTime',
        key: 'planEndTime',
        scopedSlots: { customRender: 'planEndTime' }
      }]
    }
},
methods: {
  handleRowMove (rowKeys) {
    this.rowKeys = rowKeys
  },
  onSelectChange (selectedRowKeys) {
    this.selectedRowKeys = selectedRowKeys

    this.batchOps = selectedRowKeys.length > 0
  },
  // 切换批量操作模式
  toggleBatchOps () {
    this.selectedRowKeys = []
    this.selectedRows = []
    this.batchOps = !this.batchOps
  },
  edit (iid) {
    console.log('编辑当前行')
  },
  removeCurrent (iid) {
    console.log('删除当前行')
  }
},
components: {
  HTable
}
}
</script>
<style scoped>

</style>

```

#### 左右工具栏
使用插槽 #toolbarLeft / #toolbarRight 可定制表格左右工具栏

```vue
<template>
<h-table
ref="table"
:columns="computedColumns"
:data="loadTableData"
:rowKey="record => record.iid"
:rowSelection="{ selectedRowKeys: selectedRowKeys, onChange: onSelectChange }"
:showColumnSelection="true"
:acrosPageSelect="true"
class="region-list"
>
</h-table>
</template>
<script>
import { HTable } from 'jpaas-component'
export default {
  data () {
    return {
      rowKeys:[],
      selectedRowKeys:[],
      batchOps:false,
      queryParam: {
        systemCode: '', // 类型
        originCode: '', // 类型
        applyName: '', // 办件标题检索
        transactNo: '', // 办件编号
        applyUserName: '', // 提交人
        pendingState: 0, // 办件情况检索
        applyCurrentState: 5
      },
      loadTableData:(parameter) => {
        return this.axios({
          url:'/common-workflow-server/manager/business/pending/list',
          method:'post',
          data:Object.assign(parameter, this.queryParam)
        }).then(res => {        
          return res.data
        })
      },
      computedColumns:[{
        title:'标题',
        dataIndex:'applyName',
        key:'applyName',
        width:'23%',     
      },
      {
        title:'编号',
        dataIndex:'transactNo',
        key:'transactNo',
        width:'20%'
      },
      {
        title:'提交人',
        dataIndex:'applyUserName',
        key:'applyUserName',
        customRender:this.transformLevel
      },
      {
        title:'提交时间',
        dataIndex:'ctime',
        key:'ctime',
        scopedSlots:{ customRender: 'ctime' }
  
      },
      {
        title:'类型',
        dataIndex:'originName',
        key:'originName'
      },
      {
        title:'流程节点',
        dataIndex:'currentNodeName',
        key:'currentNodeName',
        scopedSlots:{ customRender: 'currentNodeName' }
      },
      {
        title:'流程状态',
        dataIndex:'applyCurrentState',
        key:'applyCurrentState',
        scopedSlots:{ customRender: 'applyCurrentState' }
      },
      {
        title: '节点截止时间',
        dataIndex: 'planEndTime',
        key: 'planEndTime',
        scopedSlots: { customRender: 'planEndTime' }
      }]
    }
},
methods: {
  handleRowMove (rowKeys) {
    this.rowKeys = rowKeys
  },
  onSelectChange (selectedRowKeys) {
    this.selectedRowKeys = selectedRowKeys

    this.batchOps = selectedRowKeys.length > 0
  },
  // 切换批量操作模式
  toggleBatchOps () {
    this.selectedRowKeys = []
    this.selectedRows = []
    this.batchOps = !this.batchOps
  },
  edit (iid) {
    console.log('编辑当前行')
  },
  removeCurrent (iid) {
    console.log('删除当前行')
  }
},
components: {
  HTable
}
}
</script>
<style scoped>

</style>

```

#### 筛选和排序
对某一列数据进行筛选，使用列的 filters 属性来指定需要筛选菜单的列，onFilter 用于筛选当前数据，filterMultiple 用于指定多选和单选。 对某一列数据进行排序，通过指定列的 sorter 函数即可启动排序按钮。sorter: function(rowA, rowB) { ... }， rowA、rowB 为比较的两个行数据。 sortDirections: ['ascend' | 'descend']改变每列可用的排序方式，切换排序时按数组内容依次切换，设置在 table props 上时对所有列生效。 使用 defaultSortOrder 属性，设置列的默认排序顺序。

```vue
<template>
<h-table
ref="table"
:columns="computedColumns"
:data="loadTableData"
:rowKey="record => record.iid"
:rowSelection="{ selectedRowKeys: selectedRowKeys, onChange: onSelectChange }"
:showColumnSelection="true"
:acrosPageSelect="true"
class="region-list"
>
</h-table>
</template>
<script>
import { HTable } from 'jpaas-component'
export default {
  data () {
    return {
      rowKeys:[],
      selectedRowKeys:[],
      batchOps:false,
      queryParam: {
        systemCode: '', // 类型
        originCode: '', // 类型
        applyName: '', // 办件标题检索
        transactNo: '', // 办件编号
        applyUserName: '', // 提交人
        pendingState: 0, // 办件情况检索
        applyCurrentState: 5
      },
      loadTableData:(parameter) => {
        return this.axios({
          url:'/common-workflow-server/manager/business/pending/list',
          method:'post',
          data:Object.assign(parameter, this.queryParam)
        }).then(res => {        
          return res.data
        })
      },
      computedColumns:[{
        title:'标题',
        dataIndex:'applyName',
        key:'applyName',
        width:'23%',     
      },
      {
        title:'编号',
        dataIndex:'transactNo',
        key:'transactNo',
        width:'20%'
      },
      {
        title:'提交人',
        dataIndex:'applyUserName',
        key:'applyUserName',
        customRender:this.transformLevel
      },
      {
        title:'提交时间',
        dataIndex:'ctime',
        key:'ctime',
        scopedSlots:{ customRender: 'ctime' }
  
      },
      {
        title:'类型',
        dataIndex:'originName',
        key:'originName'
      },
      {
        title:'流程节点',
        dataIndex:'currentNodeName',
        key:'currentNodeName',
        scopedSlots:{ customRender: 'currentNodeName' }
      },
      {
        title:'流程状态',
        dataIndex:'applyCurrentState',
        key:'applyCurrentState',
        scopedSlots:{ customRender: 'applyCurrentState' }
      },
      {
        title: '节点截止时间',
        dataIndex: 'planEndTime',
        key: 'planEndTime',
        scopedSlots: { customRender: 'planEndTime' }
      }]
    }
},
methods: {
  handleRowMove (rowKeys) {
    this.rowKeys = rowKeys
  },
  onSelectChange (selectedRowKeys) {
    this.selectedRowKeys = selectedRowKeys

    this.batchOps = selectedRowKeys.length > 0
  },
  // 切换批量操作模式
  toggleBatchOps () {
    this.selectedRowKeys = []
    this.selectedRows = []
    this.batchOps = !this.batchOps
  },
  edit (iid) {
    console.log('编辑当前行')
  },
  removeCurrent (iid) {
    console.log('删除当前行')
  }
},
components: {
  HTable
}
}
</script>
<style scoped>

</style>

```

### Api
#### Table
| 参数                   | 说明                                                         | 类型                                                         | 默认值                                                       | 版本  |
| :--------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---- |
| tableLayout            | 表格元素的 [table-layout](https://developer.mozilla.org/zh-CN/docs/Web/CSS/table-layout) 属性，设为 `fixed` 表示内容不会影响列的布局 | - \| 'auto' \| 'fixed'                                       | 无固定表头/列或使用了 `column.ellipsis` 时，默认值为 `fixed` | 1.5.0 |
| bordered               | 是否展示外边框和列边框                                       | boolean                                                      | false                                                        |       |
| childrenColumnName     | 指定树形结构的列名                                           | string[]                                                     | children                                                     |       |
| columns                | 表格列的配置描述，具体项见[下表](https://1x.antdv.com/components/table-cn/#Column) | array                                                        | -                                                            |       |
| components             | 覆盖默认的 table 元素                                        | object                                                       | -                                                            |       |
| data                   | 数据数组                                                     | any[]                                                        |                                                              |       |
| defaultExpandAllRows   | 初始时，是否展开所有行                                       | boolean                                                      | false                                                        |       |
| defaultExpandedRowKeys | 默认展开的行                                                 | string[]                                                     | -                                                            |       |
| expandedRowKeys        | 展开的行，控制属性。可用 `.sync` 后缀, 参见 [`update:expandedRowKeys`](https://1x.antdv.com/components/table-cn/#事件) | string[]                                                     | -                                                            |       |
| expandedRowRender      | 额外的展开行                                                 | Function(record, index, indent, expanded):VNode \| slot="expandedRowRender" slot-scope="record, index, indent, expanded" | -                                                            |       |
| expandIcon             | 自定义展开图标                                               | Function(props):VNode \| slot="expandIcon" slot-scope="props" | -                                                            |       |
| expandRowByClick       | 通过点击行来展开子行                                         | boolean                                                      | `false`                                                      |       |
| expandIconColumnIndex  | 展开的图标显示在哪一列，如果没有 `rowSelection`，默认显示在第一列，否则显示在选择框后面 | `number`                                                     |                                                              |       |
| footer                 | 表格尾部                                                     | Function(currentPageData)\|slot-scope                        |                                                              |       |
| indentSize             | 展示树形数据时，每层缩进的宽度，以 px 为单位                 | number                                                       | 15                                                           |       |
| loading                | 页面是否加载中                                               | boolean\|[object](https://1x.antdv.com/components/spin-cn)   | false                                                        |       |
| locale                 | 默认文案设置，目前包括排序、过滤、空数据文案                 | object                                                       | filterConfirm: '确定' filterReset: '重置' emptyText: '暂无数据' |       |
| showPagination         | 分页器，参考[配置项](https://1x.antdv.com/components/table-cn/#pagination)或 [pagination](https://1x.antdv.com/components/pagination-cn/)文档，设为 false 时不展示和进行分页 | object                                                       |                                                              |       |
| rowClassName           | 表格行的类名                                                 | Function(record, index):string                               | -                                                            |       |
| rowKey                 | 表格行 key 的取值，可以是字符串或一个函数                    | string\|Function(record):string                              | 'key'                                                        |       |
| rowSelection           | 列表项是否可选择，[配置项](https://1x.antdv.com/components/table-cn/#rowSelection) | object                                                       | null                                                         |       |
| scroll                 | 设置横向或纵向滚动，也可用于指定滚动区域的宽和高，建议为 `x` 设置一个数字，如果要设置为 `true`，需要配合样式 `.ant-table td { white-space: nowrap; }` | { x: number \| true, y: number }                             | -                                                            |       |
| showHeader             | 是否显示表头                                                 | boolean                                                      | true                                                         |       |
| size                   | 表格大小                                                     | default \| middle \| small                                   | default                                                      |       |
| title                  | 表格标题                                                     | Function(currentPageData)\|slot-scope                        |                                                              |       |
| customHeaderRow        | 设置头部行属性                                               | Function(column, index)                                      | -                                                            |       |
| customRow              | 设置行属性                                                   | Function(record, index)                                      | -                                                            |       |
| getPopupContainer      | 设置表格内各类浮层的渲染节点，如筛选菜单                     | (triggerNode) => HTMLElement                                 | `() => TableHtmlElement`                                     | 1.5.0 |
| transformCellText      | 数据渲染前可以再次改变，一般用户空数据的默认配置，可以通过 [ConfigProvider](https://1x.antdv.com/components/config-provider-cn/) 全局统一配置 | Function({ text, column, record, index }) => any             | -                                                            | 1.5.4 |
| showColumnSelection    | 是否显示列表项                                               | Boolean                                                      | false                                                        |       |
| canDrag                | 表格是否可以拖拽                                             | Boolean                                                      | false                                                        |       |

#### 事件
| 事件名称                                  | 说明                       | 回调参数                                                     |
| :---------------------------------------- | :------------------------- | :----------------------------------------------------------- |
| change                                    | 分页、排序、筛选变化时触发 | Function(pagination, filters, sorter, { currentDataSource }) |
| expand                                    | 点击展开图标时触发         | Function(expanded, record)                                   |
| expandedRowsChange update:expandedRowKeys | 展开的行变化时触发         | Function(expandedRowKeys)                                    |

##### customRow 用法
适用于 `customRow` `customHeaderRow` `customCell` `customHeaderCell`。遵循[Vue jsx](https://github.com/vuejs/babel-plugin-transform-vue-jsx)语法。

```jsx
<Table
  customRow={(record) => {
    return {
      props: {
        xxx... //属性
      },
      on: { // 事件
        click: (event) => {},       // 点击行
        dblclick: (event) => {},
        contextmenu: (event) => {},
        mouseenter: (event) => {},  // 鼠标移入行
        mouseleave: (event) => {}
      },

    };
  )}
  customHeaderRow={(column) => {
    return {
      on: {
        click: () => {},        // 点击表头行
      }
    };
  )}
/>
```

#### Column 
列描述数据对象，是 columns 中的一项，Column 使用相同的 API。

| 参数                                                         | 说明                                                         | 类型                                                         | 默认值                  | 版本  |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------------------- | :---- |
| align                                                        | 设置列内容的对齐方式                                         | 'left' \| 'right' \| 'center'                                | 'left'                  |       |
| ellipsis                                                     | 超过宽度将自动省略，暂不支持和排序筛选一起使用。 设置为 `true` 时，表格布局将变成 `tableLayout="fixed"`。 | boolean                                                      | false                   | 1.5.0 |
| colSpan                                                      | 表头列合并,设置为 0 时，不渲染                               | number                                                       |                         |       |
| dataIndex                                                    | 列数据在数据项中对应的 key，支持 `a.b.c` 的嵌套写法          | string                                                       | -                       |       |
| defaultFilteredValue                                         | 默认筛选值                                                   | string[]                                                     | -                       | 1.5.0 |
| filterDropdown                                               | 可以自定义筛选菜单，此函数只负责渲染图层，需要自行编写各种交互 | VNode \| slot-scope                                          | -                       |       |
| filterDropdownVisible                                        | 用于控制自定义筛选菜单是否可见。在 template 中可用 `.sync` 后缀, 参见 `update:filterDropdownVisible` | boolean                                                      | -                       |       |
| filtered                                                     | 标识数据是否经过过滤，筛选图标会高亮                         | boolean                                                      | false                   |       |
| filteredValue                                                | 筛选的受控属性，外界可用此控制列的筛选状态，值为已筛选的 value 数组 | string[]                                                     | -                       |       |
| filterIcon                                                   | 自定义 filter 图标。                                         | VNode \| (filtered: boolean, column: Column) => vNode \|slot \|slot-scope | false                   |       |
| filterMultiple                                               | 是否多选                                                     | boolean                                                      | true                    |       |
| filters                                                      | 表头的筛选菜单项                                             | object[]                                                     | -                       |       |
| fixed                                                        | 列是否固定，可选 `true`(等效于 left) `'left'` `'right'`      | boolean\|string                                              | false                   |       |
| key                                                          | Vue 需要的 key。如果没有使用 [template 风格的 API](https://1x.antdv.com/components/table-cn/#components-table-demo-template-style-api)，且已经设置了唯一的 `dataIndex`，可以忽略这个属性 | string                                                       | -                       |       |
| customRender                                                 | 生成复杂数据的渲染函数，参数分别为当前行的值，当前行数据，行索引，@return 里面可以设置表格行/列合并,可参考 demo 表格行/列合并 | Function(text, record, index) {}\|slot-scope                 | -                       |       |
| sorter                                                       | 排序函数，本地排序使用一个函数(参考 [Array.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) 的 compareFunction)，需要服务端排序可设为 true | Function\|boolean                                            | -                       |       |
| sortOrder                                                    | 排序的受控属性，外界可用此控制列的排序，可设置为 `'ascend'` `'descend'` `false` | boolean\|string                                              | -                       |       |
| sortDirections                                               | 支持的排序方式，取值为 `'ascend'` `'descend'`                | Array                                                        | `['ascend', 'descend']` | 1.5.0 |
| title                                                        | 列头显示文字                                                 | string\|slot                                                 | -                       |       |
| width                                                        | 列宽度                                                       | string\|number                                               | -                       |       |
| customCell                                                   | 设置单元格属性                                               | Function(record, rowIndex)                                   | -                       |       |
| customHeaderCell                                             | 设置头部单元格属性                                           | Function(column)                                             | -                       |       |
| onFilter                                                     | 本地模式下，确定筛选的运行函数, 使用 template 或 jsx 时作为`filter`事件使用 | Function                                                     | -                       |       |
| onFilterDropdownVisibleChange @filterDropdownVisibleChange @update:filterDropdownVisible | 自定义筛选菜单可见`filterDropdownVisible`变化时调用，使用 template 或 jsx 时作为`filterDropdownVisibleChange`或`update:filterDropdownVisible`事件使用 | function(visible) {}                                         | -                       |       |
| slots                                                        | 使用 columns 时，可以通过该属性配置支持 slot 的属性，如 `slots: { filterIcon: 'XXX'}` | object                                                       | -                       |       |
| scopedSlots                                                  | 使用 columns 时，可以通过该属性配置支持 slot-scope 的属性，如 `scopedSlots: { customRender: 'XXX'}` | object                                                       | -                       |       |

#### ColumnGroup 
| 参数  | 说明                                                         | 类型            | 默认值 |
| :---- | :----------------------------------------------------------- | :-------------- | :----- |
| title | 列头显示文字                                                 | string\|slot    | -      |
| fixed | 列是否固定，可选 `true`(等效于 left) `'left'` `'right'`      | boolean\|string | false  |
| slots | 使用 columns 时，可以通过该属性配置支持 slot 的属性，如 `slots: { title: 'XXX'}` | object          | -      |

#### pagination 
分页的配置项。

| 参数     | 说明               | 类型                        | 默认值   |
| :------- | :----------------- | :-------------------------- | :------- |
| position | 指定分页显示的位置 | 'top' \| 'bottom' \| 'both' | 'bottom' |

更多配置项，请查看 [`Pagination`](https://1x.antdv.com/components/pagination/)。

#### rowSelection
选择功能的配置。

| 参数                  | 说明                                            | 类型                                                  | 默认值     |
| :-------------------- | :---------------------------------------------- | :---------------------------------------------------- | :--------- |
| columnWidth           | 自定义列表选择框宽度                            | string\|number                                        | -          |
| columnTitle           | 自定义列表选择框标题                            | string\|VNode                                         | -          |
| fixed                 | 把选择框列固定在左边                            | boolean                                               | -          |
| getCheckboxProps      | 选择框的默认属性配置                            | Function(record)                                      | -          |
| hideDefaultSelections | 去掉『全选』『反选』两个默认选项                | boolean                                               | false      |
| selectedRowKeys       | 指定选中项的 key 数组，需要和 onChange 进行配合 | string[]                                              | []         |
| selections            | 自定义选择配置项, 设为 `true` 时使用默认选择项  | object[]\|boolean                                     | -          |
| type                  | 多选/单选，`checkbox` or `radio`                | string                                                | `checkbox` |
| onChange              | 选中项发生变化时的回调                          | Function(selectedRowKeys, selectedRows)               | -          |
| onSelect              | 用户手动选择/取消选择某列的回调                 | Function(record, selected, selectedRows, nativeEvent) | -          |
| onSelectAll           | 用户手动选择/取消选择所有列的回调               | Function(selected, selectedRows, changeRows)          | -          |
| onSelectInvert        | 用户手动选择反选的回调                          | Function(selectedRows)                                | -          |

#### scroll 
| 参数                     | 说明                                                         | 类型           | 默认值 | 版本  |
| :----------------------- | :----------------------------------------------------------- | :------------- | :----- | :---- |
| x                        | 设置横向滚动，也可用于指定滚动区域的宽和高，可以设置为像素值，百分比，true 和 ['max-content'](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width#max-content) | number \| true | -      |       |
| y                        | 设置纵向滚动，也可用于指定滚动区域的宽和高，可以设置为像素值，百分比，true 和 ['max-content'](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width#max-content) | number \| true | -      |       |
| scrollToFirstRowOnChange | 当分页、排序、筛选变化后是否滚动到表格顶部                   | boolean        | -      | 1.5.0 |

#### selection 
自定义选择配置项

| 参数     | 说明                     | 类型                        | 默认值 |
| :------- | :----------------------- | :-------------------------- | :----- |
| key      | Vue 需要的 key，建议设置 | string                      | -      |
| text     | 选择项显示的文字         | string\|VNode               | -      |
| onSelect | 选择项点击回调           | Function(changeableRowKeys) | -      |

### 注意 
在 Table 中，`dataSource` 和 `columns` 里的数据值都需要指定 `key` 值。对于 `dataSource` 默认将每列数据的 `key` 属性作为唯一的标识。

如果你的数据没有这个属性，务必使用 `rowKey` 来指定数据列的主键。若没有指定，控制台会出现缺少 key 的提示，表格组件也会出现各类奇怪的错误。

```jsx
// 比如你的数据主键是 uid
return <Table rowKey="uid" />;
// 或
return <Table rowKey={record => record.uid} />;
```

## 工具条
综合各种工具,让用户方便使用的一个区域。

### 何时使用
通常配合表格一起使用，左侧为操作按钮区，右侧为检索区

### 代码演示
#### 基本使用
```VUE
<template>
<h-toolbar>
<template #toolbarLeft>
  <a-button type="primary" >操作</a-button>
</template>
<template #toolbarRight>
  <a-input-search placeholder="请输入关键字" style="width:200px"/>
</template>
</h-toolbar>
</template>
<script>
import { HToolbar } from 'jpaas-component'
export default {
  data () {
    return {
    }
},
components: {
  HToolbar
}
}
</script>
<style scoped>

</style>

```

## 树形控件
用来代表用户或事物，支持图片、图标或字符展示。

### 何时使用
通常配合表格使用，可以完整展现其中的层级关系，并具有展开收起选择等交互功能。

### 代码演示
#### 基本使用
```vue
<template>
<h-tree
ref="hTree"
:defaultTreeData="defaultTreeData"
:root="defaultTreeDataMap"
:pid="pid"
:treeDataAjax="treeDataAjax"
:defaultExpandedKeys="defaultExpandedKeys"
:expandedKeys="expandedKeys"
:expandAction="expandAction"
:decorate="decorate"
:defaultSelectedKeys="defaultSelectedKeys"
:selectedKeys="selectedKeys"
@treeSelectChange="treeSelectChange"
>
</h-tree>
</template>
<script>
import { HTree } from 'jpaas-component'
export default {
  data () {
    return {
      defaultTreeData:[],
      defaultTreeDataMap:{},
      pid:'',
      defaultExpandedKeys:[],
      defaultSelectedKeys:[],
      expandedKeys:[],
      expandAction:false,
      decorate:{
        'padding-left':'10px'
      },
      rootData:{
        key: '0',
        title: '全部分类',
        'children': []
      }
    }
},
created () {
  this.pid = '0'
  this.defaultExpandedKeys = [this.pid] // 默认展开的树节点
  this.defaultSelectedKeys = [this.pid]
  this.defaultTreeData = [this.rootData]
  this.defaultTreeDataMap[this.pid] = this.rootData
  this.selectedKeys = [this.pid]
},
methods: {
  treeDataAjax (pid) {
    return this.axios({
      //url: '/flow/pendingList',
      url:'/common-ucenter-server/manager/district/find-by-pid-keyword',
      method: 'get',
      params: {pid:pid}
    })
  },
  // 点击树节点时，接收来自子组件中改变的pid
  treeSelectChange (selectedKeys, { selectedNodes }) {
    this.treeObject = selectedNodes.length === 0 ? {} : selectedNodes[0].data.props.dataRef
    this.$refs.table.clearSelected(true)
    this.pid = selectedKeys[0]
    this.selectedKeys = selectedKeys
    this.pid = this.pid === '0' ? '' : this.pid
    this.queryParam.categoryId = this.pid
    this.queryParam.regionId = this.defaultAreaId
    this.$refs.table.refresh(true)
  }
}
components: {
  HTree
}
}
</script>
<style scoped>

</style>

```
### Api
| 属性                | 说明                                       | 类型     | 默认值 |
| :------------------ | :----------------------------------------- | :------- | :----- |
| pid                 | 对应节点的父节点                           | string   | -      |
| defaultExpandedKeys | （受控）展开指定的树节点                   | Array    | -      |
| defaultTreeData     | 树的数据源                                 | Array    | -      |
| root                | 树的数据源转化                             | Array    | -      |
| treeDataAjax        | api接口                                    | Function | -      |
| expandAction        | 目录展开逻辑，可选 false click doubleclick | string   | -      |
| decorate            | 传给Tree组件的样式                         | Object   | -      |
| defaultSelectedKeys | （受控）设置选中的树节点                   | Array    | -      |
| treeSelectChange    | 点击树节点的回调                           | Function | -      |

#### Tree props 
| 参数                 | 说明                                                         | 类型                                                         | 默认值                                           | 版本  |
| :------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------- | :---- |
| blockNode            | 是否节点占据一行                                             | boolean                                                      | false                                            | 1.5.0 |
| treeData             | treeNodes 数据，如果设置则不需要手动构造 TreeNode 节点（key 在整个树范围内唯一） | array<{key, title, children, [disabled, selectable]}>        | --                                               |       |
| replaceFields        | 替换 treeNode 中 title,key,children 字段为 treeData 中对应的字段 | object                                                       | {children:'children', title:'title', key:'key' } |       |
| autoExpandParent     | 是否自动展开父节点                                           | boolean                                                      | true                                             |       |
| checkable            | 节点前添加 Checkbox 复选框                                   | boolean                                                      | false                                            |       |
| checkedKeys(v-model) | （受控）选中复选框的树节点（注意：父子节点有关联，如果传入父节点 key，则子节点自动选中；相应当子节点 key 都传入，父节点也自动选中。当设置`checkable`和`checkStrictly`，它是一个有`checked`和`halfChecked`属性的对象，并且父子节点的选中与否不再关联 | string[] \| number[] \| {checked: string[] \| number[], halfChecked: string[] \| number[]} | []                                               |       |
| checkStrictly        | checkable 状态下节点选择完全受控（父子节点选中状态不再关联） | boolean                                                      | false                                            |       |
| defaultCheckedKeys   | 默认选中复选框的树节点                                       | string[] \| number[]                                         | []                                               |       |
| defaultExpandAll     | 默认展开所有树节点                                           | boolean                                                      | false                                            |       |
| defaultExpandedKeys  | 默认展开指定的树节点                                         | string[] \| number[]                                         | []                                               |       |
| defaultExpandParent  | 默认展开父节点                                               | bool                                                         | true                                             |       |
| defaultSelectedKeys  | 默认选中的树节点                                             | string[] \| number[]                                         | []                                               |       |
| disabled             | 将树禁用                                                     | bool                                                         | false                                            |       |
| draggable            | 设置节点可拖拽                                               | boolean                                                      | false                                            |       |
| expandedKeys(.sync)  | （受控）展开指定的树节点                                     | string[] \| number[]                                         | []                                               |       |
| filterTreeNode       | 按需筛选树节点（高亮），返回 true                            | function(node)                                               | -                                                |       |
| loadData             | 异步加载数据                                                 | function(node)                                               | -                                                |       |
| loadedKeys           | （受控）已经加载的节点，需要配合 `loadData` 使用             | string[] \| number[]                                         | []                                               |       |
| multiple             | 支持点选多个节点（节点本身）                                 | boolean                                                      | false                                            |       |
| selectable           | 是否可选中                                                   | boolean                                                      | true                                             |       |
| selectedKeys(.sync)  | （受控）设置选中的树节点                                     | string[] \| number[]                                         | -                                                |       |
| showIcon             | 是否展示 TreeNode title 前的图标，没有默认样式，如设置为 true，需要自行定义图标相关样式 | boolean                                                      | false                                            |       |
| switcherIcon         | 自定义树节点的展开/折叠图标                                  | slot                                                         | -                                                |       |
| showLine             | 是否展示连接线                                               | boolean                                                      | false                                            |       |
| title                | 标题                                                         | slot                                                         |                                                  |       |

#### 事件 
| 事件名称   | 说明                 | 回调参数                                                     |
| :--------- | :------------------- | :----------------------------------------------------------- |
| check      | 点击复选框触发       | function(checkedKeys, e:{checked: bool, checkedNodes, node, event}) |
| dragend    | dragend 触发时调用   | function({event, node})                                      |
| dragenter  | dragenter 触发时调用 | function({event, node, expandedKeys})                        |
| dragleave  | dragleave 触发时调用 | function({event, node})                                      |
| dragover   | dragover 触发时调用  | function({event, node})                                      |
| dragstart  | 开始拖拽时调用       | function({event, node})                                      |
| drop       | drop 触发时调用      | function({event, node, dragNode, dragNodesKeys})             |
| expand     | 展开/收起节点时触发  | function(expandedKeys, {expanded: bool, node})               |
| load       | 节点加载完毕时触发   | function(loadedKeys, {event, node})                          |
| rightClick | 响应右键点击         | function({event, node})                                      |
| select     | 点击树节点触发       | function(selectedKeys, e:{selected: bool, selectedNodes, node, event}) |

#### TreeNode props 
结点描述数据对象，是 treeNodes 中的一项，TreeNode 使用相同的 API。

| 参数            | 说明                                                         | 类型                     | 默认值               | 版本  |
| :-------------- | :----------------------------------------------------------- | :----------------------- | :------------------- | :---- |
| class           | 节点的 class                                                 | string                   | -                    |       |
| style           | 节点的 style                                                 | string\|object           | -                    |       |
| checkable       | 当树为 checkable 时，设置独立节点是否展示 Checkbox           | boolean                  | -                    | 1.5.0 |
| disableCheckbox | 禁掉 checkbox                                                | boolean                  | false                |       |
| disabled        | 禁掉响应                                                     | boolean                  | false                |       |
| icon            | 自定义图标。可接收组件，props 为当前节点 props               | slot\|slot-scope         | -                    |       |
| isLeaf          | 设置为叶子节点(设置了`loadData`时有效)                       | boolean                  | false                |       |
| key             | 被树的 (default)ExpandedKeys / (default)CheckedKeys / (default)SelectedKeys 属性所用。注意：整个树范围内的所有节点的 key 值不能重复！ | string \| number         | 内部计算出的节点位置 |       |
| selectable      | 设置节点是否可被选中                                         | boolean                  | true                 |       |
| title           | 标题                                                         | string\|slot\|slot-scope | '---'                |       |
| slots           | 使用 treeNodes 时，可以通过该属性配置支持 slot 的属性，如 `slots: { title: 'XXX'}` | object                   | -                    |       |
| scopedSlots     | 使用 columns 时，可以通过该属性配置支持 slot-scope 的属性，如 `scopedSlots: { title: 'XXX'}` | object                   | -                    |       |
| on              | 事件对象，仅在 treeNodes 使用方式中生效，如`{click: () => {}}` | object                   | '---'                |       |

#### DirectoryTree props 
| 参数         | 说明                                              | 类型   | 默认值 |
| :----------- | :------------------------------------------------ | :----- | :----- |
| expandAction | 目录展开逻辑，可选 `false` `'click'` `'dblclick'` | string | click  |

## 模态对话框/弹窗
模态对话框。

### 何时使用
- 需要用户处理事务，又不希望跳转页面以致打断工作流程时，可以使用 Modal 在当前页面正中打开一个浮层，承载相应的操作。 另外当需要一个简洁的确认框询问用户时，可以使用 Modal.confirm() 等语法糖方法。。

### 代码演示
#### 点击上传
经典款式，用户点击按钮弹出文件选择框。

```vue
<template>
  <div>
  <a-button type="primary" @click="openModal">弹框</a-button>
  <h-modal
  :visible="visible"
  :width="470"
  title="添加条件"
  okText="保存"
  @ok="handleOk"
  @cancel="hideModal"
>
  <div>我是弹框</div>
</h-modal>
  </div>
</template>
<script>
import { HModal } from 'jpaas-component'
export default {
  data () {
    return {
      visible: false
    }
},
methods: {
  openModal () {
    this.visible = true
  },
  // 弹框确定按钮操作
  handleOk () {
    this.visible = false
  },
  // 弹框关闭以及取消按钮操作
  hideModal () {
    this.visible = false
  }
}
components: {
  HModal
}
}
</script>
<style scoped>

</style>

```

### Api
| 参数              | 说明                                                         | 类型                                                         | 默认值              | 版本  |
| :---------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------ | :---- |
| afterClose        | Modal 完全关闭后的回调                                       | function                                                     | 无                  |       |
| bodyStyle         | Modal body 样式                                              | object                                                       | {}                  |       |
| cancelText        | 取消按钮文字                                                 | string\| slot                                                | 取消                |       |
| centered          | 垂直居中展示 Modal                                           | Boolean                                                      | `false`             |       |
| closable          | 是否显示右上角的关闭按钮                                     | boolean                                                      | true                |       |
| closeIcon         | 自定义关闭图标                                               | VNode \| slot                                                | -                   | 1.5.0 |
| confirmLoading    | 确定按钮 loading                                             | boolean                                                      | 无                  |       |
| destroyOnClose    | 关闭时销毁 Modal 里的子元素                                  | boolean                                                      | false               |       |
| footer            | 底部内容，当不需要默认底部按钮时，可以设为 `:footer="null"`  | string\|slot                                                 | 确定取消按钮        |       |
| forceRender       | 强制渲染 Modal                                               | boolean                                                      | false               |       |
| getContainer      | 指定 Modal 挂载的 HTML 节点                                  | (instance): HTMLElement                                      | () => document.body |       |
| keyboard          | 是否支持键盘 esc 关闭                                        | boolean                                                      | true                |       |
| mask              | 是否展示遮罩                                                 | Boolean                                                      | true                |       |
| maskClosable      | 点击蒙层是否允许关闭                                         | boolean                                                      | true                |       |
| maskStyle         | 遮罩样式                                                     | object                                                       | {}                  |       |
| okText            | 确认按钮文字                                                 | string\|slot                                                 | 确定                |       |
| okType            | 确认按钮类型                                                 | string                                                       | primary             |       |
| okButtonProps     | ok 按钮 props, 遵循 jsx[规范](https://github.com/vuejs/babel-plugin-transform-vue-jsx#difference-from-react-jsx) | {props: [ButtonProps](https://1x.antdv.com/components/button/#API), on: {}} | -                   |       |
| cancelButtonProps | cancel 按钮 props, 遵循 jsx[规范](https://github.com/vuejs/babel-plugin-transform-vue-jsx#difference-from-react-jsx) | {props: [ButtonProps](https://1x.antdv.com/components/button/#API), on: {}} | -                   |       |
| title             | 标题                                                         | string\|slot                                                 | 无                  |       |
| visible(v-model)  | 对话框是否可见                                               | boolean                                                      | 无                  |       |
| width             | 宽度                                                         | string\|number                                               | 520                 |       |
| wrapClassName     | 对话框外层容器的类名                                         | string                                                       | -                   |       |
| zIndex            | 设置 Modal 的 `z-index`                                      | Number                                                       | 1000                |       |
| dialogStyle       | 可用于设置浮层的样式，调整浮层位置等                         | object                                                       | -                   | 1.6.1 |
| dialogClass       | 可用于设置浮层的类名                                         | string                                                       | -                   | 1.6.1 |

#### 事件 
| 事件名称 | 说明                                 | 回调参数    |
| :------- | :----------------------------------- | :---------- |
| cancel   | 点击遮罩层或右上角叉或取消按钮的回调 | function(e) |
| ok       | 点击确定回调                         | function(e) |

##### 注意 
> `<Modal />` 默认关闭后状态不会自动清空, 如果希望每次打开都是新内容，请设置 `destroyOnClose`。

#### Modal.method() 
包括：

- `Modal.info`
- `Modal.success`
- `Modal.error`
- `Modal.warning`
- `Modal.confirm`

以上均为一个函数，参数为 object，具体属性如下：

| 参数              | 说明                                                         | 类型                                                  | 默认值                          | 版本   |
| :---------------- | :----------------------------------------------------------- | :---------------------------------------------------- | :------------------------------ | :----- |
| autoFocusButton   | 指定自动获得焦点的按钮                                       | null\|string: `ok` `cancel`                           | `ok`                            |        |
| cancelText        | 取消按钮文字                                                 | string                                                | 取消                            |        |
| centered          | 垂直居中展示 Modal                                           | Boolean                                               | `false`                         |        |
| closable          | 是否显示右上角的关闭按钮                                     | boolean                                               | `false`                         |        |
| class             | 容器类名                                                     | string                                                | -                               |        |
| content           | 内容                                                         | string \|vNode \|function(h)                          | 无                              |        |
| icon              | 自定义图标（1.14.0 新增）                                    | string\|()=>VNode                                     | `<Icon type="question-circle">` |        |
| iconType          | 图标类型（1.14.0 后废弃，请使用 `icon`）                     | string                                                | `question-circle`               |        |
| mask              | 是否展示遮罩                                                 | Boolean                                               | true                            |        |
| maskClosable      | 点击蒙层是否允许关闭                                         | Boolean                                               | `false`                         |        |
| keyboard          | 是否支持键盘 esc 关闭                                        | boolean                                               | true                            |        |
| okText            | 确认按钮文字                                                 | string                                                | 确定                            |        |
| okType            | 确认按钮类型                                                 | string                                                | primary                         |        |
| okButtonProps     | ok 按钮 props                                                | [ButtonProps](https://1x.antdv.com/components/button) | -                               |        |
| cancelButtonProps | cancel 按钮 props                                            | [ButtonProps](https://1x.antdv.com/components/button) | -                               |        |
| title             | 标题                                                         | string\|vNode \|function(h)                           | 无                              |        |
| width             | 宽度                                                         | string\|number                                        | 416                             |        |
| zIndex            | 设置 Modal 的 `z-index`                                      | Number                                                | 1000                            |        |
| onCancel          | 取消回调，参数为关闭函数，返回 promise 时 resolve 后自动关闭 | function                                              | 无                              |        |
| onOk              | 点击确定回调，参数为关闭函数，返回 promise 时 resolve 后自动关闭 | function                                              | 无                              |        |
| parentContext     | 弹窗的父级上下文，一般用于获取父级 provider， 如获取 `ConfigProvider` 的配置 | vue instance                                          | -                               | 1.4.11 |

以上函数调用后，会返回一个引用，可以通过该引用更新和关闭弹窗。

```jsx
const modal = Modal.info();

modal.update({
  title: '修改的标题',
  content: '修改的内容',
});

modal.destroy();
```

- `Modal.destroyAll`

使用 `Modal.destroyAll()` 可以销毁弹出的确认窗（即上述的 Modal.info、Modal.success、Modal.error、Modal.warning、Modal.confirm）。通常用于路由监听当中，处理路由前进、后退不能销毁确认对话框的问题，而不用各处去使用实例的返回值进行关闭（modal.destroy() 适用于主动关闭，而不是路由这样被动关闭）

```jsx
const router = new VueRouter({ ... })

// router change
router.beforeEach((to, from, next) => {
  Modal.destroyAll();
})
```

## 布局
24 栅格系统。

### 设计理念
在多数业务情况下，Ant Design Vue 需要在设计区域内解决大量信息收纳的问题，因此在 12 栅格系统的基础上，我们将整个设计建议区域按照 24 等分的原则进行划分。  
划分之后的信息区块我们称之为『盒子』。建议横向排列的盒子数量最多四个，最少一个。『盒子』在整个屏幕上占比见上图。设计部分基于盒子的单位定制盒子内部的排版规则，以保证视觉层面的舒适感。

### 概述
布局的栅格化系统，我们是基于行（row）和列（col）来定义信息区块的外部框架，以保证页面的每个区域能够稳健地排布起来。下面简单介绍一下它的工作原理：

-   通过`row`在水平方向建立一组`column`（简写col）
-   你的内容应当放置于`col`内，并且，只有`col`可以作为`row`的直接元素
-   栅格系统中的列是指 1 到 24 的值来表示其跨越的范围。例如，三个等宽的列可以使用 `<h-col :span="8" />` 来创建
-   如果一个`row`中的`col`总和超过 24，那么多余的`col`会作为一个整体另起一行排列

### Flex 布局
    我们的栅格化系统支持 Flex 布局，允许子元素在父节点内的水平对齐方式 - 居左、居中、居右、等宽排列、分散排列。子元素与子元素之间，支持顶部对齐、垂直居中对齐、底部对齐的方式。同时，支持使用 order 来定义元素的排列顺序。  
    Flex 布局是基于 24 栅格来定义每一个『盒子』的宽度，但不拘泥于栅格。

### 代码演示

#### 基础栅格
从堆叠到水平排列。  
使用单一的一组 `Row` 和 `Col` 栅格组件，就可以创建一个基本的栅格系统，所有列（Col）必须放在 `Row` 内。  

```vue
<template>
  <div>
    <h-row>
      <h-col :span="12">
        col-12
      </h-col>
      <h-col :span="12">
        col-12
      </h-col>
    </h-row>
    <h-row>
      <h-col :span="8">
        col-8
      </h-col>
      <h-col :span="8">
        col-8
      </h-col>
      <h-col :span="8">
        col-8
      </h-col>
    </h-row>
    <h-row>
      <h-col :span="6">
        col-6
      </h-col>
      <h-col :span="6">
        col-6
      </h-col>
      <h-col :span="6">
        col-6
      </h-col>
      <h-col :span="6">
        col-6
      </h-col>
    </h-row>
  </div>
</template>

```

#### Flex 对齐
Flex 子元素垂直对齐。

```vue
<template>
  <div>
    <p>Align Top</p>
    <h-row type="flex" justify="center" align="top">
      <h-col :span="4">
        <p class="height-100">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-50">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-120">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-80">
          col-4
        </p>
      </h-col>
    </h-row>

    <p>Align Center</p>
    <h-row type="flex" justify="space-around" align="middle">
      <h-col :span="4">
        <p class="height-100">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-50">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-120">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-80">
          col-4
        </p>
      </h-col>
    </h-row>

    <p>Align Bottom</p>
    <h-row type="flex" justify="space-between" align="bottom">
      <h-col :span="4">
        <p class="height-100">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-50">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-120">
          col-4
        </p>
      </h-col>
      <h-col :span="4">
        <p class="height-80">
          col-4
        </p>
      </h-col>
    </h-row>
  </div>
</template>

```

#### Flex 排序 
从堆叠到水平排列。  
通过 Flex 布局的 Order 来改变元素的排序。  

```vue
<template>
  <div>
    <h-row type="flex">
      <h-col :span="6" :order="4">
        1 col-order-4
      </h-col>
      <h-col :span="6" :order="3">
        2 col-order-3
      </h-col>
      <h-col :span="6" :order="2">
        3 col-order-2
      </h-col>
      <h-col :span="6" :order="1">
        4 col-order-1
      </h-col>
    </h-row>
  </div>
</template>

```

#### Flex 布局
Flex 布局基础。  
使用 `row-flex` 定义 `flex` 布局，其子元素根据不同的值 `start`,`center`,`end`,`space-between`,`space-around`，分别定义其在父节点里面的排版方式。  

```vue
<template>
  <div>
    <p>sub-element align left</p>
    <h-row type="flex" justify="start">
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
    </h-row>

    <p>sub-element align center</p>
    <h-row type="flex" justify="center">
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
    </h-row>

    <p>sub-element align right</p>
    <h-row type="flex" justify="end">
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
    </h-row>

    <p>sub-element monospaced arrangement</p>
    <h-row type="flex" justify="space-between">
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
    </h-row>

    <p>sub-element align full</p>
    <h-row type="flex" justify="space-around">
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
      <h-col :span="4">
        col-4
      </h-col>
    </h-row>
  </div>
</template>

```

#### Flex 填充
Col 提供 `flex` 属性以支持填充。

```vue
<template>
  <div>
    <h-divider orientation="left">
      Percentage columns
    </h-divider>
    <h-row type="flex">
      <h-col :flex="2">2 / 5</h-col>
      <h-col :flex="3">3 / 5</h-col>
    </h-row>
    <h-divider orientation="left">
      Fill rest
    </h-divider>
    <h-row type="flex">
      <h-col flex="100px">100px</h-col>
      <h-col flex="auto">auto</h-col>
    </h-row>
    <h-divider orientation="left">
      Raw flex style
    </h-divider>
    <h-row type="flex">
      <h-col flex="1 1 200px">1 1 200px</h-col>
      <h-col flex="0 1 300px">0 1 300px</h-col>
    </h-row>
  </div>
</template>

```

#### 区块间隔
栅格常常需要和间隔进行配合，你可以使用 `Row` 的 `gutter` 属性，我们推荐使用 `(16+8n)px` 作为栅格间隔。(n 是自然数)  
如果要支持响应式，可以写成 `{ xs: 8, sm: 16, md: 24, lg: 32 }`。  
如果需要垂直间距，可以写成数组形式 `[水平间距, 垂直间距]` `[16, { xs: 8, sm: 16, md: 24, lg: 32 }]`。

> 数组形式垂直间距在 `1.5.0` 之后支持。

```vue
<template>
  <div class="gutter-example">
    <h-row :gutter="16">
      <h-col class="gutter-row" :span="6">
        <div class="gutter-box">
          col-6
        </div>
      </h-col>
      <h-col class="gutter-row" :span="6">
        <div class="gutter-box">
          col-6
        </div>
      </h-col>
      <h-col class="gutter-row" :span="6">
        <div class="gutter-box">
          col-6
        </div>
      </h-col>
      <h-col class="gutter-row" :span="6">
        <div class="gutter-box">
          col-6
        </div>
      </h-col>
    </h-row>
  </div>
</template>
<style scoped>
.gutter-example >>> .ant-row > div {
  background: transparent;
  border: 0;
}
.gutter-box {
  background: #00a0e9;
  padding: 5px 0;
}
</style>

```

#### 左右偏移
列偏移。  
使用 `offset` 可以将列向右侧偏。例如，`:offset="4"` 将元素向右侧偏移了 4 个列（column）的宽度。  

```vue
<template>
  <div>
    <h-row>
      <h-col :span="8">
        col-8
      </h-col>
      <h-col :span="8" :offset="8">
        col-8
      </h-col>
    </h-row>
    <h-row>
      <h-col :span="6" :offset="6">
        col-6 col-offset-6
      </h-col>
      <h-col :span="6" :offset="6">
        col-6 col-offset-6
      </h-col>
    </h-row>
    <h-row>
      <h-col :span="12" :offset="6">
        col-12 col-offset-6
      </h-col>
    </h-row>
  </div>
</template>

```

#### 其他属性的响应式
`span` `pull` `push` `offset` `order` 属性可以通过内嵌到 `xs` `sm` `md` `lg` `xl` `xxl` 属性中来使用。  
其中 `:xs="6"` 相当于 `:xs="{ span: 6 }"`。  

```vue
<template>
  <h-row>
    <h-col :xs="{ span: 5, offset: 1 }" :lg="{ span: 6, offset: 2 }">
      Col
    </h-col>
    <h-col :xs="{ span: 11, offset: 1 }" :lg="{ span: 6, offset: 2 }">
      Col
    </h-col>
    <h-col :xs="{ span: 5, offset: 1 }" :lg="{ span: 6, offset: 2 }">
      Col
    </h-col>
  </h-row>
</template>

```

#### 响应式布局
参照 Bootstrap 的 [响应式设计](http://getbootstrap.com/css/#grid-medih-queries)，预设六个响应尺寸：`xs` `sm` `md` `lg` `xl` `xxl`。

```vue
<template>
  <h-row>
    <h-col :xs="2" :sm="4" :md="6" :lg="8" :xl="10">
      Col
    </h-col>
    <h-col :xs="20" :sm="16" :md="12" :lg="8" :xl="4">
      Col
    </h-col>
    <h-col :xs="2" :sm="4" :md="6" :lg="8" :xl="10">
      Col
    </h-col>
  </h-row>
</template>

```

#### 栅格排序
列排序。  
通过使用 `push` 和 `pull` 类就可以很容易的改变列（column）的顺序。  

```vue
<template>
  <div>
    <h-row>
      <h-col :span="18" :push="6">
        col-18 col-push-6
      </h-col>
      <h-col :span="6" :pull="18">
        col-6 col-pull-18
      </h-col>
    </h-row>
  </div>
</template>

```

#### 栅格配置器
可以简单配置几种等分栅格和间距。

```vue
<template>
  <div id="components-grid-demo-playground">
    <div style="margin-bottom:16px">
      <span style="margin-right:6px">Horizontal Gutter (px): </span>
      <div style="width:50%">
        <h-slider
          v-model="gutterKey"
          :min="0"
          :max="Object.keys(gutters).length - 1"
          :marks="gutters"
          :step="null"
        />
      </div>
      <span style="margin-right: 6px">Vertical Gutter (px): </span>
      <div style="width: 50%">
        <h-slider
          v-model="vgutterKey"
          :min="0"
          :max="Object.keys(vgutters).length - 1"
          :marks="vgutters"
          :step="null"
        />
      </div>
      <span style="margin-right:6px">Column Count:</span>
      <div style="width:50%">
        <h-slider
          v-model="colCountKey"
          :min="0"
          :max="Object.keys(colCounts).length - 1"
          :marks="colCounts"
          :step="null"
        />
      </div>
    </div>
    <h-row :gutter="[gutters[gutterKey], vgutters[vgutterKey]]">
      <h-col
        v-for="(item, index) in colCounts[colCountKey]"
        :key="item.toString()"
        :span="24 / colCounts[colCountKey]"
      >
        <div>Column</div>
      </h-col>
    </h-row>
    <h-row :gutter="[gutters[gutterKey], vgutters[vgutterKey]]">
      <h-col
        v-for="(item, index) in colCounts[colCountKey]"
        :key="item.toString()"
        :span="24 / colCounts[colCountKey]"
      >
        <div>Column</div>
      </h-col>
    </h-row>
    <pre v-text="rowColHtml" />
    <pre v-text="rowColHtml" />
  </div>
</template>
<script>
export default {
  data() {
    const gutters = {};
    const colCounts = {};
    const vgutters = {};
    [8, 16, 24, 32, 40, 48].forEach((value, i) => {
      gutters[i] = value;
    });
    [8, 16, 24, 32, 40, 48].forEach((value, i) => {
      vgutters[i] = value;
    });
    [2, 3, 4, 6, 8, 12].forEach((value, i) => {
      colCounts[i] = value;
    });
    return {
      gutterKey: 1,
      vgutterKey: 1,
      colCountKey: 2,
      colCounts,
      gutters,
      vgutters,
    };
  },
  computed: {
    rowColHtml() {
      const colCount = this.colCounts[this.colCountKey];
      const getter = [this.gutters[this.gutterKey], this.vgutters[this.vgutterKey]];
      let colCode = '<h-row :gutter="[' + getter + ']">\n';
      for (let i = 0; i < colCount; i++) {
        const spanNum = 24 / colCount;
        colCode += '  <h-col :span="' + spanNum + '"/>\n';
      }
      colCode += '</h-row>';
      return colCode;
    },
  },
};
</script>
<style scoped>
#components-grid-demo-playground [class~='ant-col'] {
  background: transparent;
  border: 0;
}
#components-grid-demo-playground [class~='ant-col'] > div {
  background: #00a0e9;
  height: 120px;
  line-height: 120px;
  font-size: 13px;
}
#components-grid-demo-playground pre {
  background: #f9f9f9;
  border-radius: 6px;
  font-size: 13px;
  padding: 8px 16px;
}
</style>

```

### API
#### Row
| 成员    | 说明                                                         | 类型                | 默认值  |
| :------ | :----------------------------------------------------------- | :------------------ | :------ |
| align   | flex 布局下的垂直对齐方式：`top` `middle` `bottom`           | string              | `top`   |
| gutter  | 栅格间隔，可以写成像素值或支持响应式的对象写法来设置水平间隔 `{ xs: 8, sm: 16, md: 24}`。或者使用数组形式同时设置 `[水平间距, 垂直间距]`（`1.5.0 后支持`）。 | number/object/array | 0       |
| justify | flex 布局下的水平排列方式：`start` `end` `center` `space-around` `space-between` | string              | `start` |
| type    | 布局模式，可选 `flex`，[现代浏览器](http://caniuse.com/#search=flex) 下有效 | string              |         |

#### Col
| 成员   | 说明                                                     | 类型           | 默认值 |
| :----- | :------------------------------------------------------- | :------------- | :----- |
| flex   | flex 布局填充                                            | string\|number | -      |
| offset | 栅格左侧的间隔格数，间隔内不可以有栅格                   | number         | 0      |
| order  | 栅格顺序，`flex` 布局模式下有效                          | number         | 0      |
| pull   | 栅格向左移动格数                                         | number         | 0      |
| push   | 栅格向右移动格数                                         | number         | 0      |
| span   | 栅格占位格数，为 0 时相当于 `display: none`              | number         | -      |
| xs     | `<576px` 响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object | -      |
| sm     | `≥576px` 响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object | -      |
| md     | `≥768px` 响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object | -      |
| lg     | `≥992px` 响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object | -      |
| xl     | `≥1200px` 响应式栅格，可为栅格数或一个包含其他属性的对象 | number\|object | -      |
| xxl    | `≥1600px` 响应式栅格，可为栅格数或一个包含其他属性的对象 | number\|object | -      |

## 间距
设置组件之间的间距。

### 何时使用
避免组件紧贴在一起，拉开统一的空间。

- 适合行内元素的水平间距。

- 可以设置各种水平对齐方式。

### 代码演示
##### 基本用法
相邻组件水平间距。

```html
<template>
  <h-space>
    Space
    <h-button type="primary">Button</h-button>
    <h-upload>
      <h-button> <h-icon type="upload" /> Click to Upload </h-button>
    </h-upload>
    <h-popconfirm title="Are you sure delete this task?" ok-text="Yes" cancel-text="No">
      <h-button>Confirm</h-button>
    </h-popconfirm>
  </h-space>
</template>
<script>
export default {};
</script>
```
##### 垂直间距
相邻组件垂直间距。
可以设置 `width: 100%` 独占一行。

```html
<template>
  <h-space direction="vertical">
    <h-card title="Card" style="width: 300px;">
      <p>Card content</p>
      <p>Card content</p>
    </h-card>
    <h-card title="Card" style="width: 300px;">
      <p>Card content</p>
      <p>Card content</p>
    </h-card>
  </h-space>
</template>
<script>
export default {};
</script>
```
##### 间距大小 
间距预设大、中、小三种大小。
通过设置 `size` 为 `large` `middle` 分别把间距设为大、中间距。若不设置 `size`，则间距为小。

```html
<template>
  <div>
    <h-radio-group v-model="size">
      <h-radio value="small">Small</h-radio>
      <h-radio value="middle">Middle</h-radio>
      <h-radio value="large">Large</h-radio>
    </h-radio-group>
    <br />
    <br />
    <h-space :size="size">
      <h-button type="primary">Primary</h-button>
      <h-button>Default</h-button>
      <h-button type="dashed">Dashed</h-button>
      <h-button type="link">Link</h-button>
    </h-space>
  </div>
</template>
<script>
export default {
  data() {
    return {
      size: 'small',
    };
  },
};
</script>
```
##### 对齐 
设置对齐模式。

```html
<template>
  <div class="space-align-container">
    <div class="space-align-block">
      <h-space align="center">
        center
        <h-button type="primary">Primary</h-button>
        <span class="mock-block">Block</span>
      </h-space>
    </div>
    <div class="space-align-block">
      <h-space align="start">
        start
        <h-button type="primary">Primary</h-button>
        <span class="mock-block">Block</span>
      </h-space>
    </div>
    <div class="space-align-block">
      <h-space align="end">
        end
        <h-button type="primary">Primary</h-button>
        <span class="mock-block">Block</span>
      </h-space>
    </div>
    <div class="space-align-block">
      <h-space align="baseline">
        baseline
        <h-button type="primary">Primary</h-button>
        <span class="mock-block">Block</span>
      </h-space>
    </div>
  </div>
</template>
<script>
export default {};
</script>

<style scoped>
.space-align-container {
  display: flex;
  align-item: flex-start;
  flex-wrap: wrap;
}
.space-align-block {
  margin: 8px 4px;
  border: 1px solid #40a9ff;
  padding: 4px;
  flex: none;
}
.space-align-block .mock-block {
  display: inline-block;
  padding: 32px 8px 16px;
  background: rgba(150, 150, 150, 0.2);
}
</style>
```
##### 自定义尺寸
自定义间距大小。

```html
<template>
  <div>
    <h-slider v-model="size" />
    <br />
    <br />
    <h-space :size="size">
      <h-button type="primary">Primary</h-button>
      <h-button>Default</h-button>
      <h-button type="dashed">Dashed</h-button>
      <h-button type="link">Link</h-button>
    </h-space>
  </div>
</template>
<script>
export default {
  data() {
    return {
      size: 8,
    };
  },
};
</script>
```

### API 
| 参数      | 说明     | 类型       | 默认值       | 版本         |
| :-------- | :------- | :--------- | :----------- | :----------- |
| align     | 对齐方式 | `start`    | `end`        | `center`     |
| direction | 间距方向 | `vertical` | `horizontal` | `horizontal` |
| size      | 间距大小 | `small`    | `middle`     | `large`      |

## 固钉
将页面元素钉在可视范围。

### 何时使用
当内容区域比较长，需要滚动页面时，这部分内容对应的操作或者导航需要在滚动范围内始终展现。常用于侧边菜单和按钮组合。
页面可视范围过小时，慎用此功能以免遮挡页面内容。

### 代码演示
##### 基本
最简单的用法。

```html
<template>
  <div>
    <h-affix :offset-top="top">
      <h-button type="primary" @click="top += 10">
        Affix top
      </h-button>
    </h-affix>
    <br />
    <h-affix :offset-bottom="bottom">
      <h-button type="primary" @click="bottom += 10">
        Affix bottom
      </h-button>
    </h-affix>
  </div>
</template>

<script>
export default {
  data() {
    return {
      top: 10,
      bottom: 10,
    };
  },
};
</script>
```

##### 滚动容器 
用 `target` 设置 `Affix` 需要监听其滚动事件的元素，默认为 `window`。

```html
<template>
  <div id="components-affix-demo-target" ref="container" class="scrollable-container">
    <div class="background">
      <h-affix :target="() => this.$refs.container">
        <h-button type="primary">
          Fixed at the top of container
        </h-button>
      </h-affix>
    </div>
  </div>
</template>
<style>
#components-affix-demo-target.scrollable-container {
  height: 100px;
  overflow-y: scroll;
}
#components-affix-demo-target .background {
  padding-top: 60px;
  height: 300px;
  background-image: url('https://zos.alipayobjects.com/rmsportal/RmjwQiJorKyobvI.jpg');
}
</style>
```

##### 固定状态改变的回调 
可以获得是否固定的状态。

```html
<template>
  <h-affix :offset-top="120" @change="change">
    <h-button>120px to affix top</h-button>
  </h-affix>
</template>
<script>
export default {
  methods: {
    change(affixed) {
      console.log(affixed);
    },
  },
};
</script>
```

### API 
| 成员         | 说明                                                         | 类型              | 默认值       | 版本 |
| :----------- | :----------------------------------------------------------- | :---------------- | :----------- | :--- |
| offsetBottom | 距离窗口底部达到指定偏移量后触发                             | number            |              |      |
| offsetTop    | 距离窗口顶部达到指定偏移量后触发                             | number            |              |      |
| target       | 设置 `Affix` 需要监听其滚动事件的元素，值为一个返回对应 DOM 元素的函数 | () => HTMLElement | () => window |      |

#### 事件 
| 事件名称 | 说明                         | 回调参数          | 版本 |
| :------- | :--------------------------- | :---------------- | :--- |
| change   | 固定状态改变时触发的回调函数 | Function(affixed) | 无   |

**注意：**`Affix` 内的元素不要使用绝对定位，如需要绝对定位的效果，可以直接设置 `Affix` 为绝对定位：

```html
<h-affix :style="{ position: 'absolute', top: y, left: x}">
  ...
</h-affix>
```

## 面包屑
显示当前页面在系统层级结构中的位置，并能向上返回。

### 何时使用
- 当系统拥有超过两级以上的层级结构时；

- 当需要告知用户『你在哪里』时；

- 当需要向上导航的功能时。

### 代码演示
##### 基本
最简单的用法

```html
<template>
  <h-breadcrumb>
    <h-breadcrumb-item>Home</h-breadcrumb-item>
    <h-breadcrumb-item><a href="">Application Center</a></h-breadcrumb-item>
    <h-breadcrumb-item><a href="">Application List</a></h-breadcrumb-item>
    <h-breadcrumb-item>An Application</h-breadcrumb-item>
  </h-breadcrumb>
</template>
```

##### 分隔符
使用`separator=">"`可以自定义分隔符，或者使用slot="separator"自定义更复杂的分隔符

```html
<template>
  <div>
    <h-breadcrumb separator=">">
      <h-breadcrumb-item>Home</h-breadcrumb-item>
      <h-breadcrumb-item href="">
        Application Center
      </h-breadcrumb-item>
      <h-breadcrumb-item href="">
        Application List
      </h-breadcrumb-item>
      <h-breadcrumb-item>An Application</h-breadcrumb-item>
    </h-breadcrumb>
    <h-breadcrumb>
      <span slot="separator" style="color: red">></span>
      <h-breadcrumb-item>Home</h-breadcrumb-item>
      <h-breadcrumb-item href="">
        Application Center
      </h-breadcrumb-item>
      <h-breadcrumb-item href="">
        Application List
      </h-breadcrumb-item>
      <h-breadcrumb-item>An Application</h-breadcrumb-item>
    </h-breadcrumb>
  </div>
</template>
```
##### 分隔符 
使用 `Breadcrumb.Separator` 可以自定义分隔符。

```html
<template>
  <h-breadcrumb separator="">
    <h-breadcrumb-item>Location</h-breadcrumb-item>
    <h-breadcrumb-separator>:</h-breadcrumb-separator>
    <h-breadcrumb-item href="">
      Application Center
    </h-breadcrumb-item>
    <h-breadcrumb-separator />
    <h-breadcrumb-item href="">
      Application List
    </h-breadcrumb-item>
    <h-breadcrumb-separator />
    <h-breadcrumb-item>An Application</h-breadcrumb-item>
  </h-breadcrumb>
</template>
```
##### 带有图标的 
图标放在文字前面

```html
<template>
  <h-breadcrumb>
    <h-breadcrumb-item href="">
      <h-icon type="home" />
    </h-breadcrumb-item>
    <h-breadcrumb-item href="">
      <h-icon type="user" />
      <span>Application List</span>
    </h-breadcrumb-item>
    <h-breadcrumb-item>
      Application
    </h-breadcrumb-item>
  </h-breadcrumb>
</template>
```

##### vue-router
和 `vue-router` 进行结合使用。

```html
<template>
  <div>
    <h-breadcrumb :routes="routes">
      <template slot="itemRender" slot-scope="{ route, params, routes, paths }">
        <span v-if="routes.indexOf(route) === routes.length - 1">
          {{ route.breadcrumbName }}
        </span>
        <router-link v-else :to="`${basePath}/${paths.join('/')}`">
          {{ route.breadcrumbName }}
        </router-link>
      </template>
    </h-breadcrumb>
    <br />
    {{ $route.path }}
  </div>
</template>
<script>
export default {
  data() {
    const { lang } = this.$route.params;
    return {
      basePath: '/components/breadcrumb',
      routes: [
        {
          path: 'index',
          breadcrumbName: 'home',
        },
        {
          path: 'first',
          breadcrumbName: 'first',
          children: [
            {
              path: '/general',
              breadcrumbName: 'General',
            },
            {
              path: '/layout',
              breadcrumbName: 'Layout',
            },
            {
              path: '/navigation',
              breadcrumbName: 'Navigation',
            },
          ],
        },
        {
          path: 'second',
          breadcrumbName: 'second',
        },
      ],
    };
  },
};
</script>
```

##### 带下拉菜单的面包屑
面包屑支持下拉菜单。

```html
<template>
  <h-breadcrumb>
    <h-breadcrumb-item>Ant Design Vue</h-breadcrumb-item>
    <h-breadcrumb-item><a href="">Component</a></h-breadcrumb-item>
    <h-breadcrumb-item>
      <a href="">General</a>
      <h-menu slot="overlay">
        <h-menu-item>
          <a target="_blank" rel="noopener noreferrer" href="http://www.alipay.com/">
            General
          </a>
        </h-menu-item>
        <h-menu-item>
          <a target="_blank" rel="noopener noreferrer" href="http://www.taobao.com/">
            Layout
          </a>
        </h-menu-item>
        <h-menu-item>
          <a target="_blank" rel="noopener noreferrer" href="http://www.tmall.com/">
            Navigation
          </a>
        </h-menu-item>
      </h-menu>
    </h-breadcrumb-item>
    <h-breadcrumb-item>Button</h-breadcrumb-item>
  </h-breadcrumb>
</template>
```

### API 
| 参数       | 说明                                                         | 类型                                                         | 可选值 | 默认值 |
| :--------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----- | :----- |
| itemRender | 自定义链接函数，和 vue-router 配置使用， 也可使用 slot="itemRender" 和 slot-scope="props" | ({route, params, routes, paths, h}) => vNode                 |        | -      |
| params     | 路由的参数                                                   | object                                                       |        | -      |
| routes     | router 的路由栈信息                                          | [routes[\]](https://1x.antdv.com/components/breadcrumb-cn/#routes) |        | -      |
| separator  | 分隔符自定义                                                 | string\|slot                                                 |        | '/'    |

#### Breadcrumb.Item
| 参数    | 参数           | 类型                                                       | 默认值 | 版本  |
| :------ | :------------- | :--------------------------------------------------------- | :----- | :---- |
| href    | 链接的目的地   | string                                                     | -      | 1.5.0 |
| overlay | 下拉菜单的内容 | [Menu](https://1x.antdv.com/components/menu) \| () => Menu | -      | 1.5.0 |

##### 事件
| 事件名称 | 说明     | 回调参数             | 版本 |
| :------- | :------- | :------------------- | :--- |
| click    | 单击事件 | (e:MouseEvent)=>void | -    |

#### Breadcrumb.Separator `3.21.0` 
| 参数 | 参数 | 类型 | 默认值 | 版本 |
| :--- | :--- | :--- | :----- | :--- |
|      |      |      |        |      |

> 注意：在使用 `Breadcrumb.Separator` 时，其父组件的分隔符必须设置为 `separator=""`，否则会出现父组件默认的分隔符。

#### routes
```ts
interface Route {
  path: string;
  breadcrumbName: string;
  children: Array<{
    path: string;
    breadcrumbName: string;
  }>;
}
```

#### 和 browserHistory 配合
和 vue-router 一起使用时，默认生成的 url 路径是带有 `#` 的，如果和 browserHistory 一起使用的话，你可以使用 `itemRender` 属性定义面包屑链接。

```html
<template>
  <h-breadcrumb :routes="routes">
    <template slot="itemRender" slot-scope="{route, params, routes, paths}">
      <span v-if="routes.indexOf(route) === routes.length - 1">
        {{route.breadcrumbName}}
      </span>
      <router-link v-else :to="paths.join('/')">
        {{route.breadcrumbName}}
      </router-link>
    </template>
  </h-breadcrumb>
</template>
<script>
  export default {
    data() {
      return {
        routes: [
          {
            path: 'index',
            breadcrumbName: 'home',
          },
          {
            path: 'first',
            breadcrumbName: 'first',
            children: [
              {
                path: '/general',
                breadcrumbName: 'General',
              },
              {
                path: '/layout',
                breadcrumbName: 'Layout',
              },
              {
                path: '/navigation',
                breadcrumbName: 'Navigation',
              },
            ],
          },
          {
            path: 'second',
            breadcrumbName: 'second',
          },
        ],
      };
    },
  };
</script>
```

## 下拉菜单
向下弹出的列表。

### 何时使用
当页面上的操作命令过多时，用此组件可以收纳操作元素。点击或移入触点，会出现一个下拉菜单。可在列表中进行选择，并执行相应的命令。

### 代码演示
##### 基本
最简单的下拉菜单。

```html
<template>
  <h-dropdown>
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Hover me <h-icon type="down" />
    </a>
    <h-menu slot="overlay">
      <h-menu-item>
        <a href="javascript:;">1st menu item</a>
      </h-menu-item>
      <h-menu-item>
        <a href="javascript:;">2nd menu item</a>
      </h-menu-item>
      <h-menu-item>
        <a href="javascript:;">3rd menu item</a>
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>
```
##### 带下拉框的按钮
左边是按钮，右边是额外的相关功能菜单。可设置 `icon` 属性来修改右边的图标。

```html
<template>
  <div>
    <h-dropdown-button @click="handleButtonClick">
      Dropdown
      <h-menu slot="overlay" @click="handleMenuClick">
        <h-menu-item key="1"> <h-icon type="user" />1st menu item </h-menu-item>
        <h-menu-item key="2"> <h-icon type="user" />2nd menu item </h-menu-item>
        <h-menu-item key="3"> <h-icon type="user" />3rd item </h-menu-item>
      </h-menu>
    </h-dropdown-button>
    <h-dropdown-button>
      Dropdown
      <h-menu slot="overlay" @click="handleMenuClick">
        <h-menu-item key="1"> <h-icon type="user" />1st menu item </h-menu-item>
        <h-menu-item key="2"> <h-icon type="user" />2nd menu item </h-menu-item>
        <h-menu-item key="3"> <h-icon type="user" />3rd item </h-menu-item>
      </h-menu>
      <h-icon slot="icon" type="user" />
    </h-dropdown-button>
    <h-dropdown-button disabled style="margin-left: 8px" @click="handleButtonClick">
      Dropdown
      <h-menu slot="overlay" @click="handleMenuClick">
        <h-menu-item key="1"> <h-icon type="user" />1st menu item </h-menu-item>
        <h-menu-item key="2"> <h-icon type="user" />2nd menu item </h-menu-item>
        <h-menu-item key="3"> <h-icon type="user" />3rd item </h-menu-item>
      </h-menu>
    </h-dropdown-button>
    <h-dropdown>
      <h-menu slot="overlay" @click="handleMenuClick">
        <h-menu-item key="1"> <h-icon type="user" />1st menu item </h-menu-item>
        <h-menu-item key="2"> <h-icon type="user" />2nd menu item </h-menu-item>
        <h-menu-item key="3"> <h-icon type="user" />3rd item </h-menu-item>
      </h-menu>
      <h-button style="margin-left: 8px"> Button <h-icon type="down" /> </h-button>
    </h-dropdown>
  </div>
</template>

<script>
export default {
  methods: {
    handleButtonClick(e) {
      console.log('click left button', e);
    },
    handleMenuClick(e) {
      console.log('click', e);
    },
  },
};
</script>
```
##### 其他元素 
分割线和不可用菜单项。

```html
<template>
  <h-dropdown>
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Hover me <h-icon type="down" />
    </a>
    <h-menu slot="overlay">
      <h-menu-item key="0">
        <a target="_blank" rel="noopener noreferrer" href="http://www.alipay.com/">1st menu item</a>
      </h-menu-item>
      <h-menu-item key="1">
        <a target="_blank" rel="noopener noreferrer" href="http://www.taobao.com/">2nd menu item</a>
      </h-menu-item>
      <h-menu-divider />
      <h-menu-item key="3" disabled>
        3rd menu item（disabled）
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>
```
##### 弹出位置 
支持 6 个弹出位置。

```html
<template>
  <div id="components-dropdown-demo-placement">
    <template v-for="(placement, index) in placements">
      <h-dropdown :placement="placement">
        <h-button>{{ placement }}</h-button>
        <h-menu slot="overlay">
          <h-menu-item>
            <a target="_blank" rel="noopener noreferrer" href="http://www.alipay.com/"
              >1st menu item</a
            >
          </h-menu-item>
          <h-menu-item>
            <a target="_blank" rel="noopener noreferrer" href="http://www.taobao.com/"
              >2nd menu item</a
            >
          </h-menu-item>
          <h-menu-item>
            <a target="_blank" rel="noopener noreferrer" href="http://www.tmall.com/"
              >3rd menu item</a
            >
          </h-menu-item>
        </h-menu>
      </h-dropdown>
      <br v-if="index === 2" />
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      placements: ['bottomLeft', 'bottomCenter', 'bottomRight', 'topLeft', 'topCenter', 'topRight'],
    };
  },
};
</script>
<style>
#components-dropdown-demo-placement .ant-btn {
  margin-right: 8px;
  margin-bottom: 8px;
}
</style>
```
##### 触发方式
默认是移入触发菜单，可以点击触发。

```html
<template>
  <h-dropdown :trigger="['click']">
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Click me <h-icon type="down" />
    </a>
    <h-menu slot="overlay">
      <h-menu-item key="0">
        <a href="http://www.alipay.com/">1st menu item</a>
      </h-menu-item>
      <h-menu-item key="1">
        <a href="http://www.taobao.com/">2nd menu item</a>
      </h-menu-item>
      <h-menu-divider />
      <h-menu-item key="3">
        3rd menu item
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>
```
##### 右键菜单
默认是移入触发菜单，可以点击鼠标右键触发。

```html
<template>
  <h-dropdown :trigger="['contextmenu']">
    <div
      :style="{
        textAlign: 'center',
        background: '#f7f7f7',
        height: '200px',
        lineHeight: '200px',
        color: '#777',
      }"
    >
      Right Click on here
    </div>
    <h-menu slot="overlay">
      <h-menu-item key="1">
        1st menu item
      </h-menu-item>
      <h-menu-item key="2">
        2nd menu item
      </h-menu-item>
      <h-menu-item key="3">
        3rd menu item
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>
```
##### 触发事件
点击菜单项后会触发事件，用户可以通过相应的菜单项 key 进行不同的操作。

```html
<template>
  <h-dropdown>
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Hover me, Click menu item <h-icon type="down" />
    </a>
    <h-menu slot="overlay" @click="onClick">
      <h-menu-item key="1">
        1st menu item
      </h-menu-item>
      <h-menu-item key="2">
        2nd menu item
      </h-menu-item>
      <h-menu-item key="3">
        3rd menu item
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>

<script>
export default {
  methods: {
    onClick({ key }) {
      console.log(`Click on item ${key}`);
    },
  },
};
</script>
```

##### 菜单隐藏方式 
默认是点击关闭菜单，可以关闭此功能。

```html
<template>
  <h-dropdown v-model="visible">
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Hover me <h-icon type="down" />
    </a>
    <h-menu slot="overlay" @click="handleMenuClick">
      <h-menu-item key="1">
        Clicking me will not close the menu.
      </h-menu-item>
      <h-menu-item key="2">
        Clicking me will not close the menu also.
      </h-menu-item>
      <h-menu-item key="3">
        Clicking me will close the menu
      </h-menu-item>
    </h-menu>
  </h-dropdown>
</template>

<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    handleMenuClick(e) {
      if (e.key === '3') {
        this.visible = false;
      }
    },
  },
};
</script>
```

##### 多级菜单
传入的菜单里有多个层级。

```html
<template>
  <h-dropdown>
    <a class="ant-dropdown-link" @click="e => e.preventDefault()">
      Cascading menu <h-icon type="down" />
    </a>
    <h-menu slot="overlay">
      <h-menu-item>1st menu item</h-menu-item>
      <h-menu-item>2nd menu item</h-menu-item>
      <h-sub-menu key="test" title="sub menu">
        <h-menu-item>3rd menu item</h-menu-item>
        <h-menu-item>4th menu item</h-menu-item>
      </h-sub-menu>
      <h-sub-menu title="disabled sub menu" disabled>
        <h-menu-item>5d menu item</h-menu-item>
        <h-menu-item>6th menu item</h-menu-item>
      </h-sub-menu>
    </h-menu>
  </h-dropdown>
</template>
```

### API 
属性如下

| 参数                | 说明                                                         | 类型                                            | 默认值                |
| :------------------ | :----------------------------------------------------------- | :---------------------------------------------- | :-------------------- |
| disabled            | 菜单是否禁用                                                 | boolean                                         | -                     |
| destroyPopupOnHide  | 关闭后是否销毁 Dropdown                                      | boolean                                         | false                 |
| getPopupContainer   | 菜单渲染父节点。默认渲染到 body 上，如果你遇到菜单滚动定位问题，试试修改为滚动的区域，并相对其定位。 | Function(triggerNode)                           | `() => document.body` |
| overlay(slot-scope) | 菜单                                                         | [Menu](https://1x.antdv.com/components/menu-cn) | -                     |
| overlayClassName    | 下拉根元素的类名称                                           | string                                          | -                     |
| overlayStyle        | 下拉根元素的样式                                             | object                                          | -                     |
| placement           | 菜单弹出位置：`bottomLeft` `bottomCenter` `bottomRight` `topLeft` `topCenter` `topRight` | String                                          | `bottomLeft`          |
| trigger             | 触发下拉的行为, 移动端不支持 hover                           | Array<`click`                                   | `hover`               |
| visible(v-model)    | 菜单是否显示                                                 | boolean                                         | -                     |

`overlay` 菜单使用 [Menu](https://1x.antdv.com/components/menu-cn/)，还包括菜单项 `Menu.Item`，分割线 `Menu.Divider`。

> 注意： Menu.Item 必须设置唯一的 key 属性。
>
> Dropdown 下的 Menu 默认不可选中。如果需要菜单可选中，可以指定 `<Menu selectable>`.

#### 事件
| 事件名称      | 说明                                   | 回调参数          |
| :------------ | :------------------------------------- | :---------------- |
| visibleChange | 菜单显示状态改变时调用，参数为 visible | function(visible) |

#### Dropdown.Button 
| 参数                | 说明                                                         | 类型                                             | 默认值       | 版本           |
| :------------------ | :----------------------------------------------------------- | :----------------------------------------------- | :----------- | :------------- |
| disabled            | 菜单是否禁用                                                 | boolean                                          | -            |                |
| icon                | 右侧的 icon                                                  | VNode \| slot                                    | -            | 1.5.0          |
| overlay(slot-scope) | 菜单                                                         | [Menu](https://1x.antdv.com/components/menu-cn/) | -            |                |
| placement           | 菜单弹出位置：`bottomLeft` `bottomCenter` `bottomRight` `topLeft` `topCenter` `topRight` | String                                           | `bottomLeft` |                |
| size                | 按钮大小，和 [Button](https://1x.antdv.com/components/button-cn/) 一致 | string                                           | 'default'    |                |
| trigger             | 触发下拉的行为                                               | Array<`click`                                    | `hover`      | `contextmenu`> |
| type                | 按钮类型，和 [Button](https://1x.antdv.com/components/button-cn/) 一致 | string                                           | 'default'    |                |
| visible(v-model)    | 菜单是否显示                                                 | boolean                                          | -            |                |

#### Dropdown.Button 事件 
| 事件名称      | 说明                                                         | 回调参数          |
| :------------ | :----------------------------------------------------------- | :---------------- |
| click         | 点击左侧按钮的回调，和 [Button](https://1x.antdv.com/components/button-cn/) 一致 | Function          |
| visibleChange | 菜单显示状态改变时调用，参数为 visible                       | function(visible) |

## 页头
页头位于页容器中，页容器顶部，起到了内容概览和引导页级操作的作用。包括由面包屑、标题、页面内容简介、页面级操作等、页面级导航组成。

### 何时使用
当需要使用户快速理解当前页是什么以及方便用户使用页面功能时使用，通常也可被用作页面间导航。

### 代码演示
##### 标准样式 
标准页头，适合使用在需要简单描述的场景。

```html
<template>
  <h-page-header
    style="border: 1px solid rgb(235, 237, 240)"
    title="Title"
    sub-title="This is a subtitle"
    @back="() => null"
  />
</template>
```

##### 带面包屑页头
带面包屑页头，适合层级比较深的页面，让用户可以快速导航。

```html
<template>
  <h-page-header
    style="border: 1px solid rgb(235, 237, 240)"
    title="Title"
    :breadcrumb="{ props: { routes } }"
    sub-title="This is a subtitle"
  />
</template>
<script>
export default {
  data() {
    return {
      routes: [
        {
          path: 'index',
          breadcrumbName: 'First-level Menu',
        },
        {
          path: 'first',
          breadcrumbName: 'Second-level Menu',
        },
        {
          path: 'second',
          breadcrumbName: 'Third-level Menu',
        },
      ],
    };
  },
};
</script>
```

##### 多种形态的 PageHeader
使用操作区，并自定义子节点，适合使用在需要展示一些复杂的信息，帮助用户快速了解这个页面的信息和操作。

```html
<template>
  <div>
    <h-page-header
      style="border: 1px solid rgb(235, 237, 240)"
      title="Title"
      sub-title="This is a subtitle"
      @back="() => $router.go(-1)"
    >
      <template slot="extra">
        <h-button key="3">
          Operation
        </h-button>
        <h-button key="2">
          Operation
        </h-button>
        <h-button key="1" type="primary">
          Primary
        </h-button>
      </template>
      <h-descriptions size="small" :column="3">
        <h-descriptions-item label="Created">
          Lili Qu
        </h-descriptions-item>
        <h-descriptions-item label="Association">
          <a>421421</a>
        </h-descriptions-item>
        <h-descriptions-item label="Creation Time">
          2017-01-10
        </h-descriptions-item>
        <h-descriptions-item label="Effective Time">
          2017-10-10
        </h-descriptions-item>
        <h-descriptions-item label="Remarks">
          Gonghu Road, Xihu District, Hangzhou, Zhejiang, China
        </h-descriptions-item>
      </h-descriptions>
    </h-page-header>
    <br />
    <h-page-header title="Title" sub-title="This is a subtitle" @back="() => $router.go(-1)">
      <template slot="tags">
        <h-tag color="blue">
          Running
        </h-tag>
      </template>
      <template slot="extra">
        <h-button key="3">
          Operation
        </h-button>
        <h-button key="2">
          Operation
        </h-button>
        <h-button key="1" type="primary">
          Primary
        </h-button>
      </template>
      <h-row type="flex">
        <h-statistic title="Status" value="Pending" />
        <h-statistic
          title="Price"
          prefix="$"
          :value="568.08"
          :style="{
            margin: '0 32px',
          }"
        />
        <h-statistic title="Balance" prefix="$" :value="3345.08" />
      </h-row>
    </h-page-header>
  </div>
</template>
<style>
tr:last-child td {
  padding-bottom: 0;
}
</style>
```

##### 响应式
在不同大小的屏幕下，应该有不同的表现

```html
<template>
  <div>
    <h-page-header
      style="border: 1px solid rgb(235, 237, 240)"
      title="Title"
      sub-title="This is a subtitle"
      @back="() => $router.go(-1)"
    >
      <template slot="extra">
        <h-button key="3">
          Operation
        </h-button>
        <h-button key="2">
          Operation
        </h-button>
        <h-button key="1" type="primary">
          Primary
        </h-button>
      </template>
      <template slot="footer">
        <h-tabs default-active-key="1">
          <h-tab-pane key="1" tab="Details" />
          <h-tab-pane key="2" tab="Rule" />
        </h-tabs>
      </template>
      <div class="content">
        <div class="main">
          <h-descriptions size="small" :column="2">
            <h-descriptions-item label="Created">
              Lili Qu
            </h-descriptions-item>
            <h-descriptions-item label="Association">
              <a>421421</a>
            </h-descriptions-item>
            <h-descriptions-item label="Creation Time">
              2017-01-10
            </h-descriptions-item>
            <h-descriptions-item label="Effective Time">
              2017-10-10
            </h-descriptions-item>
            <h-descriptions-item label="Remarks">
              Gonghu Road, Xihu District, Hangzhou, Zhejiang, China
            </h-descriptions-item>
          </h-descriptions>
        </div>
        <div class="extra">
          <div
            :style="{
              display: 'flex',
              width: 'max-content',
              justifyContent: 'flex-end',
            }"
          >
            <h-statistic
              title="Status"
              value="Pending"
              :style="{
                marginRight: '32px',
              }"
            />
            <h-statistic title="Price" prefix="$" :value="568.08" />
          </div>
        </div>
      </div>
    </h-page-header>
  </div>
</template>
<style>
tr:last-child td {
  padding-bottom: 0;
}
#components-page-header-demo-responsive .content {
  display: flex;
}
#components-page-header-demo-responsive .ant-statistic-content {
  font-size: 20px;
  line-height: 28px;
}
@media (max-width: 576px) {
  #components-page-header-demo-responsive .content {
    display: block;
  }

  #components-page-header-demo-responsive .main {
    width: 100%;
    margin-bottom: 12px;
  }

  #components-page-header-demo-responsive .extra {
    width: 100%;
    margin-left: 0;
    text-align: left;
  }
}
</style>
```

##### 白底模式 
默认 PageHeader 是透明底色的。在某些情况下，PageHeader 需要自己的背景颜色。

```html
<template>
  <div style="background-color: #F5F5F5; padding: 24px;">
    <h-page-header
      :ghost="false"
      title="Title"
      sub-title="This is a subtitle"
      @back="() => $router.go(-1)"
    >
      <template slot="extra">
        <h-button key="3">
          Operation
        </h-button>
        <h-button key="2">
          Operation
        </h-button>
        <h-button key="1" type="primary">
          Primary
        </h-button>
      </template>
      <h-descriptions size="small" :column="3">
        <h-descriptions-item label="Created">
          Lili Qu
        </h-descriptions-item>
        <h-descriptions-item label="Association">
          <a>421421</a>
        </h-descriptions-item>
        <h-descriptions-item label="Creation Time">
          2017-01-10
        </h-descriptions-item>
        <h-descriptions-item label="Effective Time">
          2017-10-10
        </h-descriptions-item>
        <h-descriptions-item label="Remarks">
          Gonghu Road, Xihu District, Hangzhou, Zhejiang, China
        </h-descriptions-item>
      </h-descriptions>
    </h-page-header>
  </div>
</template>
<style>
tr:last-child td {
  padding-bottom: 0;
}
</style>
```

### API 
| 参数       | 说明                                             | 类型                                                         | 默认值                       |
| :--------- | :----------------------------------------------- | :----------------------------------------------------------- | :--------------------------- |
| title      | 自定义标题文字                                   | string\|slot                                                 | -                            |
| subTitle   | 自定义的二级标题文字                             | string\|slot                                                 | -                            |
| ghost      | pageHeader 的类型，将会改变背景颜色              | boolean                                                      | true                         |
| avatar     | 标题栏旁的头像                                   | [avatar props](https://1x.antdv.com/components/avatar-cn/)   | -                            |
| backIcon   | 自定义 back icon ，如果为 false 不渲染 back icon | string\|slot                                                 | `<Icon type="arrow-left" />` |
| tags       | title 旁的 tag 列表                              | [Tag](https://1x.antdv.com/components/tag-cn/)[] \| [Tag](https://1x.antdv.com/components/tag-cn/) | -                            |
| extra      | 操作区，位于 title 行的行尾                      | string\|slot                                                 | -                            |
| breadcrumb | 面包屑的配置                                     | [breadcrumb](https://1x.antdv.com/components/breadcrumb-cn/) | -                            |
| footer     | PageHeader 的页脚，一般用于渲染 TabBar           | string\|slot                                                 | -                            |

#### 事件 
| 事件名称 | 说明               | 回调参数    |
| :------- | :----------------- | :---------- |
| back     | 返回按钮的点击事件 | function(e) |

## 分页 
采用分页的形式分隔长列表，每次只加载一个页面。

### 何时使用
- 当加载/渲染所有数据将花费很多时间时；
- 可切换页码浏览数据。

### 代码演示
##### 基本
基础分页。

```html
<template>
  <h-pagination v-model="current" :total="50" show-less-items />
</template>
<script>
export default {
  data() {
    return {
      current: 2,
    };
  },
};
</script>
```

##### 更多 
更多分页。

```html
<template>
  <h-pagination :default-current="6" :total="500" />
</template>
```

##### 改变
改变每页显示条目数。

```html
<template>
  <div>
    <h-pagination
      show-size-changer
      :default-current="3"
      :total="500"
      @showSizeChange="onShowSizeChange"
    />
    <br />
    <h-pagination
      v-model="current"
      show-size-changer
      :page-size.sync="pageSize"
      :total="500"
      disabled
      @showSizeChange="onShowSizeChange"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      pageSize: 20,
      current: 4,
    };
  },
  watch: {
    pageSize(val) {
      console.log('pageSize', val);
    },
    current(val) {
      console.log('current', val);
    },
  },
  methods: {
    onShowSizeChange(current, pageSize) {
      console.log(current, pageSize);
    },
  },
};
</script>
```

##### 自定义下拉选项
自定义下拉选项，例如添加全部选项

```html
<template>
  <h-pagination
    v-model="current"
    :page-size-options="pageSizeOptions"
    :total="total"
    show-size-changer
    :page-size="pageSize"
    @showSizeChange="onShowSizeChange"
  >
    <template slot="buildOptionText" slot-scope="props">
      <span v-if="props.value !== '50'">{{ props.value }}条/页</span>
      <span v-if="props.value === '50'">全部</span>
    </template>
  </h-pagination>
</template>
<script>
export default {
  data() {
    return {
      pageSizeOptions: ['10', '20', '30', '40', '50'],
      current: 1,
      pageSize: 10,
      total: 50,
    };
  },
  methods: {
    onShowSizeChange(current, pageSize) {
      this.pageSize = pageSize;
    },
  },
};
</script>
```

##### 跳转 
快速跳转到某一页。

```html
<template>
  <div>
    <h-pagination show-quick-jumper :default-current="2" :total="500" @change="onChange" />
    <br />
    <h-pagination
      show-quick-jumper
      :default-current="2"
      :total="500"
      disabled
      show-less-items
      @change="onChange"
    />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(pageNumber) {
      console.log('Page: ', pageNumber);
    },
  },
};
</script>
```

##### 迷你 
迷你版本。

```html
<template>
  <div id="components-pagination-demo-mini">
    <h-pagination size="small" :total="50" />
    <h-pagination size="small" :total="50" show-size-changer show-quick-jumper />
    <h-pagination size="small" :total="50" :show-total="total => `Total ${total} items`" />
  </div>
</template>
<style scoped>
#components-pagination-demo-mini .ant-pagination:not(:last-child) {
  margin-bottom: 24px;
}
</style>
```

##### 简洁 
简单的翻页。

```html
<template>
  <h-pagination simple :default-current="2" :total="50" />
</template>
```

##### 受控 
受控制的页码。

```html
<template>
  <h-pagination :current="current" :total="50" @change="onChange" />
</template>
<script>
export default {
  data() {
    return {
      current: 3,
    };
  },
  methods: {
    onChange(current) {
      this.current = current;
    },
  },
};
</script>
```

##### 总数 
通过设置 `showTotal` 展示总共有多少数据。

```html
<template>
  <div>
    <h-pagination
      :total="85"
      :show-total="total => `Total ${total} items`"
      :page-size="20"
      :default-current="1"
    />
    <br />
    <h-pagination
      :total="85"
      :show-total="(total, range) => `${range[0]}-${range[1]} of ${total} items`"
      :page-size="20"
      :default-current="1"
    />
  </div>
</template>
```

##### 上一步和下一步
修改上一步和下一步为文字链接。

```html
<template>
  <h-pagination :total="500" :item-render="itemRender" />
</template>
<script>
export default {
  methods: {
    itemRender(current, type, originalElement) {
      if (type === 'prev') {
        return <a>Previous</a>;
      } else if (type === 'next') {
        return <a>Next</a>;
      }
      return originalElement;
    },
  },
};
</script>
```

### API 
```html
<h-pagination @change="onChange" :total="50" />
```

| 参数             | 说明                                 | 类型                                                         | 默认值                   | 版本  |
| :--------------- | :----------------------------------- | :----------------------------------------------------------- | :----------------------- | :---- |
| current(v-model) | 当前页数                             | number                                                       | -                        |       |
| defaultCurrent   | 默认的当前页数                       | number                                                       | 1                        |       |
| defaultPageSize  | 默认的每页条数                       | number                                                       | 10                       |       |
| disabled         | 禁用分页                             | boolean                                                      | -                        | 1.5.0 |
| hideOnSinglePage | 只有一页时是否隐藏分页器             | boolean                                                      | false                    |       |
| itemRender       | 用于自定义页码的结构，可用于优化 SEO | (page, type: 'page' \| 'prev' \| 'next', originalElement) => vNode | -                        |       |
| pageSize(.sync)  | 每页条数                             | number                                                       | -                        |       |
| pageSizeOptions  | 指定每页可以显示多少条               | string[]                                                     | ['10', '20', '30', '40'] |       |
| showLessItems    | show less page items                 | boolean                                                      | false                    | 1.5.0 |
| showQuickJumper  | 是否可以快速跳转至某页               | boolean                                                      | false                    |       |
| showSizeChanger  | 是否可以改变 pageSize                | boolean                                                      | false                    |       |
| showTotal        | 用于显示数据总量和当前数据顺序       | Function(total, range)                                       | -                        |       |
| simple           | 当添加该属性时，显示为简单分页       | boolean                                                      | -                        |       |
| size             | 当为「small」时，是小尺寸分页        | string                                                       | ""                       |       |
| total            | 数据总数                             | number                                                       | 0                        |       |

#### 事件 
| 事件名称       | 说明                                         | 回调参数                 |
| :------------- | :------------------------------------------- | :----------------------- |
| change         | 页码改变的回调，参数是改变后的页码及每页条数 | Function(page, pageSize) |
| showSizeChange | pageSize 变化的回调                          | Function(current, size)  |

## 步骤条
引导用户按照流程完成任务的导航条。

### 何时使用
当任务复杂或者存在先后关系时，将其分解成一系列步骤，从而简化任务。

### 代码演示
##### 基本用法 
简单的步骤条。

```html
<template>
  <h-steps :current="1">
    <h-step>
      <!-- <span slot="title">Finished</span> -->
      <template slot="title">
        Finished
      </template>
      <span slot="description">This is a description.</span>
    </h-step>
    <h-step title="In Progress" sub-title="Left 00:00:08" description="This is a description." />
    <h-step title="Waiting" description="This is a description." />
  </h-steps>
</template>
```

##### 迷你版
迷你版的步骤条，通过设置 `<Steps size="small">` 启用。

```html
<template>
  <h-steps :current="1" size="small">
    <h-step title="Finished" />
    <h-step title="In Progress" />
    <h-step title="Waiting" />
  </h-steps>
</template>
```

##### 带图标的步骤条 
通过设置 `Steps.Step` 的 `icon` 属性，可以启用自定义图标。

```html
<template>
  <h-steps>
    <h-step status="finish" title="Login">
      <h-icon slot="icon" type="user" />
    </h-step>
    <h-step status="finish" title="Verification">
      <h-icon slot="icon" type="solution" />
    </h-step>
    <h-step status="process" title="Pay">
      <h-icon slot="icon" type="loading" />
    </h-step>
    <h-step status="wait" title="Done">
      <h-icon slot="icon" type="smile-o" />
    </h-step>
  </h-steps>
</template>
```

##### 步骤切换
通常配合内容及按钮使用，表示一个流程的处理进度。

```html
<template>
  <div>
    <h-steps :current="current">
      <h-step v-for="item in steps" :key="item.title" :title="item.title" />
    </h-steps>
    <div class="steps-content">
      {{ steps[current].content }}
    </div>
    <div class="steps-action">
      <h-button v-if="current < steps.length - 1" type="primary" @click="next">
        Next
      </h-button>
      <h-button
        v-if="current == steps.length - 1"
        type="primary"
        @click="$message.success('Processing complete!')"
      >
        Done
      </h-button>
      <h-button v-if="current > 0" style="margin-left: 8px" @click="prev">
        Previous
      </h-button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      current: 0,
      steps: [
        {
          title: 'First',
          content: 'First-content',
        },
        {
          title: 'Second',
          content: 'Second-content',
        },
        {
          title: 'Last',
          content: 'Last-content',
        },
      ],
    };
  },
  methods: {
    next() {
      this.current++;
    },
    prev() {
      this.current--;
    },
  },
};
</script>
<style scoped>
.steps-content {
  margin-top: 16px;
  border: 1px dashed #e9e9e9;
  border-radius: 6px;
  background-color: #fafafa;
  min-height: 200px;
  text-align: center;
  padding-top: 80px;
}

.steps-action {
  margin-top: 24px;
}
</style>
```

##### 竖直方向的步骤条
简单的竖直方向的步骤条。

```html
<template>
  <h-steps direction="vertical" :current="1">
    <h-step title="Finished" description="This is a description." />
    <h-step title="In Progress" description="This is a description." />
    <h-step title="Waiting" description="This is a description." />
  </h-steps>
</template>
```

##### 竖直方向的小型步骤条 
简单的竖直方向的小型步骤条。

```html
<template>
  <h-steps direction="vertical" size="small" :current="1">
    <h-step title="Finished" description="This is a description." />
    <h-step title="In Progress" description="This is a description." />
    <h-step title="Waiting" description="This is a description." />
  </h-steps>
</template>
```

##### 步骤运行错误 
使用 Steps 的 `status` 属性来指定当前步骤的状态。

```html
<template>
  <h-steps :current="1" status="error">
    <h-step title="Finished" description="This is a description." />
    <h-step title="In Progress" description="This is a description." />
    <h-step title="Waiting" description="This is a description." />
  </h-steps>
</template>
```

##### 点状步骤条
包含步骤点的进度条。

```html
<template>
  <div>
    <h-steps progress-dot :current="1">
      <h-step title="Finished" description="This is a description." />
      <h-step title="In Progress" description="This is a description." />
      <h-step title="Waiting" description="This is a description." />
    </h-steps>
    <h-divider />
    <h-steps progress-dot :current="1" direction="vertical">
      <h-step title="Finished" description="This is a description. This is a description." />
      <h-step title="Finished" description="This is a description. This is a description." />
      <h-step title="In Progress" description="This is a description. This is a description." />
      <h-step title="Waiting" description="This is a description." />
      <h-step title="Waiting" description="This is a description." />
    </h-steps>
  </div>
</template>
```

##### 自定义点状步骤条
为点状步骤条增加自定义展示。

```html
<template>
  <div>
    <h-steps :current="1">
      <h-popover slot="progressDot" slot-scope="{ index, status, prefixCls }">
        <template slot="content">
          <span>step {{ index }} status: {{ status }}</span>
        </template>
        <span :class="`${prefixCls}-icon-dot`" />
      </h-popover>
      <h-step title="Finished" description="You can hover on the dot." />
      <h-step title="In Progress" description="You can hover on the dot." />
      <h-step title="Waiting" description="You can hover on the dot." />
      <h-step title="Waiting" description="You can hover on the dot." />
    </h-steps>
  </div>
</template>
```

##### 可点击
设置 `@change` 后，Steps 变为可点击状态。

```html
<template>
  <div>
    <h-steps :current="current" @change="onChange">
      <h-step title="Step 1" description="This is a description." />
      <h-step title="Step 2" description="This is a description." />
      <h-step title="Step 3" description="This is a description." />
    </h-steps>
    <h-divider />
    <h-steps v-model="current" direction="vertical">
      <h-step title="Step 1" description="This is a description." />
      <h-step title="Step 2" description="This is a description." />
      <h-step title="Step 3" description="This is a description." />
    </h-steps>
  </div>
</template>
<script>
export default {
  data() {
    return {
      current: 0,
    };
  },
  methods: {
    onChange(current) {
      console.log('onChange:', current);
      this.current = current;
    },
  },
};
</script>
```

##### 导航步骤 
导航类型的步骤条。

```html
<template>
  <div>
    <h-steps v-model="current" type="navigation" size="small" :style="stepStyle">
      <h-step
        title="Step 1"
        sub-title="00:00:05"
        status="finish"
        description="This is a description."
      />
      <h-step
        title="Step 2"
        sub-title="00:01:02"
        status="process"
        description="This is a description."
      />
      <h-step
        title="Step 3"
        sub-title="waiting for longlong time"
        status="wait"
        description="This is a description."
      />
    </h-steps>
    <h-steps v-model="current" type="navigation" :style="stepStyle">
      <h-step status="finish" title="Step 1" />
      <h-step status="process" title="Step 2" />
      <h-step status="wait" title="Step 3" />
      <h-step status="wait" title="Step 4" />
    </h-steps>
    <h-steps v-model="current" type="navigation" size="small" :style="stepStyle">
      <h-step status="finish" title="finish 1" />
      <h-step status="finish" title="finish 2" />
      <h-step status="process" title="current process" />
      <h-step status="wait" title="wait" disabled />
    </h-steps>
  </div>
</template>
<script>
export default {
  data() {
    return {
      current: 0,
      stepStyle: {
        marginBottom: '60px',
        boxShadow: '0px -1px 0 0 #e8e8e8 inset',
      },
    };
  },
};
</script>
```

### API
#### Steps 
整体步骤条。

| 参数              | 说明                                                         | 类型                                                         | 默认值       | 版本  |
| :---------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------- | :---- |
| type              | 步骤条类型，有 `default` 和 `navigation` 两种                | string                                                       | `default`    | 1.5.0 |
| current (v-model) | 指定当前步骤，从 0 开始记数。在子 Step 元素中，可以通过 `status` 属性覆盖状态, 1.5.0 后支持 v-model | number                                                       | 0            |       |
| direction         | 指定步骤条方向。目前支持水平（`horizontal`）和竖直（`vertical`）两种方向 | string                                                       | horizontal   |       |
| labelPlacement    | 指定标签放置位置，默认水平放图标右侧，可选`vertical`放图标下方 | string                                                       | `horizontal` |       |
| progressDot       | 点状步骤条，可以设置为一个 作用域插槽,labelPlacement 将强制为`vertical` | Boolean or slot="progressDot" slot-scope="{index, status, title, description, prefixCls})" | false        |       |
| size              | 指定大小，目前支持普通（`default`）和迷你（`small`）         | string                                                       | default      |       |
| status            | 指定当前步骤的状态，可选 `wait` `process` `finish` `error`   | string                                                       | process      |       |
| initial           | 起始序号，从 0 开始记数                                      | number                                                       | 0            |       |

##### Steps 事件 
| 事件名称 | 说明               | 回调参数          | 版本 |
| :------- | :----------------- | :---------------- | :--- |
| change   | 点击切换步骤时触发 | (current) => void | -    |

#### Steps.Step
步骤条内的每一个步骤。

| 参数        | 说明                                                         | 类型           | 默认值 | 版本  |
| :---------- | :----------------------------------------------------------- | :------------- | :----- | :---- |
| description | 步骤的详情描述，可选                                         | string \| slot | -      |       |
| icon        | 步骤图标的类型，可选                                         | string \| slot | -      |       |
| status      | 指定状态。当不配置该属性时，会使用 Steps 的 `current` 来自动指定状态。可选：`wait` `process` `finish` `error` | string         | wait   |       |
| title       | 标题                                                         | string \| slot | -      |       |
| subTitle    | 子标题                                                       | string \| slot | -      | 1.5.0 |
| disabled    | 禁用点击                                                     | boolean        | false  | 1.5.0 |

## 自动完成
输入框自动完成功能。

### 何时使用
需要自动完成时。

### 代码演示
##### 基本使用 
基本使用。通过 dataSource 设置自动完成的数据源

```html
<template>
  <h-auto-complete
    v-model="value"
    :dath-source="dataSource"
    style="width: 200px"
    placeholder="input here"
    @select="onSelect"
    @search="onSearch"
    @change="onChange"
  />
</template>
<script>
export default {
  data() {
    return {
      value: '',
      dataSource: [],
    };
  },
  watch: {
    value(val) {
      console.log('value', val);
    },
  },
  methods: {
    onSearch(searchText) {
      this.dataSource = !searchText ? [] : [searchText, searchText.repeat(2), searchText.repeat(3)];
    },
    onSelect(value) {
      console.log('onSelect', value);
    },
    onChange(value) {
      console.log('onChange', value);
    },
  },
};
</script>
```

##### 自定义输入组件 
自定义输入组件。

```html
<template>
  <h-auto-complete
    :dath-source="dataSource"
    style="width: 200px"
    @search="handleSearch"
    @select="onSelect"
  >
    <h-textarea
      placeholder="input here"
      class="custom"
      style="height: 50px"
      @keypress="handleKeyPress"
    />
  </h-auto-complete>
</template>
<script>
export default {
  data() {
    return {
      dataSource: [],
    };
  },
  methods: {
    onSelect(value) {
      console.log('onSelect', value);
    },
    handleSearch(value) {
      this.dataSource = !value ? [] : [value, value + value, value + value + value];
    },
    handleKeyPress(ev) {
      console.log('handleKeyPress', ev);
    },
  },
};
</script>
```

##### 自定义选项 
也可以直接传递slot="dataSource"的Option

```html
<template>
  <h-auto-complete style="width: 200px" placeholder="input here" @search="handleSearch">
    <template slot="dataSource">
      <h-select-option v-for="email in result" :key="email">
        {{ email }}
      </h-select-option>
    </template>
  </h-auto-complete>
</template>
<script>
export default {
  data() {
    return {
      result: [],
    };
  },
  methods: {
    handleSearch(value) {
      let result;
      if (!value || value.indexOf('@') >= 0) {
        result = [];
      } else {
        result = ['gmail.com', '163.com', 'qq.com'].map(domain => `${value}@${domain}`);
      }
      this.result = result;
    },
  },
};
</script>
```

##### 查询模式 - 确定类目
查询模式 - 确定类目

```html
<template>
  <div class="certain-category-search-wrapper" style="width: 250px">
    <h-auto-complete
      class="certain-category-search"
      dropdown-class-name="certain-category-search-dropdown"
      :dropdown-match-select-width="false"
      :dropdown-style="{ width: '300px' }"
      size="large"
      style="width: 100%"
      placeholder="input here"
      option-label-prop="value"
    >
      <template slot="dataSource">
        <h-select-opt-group v-for="group in dataSource" :key="group.title">
          <span slot="label">
            {{ group.title }}
            <a
              style="float: right"
              href="https://www.google.com/search?q=antd"
              target="_blank"
              rel="noopener noreferrer"
              >more
            </a>
          </span>
          <h-select-option v-for="opt in group.children" :key="opt.title" :value="opt.title">
            {{ opt.title }}
            <span class="certain-search-item-count">{{ opt.count }} people</span>
          </h-select-option>
        </h-select-opt-group>
        <h-select-option key="all" disabled class="show-all">
          <a
            href="https://www.google.com/search?q=ant-design-vue"
            target="_blank"
            rel="noopener noreferrer"
          >
            View all results
          </a>
        </h-select-option>
      </template>
      <h-input>
        <h-icon slot="suffix" type="search" class="certain-category-icon" />
      </h-input>
    </h-auto-complete>
  </div>
</template>
<script>
const dataSource = [
  {
    title: 'Libraries',
    children: [
      {
        title: 'AntDesign',
        count: 10000,
      },
      {
        title: 'AntDesign UI',
        count: 10600,
      },
    ],
  },
  {
    title: 'Solutions',
    children: [
      {
        title: 'AntDesign UI',
        count: 60100,
      },
      {
        title: 'AntDesign',
        count: 30010,
      },
    ],
  },
  {
    title: 'Articles',
    children: [
      {
        title: 'AntDesign design language',
        count: 100000,
      },
    ],
  },
];
export default {
  data() {
    return {
      dataSource,
    };
  },
};
</script>
<style>
.certain-category-search-dropdown .ant-select-dropdown-menu-item-group-title {
  color: #666;
  font-weight: bold;
}

.certain-category-search-dropdown .ant-select-dropdown-menu-item-group {
  border-bottom: 1px solid #f6f6f6;
}

.certain-category-search-dropdown .ant-select-dropdown-menu-item {
  padding-left: 16px;
}

.certain-category-search-dropdown .ant-select-dropdown-menu-item.show-all {
  text-align: center;
  cursor: default;
}

.certain-category-search-dropdown .ant-select-dropdown-menu {
  max-height: 300px;
}
</style>
<style scoped>
.certain-category-search-wrapper
  >>> .certain-category-search.ant-select-auto-complete
  .ant-input-affix-wrapper
  .ant-input-suffix {
  right: 12px;
}
.certain-category-search-wrapper >>> .certain-search-item-count {
  position: absolute;
  color: #999;
  right: 16px;
}
.certain-category-search-wrapper
  >>> .certain-category-search.ant-select-focused
  .certain-category-icon {
  color: #108ee9;
}
.certain-category-search-wrapper >>> .certain-category-icon {
  color: #6e6e6e;
  transition: all 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
  font-size: 16px;
}
</style>
```

##### 不区分大小写 
不区分大小写的 AutoComplete

```html
<template>
  <h-auto-complete
    :dath-source="dataSource"
    style="width: 200px"
    placeholder="input here"
    :filter-option="filterOption"
  />
</template>
<script>
export default {
  data() {
    return {
      dataSource: ['Burns Bay Road', 'Downing Street', 'Wall Street'],
    };
  },
  methods: {
    filterOption(input, option) {
      return (
        option.componentOptions.children[0].text.toUpperCase().indexOf(input.toUpperCase()) >= 0
      );
    },
  },
};
</script>
```

##### 查询模式 - 不确定类目 
查询模式 - 不确定类目

```html
<template>
  <div class="global-search-wrapper" style="width: 300px">
    <h-auto-complete
      class="global-search"
      size="large"
      style="width: 100%"
      placeholder="input here"
      option-label-prop="title"
      @select="onSelect"
      @search="handleSearch"
    >
      <template slot="dataSource">
        <h-select-option v-for="item in dataSource" :key="item.category" :title="item.category">
          Found {{ item.query }} on
          <a
            :href="`https://s.taobao.com/search?q=${item.query}`"
            target="_blank"
            rel="noopener noreferrer"
          >
            {{ item.category }}
          </a>
          <span className="global-search-item-count">{{ item.count }} results</span>
        </h-select-option>
      </template>
      <h-input>
        <h-button
          slot="suffix"
          style="margin-right: -12px"
          class="search-btn"
          size="large"
          type="primary"
        >
          <h-icon type="search" />
        </h-button>
      </h-input>
    </h-auto-complete>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dataSource: [],
    };
  },
  methods: {
    onSelect(value) {
      console.log('onSelect', value);
    },

    handleSearch(value) {
      this.dataSource = value ? this.searchResult(value) : [];
    },

    getRandomInt(max, min = 0) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },

    searchResult(query) {
      return new Array(this.getRandomInt(5))
        .join('.')
        .split('.')
        .map((item, idx) => ({
          query,
          category: `${query}${idx}`,
          count: this.getRandomInt(200, 100),
        }));
    },
  },
};
</script>

<style>
.global-search-wrapper {
  padding-right: 50px;
}

.global-search {
  width: 100%;
}

.global-search.ant-select-auto-complete .ant-select-selection--single {
  margin-right: -46px;
}

.global-search.ant-select-auto-complete .ant-input-affix-wrapper .ant-input:not(:last-child) {
  padding-right: 62px;
}

.global-search.ant-select-auto-complete .ant-input-affix-wrapper .ant-input-suffix button {
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
}

.global-search-item {
  display: flex;
}

.global-search-item-desc {
  flex: auto;
  text-overflow: ellipsis;
  overflow: hidden;
}

.global-search-item-count {
  flex: none;
}
</style>
```

### API 
```html
<h-auto-complete :dataSource="dataSource" />
```

| 参数                          | 说明                                                         | 类型                                                         | 默认值      | 版本  |
| :---------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------- | :---- |
| allowClear                    | 支持清除, 单选模式有效                                       | boolean                                                      | false       |       |
| autoFocus                     | 自动获取焦点                                                 | boolean                                                      | false       |       |
| backfill                      | 使用键盘选择选项的时候把选中项回填到输入框中                 | boolean                                                      | false       |       |
| slot="default" (自定义输入框) | 自定义输入框                                                 | HTMLInputElement / HTMLTextAreaElement                       | `<Input />` |       |
| dataSource                    | 自动完成的数据源                                             | slot \| [DataSourceItemType](https://github.com/vueComponent/ant-design-vue/blob/724d53b907e577cf5880c1e6742d4c3f924f8f49/components/auto-complete/index.vue#L9)[] |             |       |
| dropdownMenuStyle             | dropdown 菜单自定义样式                                      | object                                                       |             | 1.5.0 |
| defaultActiveFirstOption      | 是否默认高亮第一个选项。                                     | boolean                                                      | true        |       |
| defaultValue                  | 指定默认选中的条目                                           | string\|string[]\| 无                                        |             |       |
| disabled                      | 是否禁用                                                     | boolean                                                      | false       |       |
| filterOption                  | 是否根据输入项进行筛选。当其为一个函数时，会接收 `inputValue` `option` 两个参数，当 `option` 符合筛选条件时，应返回 `true`，反之则返回 `false`。 | boolean or function(inputValue, option)                      | true        |       |
| optionLabelProp               | 回填到选择框的 Option 的属性值，默认是 Option 的子元素。比如在子元素需要高亮效果时，此值可以设为 `value`。 | string                                                       | `children`  |       |
| placeholder                   | 输入框提示                                                   | string \| slot                                               | -           |       |
| value(v-model)                | 指定当前选中的条目                                           | string\|string[]\|{ key: string, label: string\|vNodes }\|Array<{ key: string, label: string\|vNodes }> | 无          |       |
| defaultOpen                   | 是否默认展开下拉菜单                                         | boolean                                                      | -           |       |
| open                          | 是否展开下拉菜单                                             | boolean                                                      | -           |       |

#### 事件
| 事件名称              | 说明                                              | 回调参数                | 版本 |
| :-------------------- | :------------------------------------------------ | :---------------------- | :--- |
| change                | 选中 option，或 input 的 value 变化时，调用此函数 | function(value)         |      |
| blur                  | 失去焦点时的回调                                  | function()              |      |
| focus                 | 获得焦点时的回调                                  | function()              |      |
| search                | 搜索补全项的时候调用                              | function(value)         |      |
| select                | 被选中时调用，参数为选中项的 value 值             | function(value, option) |      |
| dropdownVisibleChange | 展开下拉菜单的回调                                | function(open)          |      |

### 方法 
| 名称    | 描述     | 版本 |
| :------ | :------- | :--- |
| blur()  | 移除焦点 |      |
| focus() | 获取焦点 |      |

## 级联选择
级联选择框。

### 何时使用
- 需要从一组相关联的数据集合进行选择，例如省市区，公司层级，事物分类等。

- 从一个较大的数据集合中进行选择时，用多级分类进行分隔，方便选择。

- 比起 Select 组件，可以在同一个浮层中完成选择，有较好的体验。

### 代码演示
##### 基本
省市区级联。

```html
<template>
  <h-cascader :options="options" placeholder="Please select" @change="onChange" />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 自定义已选项
例如给最后一项加上邮编链接。

```html
<template>
  <h-cascader
    :options="options"
    :default-value="['zhejiang', 'hangzhou', 'xihu']"
    style="width: 100%"
  >
    <template slot="displayRender" slot-scope="{ labels, selectedOptions }">
      <span v-for="(label, index) in labels" :key="selectedOptions[index].value">
        <span v-if="index === labels.length - 1">
          {{ label }} (<a @click="e => handleAreaClick(e, label, selectedOptions[index])">{{
            selectedOptions[index].code
          }}</a
          >)
        </span>
        <span v-else @click="onChange"> {{ label }} / </span>
      </span>
    </template>
  </h-cascader>
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                  code: 752100,
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                  code: 453400,
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
    handleAreaClick(e, label, option) {
      e.stopPropagation();
      console.log('clicked', label, option);
    },
  },
};
</script>
```

##### 默认值 
默认值通过数组的方式指定。

```html
<template>
  <h-cascader
    :options="options"
    :default-value="['zhejiang', 'hangzhou', 'xihu']"
    @change="onChange"
  />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 移入展开
通过移入展开下级菜单，点击完成选择。

```html
<template>
  <h-cascader
    :options="options"
    :display-render="displayRender"
    expand-trigger="hover"
    placeholder="Please select"
    @change="onChange"
  />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
    displayRender({ labels }) {
      return labels[labels.length - 1];
    },
  },
};
</script>
```

##### 搜索 
可以直接搜索选项并选择。

> `Cascader[showSearch]` 暂不支持服务端搜索，更多信息见 [#5547](https://github.com/ant-design/ant-design/issues/5547)

```html
<template>
  <h-cascader
    :options="options"
    :show-search="{ filter }"
    placeholder="Please select"
    @change="onChange"
  />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
                {
                  value: 'xiasha',
                  label: 'Xia Sha',
                  disabled: true,
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value, selectedOptions) {
      console.log(value, selectedOptions);
    },
    filter(inputValue, path) {
      return path.some(option => option.label.toLowerCase().indexOf(inputValue.toLowerCase()) > -1);
    },
  },
};
</script>
```

##### 自定义字段名 
自定义字段名。

```html
<template>
  <h-cascader
    :field-names="{ label: 'name', value: 'code', children: 'items' }"
    :options="options"
    placeholder="Please select"
    @change="onChange"
  />
</template>
<script>
const options = [
  {
    code: 'zhejiang',
    name: 'Zhejiang',
    items: [
      {
        code: 'hangzhou',
        name: 'Hangzhou',
        items: [
          {
            code: 'xihu',
            name: 'West Lake',
          },
        ],
      },
    ],
  },
  {
    code: 'jiangsu',
    name: 'Jiangsu',
    items: [
      {
        code: 'nanjing',
        name: 'Nanjing',
        items: [
          {
            code: 'zhonghuamen',
            name: 'Zhong Hua Men',
          },
        ],
      },
    ],
  },
];
export default {
  data() {
    return {
      options,
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 选择即改变
这种交互允许只选中父级选项。

```html
<template>
  <h-cascader :options="options" change-on-select @change="onChange" />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 可以自定义显示
切换按钮和结果分开。

```html
<template>
  <span>
    {{ text }} &nbsp;
    <h-cascader :options="options" @change="onChange">
      <a href="#">Change city</a>
    </h-cascader>
  </span>
</template>
<script>
export default {
  data() {
    return {
      text: 'Unselect',
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value, selectedOptions) {
      this.text = selectedOptions.map(o => o.label).join(', ');
    },
  },
};
</script>
```

##### 禁用选项 
通过指定 options 里的 `disabled` 字段。

```html
<template>
  <h-cascader :options="options" @change="onChange" />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          disabled: true,
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 动态加载选项 
使用 `loadData` 实现动态加载选项。

> 注意：`loadData` 与 `showSearch` 无法一起使用。

```html
<template>
  <h-cascader
    :options="options"
    :load-data="loadData"
    placeholder="Please select"
    change-on-select
    @change="onChange"
  />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          isLeaf: false,
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          isLeaf: false,
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
    loadData(selectedOptions) {
      const targetOption = selectedOptions[selectedOptions.length - 1];
      targetOption.loading = true;

      // load options lazily
      setTimeout(() => {
        targetOption.loading = false;
        targetOption.children = [
          {
            label: `${targetOption.label} Dynamic 1`,
            value: 'dynamic1',
          },
          {
            label: `${targetOption.label} Dynamic 2`,
            value: 'dynamic2',
          },
        ];
        this.options = [...this.options];
      }, 1000);
    },
  },
};
</script>
```

##### 大小 
不同大小的级联选择器。

```html
<template>
  <div>
    <h-cascader size="large" :options="options" @change="onChange" /><br /><br />
    <h-cascader :options="options" @change="onChange" /><br /><br />
    <h-cascader size="small" :options="options" @change="onChange" /><br /><br />
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 后缀图标 
省市区级联。

```html
<template>
  <div>
    <h-cascader
      style="margin-top: 1rem"
      :options="options"
      placeholder="Please select"
      @change="onChange"
    >
      <h-icon slot="suffixIcon" type="smile" class="test" />
    </h-cascader>
    <h-cascader
      suffix-icon="ab"
      style="margin-top: 1rem"
      :options="options"
      placeholder="Please select"
      @change="onChange"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: 'zhejiang',
          label: 'Zhejiang',
          children: [
            {
              value: 'hangzhou',
              label: 'Hangzhou',
              children: [
                {
                  value: 'xihu',
                  label: 'West Lake',
                },
              ],
            },
          ],
        },
        {
          value: 'jiangsu',
          label: 'Jiangsu',
          children: [
            {
              value: 'nanjing',
              label: 'Nanjing',
              children: [
                {
                  value: 'zhonghuamen',
                  label: 'Zhong Hua Men',
                },
              ],
            },
          ],
        },
      ],
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
    },
  },
};
</script>
```

### API 
```html
<h-cascader :options="options" @change="onChange" />
```

| 参数              | 说明                                                         | 类型                                   | 默认值                                                     |
| :---------------- | :----------------------------------------------------------- | :------------------------------------- | :--------------------------------------------------------- |
| allowClear        | 是否支持清除                                                 | boolean                                | true                                                       |
| autoFocus         | 自动获取焦点                                                 | boolean                                | false                                                      |
| changeOnSelect    | 当此项为 true 时，点选每级菜单选项值都会发生变化，具体见上面的演示 | boolean                                | false                                                      |
| defaultValue      | 默认的选中项                                                 | string[] \| number[]                   | []                                                         |
| disabled          | 禁用                                                         | boolean                                | false                                                      |
| displayRender     | 选择后展示的渲染函数,可使用 slot="displayRender" 和 slot-scope="{labels, selectedOptions}" | `({labels, selectedOptions}) => vNode` | `labels => labels.join(' / ')`                             |
| expandTrigger     | 次级菜单的展开方式，可选 'click' 和 'hover'                  | string                                 | 'click'                                                    |
| fieldNames        | 自定义 options 中 label name children 的字段                 | object                                 | `{ label: 'label', value: 'value', children: 'children' }` |
| getPopupContainer | 菜单渲染父节点。默认渲染到 body 上，如果你遇到菜单滚动定位问题，试试修改为滚动的区域，并相对其定位。 | Function(triggerNode)                  | () => document.body                                        |
| loadData          | 用于动态加载选项，无法与 `showSearch` 一起使用               | `(selectedOptions) => void`            | -                                                          |
| notFoundContent   | 当下拉列表为空时显示的内容                                   | string                                 | 'Not Found'                                                |
| options           | 可选项数据源                                                 | object                                 | -                                                          |
| placeholder       | 输入框占位文本                                               | string                                 | '请选择'                                                   |
| popupClassName    | 自定义浮层类名                                               | string                                 | -                                                          |
| popupStyle        | 自定义浮层样式                                               | object                                 | {}                                                         |
| popupPlacement    | 浮层预设位置：`bottomLeft` `bottomRight` `topLeft` `topRight` | Enum                                   | `bottomLeft`                                               |
| popupVisible      | 控制浮层显隐                                                 | boolean                                | -                                                          |
| showSearch        | 在选择框中显示搜索框                                         | boolean                                | false                                                      |
| size              | 输入框大小，可选 `large` `default` `small`                   | string                                 | `default`                                                  |
| suffixIcon        | 自定义的选择框后缀图标                                       | string \| VNode \| slot                | -                                                          |
| value(v-model)    | 指定选中项                                                   | string[] \| number[]                   | -                                                          |

`showSearch` 为对象时，其中的字段：

| 参数            | 说明                                                         | 类型                                  | 默认值 |
| :-------------- | :----------------------------------------------------------- | :------------------------------------ | :----- |
| filter          | 接收 `inputValue` `path` 两个参数，当 `path` 符合筛选条件时，应返回 true，反之则返回 false。 | `function(inputValue, path): boolean` |        |
| limit           | 搜索结果展示数量                                             | number \| false                       | 50     |
| matchInputWidth | 搜索结果列表是否与输入框同宽                                 | boolean                               |        |
| render          | 用于渲染 filter 后的选项,可使用 slot="showSearchRender" 和 slot-scope="{inputValue, path}" | `function({inputValue, path}): vNode` |        |
| sort            | 用于排序 filter 后的选项                                     | `function(a, b, inputValue)`          |        |

#### 事件 
| 事件名称           | 说明                | 回调参数                           | 版本 |
| :----------------- | :------------------ | :--------------------------------- | :--- |
| change             | 选择完成后的回调    | `(value, selectedOptions) => void` | -    |
| popupVisibleChange | 显示/隐藏浮层的回调 | `(value) => void`                  | -    |
| search             | 输入框变化时的回调  | `(value) => void`                  | -    |

### 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

> 注意，如果需要获得中国省市区数据，可以参考 react 组件的实现 [chinh-division](https://gist.github.com/afc163/7582f35654fd03d5be7009444345ea17)。

## 多选框
多选框

### 何时使用
- 在一组可选项中进行多项选择时；

- 单独使用可以表示两种状态之间的切换，和 switch 类似。区别在于切换 switch 会直接触发状态改变，而 checkbox 一般用于状态标记，需要和提交操作配合。

### 代码演示
##### 基本用法 
简单的checkbox

```html
<template>
  <h-checkbox @change="onChange">
    Checkbox
  </h-checkbox>
</template>
<script>
export default {
  methods: {
    onChange(e) {
      console.log(`checked = ${e.target.checked}`);
    },
  },
};
</script>
```

##### 不可用 
checkbox 不可用

```html
<template>
  <div>
    <h-checkbox :default-checked="false" disabled />
    <br />
    <h-checkbox default-checked disabled />
  </div>
</template>
```

##### Checkbox组
方便的从数组生成checkbox

```html
<template>
  <div>
    <h-checkbox-group
      v-model="value"
      name="checkboxgroup"
      :options="plainOptions"
      @change="onChange"
    />
    <br />
    <h-checkbox-group :options="plainOptions" :default-value="['Apple']" @change="onChange" />
    <br />
    <h-checkbox-group :options="options" :value="['Pear']" @change="onChange" />
    <br />
    <h-checkbox-group
      :options="optionsWithDisabled"
      disabled
      :default-value="['Apple']"
      @change="onChange"
    >
      <span slot="label" slot-scope="{ value }" style="color: red">{{ value }}</span>
    </h-checkbox-group>
  </div>
</template>
<script>
const plainOptions = ['Apple', 'Pear', 'Orange'];
const options = [
  { label: 'Apple', value: 'Apple' },
  { label: 'Pear', value: 'Pear' },
  { label: 'Orange', value: 'Orange' },
];
const optionsWithDisabled = [
  { value: 'Apple' },
  { label: 'Pear', value: 'Pear' },
  { label: 'Orange', value: 'Orange', disabled: false },
];
export default {
  data() {
    return {
      plainOptions,
      options,
      optionsWithDisabled,
      value: [],
    };
  },
  methods: {
    onChange(checkedValues) {
      console.log('checked = ', checkedValues);
      console.log('value = ', this.value);
    },
  },
};
</script>
```

##### 全选 
在实现全选效果时，你可能会用到`indeterminate`属性

```html
<template>
  <div>
    <div :style="{ borderBottom: '1px solid #E9E9E9' }">
      <h-checkbox :indeterminate="indeterminate" :checked="checkAll" @change="onCheckAllChange">
        Check all
      </h-checkbox>
    </div>
    <br />
    <h-checkbox-group v-model="checkedList" :options="plainOptions" @change="onChange" />
  </div>
</template>
<script>
const plainOptions = ['Apple', 'Pear', 'Orange'];
const defaultCheckedList = ['Apple', 'Orange'];
export default {
  data() {
    return {
      checkedList: defaultCheckedList,
      indeterminate: true,
      checkAll: false,
      plainOptions,
    };
  },
  methods: {
    onChange(checkedList) {
      this.indeterminate = !!checkedList.length && checkedList.length < plainOptions.length;
      this.checkAll = checkedList.length === plainOptions.length;
    },
    onCheckAllChange(e) {
      Object.assign(this, {
        checkedList: e.target.checked ? plainOptions : [],
        indeterminate: false,
        checkAll: e.target.checked,
      });
    },
  },
};
</script>
```

##### 受控的checkbox 
联动checkbox

```html
<template>
  <div>
    <p :style="{ marginBottom: '20px' }">
      <h-checkbox :checked="checked" :disabled="disabled" @change="onChange">
        {{ label }}
      </h-checkbox>
    </p>
    <p>
      <h-button type="primary" size="small" @click="toggleChecked">
        {{ !checked ? 'Check' : 'Uncheck' }}
      </h-button>
      <h-button :style="{ marginLeft: '10px' }" type="primary" size="small" @click="toggleDisable">
        {{ !disabled ? 'Disable' : 'Enable' }}
      </h-button>
    </p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      checked: true,
      disabled: false,
    };
  },
  computed: {
    label() {
      const { checked, disabled } = this;
      return `${checked ? 'Checked' : 'Unchecked'}-${disabled ? 'Disabled' : 'Enabled'}`;
    },
  },
  methods: {
    toggleChecked() {
      this.checked = !this.checked;
    },
    toggleDisable() {
      this.disabled = !this.disabled;
    },
    onChange(e) {
      this.checked = e.target.checked;
    },
  },
};
</script>
```

##### 布局
Checkbox.Group内嵌Checkbox并与Grid组件一起使用，可以实现灵活的布局

```html
<template>
  <h-checkbox-group @change="onChange">
    <h-row>
      <h-col :span="8">
        <h-checkbox value="A">
          A
        </h-checkbox>
      </h-col>
      <h-col :span="8">
        <h-checkbox value="B">
          B
        </h-checkbox>
      </h-col>
      <h-col :span="8">
        <h-checkbox value="C">
          C
        </h-checkbox>
      </h-col>
      <h-col :span="8">
        <h-checkbox value="D">
          D
        </h-checkbox>
      </h-col>
      <h-col :span="8">
        <h-checkbox value="E">
          E
        </h-checkbox>
      </h-col>
    </h-row>
  </h-checkbox-group>
</template>
<script>
export default {
  methods: {
    onChange(checkedValues) {
      console.log('checked = ', checkedValues);
    },
  },
};
</script>
```

### API 
#### 属性
##### Checkbox 
| 参数           | 说明                                    | 类型    | 默认值 | 版本 |
| :------------- | :-------------------------------------- | :------ | :----- | :--- |
| autoFocus      | 自动获取焦点                            | boolean | false  |      |
| checked        | 指定当前是否选中                        | boolean | false  |      |
| defaultChecked | 初始是否选中                            | boolean | false  |      |
| disabled       | 失效状态                                | boolean | false  |      |
| indeterminate  | 设置 indeterminate 状态，只负责样式控制 | boolean | false  |      |

##### 事件 
| 事件名称 | 说明           | 回调参数          | 版本 |
| :------- | :------------- | :---------------- | :--- |
| change   | 变化时回调函数 | Function(e:Event) | -    |

##### Checkbox Group
| 参数         | 说明                                                         | 类型                                                         | 默认值 | 版本  |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----- | :---- |
| defaultValue | 默认选中的选项                                               | string[]                                                     | []     |       |
| disabled     | 整组失效                                                     | boolean                                                      | false  |       |
| name         | CheckboxGroup 下所有 `input[type="checkbox"]` 的 `name` 属性 | string                                                       | -      | 1.5.0 |
| options      | 指定可选项，可以通过 slot="label" slot-scope="option" 定制`label` | string[] \| Array<{ label: string value: string disabled?: boolean, indeterminate?: boolean, onChange?: function }> | []     |       |
| value        | 指定选中的选项                                               | string[]                                                     | []     |       |

##### 事件 
| 事件名称 | 说明           | 回调参数               | 版本 |
| :------- | :------------- | :--------------------- | :--- |
| change   | 变化时回调函数 | Function(checkedValue) | -    |

#### 方法
##### Checkbox 
| 名称    | 描述     | 版本 |
| :------ | :------- | :--- |
| blur()  | 移除焦点 |      |
| focus() | 获取焦点 |      |

## 日期选择器
输入或选择日期的控件。

### 何时使用
当用户需要输入一个日期，可以点击标准输入框，弹出日期面板进行选择。

### 代码演示
##### 基本 
最简单的用法，在浮层中可以选择或者输入日期。

```html
<template>
  <div>
    <h-date-picker @change="onChange" />
    <br />
    <h-month-picker placeholder="Select month" @change="onChange" />
    <br />
    <h-range-picker @change="onChange" />
    <br />
    <h-week-picker placeholder="Select week" @change="onChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(date, dateString) {
      console.log(date, dateString);
    },
  },
};
</script>
```

##### 不可选择日期和时间 
可用 `disabledDate` 和 `disabledTime` 分别禁止选择部分日期和时间，其中 `disabledTime` 需要和 `showTime` 一起使用。

```html
<template>
  <div>
    <h-date-picker
      format="YYYY-MM-DD HH:mm:ss"
      :disabled-date="disabledDate"
      :disabled-time="disabledDateTime"
      :show-time="{ defaultValue: moment('00:00:00', 'HH:mm:ss') }"
    />
    <br />
    <h-month-picker :disabled-date="disabledDate" placeholder="Select month" />
    <br />
    <h-range-picker
      :disabled-date="disabledDate"
      :disabled-time="disabledRangeTime"
      :show-time="{
        hideDisabledOptions: true,
        defaultValue: [moment('00:00:00', 'HH:mm:ss'), moment('11:59:59', 'HH:mm:ss')],
      }"
      format="YYYY-MM-DD HH:mm:ss"
    />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
    range(start, end) {
      const result = [];
      for (let i = start; i < end; i++) {
        result.push(i);
      }
      return result;
    },

    disabledDate(current) {
      // Can not select days before today and today
      return current && current < moment().endOf('day');
    },

    disabledDateTime() {
      return {
        disabledHours: () => this.range(0, 24).splice(4, 20),
        disabledMinutes: () => this.range(30, 60),
        disabledSeconds: () => [55, 56],
      };
    },

    disabledRangeTime(_, type) {
      if (type === 'start') {
        return {
          disabledHours: () => this.range(0, 60).splice(4, 20),
          disabledMinutes: () => this.range(30, 60),
          disabledSeconds: () => [55, 56],
        };
      }
      return {
        disabledHours: () => this.range(0, 60).splice(20, 4),
        disabledMinutes: () => this.range(0, 31),
        disabledSeconds: () => [55, 56],
      };
    },
  },
};
</script>
```

##### 额外的页脚 
在浮层中加入额外的页脚，以满足某些定制信息的需求。

```html
<template>
  <div>
    <h-date-picker>
      <template slot="renderExtraFooter">
        extra footer
      </template>
    </h-date-picker>
    <h-date-picker show-time>
      <template slot="renderExtraFooter">
        extra footer
      </template>
    </h-date-picker>
    <h-range-picker>
      <template slot="renderExtraFooter">
        extra footer
      </template>
    </h-range-picker>
    <h-range-picker show-time>
      <template slot="renderExtraFooter">
        extra footer
      </template>
    </h-range-picker>
    <h-month-picker placeholder="Select month">
      <template slot="renderExtraFooter">
        extra footer
      </template>
    </h-month-picker>
  </div>
</template>
```

##### 受控面板 
通过组合 `mode` 与 `onPanelChange` 控制要展示的面板。

```html
<template>
  <div>
    <h-date-picker
      :mode="mode1"
      show-time
      @openChange="handleOpenChange1"
      @panelChange="handlePanelChange1"
    />
    <br />
    <h-range-picker
      :placeholder="['Start month', 'End month']"
      format="YYYY-MM"
      :value="value"
      :mode="mode2"
      @panelChange="handlePanelChange2"
      @change="handleChange"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      mode1: 'time',
      mode2: ['month', 'month'],
      value: [],
    };
  },
  methods: {
    handleOpenChange1(open) {
      if (open) {
        this.mode1 = 'time';
      }
    },
    handleChange(value) {
      this.value = value;
    },
    handlePanelChange1(value, mode) {
      this.mode1 = mode;
    },
    handlePanelChange2(value, mode) {
      this.value = value;
      this.mode2 = [mode[0] === 'date' ? 'month' : mode[0], mode[1] === 'date' ? 'month' : mode[1]];
    },
  },
};
</script>
```

##### 三种大小 
三种大小的输入框，若不设置，则为 `default`。

```html
<template>
  <div>
    <h-radio-group v-model="size">
      <h-radio-button value="large">
        Large
      </h-radio-button>
      <h-radio-button value="default">
        Default
      </h-radio-button>
      <h-radio-button value="small">
        Small
      </h-radio-button>
    </h-radio-group>
    <br /><br />
    <h-date-picker :size="size" />
    <br />
    <h-month-picker :size="size" placeholder="Select Month" />
    <br />
    <h-range-picker :size="size" />
    <br />
    <h-week-picker :size="size" placeholder="Select Week" />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      size: 'default',
    };
  },
};
</script>
```

##### 日期时间选择 
增加选择时间功能，当 `showTime` 为一个对象时，其属性会传递给内建的 `TimePicker`。

```html
<template>
  <div>
    <h-date-picker show-time placeholder="Select Time" @change="onChange" @ok="onOk" />
    <br />
    <h-range-picker
      :show-time="{ format: 'HH:mm' }"
      format="YYYY-MM-DD HH:mm"
      :placeholder="['Start Time', 'End Time']"
      @change="onChange"
      @ok="onOk"
    />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(value, dateString) {
      console.log('Selected Time: ', value);
      console.log('Formatted Selected Time: ', dateString);
    },
    onOk(value) {
      console.log('onOk: ', value);
    },
  },
};
</script>
```

##### 后缀图标 
最简单的用法，在浮层中可以选择或者输入日期。

```html
<template>
  <div>
    <h-date-picker @change="onChange">
      <h-icon slot="suffixIcon" type="smile" />
    </h-date-picker>
    <br />
    <h-month-picker placeholder="Select month" @change="onChange">
      <h-icon slot="suffixIcon" type="smile" />
    </h-month-picker>
    <br />
    <h-range-picker @change="onChange">
      <h-icon slot="suffixIcon" type="smile" />
    </h-range-picker>
    <br />
    <h-week-picker placeholder="Select week" @change="onChange">
      <h-icon slot="suffixIcon" type="smile" />
    </h-week-picker>
    <br />
    <h-date-picker suffix-icon="ab" @change="onChange" />
    <br />
    <h-month-picker suffix-icon="ab" placeholder="Select month" @change="onChange" />
    <br />
    <h-range-picker suffix-icon="ab" @change="onChange" />
    <br />
    <h-week-picker suffix-icon="ab" placeholder="Select week" @change="onChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(date, dateString) {
      console.log(date, dateString);
    },
  },
};
</script>
```

##### 定制日期单元格 
使用 `dateRender` 可以自定义日期单元格的内容和样式。

```html
<template>
  <div>
    <h-date-picker>
      <template slot="dateRender" slot-scope="current, today">
        <div class="ant-calendar-date" :style="getCurrentStyle(current, today)">
          {{ current.date() }}
        </div>
      </template>
    </h-date-picker>
    <h-range-picker>
      <template slot="dateRender" slot-scope="current">
        <div class="ant-calendar-date" :style="getCurrentStyle(current)">
          {{ current.date() }}
        </div>
      </template>
    </h-range-picker>
    <h-week-picker>
      <template slot="dateRender" slot-scope="current">
        <div class="ant-calendar-date" :style="getCurrentStyle(current)">
          {{ current.date() }}
        </div>
      </template>
    </h-week-picker>
  </div>
</template>
<script>
export default {
  methods: {
    getCurrentStyle(current, today) {
      const style = {};
      if (current.date() === 1) {
        style.border = '1px solid #1890ff';
        style.borderRadius = '50%';
      }
      return style;
    },
  },
};
</script>
```

##### 禁用 
选择框的不可用状态。

```html
<template>
  <div>
    <h-date-picker :default-value="moment('2015-06-06', dateFormat)" disabled />
    <br />
    <h-month-picker :default-value="moment('2015-06', 'YYYY-MM')" disabled />
    <br />
    <h-range-picker
      :default-value="[moment('2015-06-06', dateFormat), moment('2015-06-06', dateFormat)]"
      disabled
    />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    this.dateFormat = 'YYYY-MM-DD';
    return {};
  },
  methods: {
    moment,
  },
};
</script>
```

##### 日期格式 
使用 `format` 属性，可以自定义日期显示格式。

```html
<template>
  <div>
    <h-date-picker :default-value="moment('2015/01/01', dateFormat)" :format="dateFormat" />
    <br />
    <h-date-picker
      :default-value="moment('01/01/2015', dateFormatList[0])"
      :format="dateFormatList"
    />
    <br />
    <h-month-picker :default-value="moment('2015/01', monthFormat)" :format="monthFormat" />
    <br />
    <h-range-picker
      :default-value="[moment('2015/01/01', dateFormat), moment('2015/01/01', dateFormat)]"
      :format="dateFormat"
    />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      dateFormat: 'YYYY/MM/DD',
      monthFormat: 'YYYY/MM',
      dateFormatList: ['DD/MM/YYYY', 'DD/MM/YY'],
    };
  },
  methods: {
    moment,
  },
};
</script>
```

##### 预设范围 
可以预设常用的日期范围以提高用户体验。

```html
<template>
  <div>
    <h-range-picker
      :ranges="{ Today: [moment(), moment()], 'This Month': [moment(), moment().endOf('month')] }"
      @change="onChange"
    />
    <br />
    <h-range-picker
      :ranges="{ Today: [moment(), moment()], 'This Month': [moment(), moment().endOf('month')] }"
      show-time
      format="YYYY/MM/DD HH:mm:ss"
      @change="onChange"
    />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      dateFormat: 'YYYY/MM/DD',
      monthFormat: 'YYYY/MM',
    };
  },
  methods: {
    moment,
    onChange(dates, dateStrings) {
      console.log('From: ', dates[0], ', to: ', dates[1]);
      console.log('From: ', dateStrings[0], ', to: ', dateStrings[1]);
    },
  },
};
</script>
```

##### 自定义日期范围选择 
当 `RangePicker` 无法满足业务需求时，可以使用两个 `DatePicker` 实现类似的功能。

> - 通过设置 `disabledDate` 方法，来约束开始和结束日期。
> - 通过 `open` `openChange` 来优化交互。

```html
<template>
  <div>
    <h-date-picker
      v-model="startValue"
      :disabled-date="disabledStartDate"
      show-time
      format="YYYY-MM-DD HH:mm:ss"
      placeholder="Start"
      @openChange="handleStartOpenChange"
    />
    <h-date-picker
      v-model="endValue"
      :disabled-date="disabledEndDate"
      show-time
      format="YYYY-MM-DD HH:mm:ss"
      placeholder="End"
      :open="endOpen"
      @openChange="handleEndOpenChange"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      startValue: null,
      endValue: null,
      endOpen: false,
    };
  },
  watch: {
    startValue(val) {
      console.log('startValue', val);
    },
    endValue(val) {
      console.log('endValue', val);
    },
  },
  methods: {
    disabledStartDate(startValue) {
      const endValue = this.endValue;
      if (!startValue || !endValue) {
        return false;
      }
      return startValue.valueOf() > endValue.valueOf();
    },
    disabledEndDate(endValue) {
      const startValue = this.startValue;
      if (!endValue || !startValue) {
        return false;
      }
      return startValue.valueOf() >= endValue.valueOf();
    },
    handleStartOpenChange(open) {
      if (!open) {
        this.endOpen = true;
      }
    },
    handleEndOpenChange(open) {
      this.endOpen = open;
    },
  },
};
</script>
```

##### 自定义渲染 
增加自定义渲染功能，在默认 `slot` 中，你可以设置任何你想渲染的组件。

```html
<template>
  <div>
    <h-date-picker v-model="time1" placeholder="Select Time" @change="onChange" @ok="onOk">
      <span>{{ time1 ? time1 : 'SelectTime' }}</span>
    </h-date-picker>
    <br />
    <h-range-picker v-model="time2">
      <span>
        {{ time2 ? time2 : '请选择' }}
      </span>
    </h-range-picker>
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      time1: undefined,
      time2: undefined,
    };
  },
  methods: {
    onChange(value, dateString) {
      console.log('Selected Time: ', value);
      console.log('Formatted Selected Time: ', dateString);
    },
    onOk(value) {
      console.log('onOk: ', value);
    },
    clearTime() {
      this.time1 = undefined;
    },
  },
};
</script>
```

### API 
日期类组件包括以下四种形式。

- DatePicker
- MonthPicker
- RangePicker
- WeekPicker

#### 国际化配置 
默认配置为 en-US，如果你需要设置其他语言，推荐在入口处使用我们提供的国际化组件，详见：[ConfigProvider 国际化](http://ant.design/components/config-provider-cn/)。

如有特殊需求（仅修改单一组件的语言），请使用 locale 参数，参考：[默认配置](https://github.com/ant-design/ant-design/blob/master/components/date-picker/locale/example.json)。

```html
<template>
  <h-date-picker :locale="locale" />
</template>
<script>
  import locale from 'ant-design-vue/es/date-picker/locale/zh_CN';
  export default {
    data() {
      return {
        locale,
      };
    },
  };
</script>
```

**注意：**DatePicker、MonthPicker、RangePicker、WeekPicker 部分 locale 是从 value 中读取，所以请先正确设置 moment 的 locale。

```html
<template>
  <h-date-picker :defaultValue="moment('2015-01-01', 'YYYY-MM-DD')" />
</template>
<script>
  // 默认语言为 en-US，如果你需要设置其他语言，推荐在入口文件全局设置 locale
  import moment from 'moment';
  import 'moment/locale/zh-cn';
  export default {
    data() {
      return {
        moment,
      };
    },
  };
</script>
```

#### 共同的 API 
以下 API 为 DatePicker、MonthPicker、RangePicker, WeekPicker 共享的 API。

| 参数                 | 说明                                                         | 类型                                                         | 默认值                                                       | 版本  |
| :------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---- |
| allowClear           | 是否显示清除按钮                                             | boolean                                                      | true                                                         | -     |
| autoFocus            | 自动获取焦点                                                 | boolean                                                      | false                                                        | -     |
| dateRender           | 作用域插槽，自定义日期单元格的内容                           | slot="dateRender" slot-scope="current, today"                | -                                                            | -     |
| disabled             | 禁用                                                         | boolean                                                      | false                                                        | -     |
| disabledDate         | 不可选择的日期                                               | (currentDate: moment) => boolean                             | 无                                                           | -     |
| getCalendarContainer | 定义浮层的容器，默认为 body 上新建 div                       | function(trigger)                                            | 无                                                           | -     |
| locale               | 国际化配置                                                   | object                                                       | [默认配置](https://github.com/vueComponent/ant-design-vue/blob/master/components/date-picker/locale/example.json) | -     |
| mode                 | 日期面板的状态（[设置后无法选择年份/月份？](https://1x.antdv.com/docs/vue/faq#当我指定了-DatePicker/RangePicker-的-mode-属性后，点击后无法选择年份/月份？)） | `time|date|month|year|decade`                                | 'date'                                                       | -     |
| open                 | 控制弹层是否展开                                             | boolean                                                      | -                                                            | -     |
| placeholder          | 输入框提示文字                                               | string\|RangePicker[]                                        | -                                                            | -     |
| popupStyle           | 额外的弹出日历样式                                           | object                                                       | {}                                                           | -     |
| dropdownClassName    | 额外的弹出日历 className                                     | string                                                       | -                                                            | -     |
| size                 | 输入框大小，`large` 高度为 40px，`small` 为 24px，默认是 32px | string                                                       | 无                                                           | -     |
| suffixIcon           | 自定义的选择框后缀图标                                       | VNode \| slot                                                | -                                                            | -     |
| inputReadOnly        | 设置输入框为只读（避免在移动设备上打开虚拟键盘）             | boolean                                                      | -                                                            | 1.5.4 |
| align                | 该值将合并到 placement 的配置中，设置参考 [dom-align](https://github.com/yiminghe/dom-align) | Object                                                       | 无                                                           | 1.5.4 |
| valueFormat          | 可选，绑定值的格式，对 value、defaultValue、defaultPickerValue 起作用。不指定则绑定值为 moment 对象 | string，[具体格式](https://momentjs.com/docs/#/displaying/format/) | -                                                            | 1.5.4 |

#### 共有的事件 
| 事件名称    | 说明                     | 回调参数              |
| :---------- | :----------------------- | :-------------------- |
| openChange  | 弹出日历和关闭日历的回调 | function(status)      |
| panelChange | 日期面板变化时的回调     | function(value, mode) |

#### 共同的方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

#### DatePicker 
| 参数                  | 说明                                                         | 类型                                       | 默认值                                                       |
| :-------------------- | :----------------------------------------------------------- | :----------------------------------------- | :----------------------------------------------------------- |
| defaultValue          | 默认日期                                                     | [moment](http://momentjs.com/)             | 无                                                           |
| defaultPickerValue    | 默认面板日期                                                 | [moment](http://momentjs.com/)             | 无                                                           |
| disabledTime          | 不可选择的时间                                               | function(date)                             | 无                                                           |
| format                | 设置日期格式，为数组时支持多格式匹配，展示以第一个为准。配置参考 [moment.js](http://momentjs.com/) | string \| string[]                         | "YYYY-MM-DD"                                                 |
| renderExtraFooter     | 在面板中添加额外的页脚                                       | slot="renderExtraFooter" slot-scope="mode" | -                                                            |
| showTime              | 增加时间选择功能                                             | Object\|boolean                            | [TimePicker Options](https://1x.antdv.com/components/time-picker-cn/#API) |
| showTime.defaultValue | 设置用户选择日期时默认的时分秒                               | [moment](http://momentjs.com/)             | moment()                                                     |
| showToday             | 是否展示“今天”按钮                                           | boolean                                    | true                                                         |
| value(v-model)        | 日期                                                         | [moment](http://momentjs.com/)             | 无                                                           |

#### DatePicker 事件 
| 事件名称 | 说明               | 回调参数                                             |
| :------- | :----------------- | :--------------------------------------------------- |
| change   | 时间发生变化的回调 | function(date: moment \| string, dateString: string) |
| ok       | 点击确定按钮的回调 | function()                                           |

#### MonthPicker 
| 参数                   | 说明                                                       | 类型                                                    | 默认值    |
| :--------------------- | :--------------------------------------------------------- | :------------------------------------------------------ | :-------- |
| defaultValue           | 默认日期                                                   | [moment](http://momentjs.com/)                          | 无        |
| defaultPickerValue     | 默认面板日期                                               | [moment](http://momentjs.com/)                          | 无        |
| format                 | 展示的日期格式，配置参考 [moment.js](http://momentjs.com/) | string                                                  | "YYYY-MM" |
| monthCellContentRender | 自定义的月份内容渲染方法                                   | slot="monthCellContentRender" slot-scope="date, locale" | -         |
| renderExtraFooter      | 在面板中添加额外的页脚                                     | slot="renderExtraFooter" slot-scope="mode"              | -         |
| value(v-model)         | 日期                                                       | [moment](http://momentjs.com/)                          | 无        |

#### MonthPicker 事件 
| 事件名称 | 说明                                     | 回调参数                                             |
| :------- | :--------------------------------------- | :--------------------------------------------------- |
| change   | 时间发生变化的回调，发生在用户选择时间时 | function(date: moment \| string, dateString: string) |

#### WeekPicker 
| 参数               | 说明                                                       | 类型                                       | 默认值    |
| :----------------- | :--------------------------------------------------------- | :----------------------------------------- | :-------- |
| defaultValue       | 默认日期                                                   | [moment](http://momentjs.com/)             | -         |
| defaultPickerValue | 默认面板日期                                               | [moment](http://momentjs.com/)             | 无        |
| format             | 展示的日期格式，配置参考 [moment.js](http://momentjs.com/) | string                                     | "YYYY-wo" |
| value(v-model)     | 日期                                                       | [moment](http://momentjs.com/)             | -         |
| renderExtraFooter  | 在面板中添加额外的页脚                                     | slot="renderExtraFooter" slot-scope="mode" | -         |

#### WeekPicker 事件 
| 事件名称 | 说明                                     | 回调参数                                             |
| :------- | :--------------------------------------- | :--------------------------------------------------- |
| change   | 时间发生变化的回调，发生在用户选择时间时 | function(date: moment \| string, dateString: string) |

#### RangePicker
| 参数                  | 说明                           | 类型                                                         | 默认值                                                       | 版本  |
| :-------------------- | :----------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---- |
| defaultValue          | 默认日期                       | [moment](http://momentjs.com/)[]                             | 无                                                           |       |
| defaultPickerValue    | 默认面板日期                   | [moment](http://momentjs.com/)[]                             | 无                                                           |       |
| disabledTime          | 不可选择的时间                 | function(dates: [moment, moment], partial: `'start'|'end'`)  | 无                                                           |       |
| format                | 展示的日期格式                 | string                                                       | "YYYY-MM-DD HH:mm:ss"                                        |       |
| ranges                | 预设时间范围快捷选择           | { [range: string]: [moment](http://momentjs.com/)[] } \| { [range: string]: () => [moment](http://momentjs.com/)[] } | 无                                                           |       |
| renderExtraFooter     | 在面板中添加额外的页脚         | slot="renderExtraFooter" slot-scope="mode"                   | -                                                            |       |
| separator             | 设置分隔符                     | string                                                       | '~'                                                          | 1.5.0 |
| showTime              | 增加时间选择功能               | Object\|boolean                                              | [TimePicker Options](https://1x.antdv.com/components/time-picker-cn/#API) |       |
| showTime.defaultValue | 设置用户选择日期时默认的时分秒 | [moment](http://momentjs.com/)[]                             | [moment(), moment()]                                         |       |
| value(v-model)        | 日期                           | [moment](http://momentjs.com/)[]                             | 无                                                           |       |

#### RangePicker 事件 
| 事件名称       | 说明                   | 回调参数                                                     |
| :------------- | :--------------------- | :----------------------------------------------------------- |
| calendarChange | 待选日期发生变化的回调 | function(dates: [moment, moment] \| [string, string], dateStrings: [string, string]) |
| change         | 日期范围发生变化的回调 | function(dates: [moment, moment] \| [string, string], dateStrings: [string, string]) |
| ok             | 点击确定按钮的回调     | function(dates: [moment, moment] \| [string, string])        |

## 表单
具有数据收集、校验和提交功能的表单，包含复选框、单选框、输入框、下拉选择框等元素。

##### 如需要使用 `v-model` 双向绑定式的校验功能可使用新的表单 [`h-form-model`](https://1x.antdv.com/components/form-model-cn/)。
### 何时使用
- 用于创建一个实体或收集信息。
- 需要对输入的数据类型进行校验时。

### 表单
我们为 `form` 提供了以下三种排列方式：

- 水平排列：标签和表单控件水平排列；（默认）
- 垂直排列：标签和表单控件上下垂直排列；
- 行内排列：表单项水平行内排列。

### 表单域
表单一定会包含表单域，表单域可以是输入控件，标准表单域，标签，下拉菜单，文本域等。

这里我们封装了表单域 `<Form.Item />` 。

### 注意：
1、如果使用 `Form.create` 处理表单使其具有自动收集数据并校验的功能，建议使用`jsx`。
2、如果不是使用Vue.use(Form)形式注册的`Form`组件，你需要自行将`$form`挂载到Vue原型上。
`Vue.prototype.$form = Form`

### 代码演示
##### 表单联动
使用 `setFieldsValue` 来动态设置其他控件的值。

```html
<template>
  <h-form :form="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="handleSubmit">
    <h-form-item label="Note">
      <h-input
        v-decorator="['note', { rules: [{ required: true, message: 'Please input your note!' }] }]"
      />
    </h-form-item>
    <h-form-item label="Gender">
      <h-select
        v-decorator="[
          'gender',
          { rules: [{ required: true, message: 'Please select your gender!' }] },
        ]"
        placeholder="Select a option and change input text above"
        @change="handleSelectChange"
      >
        <h-select-option value="male">
          male
        </h-select-option>
        <h-select-option value="female">
          female
        </h-select-option>
      </h-select>
    </h-form-item>
    <h-form-item :wrapper-col="{ span: 12, offset: 5 }">
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
export default {
  data() {
    return {
      formLayout: 'horizontal',
      form: this.$form.createForm(this, { name: 'coordinated' }),
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    handleSelectChange(value) {
      console.log(value);
      this.form.setFieldsValue({
        note: `Hi, ${value === 'male' ? 'man' : 'lady'}!`,
      });
    },
  },
};
</script>
```

##### 动态校验规则
根据不同情况执行不同的校验规则。

```html
<template>
  <h-form :form="form">
    <h-form-item
      :label-col="formItemLayout.labelCol"
      :wrapper-col="formItemLayout.wrapperCol"
      label="Name"
    >
      <h-input
        v-decorator="[
          'username',
          { rules: [{ required: true, message: 'Please input your name' }] },
        ]"
        placeholder="Please input your name"
      />
    </h-form-item>
    <h-form-item
      :label-col="formItemLayout.labelCol"
      :wrapper-col="formItemLayout.wrapperCol"
      label="Nickname"
    >
      <h-input
        v-decorator="[
          'nickname',
          { rules: [{ required: checkNick, message: 'Please input your nickname' }] },
        ]"
        placeholder="Please input your nickname"
      />
    </h-form-item>
    <h-form-item :label-col="formTailLayout.labelCol" :wrapper-col="formTailLayout.wrapperCol">
      <h-checkbox :checked="checkNick" @change="handleChange">
        Nickname is required
      </h-checkbox>
    </h-form-item>
    <h-form-item :label-col="formTailLayout.labelCol" :wrapper-col="formTailLayout.wrapperCol">
      <h-button type="primary" @click="check">
        Check
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
const formItemLayout = {
  labelCol: { span: 4 },
  wrapperCol: { span: 8 },
};
const formTailLayout = {
  labelCol: { span: 4 },
  wrapperCol: { span: 8, offset: 4 },
};
export default {
  data() {
    return {
      checkNick: false,
      formItemLayout,
      formTailLayout,
      form: this.$form.createForm(this, { name: 'dynamic_rule' }),
    };
  },
  methods: {
    check() {
      this.form.validateFields(err => {
        if (!err) {
          console.info('success');
        }
      });
    },
    handleChange(e) {
      this.checkNick = e.target.checked;
      this.$nextTick(() => {
        this.form.validateFields(['nickname'], { force: true });
      });
    },
  },
};
</script>
```

##### 内联登录栏
水平登录栏，常用在顶部导航栏中。

```html
<template>
  <h-form layout="inline" :form="form" @submit="handleSubmit">
    <h-form-item :validate-status="userNameError() ? 'error' : ''" :help="userNameError() || ''">
      <h-input
        v-decorator="[
          'userName',
          { rules: [{ required: true, message: 'Please input your username!' }] },
        ]"
        placeholder="Username"
      >
        <h-icon slot="prefix" type="user" style="color:rgba(0,0,0,.25)" />
      </h-input>
    </h-form-item>
    <h-form-item :validate-status="passwordError() ? 'error' : ''" :help="passwordError() || ''">
      <h-input
        v-decorator="[
          'password',
          { rules: [{ required: true, message: 'Please input your Password!' }] },
        ]"
        type="password"
        placeholder="Password"
      >
        <h-icon slot="prefix" type="lock" style="color:rgba(0,0,0,.25)" />
      </h-input>
    </h-form-item>
    <h-form-item>
      <h-button type="primary" html-type="submit" :disabled="hasErrors(form.getFieldsError())">
        Log in
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
function hasErrors(fieldsError) {
  return Object.keys(fieldsError).some(field => fieldsError[field]);
}
export default {
  data() {
    return {
      hasErrors,
      form: this.$form.createForm(this, { name: 'horizontal_login' }),
    };
  },
  mounted() {
    this.$nextTick(() => {
      // To disabled submit button at the beginning.
      this.form.validateFields();
    });
  },
  methods: {
    // Only show error after a field is touched.
    userNameError() {
      const { getFieldError, isFieldTouched } = this.form;
      return isFieldTouched('userName') && getFieldError('userName');
    },
    // Only show error after a field is touched.
    passwordError() {
      const { getFieldError, isFieldTouched } = this.form;
      return isFieldTouched('password') && getFieldError('password');
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
  },
};
</script>
```

##### 表单布局
表单有三种布局。

```html
<template>
  <h-form :layout="formLayout">
    <h-form-item
      label="Form Layout"
      :label-col="formItemLayout.labelCol"
      :wrapper-col="formItemLayout.wrapperCol"
    >
      <h-radio-group default-value="horizontal" @change="handleFormLayoutChange">
        <h-radio-button value="horizontal">
          Horizontal
        </h-radio-button>
        <h-radio-button value="vertical">
          Vertical
        </h-radio-button>
        <h-radio-button value="inline">
          Inline
        </h-radio-button>
      </h-radio-group>
    </h-form-item>
    <h-form-item
      label="Field A"
      :label-col="formItemLayout.labelCol"
      :wrapper-col="formItemLayout.wrapperCol"
    >
      <h-input placeholder="input placeholder" />
    </h-form-item>
    <h-form-item
      label="Field B"
      :label-col="formItemLayout.labelCol"
      :wrapper-col="formItemLayout.wrapperCol"
    >
      <h-input placeholder="input placeholder" />
    </h-form-item>
    <h-form-item :wrapper-col="buttonItemLayout.wrapperCol">
      <h-button type="primary">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
export default {
  data() {
    return {
      formLayout: 'horizontal',
    };
  },
  computed: {
    formItemLayout() {
      const { formLayout } = this;
      return formLayout === 'horizontal'
        ? {
            labelCol: { span: 4 },
            wrapperCol: { span: 14 },
          }
        : {};
    },
    buttonItemLayout() {
      const { formLayout } = this;
      return formLayout === 'horizontal'
        ? {
            wrapperCol: { span: 14, offset: 4 },
          }
        : {};
    },
  },
  methods: {
    handleFormLayoutChange(e) {
      this.formLayout = e.target.value;
    },
  },
};
</script>
```

##### 自定义校验
我们提供了 `validateStatus` `help` `hasFeedback` 等属性，你可以不需要使用 `Form.create` 和 `getFieldDecorator`，自己定义校验的时机和内容。

1. `validateStatus`: 校验状态，可选 ‘success’, ‘warning’, ‘error’, ‘validating’。
2. `hasFeedback`：用于给输入框添加反馈图标。
3. `help`：设置校验文案。

```html
<template>
  <h-form :label-col="labelCol" :wrapper-col="wrapperCol">
    <h-form-item
      label="Fail"
      validate-status="error"
      help="Should be combination of numbers & alphabets"
    >
      <h-input id="error" placeholder="unavailable choice" />
    </h-form-item>
    <h-form-item label="Warning" validate-status="warning">
      <h-input id="warning" placeholder="Warning" />
    </h-form-item>
    <h-form-item
      label="Validating"
      has-feedback
      validate-status="validating"
      help="The information is being validated..."
    >
      <h-input id="validating" placeholder="I'm the content is being validated" />
    </h-form-item>
    <h-form-item label="Success" has-feedback validate-status="success">
      <h-input id="success" placeholder="I'm the content" />
    </h-form-item>
    <h-form-item label="Warning" has-feedback validate-status="warning">
      <h-input id="warning2" placeholder="Warning" />
    </h-form-item>
    <h-form-item
      label="Fail"
      has-feedback
      validate-status="error"
      help="Should be combination of numbers & alphabets"
    >
      <h-input id="error2" placeholder="unavailable choice" />
    </h-form-item>
    <h-form-item label="Success" has-feedback validate-status="success">
      <h-date-picker style="width: 100%" />
    </h-form-item>
    <h-form-item label="Warning" has-feedback validate-status="warning">
      <h-time-picker style="width: 100%" />
    </h-form-item>
    <h-form-item label="Error" has-feedback validate-status="error">
      <h-select default-value="1">
        <h-select-option value="1">
          Option 1
        </h-select-option>
        <h-select-option value="2">
          Option 2
        </h-select-option>
        <h-select-option value="3">
          Option 3
        </h-select-option>
      </h-select>
    </h-form-item>
    <h-form-item
      label="Validating"
      has-feedback
      validate-status="validating"
      help="The information is being validated..."
    >
      <h-cascader :default-value="['1']" :options="[]" />
    </h-form-item>
    <h-form-item label="inline" style="margin-bottom:0;">
      <h-form-item
        validate-status="error"
        help="Please select the correct date"
        :style="{ display: 'inline-block', width: 'calc(50% - 12px)' }"
      >
        <h-date-picker style="width: 100%" />
      </h-form-item>
      <span :style="{ display: 'inline-block', width: '24px', textAlign: 'center' }">
        -
      </span>
      <h-form-item :style="{ display: 'inline-block', width: 'calc(50% - 12px)' }">
        <h-date-picker style="width: 100%" />
      </h-form-item>
    </h-form-item>
    <h-form-item label="Success" has-feedback validate-status="success">
      <h-input-number style="width: 100%" />
    </h-form-item>
    <h-form-item label="Success" has-feedback validate-status="success">
      <h-input allow-clear placeholder="with allowClear" />
    </h-form-item>

    <h-form-item label="Warning" has-feedback validate-status="warning">
      <h-input-password placeholder="with input password" />
    </h-form-item>

    <h-form-item label="Error" has-feedback validate-status="error">
      <h-input-password allow-clear placeholder="with input password and allowClear" />
    </h-form-item>
  </h-form>
</template>
<script>
export default {
  data() {
    return {
      labelCol: {
        xs: { span: 24 },
        sm: { span: 5 },
      },
      wrapperCol: {
        xs: { span: 24 },
        sm: { span: 12 },
      },
    };
  },
};
</script>
```

##### 自行处理表单数据
使用 `Form.create` 处理后的表单具有自动收集数据并校验的功能，但如果您不需要这个功能，或者默认的行为无法满足业务需求，可以选择不使用 `Form.create` 并自行处理数据。

```html
<template>
  <h-form>
    <h-form-item
      :label-col="labelCol"
      :wrapper-col="wrapperCol"
      label="Prime between 8 & 12"
      :validate-status="number.validateStatus"
      :help="number.errorMsg || tips"
    >
      <h-input-number :min="8" :max="12" :value="number.value" @change="handleNumberChange" />
    </h-form-item>
  </h-form>
</template>
<script>
function validatePrimeNumber(number) {
  if (number === 11) {
    return {
      validateStatus: 'success',
      errorMsg: null,
    };
  }
  return {
    validateStatus: 'error',
    errorMsg: 'The prime between 8 and 12 is 11!',
  };
}
export default {
  data() {
    return {
      labelCol: { span: 7 },
      wrapperCol: { span: 12 },
      number: {
        value: 11,
      },
      tips:
        'A prime is a natural number greater than 1 that has no positive divisors other than 1 and itself.',
    };
  },
  methods: {
    handleNumberChange(value) {
      this.number = {
        ...validatePrimeNumber(value),
        value,
      };
    },
  },
};
</script>
```

##### 高级搜索
三列栅格式的表单排列方式，常用于数据表格的高级搜索。
有部分定制的样式代码，由于输入标签长度不确定，需要根据具体情况自行调整。

```html
<template>
  <div id="components-form-demo-advanced-search">
    <h-form class="ant-advanced-search-form" :form="form" @submit="handleSearch">
      <h-row :gutter="24">
        <h-col
          v-for="i in 10"
          :key="i"
          :span="8"
          :style="{ display: i < count ? 'block' : 'none' }"
        >
          <h-form-item :label="`Field ${i}`">
            <h-input
              v-decorator="[
                `field-${i}`,
                {
                  rules: [
                    {
                      required: true,
                      message: 'Input something!',
                    },
                  ],
                },
              ]"
              placeholder="placeholder"
            />
          </h-form-item>
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="24" :style="{ textAlign: 'right' }">
          <h-button type="primary" html-type="submit">
            Search
          </h-button>
          <h-button :style="{ marginLeft: '8px' }" @click="handleReset">
            Clear
          </h-button>
          <a :style="{ marginLeft: '8px', fontSize: '12px' }" @click="toggle">
            Collapse <h-icon :type="expand ? 'up' : 'down'" />
          </a>
        </h-col>
      </h-row>
    </h-form>
    <div class="search-result-list">
      Search Result List
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      expand: false,
      form: this.$form.createForm(this, { name: 'advanced_search' }),
    };
  },
  computed: {
    count() {
      return this.expand ? 11 : 7;
    },
  },
  updated() {
    console.log('updated');
  },
  methods: {
    handleSearch(e) {
      e.preventDefault();
      this.form.validateFields((error, values) => {
        console.log('error', error);
        console.log('Received values of form: ', values);
      });
    },

    handleReset() {
      this.form.resetFields();
    },

    toggle() {
      this.expand = !this.expand;
    },
  },
};
</script>
<style>
.ant-advanced-search-form {
  padding: 24px;
  background: #fbfbfb;
  border: 1px solid #d9d9d9;
  border-radius: 6px;
}

.ant-advanced-search-form .ant-form-item {
  display: flex;
}

.ant-advanced-search-form .ant-form-item-control-wrapper {
  flex: 1;
}

#components-form-demo-advanced-search .ant-form {
  max-width: none;
}
#components-form-demo-advanced-search .search-result-list {
  margin-top: 16px;
  border: 1px dashed #e9e9e9;
  border-radius: 6px;
  background-color: #fafafa;
  min-height: 200px;
  text-align: center;
  padding-top: 80px;
}
</style>
```

##### 自定义表单控件
自定义或第三方的表单控件，也可以与 Form 组件一起使用。只要该组件遵循以下的约定：

> - 提供受控属性 `value` 或其它与 [`valuePropName`](https://1x.antdv.com/components/form-cn/#getFieldDecorator(id,-options)-参数) 的值同名的属性。
> - 提供 `onChange` 事件或 [`trigger`](https://1x.antdv.com/components/form-cn/#getFieldDecorator(id,-options)-参数) 的值同名的事件。
> - 不能是函数式组件。

```html
<template>
  <h-form layout="inline" :form="form" @submit="handleSubmit">
    <h-form-item label="Price">
      <price-input
        v-decorator="[
          'price',
          {
            initialValue: { number: 0, currency: 'rmb' },
            rules: [{ validator: checkPrice }],
          },
        ]"
      />
    </h-form-item>
    <h-form-item>
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
const PriceInput = {
  props: ['value'],
  template: `
    <span>
      <h-input
        type='text'
        :value="number"
        @change="handleNumberChange"
        style="width: 63%; margin-right: 2%;"
      />
      <h-select
        :value="currency"
        style="width: 32%"
        @change="handleCurrencyChange"
      >
        <h-select-option value='rmb'>RMB</h-select-option>
        <h-select-option value='dollar'>Dollar</h-select-option>
      </h-select>
    </span>
  `,
  data() {
    const value = this.value || {};
    return {
      number: value.number || 0,
      currency: value.currency || 'rmb',
    };
  },
  watch: {
    value(val = {}) {
      this.number = val.number || 0;
      this.currency = val.currency || 'rmb';
    },
  },
  methods: {
    handleNumberChange(e) {
      const number = parseInt(e.target.value || 0, 10);
      if (isNaN(number)) {
        return;
      }
      this.triggerChange({ number });
    },
    handleCurrencyChange(currency) {
      this.triggerChange({ currency });
    },
    triggerChange(changedValue) {
      // Should provide an event to pass value to Form.
      this.$emit('change', Object.assign({}, this.$data, changedValue));
    },
  },
};

export default {
  components: {
    PriceInput,
  },
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'customized_form_controls' });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    checkPrice(rule, value, callback) {
      if (value.number > 0) {
        callback();
        return;
      }
      callback('Price must greater than zero!');
    },
  },
};
</script>
```

##### 动态增减表单项
动态增加、减少表单项。

```html
<template>
  <h-form :form="form" @submit="handleSubmit">
    <h-form-item
      v-for="(k, index) in form.getFieldValue('keys')"
      :key="k"
      v-bind="index === 0 ? formItemLayout : formItemLayoutWithOutLabel"
      :label="index === 0 ? 'Passengers' : ''"
      :required="false"
    >
      <h-input
        v-decorator="[
          `names[${k}]`,
          {
            validateTrigger: ['change', 'blur'],
            rules: [
              {
                required: true,
                whitespace: true,
                message: 'Please input passenger\'s name or delete this field.',
              },
            ],
          },
        ]"
        placeholder="passenger name"
        style="width: 60%; margin-right: 8px"
      />
      <h-icon
        v-if="form.getFieldValue('keys').length > 1"
        class="dynamic-delete-button"
        type="minus-circle-o"
        :disabled="form.getFieldValue('keys').length === 1"
        @click="() => remove(k)"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayoutWithOutLabel">
      <h-button type="dashed" style="width: 60%" @click="add">
        <h-icon type="plus" /> Add field
      </h-button>
    </h-form-item>
    <h-form-item v-bind="formItemLayoutWithOutLabel">
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
let id = 0;
export default {
  data() {
    return {
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 4 },
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 20 },
        },
      },
      formItemLayoutWithOutLabel: {
        wrapperCol: {
          xs: { span: 24, offset: 0 },
          sm: { span: 20, offset: 4 },
        },
      },
    };
  },
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'dynamic_form_item' });
    this.form.getFieldDecorator('keys', { initialValue: [], preserve: true });
  },
  methods: {
    remove(k) {
      const { form } = this;
      // can use dath-binding to get
      const keys = form.getFieldValue('keys');
      // We need at least one passenger
      if (keys.length === 1) {
        return;
      }

      // can use dath-binding to set
      form.setFieldsValue({
        keys: keys.filter(key => key !== k),
      });
    },

    add() {
      const { form } = this;
      // can use dath-binding to get
      const keys = form.getFieldValue('keys');
      const nextKeys = keys.concat(id++);
      // can use dath-binding to set
      // important! notify form to detect changes
      form.setFieldsValue({
        keys: nextKeys,
      });
    },

    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          const { keys, names } = values;
          console.log('Received values of form: ', values);
          console.log(
            'Merged values:',
            keys.map(key => names[key]),
          );
        }
      });
    },
  },
};
</script>
<style>
.dynamic-delete-button {
  cursor: pointer;
  position: relative;
  top: 4px;
  font-size: 24px;
  color: #999;
  transition: all 0.3s;
}
.dynamic-delete-button:hover {
  color: #777;
}
.dynamic-delete-button[disabled] {
  cursor: not-allowed;
  opacity: 0.5;
}
</style>
```

##### 弹出层中的新建表单
当用户访问一个展示了某个列表的页面，想新建一项但又不想跳转页面时，可以用 Modal 弹出一个表单，用户填写必要信息后创建新的项。

```html
<template>
  <div>
    <h-button type="primary" @click="showModal">
      New Collection
    </h-button>
    <collection-create-form
      ref="collectionForm"
      :visible="visible"
      @cancel="handleCancel"
      @create="handleCreate"
    />
  </div>
</template>

<script>
const CollectionCreateForm = {
  props: ['visible'],
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'form_in_modal' });
  },
  template: `
    <h-modal
      :visible="visible"
      title='Create a new collection'
      okText='Create'
      @cancel="() => { $emit('cancel') }"
      @ok="() => { $emit('create') }"
    >
      <h-form layout='vertical' :form="form">
        <h-form-item label='Title'>
          <h-input
            v-decorator="[
              'title',
              {
                rules: [{ required: true, message: 'Please input the title of collection!' }],
              }
            ]"
          />
        </h-form-item>
        <h-form-item label='Description'>
          <h-input
            type='textarea'
            v-decorator="['description']"
          />
        </h-form-item>
        <h-form-item class='collection-create-form_last-form-item'>
          <h-radio-group
            v-decorator="[
              'modifier',
              {
                initialValue: 'private',
              }
            ]"
          >
              <h-radio value='public'>Public</h-radio>
              <h-radio value='private'>Private</h-radio>
            </h-radio-group>
        </h-form-item>
      </h-form>
    </h-modal>
  `,
};

export default {
  components: { CollectionCreateForm },
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    showModal() {
      this.visible = true;
    },
    handleCancel() {
      this.visible = false;
    },
    handleCreate() {
      const form = this.$refs.collectionForm.form;
      form.validateFields((err, values) => {
        if (err) {
          return;
        }
        console.log('Received values of form: ', values);
        form.resetFields();
        this.visible = false;
      });
    },
  },
};
</script>
```

```bash
    {
  "username": {
    "value": "benjycui"
  }
}
  
```

##### 表单数据存储于上层组件
通过使用 `onFieldsChange` 与 `mapPropsToFields`，可以把表单的数据存储到上层组件。
**注意：**
`mapPropsToFields` 里面返回的表单域数据必须使用 `Form.createFormField` 包装。
如果你使用`Form.create`，上层组件传递的属性，必须在`Form.create({ props: ...})`的props中声明。
如果使用`this.$form.createForm`，你可以使用任何数据，不仅仅局限于上层组件的属性。

```html
<template>
  <div id="components-form-demo-global-state">
    <customized-form :username="fields.username" @change="handleFormChange" />
    <pre class="language-bash">
      {{ JSON.stringify(fields, null, 2) }}
    </pre>
  </div>
</template>

<script>
const CustomizedForm = {
  props: ['username'],
  template: `
    <h-form layout='inline' :form="form">
      <h-form-item label='Username'>
        <h-input
          v-decorator="[
            'username',
            {
              rules: [{ required: true, message: 'Username is required!' }],
            }
          ]"
        />
      </h-form-item>
    </h-form>
  `,
  created() {
    this.form = this.$form.createForm(this, {
      name: 'global_state',
      onFieldsChange: (_, changedFields) => {
        this.$emit('change', changedFields);
      },
      mapPropsToFields: () => {
        return {
          username: this.$form.createFormField({
            ...this.username,
            value: this.username.value,
          }),
        };
      },
      onValuesChange(_, values) {
        console.log(values);
      },
    });
  },
  watch: {
    username() {
      this.form.updateFields({
        username: this.$form.createFormField({
          ...this.username,
          value: this.username.value,
        }),
      });
    },
  },
};

export default {
  components: {
    CustomizedForm,
  },
  data() {
    return {
      fields: {
        username: {
          value: 'benjycui',
        },
      },
    };
  },
  methods: {
    handleFormChange(changedFields) {
      console.log('changedFields', changedFields);
      this.fields = { ...this.fields, ...changedFields };
    },
  },
};
</script>
<style>
#components-form-demo-global-state .language-bash {
  max-width: 400px;
  border-radius: 6px;
  margin-top: 24px;
}
</style>
```

##### 表单数据存储于 Vuex Store 中
通过使用 onFieldsChange 与 mapPropsToFields，可以把表单的数据存储到 Vuex 中。
**注意：**
`mapPropsToFields` 里面返回的表单域数据必须使用 `Form.createFormField` 包装。

```html
<template>
  <div id="components-form-demo-vuex">
    <h-form :form="form" @submit="handleSubmit">
      <h-form-item label="Username">
        <h-input
          v-decorator="[
            'username',
            {
              rules: [{ required: true, message: 'Username is required!' }],
            },
          ]"
        />
      </h-form-item>
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form>
  </div>
</template>

<script>
export default {
  computed: {
    username() {
      return this.$store.state.username;
    },
  },
  watch: {
    username(val) {
      console.log('this.$store.state.username: ', val);
      this.form.setFieldsValue({ username: val });
    },
  },
  created() {
    this.form = this.$form.createForm(this, {
      onFieldsChange: (_, changedFields) => {
        this.$emit('change', changedFields);
      },
      mapPropsToFields: () => {
        return {
          username: this.$form.createFormField({
            value: this.username,
          }),
        };
      },
      onValuesChange: (_, values) => {
        console.log(values);
        // Synchronize to vuex store in real time
        // this.$store.commit('update', values)
      },
    });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
          this.$store.commit('update', values);
        }
      });
    },
  },
};
</script>
<style>
#components-form-demo-vuex .language-bash {
  max-width: 400px;
  border-radius: 6px;
  margin-top: 24px;
}
</style>
```

##### 登录框
普通的登录框，可以容纳更多的元素。

```html
<template>
  <h-form
    id="components-form-demo-normal-login"
    :form="form"
    class="login-form"
    @submit="handleSubmit"
  >
    <h-form-item>
      <h-input
        v-decorator="[
          'userName',
          { rules: [{ required: true, message: 'Please input your username!' }] },
        ]"
        placeholder="Username"
      >
        <h-icon slot="prefix" type="user" style="color: rgba(0,0,0,.25)" />
      </h-input>
    </h-form-item>
    <h-form-item>
      <h-input
        v-decorator="[
          'password',
          { rules: [{ required: true, message: 'Please input your Password!' }] },
        ]"
        type="password"
        placeholder="Password"
      >
        <h-icon slot="prefix" type="lock" style="color: rgba(0,0,0,.25)" />
      </h-input>
    </h-form-item>
    <h-form-item>
      <h-checkbox
        v-decorator="[
          'remember',
          {
            valuePropName: 'checked',
            initialValue: true,
          },
        ]"
      >
        Remember me
      </h-checkbox>
      <a class="login-form-forgot" href="">
        Forgot password
      </a>
      <h-button type="primary" html-type="submit" class="login-form-button">
        Log in
      </h-button>
      Or
      <a href="">
        register now!
      </a>
    </h-form-item>
  </h-form>
</template>

<script>
export default {
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'normal_login' });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
  },
};
</script>
<style>
#components-form-demo-normal-login .login-form {
  max-width: 300px;
}
#components-form-demo-normal-login .login-form-forgot {
  float: right;
}
#components-form-demo-normal-login .login-form-button {
  width: 100%;
}
</style>
```

##### 注册新用户
用户填写必须的信息以注册新用户。

```html
<template>
  <h-form :form="form" @submit="handleSubmit">
    <h-form-item v-bind="formItemLayout" label="E-mail">
      <h-input
        v-decorator="[
          'email',
          {
            rules: [
              {
                type: 'email',
                message: 'The input is not valid E-mail!',
              },
              {
                required: true,
                message: 'Please input your E-mail!',
              },
            ],
          },
        ]"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayout" label="Password" has-feedback>
      <h-input
        v-decorator="[
          'password',
          {
            rules: [
              {
                required: true,
                message: 'Please input your password!',
              },
              {
                validator: validateToNextPassword,
              },
            ],
          },
        ]"
        type="password"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayout" label="Confirm Password" has-feedback>
      <h-input
        v-decorator="[
          'confirm',
          {
            rules: [
              {
                required: true,
                message: 'Please confirm your password!',
              },
              {
                validator: compareToFirstPassword,
              },
            ],
          },
        ]"
        type="password"
        @blur="handleConfirmBlur"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayout">
      <span slot="label">
        Nickname&nbsp;
        <h-tooltip title="What do you want others to call you?">
          <h-icon type="question-circle-o" />
        </h-tooltip>
      </span>
      <h-input
        v-decorator="[
          'nickname',
          {
            rules: [{ required: true, message: 'Please input your nickname!', whitespace: true }],
          },
        ]"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayout" label="Habitual Residence">
      <h-cascader
        v-decorator="[
          'residence',
          {
            initialValue: ['zhejiang', 'hangzhou', 'xihu'],
            rules: [
              { type: 'array', required: true, message: 'Please select your habitual residence!' },
            ],
          },
        ]"
        :options="residences"
      />
    </h-form-item>
    <h-form-item v-bind="formItemLayout" label="Phone Number">
      <h-input
        v-decorator="[
          'phone',
          {
            rules: [{ required: true, message: 'Please input your phone number!' }],
          },
        ]"
        style="width: 100%"
      >
        <h-select
          slot="addonBefore"
          v-decorator="['prefix', { initialValue: '86' }]"
          style="width: 70px"
        >
          <h-select-option value="86">
            +86
          </h-select-option>
          <h-select-option value="87">
            +87
          </h-select-option>
        </h-select>
      </h-input>
    </h-form-item>
    <h-form-item v-bind="formItemLayout" label="Website">
      <h-auto-complete
        v-decorator="['website', { rules: [{ required: true, message: 'Please input website!' }] }]"
        placeholder="website"
        @change="handleWebsiteChange"
      >
        <template slot="dataSource">
          <h-select-option v-for="website in autoCompleteResult" :key="website">
            {{ website }}
          </h-select-option>
        </template>
        <h-input />
      </h-auto-complete>
    </h-form-item>
    <h-form-item
      v-bind="formItemLayout"
      label="Captcha"
      extra="We must make sure that your are a human."
    >
      <h-row :gutter="8">
        <h-col :span="12">
          <h-input
            v-decorator="[
              'captcha',
              { rules: [{ required: true, message: 'Please input the captcha you got!' }] },
            ]"
          />
        </h-col>
        <h-col :span="12">
          <h-button>Get captcha</h-button>
        </h-col>
      </h-row>
    </h-form-item>
    <h-form-item v-bind="tailFormItemLayout">
      <h-checkbox v-decorator="['agreement', { valuePropName: 'checked' }]">
        I have read the
        <a href="">
          agreement
        </a>
      </h-checkbox>
    </h-form-item>
    <h-form-item v-bind="tailFormItemLayout">
      <h-button type="primary" html-type="submit">
        Register
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
const residences = [
  {
    value: 'zhejiang',
    label: 'Zhejiang',
    children: [
      {
        value: 'hangzhou',
        label: 'Hangzhou',
        children: [
          {
            value: 'xihu',
            label: 'West Lake',
          },
        ],
      },
    ],
  },
  {
    value: 'jiangsu',
    label: 'Jiangsu',
    children: [
      {
        value: 'nanjing',
        label: 'Nanjing',
        children: [
          {
            value: 'zhonghuamen',
            label: 'Zhong Hua Men',
          },
        ],
      },
    ],
  },
];

export default {
  data() {
    return {
      confirmDirty: false,
      residences,
      autoCompleteResult: [],
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 8 },
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 16 },
        },
      },
      tailFormItemLayout: {
        wrapperCol: {
          xs: {
            span: 24,
            offset: 0,
          },
          sm: {
            span: 16,
            offset: 8,
          },
        },
      },
    };
  },
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'register' });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFieldsAndScroll((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    handleConfirmBlur(e) {
      const value = e.target.value;
      this.confirmDirty = this.confirmDirty || !!value;
    },
    compareToFirstPassword(rule, value, callback) {
      const form = this.form;
      if (value && value !== form.getFieldValue('password')) {
        callback('Two passwords that you enter is inconsistent!');
      } else {
        callback();
      }
    },
    validateToNextPassword(rule, value, callback) {
      const form = this.form;
      if (value && this.confirmDirty) {
        form.validateFields(['confirm'], { force: true });
      }
      callback();
    },
    handleWebsiteChange(value) {
      let autoCompleteResult;
      if (!value) {
        autoCompleteResult = [];
      } else {
        autoCompleteResult = ['.com', '.org', '.net'].map(domain => `${value}${domain}`);
      }
      this.autoCompleteResult = autoCompleteResult;
    },
  },
};
</script>
```

##### 时间类控件
时间类组件的 `value` 类型为 `moment` 对象，所以在提交服务器前需要预处理。

```html
<template>
  <h-form v-bind="formItemLayout" :form="form" @submit="handleSubmit">
    <h-form-item label="DatePicker">
      <h-date-picker v-decorator="['date-picker', config]" />
    </h-form-item>
    <h-form-item label="DatePicker[showTime]">
      <h-date-picker
        v-decorator="['date-time-picker', config]"
        show-time
        format="YYYY-MM-DD HH:mm:ss"
      />
    </h-form-item>
    <h-form-item label="MonthPicker">
      <h-month-picker v-decorator="['month-picker', config]" />
    </h-form-item>
    <h-form-item label="RangePicker">
      <h-range-picker v-decorator="['range-picker', rangeConfig]" />
    </h-form-item>
    <h-form-item label="RangePicker[showTime]">
      <h-range-picker
        v-decorator="['range-time-picker', rangeConfig]"
        show-time
        format="YYYY-MM-DD HH:mm:ss"
      />
    </h-form-item>
    <h-form-item label="TimePicker">
      <h-time-picker v-decorator="['time-picker', config]" />
    </h-form-item>
    <h-form-item
      :wrapper-col="{
        xs: { span: 24, offset: 0 },
        sm: { span: 16, offset: 8 },
      }"
    >
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>
<script>
export default {
  data() {
    return {
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 8 },
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 16 },
        },
      },
      config: {
        rules: [{ type: 'object', required: true, message: 'Please select time!' }],
      },
      rangeConfig: {
        rules: [{ type: 'array', required: true, message: 'Please select time!' }],
      },
    };
  },
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'time_related_controls' });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, fieldsValue) => {
        if (err) {
          return;
        }

        // Should format date value before submit.
        const rangeValue = fieldsValue['range-picker'];
        const rangeTimeValue = fieldsValue['range-time-picker'];
        const values = {
          ...fieldsValue,
          'date-picker': fieldsValue['date-picker'].format('YYYY-MM-DD'),
          'date-time-picker': fieldsValue['date-time-picker'].format('YYYY-MM-DD HH:mm:ss'),
          'month-picker': fieldsValue['month-picker'].format('YYYY-MM'),
          'range-picker': [rangeValue[0].format('YYYY-MM-DD'), rangeValue[1].format('YYYY-MM-DD')],
          'range-time-picker': [
            rangeTimeValue[0].format('YYYY-MM-DD HH:mm:ss'),
            rangeTimeValue[1].format('YYYY-MM-DD HH:mm:ss'),
          ],
          'time-picker': fieldsValue['time-picker'].format('HH:mm:ss'),
        };
        console.log('Received values of form: ', values);
      });
    },
  },
};
</script>
```

##### 校验其他组件
以上演示没有出现的表单控件对应的校验演示。

```html
<template>
  <h-form
    id="components-form-demo-validate-other"
    :form="form"
    v-bind="formItemLayout"
    @submit="handleSubmit"
  >
    <h-form-item label="Plain Text">
      <span class="ant-form-text">
        China
      </span>
    </h-form-item>
    <h-form-item label="Select" has-feedback>
      <h-select
        v-decorator="[
          'select',
          { rules: [{ required: true, message: 'Please select your country!' }] },
        ]"
        placeholder="Please select a country"
      >
        <h-select-option value="china">
          China
        </h-select-option>
        <h-select-option value="usa">
          U.S.A
        </h-select-option>
      </h-select>
    </h-form-item>

    <h-form-item label="Select[multiple]">
      <h-select
        v-decorator="[
          'select-multiple',
          {
            rules: [
              { required: true, message: 'Please select your favourite colors!', type: 'array' },
            ],
          },
        ]"
        mode="multiple"
        placeholder="Please select favourite colors"
      >
        <h-select-option value="red">
          Red
        </h-select-option>
        <h-select-option value="green">
          Green
        </h-select-option>
        <h-select-option value="blue">
          Blue
        </h-select-option>
      </h-select>
    </h-form-item>

    <h-form-item label="InputNumber">
      <h-input-number v-decorator="['input-number', { initialValue: 3 }]" :min="1" :max="10" />
      <span class="ant-form-text">
        machines
      </span>
    </h-form-item>

    <h-form-item label="Switch">
      <h-switch v-decorator="['switch', { valuePropName: 'checked' }]" />
    </h-form-item>

    <h-form-item label="Slider">
      <h-slider
        v-decorator="['slider']"
        :marks="{ 0: 'A', 20: 'B', 40: 'C', 60: 'D', 80: 'E', 100: 'F' }"
      />
    </h-form-item>

    <h-form-item label="Radio.Group">
      <h-radio-group v-decorator="['radio-group']">
        <h-radio value="a">
          item 1
        </h-radio>
        <h-radio value="b">
          item 2
        </h-radio>
        <h-radio value="c">
          item 3
        </h-radio>
      </h-radio-group>
    </h-form-item>

    <h-form-item label="Radio.Button">
      <h-radio-group v-decorator="['radio-button']">
        <h-radio-button value="a">
          item 1
        </h-radio-button>
        <h-radio-button value="b">
          item 2
        </h-radio-button>
        <h-radio-button value="c">
          item 3
        </h-radio-button>
      </h-radio-group>
    </h-form-item>

    <h-form-item label="Checkbox.Group">
      <h-checkbox-group
        v-decorator="['checkbox-group', { initialValue: ['A', 'B'] }]"
        style="width: 100%;"
      >
        <h-row>
          <h-col :span="8">
            <h-checkbox value="A">
              A
            </h-checkbox>
          </h-col>
          <h-col :span="8">
            <h-checkbox disabled value="B">
              B
            </h-checkbox>
          </h-col>
          <h-col :span="8">
            <h-checkbox value="C">
              C
            </h-checkbox>
          </h-col>
          <h-col :span="8">
            <h-checkbox value="D">
              D
            </h-checkbox>
          </h-col>
          <h-col :span="8">
            <h-checkbox value="E">
              E
            </h-checkbox>
          </h-col>
        </h-row>
      </h-checkbox-group>
    </h-form-item>

    <h-form-item label="Rate">
      <h-rate v-decorator="['rate', { initialValue: 3.5 }]" allow-half />
    </h-form-item>

    <h-form-item label="Upload" extra="longgggggggggggggggggggggggggggggggggg">
      <h-upload
        v-decorator="[
          'upload',
          {
            valuePropName: 'fileList',
            getValueFromEvent: normFile,
          },
        ]"
        name="logo"
        action="/upload.do"
        list-type="picture"
      >
        <h-button> <h-icon type="upload" /> Click to upload </h-button>
      </h-upload>
    </h-form-item>

    <h-form-item label="Dragger">
      <div class="dropbox">
        <h-upload-dragger
          v-decorator="[
            'dragger',
            {
              valuePropName: 'fileList',
              getValueFromEvent: normFile,
            },
          ]"
          name="files"
          action="/upload.do"
        >
          <p class="ant-upload-drag-icon">
            <h-icon type="inbox" />
          </p>
          <p class="ant-upload-text">
            Click or drag file to this area to upload
          </p>
          <p class="ant-upload-hint">
            Support for a single or bulk upload.
          </p>
        </h-upload-dragger>
      </div>
    </h-form-item>

    <h-form-item :wrapper-col="{ span: 12, offset: 6 }">
      <h-button type="primary" html-type="submit">
        Submit
      </h-button>
    </h-form-item>
  </h-form>
</template>

<script>
export default {
  data: () => ({
    formItemLayout: {
      labelCol: { span: 6 },
      wrapperCol: { span: 14 },
    },
  }),
  beforeCreate() {
    this.form = this.$form.createForm(this, { name: 'validate_other' });
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    normFile(e) {
      console.log('Upload event:', e);
      if (Array.isArray(e)) {
        return e;
      }
      return e && e.fileList;
    },
  },
};
</script>
<style>
#components-form-demo-validate-other .dropbox {
  height: 180px;
  line-height: 1.5;
}
</style>
```

### API 
#### Form
| 参数             | 说明                                                         | 类型                                                   | 默认值       | 版本   |
| :--------------- | :----------------------------------------------------------- | :----------------------------------------------------- | :----------- | :----- |
| form             | 经 `Form.create()` 包装过的组件会自带 `this.form` 属性，如果使用 template 语法，可以使用 this.$form.createForm(this, options) | object                                                 | 无           |        |
| hideRequiredMark | 隐藏所有表单项的必选标记                                     | Boolean                                                | false        |        |
| labelAlign       | label 标签的文本对齐方式                                     | 'left' \| 'right'                                      | 'right'      | 1.5.0  |
| layout           | 表单布局                                                     | 'horizontal'\|'vertical'\|'inline'                     | 'horizontal' |        |
| labelCol         | label 标签布局，同 `<Col>` 组件，设置 `span` `offset` 值，如 `{span: 3, offset: 12}` 或 `sm: {span: 3, offset: 12}` | [object](https://1x.antdv.com/components/grid-cn/#Col) |              |        |
| wrapperCol       | 需要为输入控件设置布局样式时，使用该属性，用法同 labelCol    | [object](https://1x.antdv.com/components/grid-cn/#Col) |              |        |
| selfUpdate       | 自定义字段更新逻辑，说明[见下](https://1x.antdv.com/components/form-cn/#selfUpdate)，需 1.3.17 版本以上 | boolean                                                | false        | 1.3.17 |
| colon            | 配置 Form.Item 的 colon 的默认值 (只有在属性 layout 为 horizontal 时有效) | boolean                                                | true         | 1.5.0  |

#### 事件
| 事件名称 | 说明                   | 回调参数          |
| :------- | :--------------------- | :---------------- |
| submit   | 数据验证成功后回调事件 | Function(e:Event) |

#### Form.create(options) | this.$form.createForm(this, options) 
使用方式如下：

##### jsx 使用方式，使用方式和 React 版 antd 一致 
```jsx
const CustomizedForm = {};

CustomizedForm = Form.create({})(CustomizedForm);
```

如果需要为包装组件实例维护一个 ref，可以使用`wrappedComponentRef`。

##### 单文件 template 使用方式
```html
<template>
  <h-form :form="form" />
</template>
<script>
  export default {
    beforeCreate() {
      this.form = this.$form.createForm(this, options);
    },
  };
</script>
```

`options` 的配置项如下。

| 参数             | 说明                                                         | 类型                                              |
| :--------------- | :----------------------------------------------------------- | :------------------------------------------------ |
| props            | 仅仅支持 Form.create({})(CustomizedForm)的使用方式，父组件需要映射到表单项上的属性声明(和[vue 组件 props 一致](https://vuejs.org/v2/api/#props)) | {}                                                |
| mapPropsToFields | 把父组件的属性映射到表单项上（如：把 Redux store 中的值读出），需要对返回值中的表单域数据用 [`Form.createFormField`](https://1x.antdv.com/components/form-cn/#Form.createFormField) 标记，如果使用$form.createForm 创建收集器，你可以将任何数据映射到 Field 中，不受父组件约束 | (props) => ({ [fieldName]: FormField { value } }) |
| name             | 设置表单域内字段 id 的前缀                                   | -                                                 |
| validateMessages | 默认校验信息，可用于把默认错误信息改为中文等，格式与 [newMessages](https://github.com/yiminghe/async-validator/blob/master/src/messages.js) 返回值一致 | Object { [nested.path]: String }                  |
| onFieldsChange   | 当 `Form.Item` 子节点的值发生改变时触发，可以把对应的值转存到 Redux store | Function(props, fields)                           |
| onValuesChange   | 任一表单域的值发生改变时的回调                               | (props, values) => void                           |

经过 `Form.create` 包装的组件将会自带 `this.form` 属性，`this.form` 提供的 API 如下：

> 注意：使用 `getFieldsValue` `getFieldValue` `setFieldsValue` 等时，应确保对应的 field 已经用 `getFieldDecorator` 或 `v-decorator` 注册过了。

| 方法                    | 说明                                                         | 类型                                                         |
| :---------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| getFieldDecorator       | 用于和表单进行双向绑定，单文件 template 可以使用指令`v-decorator`进行绑定，详见下方描述 |                                                              |
| getFieldError           | 获取某个输入控件的 Error                                     | Function(name)                                               |
| getFieldsError          | 获取一组输入控件的 Error ，如不传入参数，则获取全部组件的 Error | Function([names: string[]])                                  |
| getFieldsValue          | 获取一组输入控件的值，如不传入参数，则获取全部组件的值       | Function([fieldNames: string[]])                             |
| getFieldValue           | 获取一个输入控件的值                                         | Function(fieldName: string)                                  |
| isFieldsTouched         | 判断是否任一输入控件经历过 `getFieldDecorator` 或 `v-decorator` 的值收集时机 `options.trigger` | (names?: string[]) => boolean                                |
| isFieldTouched          | 判断一个输入控件是否经历过 `getFieldDecorator` 或 `v-decorator` 的值收集时机 `options.trigger` | (name: string) => boolean                                    |
| isFieldValidating       | 判断一个输入控件是否在校验状态                               | Function(name)                                               |
| resetFields             | 重置一组输入控件的值（为 `initialValue`）与状态，如不传入参数，则重置所有组件 | Function([names: string[]])                                  |
| setFields               | 设置一组输入控件的值与错误状态。                             | Function({ [fieldName]: { value: any, errors: [Error] } })   |
| setFieldsValue          | 设置一组输入控件的值                                         | Function({ [fieldName]: value })                             |
| validateFields          | 校验并获取一组输入域的值与 Error，若 fieldNames 参数为空，则校验全部组件 | Function([fieldNames: string[]], [options: object], callback: Function(errors, values)) |
| validateFieldsAndScroll | 与 `validateFields` 相似，但校验完后，如果校验不通过的菜单域不在可见范围内，则自动滚动进可见范围 | 参考 `validateFields`                                        |

#### validateFields/validateFieldsAndScroll 
```jsx
const {
  form: { validateFields },
} = this;
validateFields((errors, values) => {
  // ...
});
validateFields(['field1', 'field2'], (errors, values) => {
  // ...
});
validateFields(['field1', 'field2'], options, (errors, values) => {
  // ...
});
```

| 参数                | 说明                                                         | 类型     | 默认值 |
| :------------------ | :----------------------------------------------------------- | :------- | :----- |
| options.first       | 若为 true，则每一表单域的都会在碰到第一个失败了的校验规则后停止校验 | boolean  | false  |
| options.firstFields | 指定表单域会在碰到第一个失败了的校验规则后停止校验           | String[] | []     |
| options.force       | 对已经校验过的表单域，在 validateTrigger 再次被触发时是否再次校验 | boolean  | false  |
| options.scroll      | 定义 validateFieldsAndScroll 的滚动行为，详细配置见 [dom-scroll-into-view config](https://github.com/yiminghe/dom-scroll-into-view#function-parameter) | Object   | {}     |

##### validateFields 的 callback 参数示例 
- `errors`:

  ```js
  {
    "userName": {
      "errors": [
        {
          "message": "Please input your username!",
          "field": "userName"
        }
      ]
    },
    "password": {
      "errors": [
        {
          "message": "Please input your Password!",
          "field": "password"
        }
      ]
    }
  }
  ```

- `values`:

  ```js
  {
    "userName": "username",
    "password": "password",
  }
  ```

#### Form.createFormField 
用于标记 `mapPropsToFields` 返回的表单域数据，[例子](https://1x.antdv.com/components/form-cn/#components-form-demo-global-state)。

#### this.form.getFieldDecorator(id, options) 和 v-decorator="[id, options]" 
经过 `getFieldDecorator`或`v-decorator` 包装的控件，表单控件会自动添加 `value`（或 `valuePropName` 指定的其他属性） `onChange`（或 `trigger` 指定的其他属性），数据同步将被 Form 接管，这会导致以下结果：

1. 你**不再需要也不应该**用 `onChange` 来做同步，但还是可以继续监听 `onChange` 等事件。
2. 你不能用控件的 `value` `defaultValue` 等属性来设置表单域的值，默认值可以用 `getFieldDecorator` 或 `v-decorator` 里的 `initialValue`。
3. 你不应该用 `v-model`，可以使用 `this.form.setFieldsValue` 来动态改变表单值。

##### 特别注意 
1. `getFieldDecorator` 和 `v-decorator` 不能用于装饰纯函数组件。
2. `getFieldDecorator` 和 `v-decorator` 调用不能位于纯函数组件中

##### getFieldDecorator(id, options) 和 v-decorator="[id, options]" 参数 
| 参数                      | 说明                                                         | 类型                                       | 默认值                                                       |
| :------------------------ | :----------------------------------------------------------- | :----------------------------------------- | :----------------------------------------------------------- |
| id                        | 必填输入控件唯一标志。支持嵌套式的写法。                     | string                                     |                                                              |
| options.getValueFromEvent | 可以把 onChange 的参数（如 event）转化为控件的值             | function(..args)                           | [reference](https://github.com/react-component/form#option-object) |
| options.initialValue      | 子节点的初始值，类型、可选值均由子节点决定(注意：由于内部校验时使用 `===` 判断是否变化，建议使用变量缓存所需设置的值而非直接使用字面量) |                                            |                                                              |
| options.normalize         | 转换默认的 value 给控件，[一个选择全部的例子](https://codesandbox.io/s/kw4l2vqqmv) | function(value, prevValue, allValues): any | -                                                            |
| options.preserve          | 即便字段不再使用，也保留该字段的值                           | boolean                                    | false                                                        |
| options.rules             | 校验规则，参考下方文档                                       | object[]                                   |                                                              |
| options.trigger           | 收集子节点的值的时机                                         | string                                     | 'change'                                                     |
| options.validateFirst     | 当某一规则校验不通过时，是否停止剩下的规则的校验             | boolean                                    | false                                                        |
| options.validateTrigger   | 校验子节点值的时机                                           | string\|string[]                           | 'change'                                                     |
| options.valuePropName     | 子节点的值的属性，如 Switch 的是 'checked'                   | string                                     | 'value'                                                      |

#### Form.Item 
注意：一个 Form.Item 建议只放一个被 getFieldDecorator 或 v-decorator 装饰过的 child，当有多个被装饰过的 child 时，`help` `required` `validateStatus` 无法自动生成。

| 参数           | 说明                                                         | 类型                                                   | 默认值  | 版本   |
| :------------- | :----------------------------------------------------------- | :----------------------------------------------------- | :------ | :----- |
| colon          | 配合 label 属性使用，表示是否显示 label 后面的冒号           | boolean                                                | true    |        |
| extra          | 额外的提示信息，和 help 类似，当需要错误信息和提示文案同时出现时，可以使用这个。 | string\|slot                                           |         |        |
| hasFeedback    | 配合 validateStatus 属性使用，展示校验状态图标，建议只配合 Input 组件使用 | boolean                                                | false   |        |
| help           | 提示信息，如不设置，则会根据校验规则自动生成                 | string\|slot                                           |         |        |
| htmlFor        | 设置子元素 label `htmlFor` 属性                              | string                                                 |         | 1.5.0  |
| label          | label 标签的文本                                             | string\|slot                                           |         |        |
| labelCol       | label 标签布局，同 `<Col>` 组件，设置 `span` `offset` 值，如 `{span: 3, offset: 12}` 或 `sm: {span: 3, offset: 12}` | [object](https://1x.antdv.com/components/grid-cn/#Col) |         |        |
| labelAlign     | 标签文本对齐方式                                             | 'left' \| 'right'                                      | 'right' | 1.5.0  |
| required       | 是否必填，如不设置，则会根据校验规则自动生成                 | boolean                                                | false   |        |
| validateStatus | 校验状态，如不设置，则会根据校验规则自动生成，可选：'success' 'warning' 'error' 'validating' | string                                                 |         |        |
| wrapperCol     | 需要为输入控件设置布局样式时，使用该属性，用法同 labelCol    | [object](https://1x.antdv.com/components/grid-cn/#Col) |         |        |
| selfUpdate     | 自定义字段更新逻辑，你可以通过 Form 的 selfUpdate 进行统一设置。当和 Form 同时设置时，以 Item 为准。 说明[见下](https://1x.antdv.com/components/form-cn/#selfUpdate) 需 1.3.17 版本以上 | boolean                                                | false   | 1.3.17 |

#### 校验规则 
| 参数       | 说明                                                         | 类型                                    | 默认值   |
| :--------- | :----------------------------------------------------------- | :-------------------------------------- | :------- |
| enum       | 枚举类型                                                     | string                                  | -        |
| len        | 字段长度                                                     | number                                  | -        |
| max        | 最大长度                                                     | number                                  | -        |
| message    | 校验文案                                                     | string                                  | -        |
| min        | 最小长度                                                     | number                                  | -        |
| pattern    | 正则表达式校验                                               | RegExp                                  | -        |
| required   | 是否必选                                                     | boolean                                 | `false`  |
| transform  | 校验前转换字段值                                             | function(value) => transformedValue:any | -        |
| type       | 内建校验类型，[可选项](https://github.com/yiminghe/async-validator#type) | string                                  | 'string' |
| validator  | 自定义校验（注意，[callback 必须被调用](https://github.com/ant-design/ant-design/issues/5155)） | function(rule, value, callback)         | -        |
| whitespace | 必选时，空格是否会被视为错误                                 | boolean                                 | `false`  |

更多高级用法可研究 [async-validator](https://github.com/yiminghe/async-validator)。

#### selfUpdate 
设置 `selfUpdate` 为 `true` 后，`Form` 通过增量方式更新，只更新被修改的字段。大部分场景下，你只需要编写代码即可。而在某些特定场景，例如修改某个字段值后出现新的字段选项、或者纯粹希望表单任意变化都需要进行渲染。你可以通过修改 Form.Item 取消 selfUpdate，或者在 `change` / `onValuesChange` 回调中手动调用 `this.$forceUpdate()` 更新组件。[示例](https://1x.antdv.com/components/form-cn/)

如果你并不精通 Vue，并不建议使用 selfUpdate，如果出现性能问题，可以尝试这把 Form 相关的业务独立到一个单独的组件中，减少组件渲染的消耗。

## 表单 (支持 v-model 检验)
具有数据收集、校验和提交功能的表单，包含复选框、单选框、输入框、下拉选择框等元素。

### 何时使用
- 需要对输入的数据类型进行校验时。

### 表单
我们为 `form` 提供了以下三种排列方式：

- 水平排列：标签和表单控件水平排列；（默认）
- 垂直排列：标签和表单控件上下垂直排列；
- 行内排列：表单项水平行内排列。

### 表单域
表单一定会包含表单域，表单域可以是输入控件，标准表单域，标签，下拉菜单，文本域等。

这里我们封装了表单域 `<FormModel.Item />` 。

### 组件注册
```js
import { FormModel } from 'ant-design-vue';
Vue.use(FormModel);
```

### 代码演示
##### 典型表单 
在 `Form` 组件中，每一个表单域由一个 `FormItem` 组件构成，表单域中可以放置各种类型的表单控件，比如输入框、选择器、开关、单选框、多选框等。

```html
<template>
  <h-form-model :model="form" :label-col="labelCol" :wrapper-col="wrapperCol">
    <h-form-model-item label="Activity name">
      <h-input v-model="form.name" />
    </h-form-model-item>
    <h-form-model-item label="Activity zone">
      <h-select v-model="form.region" placeholder="please select your zone">
        <h-select-option value="shanghai">
          Zone one
        </h-select-option>
        <h-select-option value="beijing">
          Zone two
        </h-select-option>
      </h-select>
    </h-form-model-item>
    <h-form-model-item label="Activity time">
      <h-date-picker
        v-model="form.date1"
        show-time
        type="date"
        placeholder="Pick a date"
        style="width: 100%;"
      />
    </h-form-model-item>
    <h-form-model-item label="Instant delivery">
      <h-switch v-model="form.delivery" />
    </h-form-model-item>
    <h-form-model-item label="Activity type">
      <h-checkbox-group v-model="form.type">
        <h-checkbox value="1" name="type">
          Online
        </h-checkbox>
        <h-checkbox value="2" name="type">
          Promotion
        </h-checkbox>
        <h-checkbox value="3" name="type">
          Offline
        </h-checkbox>
      </h-checkbox-group>
    </h-form-model-item>
    <h-form-model-item label="Resources">
      <h-radio-group v-model="form.resource">
        <h-radio value="1">
          Sponsor
        </h-radio>
        <h-radio value="2">
          Venue
        </h-radio>
      </h-radio-group>
    </h-form-model-item>
    <h-form-model-item label="Activity form">
      <h-input v-model="form.desc" type="textarea" />
    </h-form-model-item>
    <h-form-model-item :wrapper-col="{ span: 14, offset: 4 }">
      <h-button type="primary" @click="onSubmit">
        Create
      </h-button>
      <h-button style="margin-left: 10px;">
        Cancel
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>
<script>
export default {
  data() {
    return {
      labelCol: { span: 4 },
      wrapperCol: { span: 14 },
      form: {
        name: '',
        region: undefined,
        date1: undefined,
        delivery: false,
        type: [],
        resource: '',
        desc: '',
      },
    };
  },
  methods: {
    onSubmit() {
      console.log('submit!', this.form);
    },
  },
};
</script>
```

##### 内联登录栏 
水平登录栏，常用在顶部导航栏中。

```html
<template>
  <h-form-model layout="inline" :model="formInline" @submit="handleSubmit" @submit.native.prevent>
    <h-form-model-item>
      <h-input v-model="formInline.user" placeholder="Username">
        <h-icon slot="prefix" type="user" style="color:rgba(0,0,0,.25)" />
      </h-input>
    </h-form-model-item>
    <h-form-model-item>
      <h-input v-model="formInline.password" type="password" placeholder="Password">
        <h-icon slot="prefix" type="lock" style="color:rgba(0,0,0,.25)" />
      </h-input>
    </h-form-model-item>
    <h-form-model-item>
      <h-button
        type="primary"
        html-type="submit"
        :disabled="formInline.user === '' || formInline.password === ''"
      >
        Log in
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>
<script>
export default {
  data() {
    return {
      formInline: {
        user: '',
        password: '',
      },
    };
  },
  methods: {
    handleSubmit(e) {
      console.log(this.formInline);
    },
  },
};
</script>
```

##### 表单布局
表单有三种布局。

```html
<template>
  <h-form-model :layout="form.layout" :model="form" v-bind="formItemLayout">
    <h-form-model-item label="Form Layout">
      <h-radio-group v-model="form.layout">
        <h-radio-button value="horizontal">
          Horizontal
        </h-radio-button>
        <h-radio-button value="vertical">
          Vertical
        </h-radio-button>
        <h-radio-button value="inline">
          Inline
        </h-radio-button>
      </h-radio-group>
    </h-form-model-item>
    <h-form-model-item label="Field A">
      <h-input v-model="form.fieldA" placeholder="input placeholder" />
    </h-form-model-item>
    <h-form-model-item label="Field B">
      <h-input v-model="form.fieldB" placeholder="input placeholder" />
    </h-form-model-item>
    <h-form-model-item :wrapper-col="buttonItemLayout.wrapperCol">
      <h-button type="primary">
        Submit
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>
<script>
export default {
  data() {
    return {
      form: {
        layout: 'horizontal',
        fieldA: '',
        fieldB: '',
      },
    };
  },
  computed: {
    formItemLayout() {
      const { layout } = this.form;
      return layout === 'horizontal'
        ? {
            labelCol: { span: 4 },
            wrapperCol: { span: 14 },
          }
        : {};
    },
    buttonItemLayout() {
      const { layout } = this.form;
      return layout === 'horizontal'
        ? {
            wrapperCol: { span: 14, offset: 4 },
          }
        : {};
    },
  },
};
</script>
```

##### 表单验证 
Form 组件提供了表单验证的功能，只需要通过 `rules` 属性传入约定的验证规则，并将 `FormItem` 的 `prop` 属性设置为需校验的字段名即可。校验规则参见 [async-validator](https://github.com/yiminghe/async-validator)

```html
<template>
  <h-form-model
    ref="ruleForm"
    :model="form"
    :rules="rules"
    :label-col="labelCol"
    :wrapper-col="wrapperCol"
  >
    <h-form-model-item ref="name" label="Activity name" prop="name">
      <h-input
        v-model="form.name"
        @blur="
          () => {
            $refs.name.onFieldBlur();
          }
        "
      />
    </h-form-model-item>
    <h-form-model-item label="Activity zone" prop="region">
      <h-select v-model="form.region" placeholder="please select your zone">
        <h-select-option value="shanghai">
          Zone one
        </h-select-option>
        <h-select-option value="beijing">
          Zone two
        </h-select-option>
      </h-select>
    </h-form-model-item>
    <h-form-model-item label="Activity time" required prop="date1">
      <h-date-picker
        v-model="form.date1"
        show-time
        type="date"
        placeholder="Pick a date"
        style="width: 100%;"
      />
    </h-form-model-item>
    <h-form-model-item label="Instant delivery" prop="delivery">
      <h-switch v-model="form.delivery" />
    </h-form-model-item>
    <h-form-model-item label="Activity type" prop="type">
      <h-checkbox-group v-model="form.type">
        <h-checkbox value="1" name="type">
          Online
        </h-checkbox>
        <h-checkbox value="2" name="type">
          Promotion
        </h-checkbox>
        <h-checkbox value="3" name="type">
          Offline
        </h-checkbox>
      </h-checkbox-group>
    </h-form-model-item>
    <h-form-model-item label="Resources" prop="resource">
      <h-radio-group v-model="form.resource">
        <h-radio value="1">
          Sponsor
        </h-radio>
        <h-radio value="2">
          Venue
        </h-radio>
      </h-radio-group>
    </h-form-model-item>
    <h-form-model-item label="Activity form" prop="desc">
      <h-input v-model="form.desc" type="textarea" />
    </h-form-model-item>
    <h-form-model-item :wrapper-col="{ span: 14, offset: 4 }">
      <h-button type="primary" @click="onSubmit">
        Create
      </h-button>
      <h-button style="margin-left: 10px;" @click="resetForm">
        Reset
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>
<script>
export default {
  data() {
    return {
      labelCol: { span: 4 },
      wrapperCol: { span: 14 },
      other: '',
      form: {
        name: '',
        region: undefined,
        date1: undefined,
        delivery: false,
        type: [],
        resource: '',
        desc: '',
      },
      rules: {
        name: [
          { required: true, message: 'Please input Activity name', trigger: 'blur' },
          { min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' },
        ],
        region: [{ required: true, message: 'Please select Activity zone', trigger: 'change' }],
        date1: [{ required: true, message: 'Please pick a date', trigger: 'change' }],
        type: [
          {
            type: 'array',
            required: true,
            message: 'Please select at least one activity type',
            trigger: 'change',
          },
        ],
        resource: [
          { required: true, message: 'Please select activity resource', trigger: 'change' },
        ],
        desc: [{ required: true, message: 'Please input activity form', trigger: 'blur' }],
      },
    };
  },
  methods: {
    onSubmit() {
      this.$refs.ruleForm.validate(valid => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm() {
      this.$refs.ruleForm.resetFields();
    },
  },
};
</script>
```

##### 自定义校验规则 
这个例子中展示了如何使用自定义验证规则来完成密码的二次验证。本例还使用 `has-feedback` 属性为输入框添加了表示校验结果的反馈图标。
自定义校验 callback 必须被调用。 更多高级用法可参考 [async-validator](https://github.com/yiminghe/async-validator)

```html
<template>
  <h-form-model ref="ruleForm" :model="ruleForm" :rules="rules" v-bind="layout">
    <h-form-model-item has-feedback label="Password" prop="pass">
      <h-input v-model="ruleForm.pass" type="password" autocomplete="off" />
    </h-form-model-item>
    <h-form-model-item has-feedback label="Confirm" prop="checkPass">
      <h-input v-model="ruleForm.checkPass" type="password" autocomplete="off" />
    </h-form-model-item>
    <h-form-model-item has-feedback label="Age" prop="age">
      <h-input v-model.number="ruleForm.age" />
    </h-form-model-item>
    <h-form-model-item :wrapper-col="{ span: 14, offset: 4 }">
      <h-button type="primary" @click="submitForm('ruleForm')">
        Submit
      </h-button>
      <h-button style="margin-left: 10px" @click="resetForm('ruleForm')">
        Reset
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>
<script>
export default {
  data() {
    let checkPending;
    let checkAge = (rule, value, callback) => {
      clearTimeout(checkPending);
      if (!value) {
        return callback(new Error('Please input the age'));
      }
      checkPending = setTimeout(() => {
        if (!Number.isInteger(value)) {
          callback(new Error('Please input digits'));
        } else {
          if (value < 18) {
            callback(new Error('Age must be greater than 18'));
          } else {
            callback();
          }
        }
      }, 1000);
    };
    let validatePass = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the password'));
      } else {
        if (this.ruleForm.checkPass !== '') {
          this.$refs.ruleForm.validateField('checkPass');
        }
        callback();
      }
    };
    let validatePass2 = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input the password again'));
      } else if (value !== this.ruleForm.pass) {
        callback(new Error("Two inputs don't match!"));
      } else {
        callback();
      }
    };
    return {
      ruleForm: {
        pass: '',
        checkPass: '',
        age: '',
      },
      rules: {
        pass: [{ validator: validatePass, trigger: 'change' }],
        checkPass: [{ validator: validatePass2, trigger: 'change' }],
        age: [{ validator: checkAge, trigger: 'change' }],
      },
      layout: {
        labelCol: { span: 4 },
        wrapperCol: { span: 14 },
      },
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
  },
};
</script>
```

##### 动态增减表单项 
动态增加、减少表单项。

```html
<template>
  <h-form-model
    ref="dynamicValidateForm"
    :model="dynamicValidateForm"
    v-bind="formItemLayoutWithOutLabel"
  >
    <h-form-model-item
      v-for="(domain, index) in dynamicValidateForm.domains"
      :key="domain.key"
      v-bind="index === 0 ? formItemLayout : {}"
      :label="index === 0 ? 'Domains' : ''"
      :prop="'domains.' + index + '.value'"
      :rules="{
        required: true,
        message: 'domain can not be null',
        trigger: 'blur',
      }"
    >
      <h-input
        v-model="domain.value"
        placeholder="please input domain"
        style="width: 60%; margin-right: 8px"
      />
      <h-icon
        v-if="dynamicValidateForm.domains.length > 1"
        class="dynamic-delete-button"
        type="minus-circle-o"
        :disabled="dynamicValidateForm.domains.length === 1"
        @click="removeDomain(domain)"
      />
    </h-form-model-item>
    <h-form-model-item v-bind="formItemLayoutWithOutLabel">
      <h-button type="dashed" style="width: 60%" @click="addDomain">
        <h-icon type="plus" /> Add field
      </h-button>
    </h-form-model-item>
    <h-form-model-item v-bind="formItemLayoutWithOutLabel">
      <h-button type="primary" html-type="submit" @click="submitForm('dynamicValidateForm')">
        Submit
      </h-button>
      <h-button style="margin-left: 10px" @click="resetForm('dynamicValidateForm')">
        Reset
      </h-button>
    </h-form-model-item>
  </h-form-model>
</template>

<script>
export default {
  data() {
    return {
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 4 },
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 20 },
        },
      },
      formItemLayoutWithOutLabel: {
        wrapperCol: {
          xs: { span: 24, offset: 0 },
          sm: { span: 20, offset: 4 },
        },
      },
      dynamicValidateForm: {
        domains: [],
      },
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
    removeDomain(item) {
      let index = this.dynamicValidateForm.domains.indexOf(item);
      if (index !== -1) {
        this.dynamicValidateForm.domains.splice(index, 1);
      }
    },
    addDomain() {
      this.dynamicValidateForm.domains.push({
        value: '',
        key: Date.now(),
      });
    },
  },
};
</script>
<style>
.dynamic-delete-button {
  cursor: pointer;
  position: relative;
  top: 4px;
  font-size: 24px;
  color: #999;
  transition: all 0.3s;
}
.dynamic-delete-button:hover {
  color: #777;
}
.dynamic-delete-button[disabled] {
  cursor: not-allowed;
  opacity: 0.5;
}
</style>
```

### API 
#### Form 
| 参数                 | 说明                                                         | 类型                                                   | 默认值       | 版本 |
| :------------------- | :----------------------------------------------------------- | :----------------------------------------------------- | :----------- | :--- |
| model                | 表单数据对象                                                 | object                                                 |              |      |
| rules                | 表单验证规则                                                 | object                                                 |              |      |
| hideRequiredMark     | 隐藏所有表单项的必选标记                                     | Boolean                                                | false        |      |
| labelAlign           | label 标签的文本对齐方式                                     | 'left' \| 'right'                                      | 'right'      |      |
| layout               | 表单布局                                                     | 'horizontal'\|'vertical'\|'inline'                     | 'horizontal' |      |
| labelCol             | label 标签布局，同 `<Col>` 组件，设置 `span` `offset` 值，如 `{span: 3, offset: 12}` 或 `sm: {span: 3, offset: 12}` | [object](https://1x.antdv.com/components/grid-cn/#Col) |              |      |
| wrapperCol           | 需要为输入控件设置布局样式时，使用该属性，用法同 labelCol    | [object](https://1x.antdv.com/components/grid-cn/#Col) |              |      |
| colon                | 配置 Form.Item 的 colon 的默认值 (只有在属性 layout 为 horizontal 时有效) | boolean                                                | true         |      |
| validateOnRuleChange | 是否在 rules 属性改变后立即触发一次验证                      | boolean                                                | false        |      |

#### 事件 
| 事件名称 | 说明                   | 回调参数                                                   |
| :------- | :--------------------- | :--------------------------------------------------------- |
| submit   | 数据验证成功后回调事件 | Function(e:Event)                                          |
| validate | 任一表单项被校验后触发 | 被校验的表单项 prop 值，校验是否通过，错误消息（如果存在） |

#### 方法 
| 方法名        | 说明                                                         | 参数                                                         |
| :------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| validate      | 对整个表单进行校验的方法，参数为一个回调函数。该回调函数会在校验结束后被调用，并传入两个参数：是否校验成功和未通过校验的字段。若不传入回调函数，则会返回一个 promise | Function(callback: Function(boolean, object))                |
| validateField | 对部分表单字段进行校验的方法                                 | Function(props: array \| string, callback: Function(errorMessage: string)) |
| resetFields   | 对整个表单进行重置，将所有字段值重置为初始值并移除校验结果   | —                                                            |
| clearValidate | 移除表单项的校验结果。传入待移除的表单项的 prop 属性或者 prop 组成的数组，如不传则移除整个表单的校验结果 | Function(props: array \| string)                             |

#### Form.Item 
| 参数           | 说明                                                         | 类型                                                   | 默认值  | 版本 |
| :------------- | :----------------------------------------------------------- | :----------------------------------------------------- | :------ | :--- |
| prop           | 表单域 model 字段，在使用 validate、resetFields 方法的情况下，该属性是必填的 | string                                                 |         |      |
| rules          | 表单验证规则                                                 | object \| array                                        |         |      |
| autoLink       | 是否自动关联表单域，对于大部分情况都可以使用自动关联，如果不满足自动关联的条件，可以手动关联，参见下方注意事项 | boolean                                                | true    |      |
| colon          | 配合 label 属性使用，表示是否显示 label 后面的冒号           | boolean                                                | true    |      |
| extra          | 额外的提示信息，和 help 类似，当需要错误信息和提示文案同时出现时，可以使用这个。 | string\|slot                                           |         |      |
| hasFeedback    | 配合 validateStatus 属性使用，展示校验状态图标，建议只配合 Input 组件使用 | boolean                                                | false   |      |
| help           | 提示信息，如不设置，则会根据校验规则自动生成                 | string\|slot                                           |         |      |
| htmlFor        | 设置子元素 label `htmlFor` 属性                              | string                                                 |         |      |
| label          | label 标签的文本                                             | string\|slot                                           |         |      |
| labelCol       | label 标签布局，同 `<Col>` 组件，设置 `span` `offset` 值，如 `{span: 3, offset: 12}` 或 `sm: {span: 3, offset: 12}` | [object](https://1x.antdv.com/components/grid-cn/#Col) |         |      |
| labelAlign     | 标签文本对齐方式                                             | 'left' \| 'right'                                      | 'right' |      |
| required       | 是否必填，如不设置，则会根据校验规则自动生成                 | boolean                                                | false   |      |
| validateStatus | 校验状态，如不设置，则会根据校验规则自动生成，可选：'success' 'warning' 'error' 'validating' | string                                                 |         |      |
| wrapperCol     | 需要为输入控件设置布局样式时，使用该属性，用法同 labelCol    | [object](https://1x.antdv.com/components/grid-cn/#Col) |         |      |

##### 注意：
Form.Item 会对唯一子元素进行劫持，并监听 `blur` 和 `change` 事件，来达到自动校验的目的，所以请确保表单域没有其它元素包裹。如果有多个子元素，将只会监听第一个子元素的变化。

如果要监听的表单域不满足自动监听的条件，可以通过如下方式关联表单域：

```html
<h-form-model-item prop="form.name" ref="name" :autoLink="false">
  <h-input v-model="other" />
  <span>hahha</span>
  <div>
    <h-input
      v-model="form.name"
      @blur="() => {$refs.name.onFieldBlur()}"
      @change="() => {$refs.name.onFieldChange()}"
    />
  </div>
</h-form-model-item>
```

#### 校验规则
| 参数       | 说明                                                         | 类型                                       | 默认值   |
| :--------- | :----------------------------------------------------------- | :----------------------------------------- | :------- |
| trigger    | 校验触发的时机                                               | 'blur' \| 'change' \| `['change', 'blur']` | -        |
| enum       | 枚举类型                                                     | string                                     | -        |
| len        | 字段长度                                                     | number                                     | -        |
| max        | 最大长度                                                     | number                                     | -        |
| message    | 校验文案                                                     | string                                     | -        |
| min        | 最小长度                                                     | number                                     | -        |
| pattern    | 正则表达式校验                                               | RegExp                                     | -        |
| required   | 是否必选                                                     | boolean                                    | `false`  |
| transform  | 校验前转换字段值                                             | function(value) => transformedValue:any    | -        |
| type       | 内建校验类型，[可选项](https://github.com/yiminghe/async-validator#type) | string                                     | 'string' |
| validator  | 自定义校验（注意，[callback 必须被调用](https://github.com/ant-design/ant-design/issues/5155)） | function(rule, value, callback)            | -        |
| whitespace | 必选时，空格是否会被视为错误                                 | boolean                                    | `false`  |

更多高级用法可研究 [async-validator](https://github.com/yiminghe/async-validator)。

## 数字输入框
通过鼠标或键盘，输入范围内的数值。

### 何时使用
当需要获取标准数值时。

### 代码演示
##### 基本 
数字输入框。

```html
<template>
  <div>
    <h-input-number id="inputNumber" v-model="value" :min="1" :max="10" @change="onChange" />
    当前值：{{ value }}
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: 3,
    };
  },
  methods: {
    onChange(value) {
      console.log('changed', value);
    },
  },
};
</script>
```

##### 不可用
点击按钮切换可用状态。

```html
<template>
  <div>
    <h-input-number :min="1" :max="10" :disabled="disabled" :default-value="3" />
    <div style="marginTop:20px">
      <h-button type="primary" @click="toggle">
        Toggle disabled
      </h-button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: true,
    };
  },
  methods: {
    toggle() {
      this.disabled = !this.disabled;
    },
  },
};
</script>
```

##### 格式化展示 
通过 `formatter` 格式化数字，以展示具有具体含义的数据，往往需要配合 `parser` 一起使用。

```html
<template>
  <div>
    <h-input-number
      :default-value="1000"
      :formatter="value => `$ ${value}`.replace(/\B(?=(\d{3})+(?!\d))/g, ',')"
      :parser="value => value.replace(/\$\s?|(,*)/g, '')"
      @change="onChange"
    />
    <h-input-number
      :default-value="100"
      :min="0"
      :max="100"
      :formatter="value => `${value}%`"
      :parser="value => value.replace('%', '')"
      @change="onChange"
    />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(value) {
      console.log('changed', value);
    },
  },
};
</script>
```

##### 三种大小 
三种大小的数字输入框，当 size 分别为 `large` 和 `small` 时，输入框高度为 `40px` 和 `24px` ，默认高度为 `32px`。

```html
<template>
  <div>
    <h-input-number size="large" :min="1" :max="100000" :default-value="3" @change="onChange" />
    <h-input-number :min="1" :max="100000" :default-value="3" @change="onChange" />
    <h-input-number size="small" :min="1" :max="100000" :default-value="3" @change="onChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(value) {
      console.log('changed', value);
    },
  },
};
</script>
<style scoped>
.ant-input-number {
  margin-right: 10px;
}
</style>
```

##### 小数 
和原生的数字输入框一样，value 的精度由 step 的小数位数决定。

```html
<template>
  <h-input-number :min="0" :max="10" :step="0.1" @change="onChange" />
</template>
<script>
export default {
  methods: {
    onChange(value) {
      console.log('changed', value);
    },
  },
};
</script>
```

### API
属性如下

| 成员             | 说明                                                       | 类型                                      | 默认值    |
| :--------------- | :--------------------------------------------------------- | :---------------------------------------- | :-------- |
| autoFocus        | 自动获取焦点                                               | boolean                                   | false     |
| defaultValue     | 初始值                                                     | number                                    |           |
| disabled         | 禁用                                                       | boolean                                   | false     |
| formatter        | 指定输入框展示值的格式                                     | function(value: number \| string): string | -         |
| max              | 最大值                                                     | number                                    | Infinity  |
| min              | 最小值                                                     | number                                    | -Infinity |
| parser           | 指定从 formatter 里转换回数字的方式，和 formatter 搭配使用 | function( string): number                 | -         |
| precision        | 数值精度                                                   | number                                    | -         |
| decimalSeparator | 小数点                                                     | string                                    | -         |
| size             | 输入框大小                                                 | string                                    | 无        |
| step             | 每次改变步数，可以为小数                                   | number\|string                            | 1         |
| value(v-model)   | 当前值                                                     | number                                    |           |

#### 事件 
| 事件名称   | 说明           | 回调参数                          | 版本 |
| :--------- | :------------- | :-------------------------------- | :--- |
| change     | 变化回调       | Function(value: number \| string) |      |
| pressEnter | 按下回车的回调 | function(e)                       |      |

### 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 提及
提及组件。

### 何时使用
- 用于在输入中提及某人或某事，常用于发布、聊天或评论功能。

### 代码演示
##### 基础列表
基本使用。

```html
<template>
  <h-mentions v-model="value" @change="onChange" @select="onSelect">
    <h-mentions-option value="afc163">
      afc163
    </h-mentions-option>
    <h-mentions-option value="zombieJ">
      zombieJ
    </h-mentions-option>
    <h-mentions-option value="yesmeck">
      yesmeck
    </h-mentions-option>
  </h-mentions>
</template>
<script>
export default {
  data() {
    return {
      value: '@afc163',
    };
  },
  methods: {
    onSelect(option) {
      console.log('select', option);
    },
    onChange(value) {
      console.log('Change:', value);
    },
  },
};
</script>
```

##### 配合 Form 使用 
受控模式，例如配合 Form 使用。

```html
<template>
  <h-form :form="form" layout="horizontal">
    <h-form-item label="Top coders" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
      <h-mentions
        v-decorator="[
          'coders',
          {
            rules: [{ validator: checkMention }],
          },
        ]"
        rows="1"
      >
        <h-mentions-option value="afc163">
          afc163
        </h-mentions-option>
        <h-mentions-option value="zombieJ">
          zombieJ
        </h-mentions-option>
        <h-mentions-option value="yesmeck">
          yesmeck
        </h-mentions-option>
      </h-mentions>
    </h-form-item>
    <h-form-item label="Bio" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }">
      <h-mentions
        v-decorator="[
          'bio',
          {
            rules: [{ required: true }],
          },
        ]"
        rows="3"
        placeholder="You can use @ to ref user here"
      >
        <h-mentions-option value="afc163">
          afc163
        </h-mentions-option>
        <h-mentions-option value="zombieJ">
          zombieJ
        </h-mentions-option>
        <h-mentions-option value="yesmeck">
          yesmeck
        </h-mentions-option>
      </h-mentions>
    </h-form-item>
    <h-form-item :wrapper-col="{ span: 12, offset: 5 }">
      <h-button type="primary" @click="handleSubmit">
        Submit
      </h-button>
      <h-button style="margin-left: 8px;" @click="handleReset">
        Reset
      </h-button>
    </h-form-item>
  </h-form>
</template>
<script>
import { Mentions } from 'ant-design-vue';
const { getMentions } = Mentions;
export default {
  data() {
    return {
      form: this.$form.createForm(this, { name: 'mentions' }),
    };
  },
  methods: {
    handleReset(e) {
      e.preventDefault();
      this.form.resetFields();
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((errors, values) => {
        if (errors) {
          console.log('Errors in the form!!!');
          return;
        }
        console.log('Submit!!!');
        console.log(values);
      });
    },
    checkMention(rule, value, callback) {
      const mentions = getMentions(value);
      if (mentions.length < 2) {
        callback(new Error('More than one must be selected!'));
      } else {
        callback();
      }
    },
  },
};
</script>
```

##### 无效或只读
通过 `disabled` 属性设置是否生效。通过 `readOnly` 属性设置是否只读。

```html
<template>
  <div>
    <div style="margin-bottom: 10px">
      <h-mentions placeholder="this is disabled Mentions" disabled>
        <h-mentions-option v-for="value in options" :key="value" :value="value">
          {{ value }}
        </h-mentions-option>
      </h-mentions>
    </div>
    <h-mentions placeholder="this is readOnly h-mentions" readonly>
      <h-mentions-option v-for="value in options" :key="value" :value="value">
        {{ value }}
      </h-mentions-option>
    </h-mentions>
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: ['afc163', 'zombieJ', 'yesmeck'],
    };
  },
};
</script>
```

##### 异步加载 
匹配内容列表为异步返回时。

```html
<template>
  <h-mentions :loading="loading" @search="onSearch">
    <h-mentions-option
      v-for="({ login, avatar_url: avatar }) in users"
      :key="login"
      :value="login"
    >
      <img :src="avatar" :alt="login" style="width: 20px; margin-right: 8px;">
      <span>{{ login }}</span>
    </h-mentions-option>
  </h-mentions>
</template>

<script>
import debounce from 'lodash/debounce';
export default {
  data() {
    return {
      loading: false,
      users: [],
    };
  },
  mounted() {
    this.loadGithubUsers = debounce(this.loadGithubUsers, 800);
  },
  methods: {
    onSearch(search) {
      this.search = search;
      this.loading = !!search;
      console.log(!!search);
      this.users = [];
      console.log('Search:', search);
      this.loadGithubUsers(search);
    },
    loadGithubUsers(key) {
      if (!key) {
        this.users = [];
        return;
      }
      fetch(`https://api.github.com/search/users?q=${key}`)
        .then(res => res.json())
        .then(({ items = [] }) => {
          const { search } = this;
          if (search !== key) return;

          this.users = items.slice(0, 10);
          this.loading = false;
        });
      },
  },
};
</script>
<style>
```

##### 自定义触发字符
通过 prefix 属性自定义触发字符。默认为 @, 可以定义为数组。

```html
<template>
  <h-mentions
    placeholder="input @ to mention people, # to mention tag"
    :prefix="['@', '#']"
    @search="onSearch"
  >
    <h-mentions-option v-for="value in MOCK_DATA[prefix] || []" :key="value" :value="value">
      {{ value }}
    </h-mentions-option>
  </h-mentions>
</template>
<script>
const MOCK_DATA = {
  '@': ['afc163', 'zombiej', 'yesmeck'],
  '#': ['1.0', '2.0', '3.0'],
};

export default {
  data() {
    return {
      prefix: '@',
      MOCK_DATA,
    };
  },
  methods: {
    onSearch(_, prefix) {
      console.log(_, prefix);
      this.prefix = prefix;
    },
  },
};
</script>
```

##### 向上展开
向上展开建议。

```html
<template>
  <h-mentions placement="top">
    <h-mentions-option value="afc163">
      afc163
    </h-mentions-option>
    <h-mentions-option value="zombieJ">
      zombieJ
    </h-mentions-option>
    <h-mentions-option value="yesmeck">
      yesmeck
    </h-mentions-option>
  </h-mentions>
</template>
```

### API 
#### Mentions 
| 参数              | 说明                       | 类型                                                     | 默认值      |
| :---------------- | :------------------------- | :------------------------------------------------------- | :---------- |
| autoFocus         | 自动获得焦点               | boolean                                                  | `false`     |
| defaultValue      | 默认值                     | string                                                   |             |
| filterOption      | 自定义过滤逻辑             | false \| (input: string, option: OptionProps) => boolean |             |
| notFoundContent   | 当下拉列表为空时显示的内容 | ReactNode                                                | 'Not Found' |
| placement         | 弹出层展示位置             | `top`                                                    | `bottom`    |
| prefix            | 设置触发关键字             | string \| string[]                                       | '@'         |
| split             | 设置选中项前后分隔符       | string                                                   | ' '         |
| validateSearch    | 自定义触发验证逻辑         | (text: string, props: MentionsProps) => void             |             |
| value(v-model)    | 设置值                     | string                                                   |             |
| getPopupContainer | 指定建议框挂载的 HTML 节点 | () => HTMLElement                                        |             |

#### 事件
| 事件名称 | 说明               | 回调参数                                      |
| :------- | :----------------- | :-------------------------------------------- |
| blur     | 失去焦点的时回调   | function                                      |
| change   | 值改变时触发       | function(value: string)                       |
| focus    | 获得焦点时回调     | function                                      |
| search   | 文本框值变化时回调 | function(value: string, prefix: string)       |
| select   | 选择选项时触发     | function(option: OptionProps, prefix: string) |

#### Mentions 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

#### Option 
| 参数  | 说明           | 类型   | 默认值 |
| :---- | :------------- | :----- | :----- |
| value | 选择时填充的值 | string | ''     |

## 单选框
单选框。

### 何时使用
- 用于在多个备选项中选中单个状态。

- 和 Select 的区别是，Radio 所有选项默认可见，方便用户在比较中选择，因此选项不宜过多。

### 代码演示
##### 基本 
最简单的用法。

```html
<template>
  <h-radio>Radio</h-radio>
</template>
```

##### 按钮样式 
按钮样式的单选组合。

```html
<template>
  <div>
    <div>
      <h-radio-group v-model="value" @change="onChange">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
    <div :style="{ marginTop: '16px' }">
      <h-radio-group default-value="a" @change="onChange">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b" disabled>
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
    <div :style="{ marginTop: '16px' }">
      <h-radio-group disabled default-value="a" @change="onChange">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: 'a',
    };
  },
  methods: {
    onChange(e) {
      console.log(`checked = ${e.target.value}`);
    },
  },
};
</script>
```

##### RadioGroup 垂直
垂直的 RadioGroup，配合更多输入框选项。

```html
<template>
  <h-radio-group v-model="value" @change="onChange">
    <h-radio :style="radioStyle" :value="1">
      Option A
    </h-radio>
    <h-radio :style="radioStyle" :value="2">
      Option B
    </h-radio>
    <h-radio :style="radioStyle" :value="3">
      Option C
    </h-radio>
    <h-radio :style="radioStyle" :value="4">
      More...
      <h-input v-if="value === 4" :style="{ width: 100, marginLeft: 10 }" />
    </h-radio>
  </h-radio-group>
</template>
<script>
export default {
  data() {
    return {
      value: 1,
      radioStyle: {
        display: 'block',
        height: '30px',
        lineHeight: '30px',
      },
    };
  },
  methods: {
    onChange(e) {
      console.log('radio checked', e.target.value);
    },
  },
};
</script>
```

##### 单选组合 - 配合 name 使用 
可以为 Radio.Group 配置 `name` 参数，为组合内的 input 元素赋予相同的 `name` 属性，使浏览器把 Radio.Group 下的 Radio 真正看作是一组（例如可以通过方向键始终**在同一组内**更改选项）。

```html
<template>
  <h-radio-group name="radioGroup" :default-value="1">
    <h-radio :value="1">
      A
    </h-radio>
    <h-radio :value="2">
      B
    </h-radio>
    <h-radio :value="3">
      C
    </h-radio>
    <h-radio :value="4">
      D
    </h-radio>
  </h-radio-group>
</template>
```

##### 大小 
大中小三种组合，可以和表单输入框进行对应配合。

```html
<template>
  <div>
    <div>
      <h-radio-group default-value="a" size="large">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
    <div :style="{ marginTop: '16px' }">
      <h-radio-group default-value="a">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d[#](https://1x.antdv.com/components/radio-cn/#Radio-2)">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
    <div :style="{ marginTop: '16px' }">
      <h-radio-group default-value="a" size="small">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
  </div>
</template>
```

##### 不可用 
Radio 不可用。

```html
<template>
  <div>
    <h-radio :default-checked="false" :disabled="disabled">
      Disabled
    </h-radio>
    <br />
    <h-radio default-checked :disabled="disabled">
      Disabled
    </h-radio>
    <div :style="{ marginTop: 20 }">
      <h-button type="primary" @click="toggleDisabled">
        Toggle disabled
      </h-button>
    </div>
  </div>
</template>
<script>[#](https://1x.antdv.com/components/radio-cn/#Radio-2)
export default {
  data() {
    return {
      disabled: true,
    };
  },
  methods: {
    toggleDisabled() {
      this.disabled = !this.disabled;
    },
  },
};
</script>
```

##### 填底的按钮样式 
实色填底的单选按钮样式。

```html
<template>
  <div>
    <div>
      <h-radio-group default-value="a" button-style="solid">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b">
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
    <div :style="{ marginTop: '16px' }">
      <h-radio-group default-value="c" button-style="solid">
        <h-radio-button value="a">
          Hangzhou
        </h-radio-button>
        <h-radio-button value="b" disabled>
          Shanghai
        </h-radio-button>
        <h-radio-button value="c">
          Beijing
        </h-radio-button>
        <h-radio-button value="d">
          Chengdu
        </h-radio-button>
      </h-radio-group>
    </div>
  </div>
</template>
```

##### RadioGroup 组合 - 配置方式
通过配置 `options` 参数来渲染单选框。

```html
<template>
  <div>
    <h-radio-group :options="plainOptions" :default-value="value1" @change="onChange1" />
    <br />
    <h-radio-group v-model="value2" :options="options" @change="onChange2" />
    <br />
    <h-radio-group v-model="value3" :options="optionsWithDisabled" disabled @change="onChange3" />
  </div>
</template>
<script>
const plainOptions = ['Apple', 'Pear', 'Orange'];
const options = [
  { label: 'Apple', value: 'Apple' },
  { label: 'Pear', value: 'Pear' },
  { label: 'Orange', value: 'Orange' },
];
const optionsWithDisabled = [
  { label: 'Apple', value: 'Apple' },
  { label: 'Pear', value: 'Pear' },
  { label: 'Orange', value: 'Orange', disabled: false },
];
export default {
  data() {
    return {
      plainOptions,
      options,
      optionsWithDisabled,
      value1: 'Apple',
      value2: 'Apple',
      value3: 'Apple',
    };
  },
  methods: {
    onChange1(e) {
      console.log('radio1 checked', e.target.value);
    },
    onChange2(e) {
      console.log('radio2 checked', e.target.value);
    },
    onChange3(e) {
      console.log('radio3 checked', e.target.value);
    },
  },
};
</script>
```

##### 单选组合 
一组互斥的 Radio 配合使用。

```html
<template>
  <div>
    <h-radio-group v-model="value" @change="onChange">
      <h-radio :value="1">
        A
      </h-radio>
      <h-radio :value="2">
        B
      </h-radio>
      <h-radio :value="3">
        C
      </h-radio>
      <h-radio :value="4">
        D
      </h-radio>
    </h-radio-group>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: 1,
    };
  },
  methods: {
    onChange(e) {
      console.log('radio checked', e.target.value);
    },
  },
};
</script>
```

### API 
#### Radio 
| 参数           | 说明                              | 类型    | 默认值 |
| :------------- | :-------------------------------- | :------ | :----- |
| autoFocus      | 自动获取焦点                      | boolean | false  |
| checked        | 指定当前是否选中                  | boolean | false  |
| defaultChecked | 初始是否选中                      | boolean | false  |
| value          | 根据 value 进行比较，判断是否选中 | any     | -      |

#### RadioGroup 
单选框组合，用于包裹一组 `Radio`。

| 参数           | 说明                                                   | 类型                                                         | 默认值    |
| :------------- | :----------------------------------------------------- | :----------------------------------------------------------- | :-------- |
| defaultValue   | 默认选中的值                                           | any                                                          | -         |
| disabled       | 禁选所有子单选器                                       | boolean                                                      | false     |
| name           | RadioGroup 下所有 `input[type="radio"]` 的 `name` 属性 | string                                                       | -         |
| options        | 以配置形式设置子元素                                   | string[] \| Array<{ label: string value: string disabled?: boolean }> | -         |
| size           | 大小，只对按钮样式生效                                 | `large`                                                      | `default` |
| value(v-model) | 用于设置当前选中的值                                   | any                                                          | -         |
| buttonStyle    | RadioButton 的风格样式，目前有描边和填色两种风格       | `outline`                                                    | `solid`   |

#### RadioGroup 事件
| 事件名称 | 说明                 | 回调参数          |
| :------- | :------------------- | :---------------- |
| change   | 选项变化时的回调函数 | Function(e:Event) |

### 方法 
#### Radio 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 评分
评分组件。

### 何时使用
- 对评价进行展示。

- 对事物进行快速的评级操作。

### 代码演示
##### 基本
最简单的用法。

```html
<template>
  <h-rate v-model="value" />
</template>
<script>
export default {
  data() {
    return {
      value: 2,
    };
  },
};
</script>
```

##### 文案展现 
给评分组件加上文案展示。

```html
<template>
  <span>
    <h-rate v-model="value" :tooltips="desc" />
    <span class="ant-rate-text">{{ desc[value - 1] }}</span>
  </span>
</template>
<script>
export default {
  data() {
    return {
      value: 3,
      desc: ['terrible', 'bad', 'normal', 'good', 'wonderful'],
    };
  },
};
</script>
```

##### 清除 
支持允许或者禁用清除。

```html
<template>
  <div>
    <h-rate :default-value="3" />
    <span class="ant-rate-text">allowClear: true</span>
    <br />
    <h-rate :allow-clear="false" :default-value="3" />
    <span class="ant-rate-text">allowClear: false</span>
  </div>
</template>
```

##### 半星 
支持选中半星。

```html
<template>
  <h-rate :default-value="2.5" allow-half />
</template>
```

##### 只读 
只读，无法进行鼠标交互。

```html
<template>
  <h-rate :default-value="2" disabled />
</template>
```

##### 其他字符
可以将星星替换为其他字符，比如字母，数字，字体图标甚至中文。

```html
<template>
  <div>
    <h-rate allow-half>
      <h-icon slot="character" type="heart" />
    </h-rate>
    <br />
    <h-rate character="A" allow-half style="fontSize: 36px" />
    <br />
    <h-rate character="好" allow-half />
    <br />
  </div>
</template>
```

### API 
| 属性           | 说明                   | 类型                       | 默认值                 |
| :------------- | :--------------------- | :------------------------- | :--------------------- |
| allowClear     | 是否允许再次点击后清除 | boolean                    | true                   |
| allowHalf      | 是否允许半选           | boolean                    | false                  |
| autoFocus      | 自动获取焦点           | boolean                    | false                  |
| character      | 自定义字符             | String or slot="character" | `<Icon type="star" />` |
| count          | star 总数              | number                     | 5                      |
| defaultValue   | 默认值                 | number                     | 0                      |
| disabled       | 只读，无法进行交互     | boolean                    | false                  |
| tooltips       | 自定义每项的提示信息   | string[]                   | -                      |
| value(v-model) | 当前数，受控值         | number                     | -                      |

#### 事件 
| 事件名称    | 说明                     | 回调参数                |
| :---------- | :----------------------- | :---------------------- |
| blur        | 失去焦点时的回调         | Function()              |
| change      | 选择时的回调             | Function(value: number) |
| focus       | 获取焦点时的回调         | Function()              |
| hoverChange | 鼠标经过时数值变化的回调 | Function(value: number) |
| keydown     | 按键回调                 | Function(event)         |

### 方法
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 选择器
下拉选择器。

### 何时使用
- 弹出一个下拉菜单给用户选择操作，用于代替原生的选择器，或者需要一个更优雅的多选器时。
- 当选项少时（少于 5 项），建议直接将选项平铺，使用 [Radio](https://1x.antdv.com/ant-design/components/radio-cn/) 是更好的选择。

### 代码演示
##### 基本使用 
基本使用。

```html
<template>
  <div>
    <h-select default-value="lucy" style="width: 120px" @change="handleChange">
      <h-select-option value="jack">
        Jack
      </h-select-option>
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
      <h-select-option value="disabled" disabled>
        Disabled
      </h-select-option>
      <h-select-option value="Yiminghe">
        yiminghe
      </h-select-option>
    </h-select>
    <h-select default-value="lucy" style="width: 120px" disabled>
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
    </h-select>
    <h-select default-value="lucy" style="width: 120px" loading>
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
    </h-select>
  </div>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 标签
tags select，随意输入的内容（scroll the menu）

```html
<template>
  <h-select mode="tags" style="width: 100%" placeholder="Tags Mode" @change="handleChange">
    <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
      {{ (i + 9).toString(36) + i }}
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 获得选项的文本
默认情况下 `onChange` 里只能拿到 value，如果需要拿到选中的节点文本 label，可以使用 `labelInValue` 属性。
选中项的 label 会被包装到 value 中传递给 `onChange` 等函数，此时 value 是一个对象。

```html
<template>
  <h-select
    label-in-value
    :default-value="{ key: 'lucy' }"
    style="width: 120px"
    @change="handleChange"
  >
    <h-select-option value="jack">
      Jack (100)
    </h-select-option>
    <h-select-option value="lucy">
      Lucy (101)
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(value); // { key: "lucy", label: "Lucy (101)" }
    },
  },
};
</script>
```

##### 联动 
省市联动是典型的例子。
推荐使用 [Cascader](https://1x.antdv.com/components/cascader-cn/) 组件。

```html
<template>
  <div>
    <h-select :default-value="provinceData[0]" style="width: 120px" @change="handleProvinceChange">
      <h-select-option v-for="province in provinceData" :key="province">
        {{ province }}
      </h-select-option>
    </h-select>
    <h-select v-model="secondCity" style="width: 120px">
      <h-select-option v-for="city in cities" :key="city">
        {{ city }}
      </h-select-option>
    </h-select>
  </div>
</template>
<script>
const provinceData = ['Zhejiang', 'Jiangsu'];
const cityData = {
  Zhejiang: ['Hangzhou', 'Ningbo', 'Wenzhou'],
  Jiangsu: ['Nanjing', 'Suzhou', 'Zhenjiang'],
};
export default {
  data() {
    return {
      provinceData,
      cityData,
      cities: cityData[provinceData[0]],
      secondCity: cityData[provinceData[0]][0],
    };
  },
  methods: {
    handleProvinceChange(value) {
      this.cities = cityData[value];
      this.secondCity = cityData[value][0];
    },
  },
};
</script>
```

##### 搜索框
搜索和远程数据结合。

```html
<template>
  <h-select
    show-search
    :value="value"
    placeholder="input search text"
    style="width: 200px"
    :default-active-first-option="false"
    :show-arrow="false"
    :filter-option="false"
    :not-found-content="null"
    @search="handleSearch"
    @change="handleChange"
  >
    <h-select-option v-for="d in data" :key="d.value">
      {{ d.text }}
    </h-select-option>
  </h-select>
</template>
<script>
import jsonp from 'fetch-jsonp';
import querystring from 'querystring';

let timeout;
let currentValue;

function fetch(value, callback) {
  if (timeout) {
    clearTimeout(timeout);
    timeout = null;
  }
  currentValue = value;

  function fake() {
    const str = querystring.encode({
      code: 'utf-8',
      q: value,
    });
    jsonp(`https://suggest.taobao.com/sug?${str}`)
      .then(response => response.json())
      .then(d => {
        if (currentValue === value) {
          const result = d.result;
          const data = [];
          result.forEach(r => {
            data.push({
              value: r[0],
              text: r[0],
            });
          });
          callback(data);
        }
      });
  }

  timeout = setTimeout(fake, 300);
}
export default {
  data() {
    return {
      data: [],
      value: undefined,
    };
  },
  methods: {
    handleSearch(value) {
      fetch(value, data => (this.data = data));
    },
    handleChange(value) {
      console.log(value);
      this.value = value;
      fetch(value, data => (this.data = data));
    },
  },
};
</script>
```

##### 搜索用户 
一个带有远程搜索，节流控制，请求时序控制，加载状态的多选示例。

```html
<template>
  <h-select
    mode="multiple"
    label-in-value
    :value="value"
    placeholder="Select users"
    style="width: 100%"
    :filter-option="false"
    :not-found-content="fetching ? undefined : null"
    @search="fetchUser"
    @change="handleChange"
  >
    <h-spin v-if="fetching" slot="notFoundContent" size="small" />
    <h-select-option v-for="d in data" :key="d.value">
      {{ d.text }}
    </h-select-option>
  </h-select>
</template>
<script>
import debounce from 'lodash/debounce';

export default {
  data() {
    this.lastFetchId = 0;
    this.fetchUser = debounce(thi[#](https://1x.antdv.com/components/select-cn/#FAQ)s.fetchUser, 800);
    return {
      data: [],
      value: [],
      fetching: false,
    };
  },
  methods: {
    fetchUser(value) {
      console.log('fetching user', value);
      this.lastFetchId += 1;
      const fetchId = this.lastFetchId;
      this.data = [];
      this.fetching = true;
      fetch('https://randomuser.me/api/?results=5')
        .then(response => response.json())
        .then(body => {
          if (fetchId !== this.lastFetchId) {
            // for fetch callback order
            return;
          }
          const data = body.results.map(user => ({
            text: `${user.name.first} ${user.name.last}`,
            value: user.login.username,
          }));
          this.data = data;
          this.fetching = false;
        });
    },
    handleChange(value) {
      Object.assign(this, {
        value,
        data: [],
        fetching: false,
      });
    },
  },
};
</script>
```

##### 隐藏已选择选项
隐藏下拉列表中已选择的选项。

```html
<template>
  <h-select
    mode="multiple"
    placeholder="Inserted are removed"
    :value="selectedItems"
    style="width: 100%"
    @change="handleChange"
  >
    <h-select-option v-for="item in filteredOptions" :key="item" :value="item">
      {{ item }}
    </h-select-option>
  </h-select>
</template>
<script>
const OPTIONS = ['Apples', 'Nails', 'Bananas', 'Helicopters'];
export default {
  data() {
    return {
      selectedItems: [],
    };
  },
  computed: {
    filteredOptions() {
      return OPTIONS.filter(o => !this.selectedItems.includes(o));
    },
  },
  methods: {
    handleChange(selectedItems) {
      this.selectedItems = selectedItems;
    },
  },
};
</script>
```

##### 定制回填内容 
使用 `optionLabelProp` 指定回填到选择框的 `Option` 属性。

```html
<template>
  <h-select
    v-model="value"
    mode="multiple"
    style="width: 100%"
    placeholder="select one country"
    option-label-prop="label"
  >
    <h-select-option value="china" label="China">
      <span role="img" arih-label="China">
        🇨🇳
      </span>
      China (中国)
    </h-select-option>
    <h-select-option value="usa" label="USA">
      <span role="img" arih-label="USA">
        🇺🇸
      </span>
      USA (美国)
    </h-select-option>
    <h-select-option value="japan" label="Japan">
      <span role="img" arih-label="Japan">
        🇯🇵
      </span>
      Japan (日本)
    </h-select-option>
    <h-select-option value="korea" label="Korea">
      <span role="img" arih-label="Korea">
        🇰🇷
      </span>
      Korea (韩国)
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  data() {
    return {
      value: ['china'],
    };
  },
  watch: {
    value(val) {
      console.log(`selected:`, val);
    },
  },
};
</script>
```

##### 三种大小
三种大小的选择框，当 size 分别为 `large` 和 `small` 时，输入框高度为 `40px` 和 `24px` ，默认高度为 `32px`。

```html
<template>
  <div>
    <h-radio-group v-model="size">
      <h-radio-button value="large">
        Large
      </h-radio-button>
      <h-radio-button value="default">
        Default
      </h-radio-button>
      <h-radio-button value="small">
        Small
      </h-radio-button>
    </h-radio-group>
    <br /><br />
    <h-select :size="size" default-value="a1" style="width: 200px" @change="handleChange">
      <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
        {{ (i + 9).toString(36) + i }}
      </h-select-option>
    </h-select>
    <br />
    <h-select
      mode="multiple"
      :size="size"
      placeholder="Please select"
      :default-value="['a1', 'b2']"
      style="width: 200px"
      @change="handleChange"
      @popupScroll="popupScroll"
    >
      <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
        {{ (i + 9).toString(36) + i }}
      </h-select-option>
    </h-select>
    <br />
    <h-select
      mode="tags"
      :size="size"
      placeholder="Please select"
      :default-value="['a1', 'b2']"
      style="width: 200px"
      @change="handleChange"
    >
      <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
        {{ (i + 9).toString(36) + i }}
      </h-select-option>
    </h-select>
  </div>
</template>
<script>
export default {
  data() {
    return {
      size: 'default',
    };
  },
  methods: {
    handleChange(value) {
      console.log(`Selected: ${value}`);
    },
    popupScroll() {
      console.log('popupScroll');
    },
  },
};
</script>
```

##### 自动分词 
试下复制 `露西,杰克` 到输入框里。只在 tags 和 multiple 模式下可用。

```html
<template>
  <h-select mode="tags" style="width: 100%" :token-separators="[',']" @change="handleChange">
    <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
      {{ (i + 9).toString(36) + i }}
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 多选
多选，从已有条目中选择（scroll the menu）

```html
<template>
  <h-select
    mode="multiple"
    :default-value="['a1', 'b2']"
    style="width: 100%"
    placeholder="Please select"
    @change="handleChange"
  >
    <h-select-option v-for="i in 25" :key="(i + 9).toString(36) + i">
      {{ (i + 9).toString(36) + i }}
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 分组 
用 `OptGroup` 进行选项分组。

```html
<template>
  <h-select default-value="lucy" style="width: 200px" @change="handleChange">
    <h-select-opt-group>
      <span slot="label"><h-icon type="user" />Manager</span>
      <h-select-option value="jack">
        Jack
      </h-select-option>
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
    </h-select-opt-group>
    <h-select-opt-group label="Engineer">
      <h-select-option value="Yiminghe">
        yiminghe
      </h-select-option>
    </h-select-opt-group>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 带搜索框 
展开后可对选项进行搜索。

```html
<template>
  <h-select
    show-search
    placeholder="Select a person"
    option-filter-prop="children"
    style="width: 200px"
    :filter-option="filterOption"
    @focus="handleFocus"
    @blur="handleBlur"
    @change="handleChange"
  >
    <h-select-option value="jack">
      Jack
    </h-select-option>
    <h-select-option value="lucy">
      Lucy
    </h-select-option>
    <h-select-option value="tom">
      Tom
    </h-select-option>
  </h-select>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
    handleBlur() {
      console.log('blur');
    },
    handleFocus() {
      console.log('focus');
    },
    filterOption(input, option) {
      return (
        option.componentOptions.children[0].text.toLowerCase().indexOf(input.toLowerCase()) >= 0
      );
    },
  },
};
</script>
```

##### 后缀图标
基本使用。

```html
<template>
  <div>
    <h-select default-value="lucy" style="width: 120px" @change="handleChange">
      <h-icon slot="suffixIcon" type="smile" />
      <h-select-option value="jack">
        Jack
      </h-select-option>
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
      <h-select-option value="disabled" disabled>
        Disabled
      </h-select-option>
      <h-select-option value="Yiminghe">
        yiminghe
      </h-select-option>
    </h-select>
    <h-select default-value="lucy" style="width: 120px" disabled>
      <h-icon slot="suffixIcon" type="meh" />
      <h-select-option value="lucy">
        Lucy
      </h-select-option>
    </h-select>
  </div>
</template>
<script>
export default {
  methods: {
    handleChange(value) {
      console.log(`selected ${value}`);
    },
  },
};
</script>
```

##### 扩展菜单
使用 `dropdownRender` 对下拉菜单进行自由扩展。

```html
<template>
  <h-select default-value="lucy" style="width: 120px">
    <div slot="dropdownRender" slot-scope="menu">
      <v-nodes :vnodes="menu" />
      <h-divider style="margin: 4px 0;" />
      <div
        style="padding: 4px 8px; cursor: pointer;"
        @mousedown="e => e.preventDefault()"
        @click="addItem"
      >
        <h-icon type="plus" /> Add item
      </div>
    </div>
    <h-select-option v-for="item in items" :key="item" :value="item">
      {{ item }}
    </h-select-option>
  </h-select>
</template>
<script>
let index = 0;
export default {
  components: {
    VNodes: {
      functional: true,
      render: (h, ctx) => ctx.props.vnodes,
    },
  },
  data: () => ({ items: ['jack', 'lucy'] }),
  methods: {
    addItem() {
      console.log('addItem');
      this.items.push(`New item ${index++}`);
    },
  },
};
</script>
```

### API 
```html
<h-select>
  <h-select-option value="lucy">lucy</h-select-option>
</h-select>
```

#### Select props 
| 参数                     | 说明                                                         | 类型                                            | 默认值                                   |
| :----------------------- | :----------------------------------------------------------- | :---------------------------------------------- | :--------------------------------------- |
| allowClear               | 支持清除                                                     | boolean                                         | false                                    |
| autoClearSearchValue     | 是否在选中项后清空搜索框，只在 `mode` 为 `multiple` 或 `tags` 时有效。 | boolean                                         | true                                     |
| autoFocus                | 默认获取焦点                                                 | boolean                                         | false                                    |
| defaultActiveFirstOption | 是否默认高亮第一个选项。                                     | boolean                                         | true                                     |
| defaultValue             | 指定默认选中的条目                                           | string\|string[]\|number\|number[]              | -                                        |
| disabled                 | 是否禁用                                                     | boolean                                         | false                                    |
| dropdownClassName        | 下拉菜单的 className 属性                                    | string                                          | -                                        |
| dropdownMatchSelectWidth | 下拉菜单和选择器同宽                                         | boolean                                         | true                                     |
| dropdownRender           | 自定义下拉框内容                                             | (menuNode: VNode, props) => VNode               | -                                        |
| dropdownStyle            | 下拉菜单的 style 属性                                        | object                                          | -                                        |
| dropdownMenuStyle        | dropdown 菜单自定义样式                                      | object                                          | -                                        |
| filterOption             | 是否根据输入项进行筛选。当其为一个函数时，会接收 `inputValue` `option` 两个参数，当 `option` 符合筛选条件时，应返回 `true`，反之则返回 `false`。 | boolean or function(inputValue, option)         | true                                     |
| firstActiveValue         | 默认高亮的选项                                               | string\|string[]                                | -                                        |
| getPopupContainer        | 菜单渲染父节点。默认渲染到 body 上，如果你遇到菜单滚动定位问题，试试修改为滚动的区域，并相对其定位。 | Function(triggerNode)                           | () => document.body                      |
| labelInValue             | 是否把每个选项的 label 包装到 value 中，会把 Select 的 value 类型从 `string` 变为 `{key: string, label: vNodes}` 的格式 | boolean                                         | false                                    |
| maxTagCount              | 最多显示多少个 tag                                           | number                                          | -                                        |
| maxTagPlaceholder        | 隐藏 tag 时显示的内容                                        | slot/function(omittedValues)                    | -                                        |
| maxTagTextLength         | 最大显示的 tag 文本长度                                      | number                                          | -                                        |
| mode                     | 设置 Select 的模式为多选或标签                               | 'default' \| 'multiple' \| 'tags' \| 'combobox' | -                                        |
| notFoundContent          | 当下拉列表为空时显示的内容                                   | string\|slot                                    | 'Not Found'                              |
| optionFilterProp         | 搜索时过滤对应的 option 属性，如设置为 children 表示对内嵌内容进行搜索 | string                                          | value                                    |
| optionLabelProp          | 回填到选择框的 Option 的属性值，默认是 Option 的子元素。比如在子元素需要高亮效果时，此值可以设为 `value`。 | string                                          | `children` （combobox 模式下为 `value`） |
| placeholder              | 选择框默认文字                                               | string\|slot                                    | -                                        |
| showSearch               | 使单选模式可搜索                                             | boolean                                         | false                                    |
| showArrow                | 是否显示下拉小箭头                                           | boolean                                         | true                                     |
| size                     | 选择框大小，可选 `large` `small`                             | string                                          | default                                  |
| suffixIcon               | 自定义的选择框后缀图标                                       | VNode \| slot                                   | -                                        |
| removeIcon               | 自定义的多选框清除图标                                       | VNode \| slot                                   | -                                        |
| clearIcon                | 自定义的多选框清空图标                                       | VNode \| slot                                   | -                                        |
| menuItemSelectedIcon     | 自定义当前选中的条目图标                                     | VNode \| slot                                   | -                                        |
| tokenSeparators          | 在 tags 和 multiple 模式下自动分词的分隔符                   | string[]                                        |                                          |
| value(v-model)           | 指定当前选中的条目                                           | string\|string[]\|number\|number[]              | -                                        |
| options                  | options 数据，如果设置则不需要手动构造 selectOption 节点     | array<{value, label, [disabled, key, title]}>   | []                                       |
| defaultOpen              | 是否默认展开下拉菜单                                         | boolean                                         | -                                        |
| open                     | 是否展开下拉菜单                                             | boolean                                         | -                                        |

> 注意，如果发现下拉菜单跟随页面滚动，或者需要在其他弹层中触发 Select，请尝试使用 `getPopupContainer={triggerNode => triggerNode.parentNode}` 将下拉弹层渲染节点固定在触发器的父元素中。

#### 事件 
| 事件名称              | 说明                                                         | 回调参数                                     |
| :-------------------- | :----------------------------------------------------------- | :------------------------------------------- |
| blur                  | 失去焦点的时回调                                             | function                                     |
| change                | 选中 option，或 input 的 value 变化（combobox 模式下）时，调用此函数 | function(value, option:Option/Array<Option>) |
| deselect              | 取消选中时调用，参数为选中项的 value (或 key) 值，仅在 multiple 或 tags 模式下生效 | function(value，option:Option)               |
| focus                 | 获得焦点时回调                                               | function                                     |
| inputKeydown          | 键盘按下时回调                                               | function                                     |
| mouseenter            | 鼠标移入时回调                                               | function                                     |
| mouseleave            | 鼠标移出时回调                                               | function                                     |
| popupScroll           | 下拉列表滚动时的回调                                         | function                                     |
| search                | 文本框值变化时回调                                           | function(value: string)                      |
| select                | 被选中时调用，参数为选中项的 value (或 key) 值               | function(value, option:Option)               |
| dropdownVisibleChange | 展开下拉菜单的回调                                           | function(open)                               |

#### Select Methods 
| 名称    | 说明     |
| :------ | :------- |
| blur()  | 取消焦点 |
| focus() | 获取焦点 |

#### Option props
| 参数     | 说明                                                         | 类型           | 默认值 |
| :------- | :----------------------------------------------------------- | :------------- | :----- |
| disabled | 是否禁用                                                     | boolean        | false  |
| key      | 和 value 含义一致。如果 Vue 需要你设置此项，此项值与 value 的值相同，然后可以省略 value 设置 | string         |        |
| title    | 选中该 Option 后，Select 的 title                            | string         | -      |
| value    | 默认根据此属性值进行筛选                                     | string\|number | -      |
| class    | Option 器类名                                                | string         | -      |

#### OptGroup props 
| 参数  | 说明 | 类型                        | 默认值 |
| :---- | :--- | :-------------------------- | :----- |
| key   |      | string                      | -      |
| label | 组名 | string\|\|function(h)\|slot | 无     |

## 滑动输入条
滑动型输入器，展示当前值和可选范围。

### 何时使用
当用户需要在数值区间/自定义区间内进行选择时，可为连续或离散值。

### 代码演示
##### 基本 
基本滑动条。当 `range` 为 `true` 时，渲染为双滑块。当 `disabled` 为 `true` 时，滑块处于不可用状态。

```html
<template>
  <div>
    <h-slider id="test" :default-value="30" :disabled="disabled" />
    <h-slider range :default-value="[20, 50]" :disabled="disabled" />
    Disabled: <h-switch size="small" :checked="disabled" @change="handleDisabledChange" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: false,
    };
  },
  methods: {
    handleDisabledChange(disabled) {
      this.disabled = disabled;
    },
  },
};
</script>
<style scoped>
.code-box-demo .ant-slider {
  margin-bottom: 16px;
}
</style>
```

##### 带 icon 的滑块 
滑块左右可以设置图标来表达业务含义。

```html
<template>
  <div class="icon-wrapper">
    <h-icon :style="{ color: preColor }" type="frown-o" />
    <h-slider :min="0" :max="20" :value="value" @change="handleChange" />
    <h-slider v-model="value" :min="0" :max="20" />
    <h-icon :style="{ color: nextColor }" type="smile-o" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: 0,
      min: 0,
      max: 20,
    };
  },
  computed: {
    preColor() {
      const { max, min, value } = this;
      const mid = ((max - min) / 2).toFixed(5);
      return value >= mid ? '' : 'rgba(0, 0, 0, .45)';
    },
    nextColor() {
      const { max, min, value } = this;
      const mid = ((max - min) / 2).toFixed(5);
      return value >= mid ? 'rgba(0, 0, 0, .45)' : '';
    },
  },
  methods: {
    handleChange(value) {
      this.value = value;
    },
  },
};
</script>
<style scoped>
.icon-wrapper {
  position: relative;
  padding: 0px 30px;
}

.icon-wrapper .anticon {
  position: absolute;
  top: -2px;
  width: 16px;
  height: 16px;
  line-height: 1;
  font-size: 16px;
  color: rgba(0, 0, 0, 0.25);
}

.icon-wrapper .anticon:first-child {
  left: 0;
}

.icon-wrapper .anticon:last-child {
  right: 0;
}
</style>
```

##### 事件
当 Slider 的值发生改变时，会触发 `onChange` 事件，并把改变后的值作为参数传入。在 `onmouseup` 时，会触发 `onAfterChange` 事件，并把当前值作为参数传入。

```html
<template>
  <div class="code-box-demo">
    <h-slider :default-value="30" @change="onChange" @afterChange="onAfterChange" />
    <h-slider
      range
      :step="10"
      :default-value="[20, 50]"
      @change="onChange"
      @afterChange="onAfterChange"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: false,
    };
  },
  methods: {
    onChange(value) {
      console.log('change: ', value);
    },
    onAfterChange(value) {
      console.log('afterChange: ', value);
    },
  },
};
</script>
<style scoped>
.code-box-demo .ant-slider {
  margin-bottom: 16px;
}
</style>
```

##### 垂直
垂直方向的 Slider。

```html
<template>
  <div style="height: 300px">
    <div style="display: inline-block;height: 300px;marginLeft: 70px">
      <h-slider vertical :default-value="30" />
    </div>
    <div style="display: inline-block;height: 300px;marginLeft: 70px">
      <h-slider vertical range :step="10" :default-value="[20, 50]" />
    </div>
    <div style="display: inline-block;height: 300px;marginLeft: 70px">
      <h-slider vertical range :marks="marks" :default-value="[26, 37]" />
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      marks: {
        0: '0°C',
        26: '26°C',
        37: '37°C',
        100: {
          style: {
            color: '#f50',
          },
          label: <strong>100°C</strong>,
        },
      },
    };
  },
  methods: {
    handleDisabledChange(disabled) {
      this.disabled = disabled;
    },
  },
};
</script>
<style scoped>
.code-box-demo .ant-slider {
  margin-bottom: 16px;
}
</style>
```

##### 反向 
设置 `reverse` 可以将滑动条置反。

```html
<template>
  <div>
    <h-slider :default-value="30" :reverse="reverse" />
    <h-slider range :default-value="[20, 50]" :reverse="reverse" />
    Reversed: <h-switch size="small" :checked="reverse" @change="handleReverseChange" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      reverse: true,
    };
  },
  methods: {
    handleReverseChange(reverse) {
      this.reverse = reverse;
    },
  },
};
</script>
```

##### 带输入框的滑块
和 [数字输入框](https://1x.antdv.com/components/input-number-cn/) 组件保持同步。

```html
<template>
  <div>
    <h-row>
      <h-col :span="12">
        <h-slider v-model="inputValue1" :min="1" :max="20" />
      </h-col>
      <h-col :span="4">
        <h-input-number v-model="inputValue1" :min="1" :max="20" style="marginLeft: 16px" />
      </h-col>
    </h-row>
    <h-row>
      <h-col :span="12">
        <h-slider v-model="inputValue" :min="0" :max="1" :step="0.01" />
      </h-col>
      <h-col :span="4">
        <h-input-number
          v-model="inputValue"
          :min="0"
          :max="1"
          :step="0.01"
          style="marginLeft: 16px"
        />
      </h-col>
    </h-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      inputValue: 0,
      inputValue1: 1,
    };
  },
};
</script>
<style scoped>
.code-box-demo .ant-slider {
  margin-bottom: 16px;
}
</style>
```

##### 自定义提示
使用 `tipFormatter` 可以格式化 `Tooltip` 的内容，设置 `tipFormatter={null}`，则隐藏 `Tooltip`。

```html
<template>
  <div>
    <h-slider :tip-formatter="formatter" />
    <h-slider :tip-formatter="null" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: false,
    };
  },
  methods: {
    formatter(value) {
      return `${value}%`;
    },
  },
};
</script>
```

##### 带标签的滑块 
使用 `marks` 属性标注分段式滑块，使用 `value` / `defaultValue` 指定滑块位置。当 `included=false` 时，表明不同标记间为并列关系。当 `step=null` 时，Slider 的可选值仅有 `marks` 标出来的部分。

```html
<template>
  <div id="components-slider-demo-mark">
    <h4>included=true</h4>
    <h-slider :marks="marks" :default-value="37" />
    <h-slider range :marks="marks" :default-value="[26, 37]" />

    <h4>included=false</h4>
    <h-slider :marks="marks" :included="false" :default-value="37" />

    <h4>marks & step</h4>
    <h-slider :marks="marks" :step="10" :default-value="37" />

    <h4>step=null</h4>
    <h-slider :marks="marks" :step="null" :default-value="37" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      marks: {
        0: '0°C',
        26: '26°C',
        37: '37°C',
        100: {
          style: {
            color: '#f50',
          },
          label: <strong>100°C</strong>,
        },
      },
    };
  },
  methods: {
    onChange(value) {
      console.log('change: ', value);
    },
    onAfterChange(value) {
      console.log('afterChange: ', value);
    },
  },
};
</script>
<style scoped>
#components-slider-demo-mark h4 {
  margin: 0 0 16px;
}
#components-slider-demo-mark .ant-slider-with-marks {
  margin-bottom: 44px;
}
</style>
```

##### 控制 ToolTip 的显示
当 `tooltipVisible` 为 `true` 时，将始终显示ToolTip；反之则始终不显示，即使在拖动、移入时也是如此。

```html
<template>
  <h-slider :default-value="30" :tooltip-visible="true" />
</template>
```

### API
| 参数                     | 说明                                                         | 类型             | 默认值                                                       | 版本  |
| :----------------------- | :----------------------------------------------------------- | :--------------- | :----------------------------------------------------------- | :---- |
| autoFocus                | 自动获取焦点                                                 | boolean          | false                                                        |       |
| defaultValue             | 设置初始取值。当 `range` 为 `false` 时，使用 `number`，否则用 `[number, number]` | number\|number[] | 0 or [0, 0]                                                  |       |
| disabled                 | 值为 `true` 时，滑块为禁用状态                               | boolean          | false                                                        |       |
| dots                     | 是否只能拖拽到刻度上                                         | boolean          | false                                                        |       |
| included                 | `marks` 不为空对象时有效，值为 true 时表示值为包含关系，false 表示并列 | boolean          | true                                                         |       |
| marks                    | 刻度标记，key 的类型必须为 `number` 且取值在闭区间 [min, max] 内，每个标签可以单独设置样式 | object           | { number: string\|VNode } or { number: { style: object, label: string\|VNode } } or { number: () => VNode } |       |
| max                      | 最大值                                                       | number           | 100                                                          |       |
| min                      | 最小值                                                       | number           | 0                                                            |       |
| range                    | 双滑块模式                                                   | boolean          | false                                                        |       |
| reverse                  | 反向坐标轴                                                   | boolean          | false                                                        | 1.5.0 |
| step                     | 步长，取值必须大于 0，并且可被 (max - min) 整除。当 `marks` 不为空对象时，可以设置 `step` 为 `null`，此时 Slider 的可选值仅有 marks 标出来的部分。 | number\|null     | 1                                                            |       |
| tipFormatter             | Slider 会把当前值传给 `tipFormatter`，并在 Tooltip 中显示 `tipFormatter` 的返回值，若为 null，则隐藏 Tooltip。 | Function\|null   | IDENTITY                                                     |       |
| value(v-model)           | 设置当前取值。当 `range` 为 `false` 时，使用 `number`，否则用 `[number, number]` | number\|number[] |                                                              |       |
| vertical                 | 值为 `true` 时，Slider 为垂直方向                            | Boolean          | false                                                        |       |
| tooltipPlacement         | 设置 Tooltip 展示位置。参考 [`Tooltip`](https://1x.antdv.com/components/tooltip/)。 | string           |                                                              | 1.5.0 |
| tooltipVisible           | 值为`true`时，Tooltip 将会始终显示；否则始终不显示，哪怕在拖拽及移入时。 | Boolean          |                                                              |       |
| getTooltipPopupContainer | Tooltip 渲染父节点，默认渲染到 body 上。                     | Function         | () => document.body                                          | 1.5.0 |

#### 事件
| 事件名称    | 说明                                                         | 回调参数        |
| :---------- | :----------------------------------------------------------- | :-------------- |
| afterChange | 与 `mouseup` 触发时机一致，把当前值作为参数传入。            | Function(value) |
| change      | 当 Slider 的值发生改变时，会触发 change 事件，并把改变后的值作为参数传入。 | Function(value) |

### 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 开关
开关选择器。

### 何时使用
- 需要表示开关状态/两种状态之间的切换时；
- 和 `checkbox`的区别是，切换 `switch` 会直接触发状态改变，而 `checkbox` 一般用于状态标记，需要和提交操作配合。

### 代码演示
##### 基本用法
最简单的用法。

```html
<template>
  <div>
    <h-switch default-checked @change="onChange" />
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    onChange(checked) {
      console.log(`h-switch to ${checked}`);
    },
  },
};
</script>
```

##### 文字和图标
带有文字和图标。

```html
<template>
  <div>
    <h-switch checked-children="开" un-checked-children="关" default-checked />
    <br />
    <h-switch checked-children="1" un-checked-children="0" />
    <br />
    <h-switch default-checked>
      <h-icon slot="checkedChildren" type="check" />
      <h-icon slot="unCheckedChildren" type="close" />
    </h-switch>
  </div>
</template>
```

##### 加载中 
标识开关操作仍在执行中。

```html
<template>
  <div>
    <h-switch loading default-checked />
    <br />
    <h-switch size="small" loading />
  </div>
</template>
```

##### 不可用
Switch 失效状态。

```html
<template>
  <div>
    <h-switch default-checked :disabled="disabled" style="margin-bottom:5px" />
    <br />
    <h-button type="primary" @click="onToggle">
      Toggle disabled
    </h-button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      disabled: true,
    };
  },
  methods: {
    onToggle() {
      this.disabled = !this.disabled;
    },
  },
};
</script>
```

##### 两种大小
`size="small"` 表示小号开关。

```html
<template>
  <div>
    <h-switch default-checked />
    <br />
    <h-switch size="small" default-checked />
  </div>
</template>
```

### API 
| 参数              | 说明                                | 类型         | 默认值  |
| :---------------- | :---------------------------------- | :----------- | :------ |
| autoFocus         | 组件自动获取焦点                    | boolean      | false   |
| checked(v-model)  | 指定当前是否选中                    | boolean      | false   |
| checkedChildren   | 选中时的内容                        | string\|slot |         |
| defaultChecked    | 初始是否选中                        | boolean      | false   |
| disabled          | 是否禁用                            | boolean      | false   |
| loading           | 加载中的开关                        | boolean      | false   |
| size              | 开关大小，可选值：`default` `small` | string       | default |
| unCheckedChildren | 非选中时的内容                      | string\|slot |         |

#### 事件
| 事件名称 | 说明           | 回调参数                                 |
| :------- | :------------- | :--------------------------------------- |
| change   | 变化时回调函数 | Function(checked:Boolean, event: Event)  |
| click    | 点击时回调函数 | Function(checked: boolean, event: Event) |

### 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 时间选择框
输入或选择时间的控件。

### 何时使用
当用户需要输入一个时间，可以点击标准输入框，弹出时间面板进行选择。

### 代码演示
##### 12 小时制 
12 小时制的时间选择器，默认的 format 为 `h:mm:ss a`。

```html
<template>
  <div>
    <h-time-picker use12-hours @change="onChange" />
    <h-time-picker use12-hours format="h:mm:ss A" @change="onChange" />
    <h-time-picker use12-hours format="h:mm a" @change="onChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onChange(time, timeString) {
      console.log(time, timeString);
    },
  },
};
</script>
```

##### 基本 
点击 TimePicker，然后可以在浮层中选择或者输入某一时间。

```html
<template>
  <h-time-picker :default-open-value="moment('00:00:00', 'HH:mm:ss')" @change="onChange" />
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
    onChange(time, timeString) {
      console.log(time, timeString);
    },
  },
};
</script>
```

##### 选择时分 
TimePicker 浮层中的列会随着 `format` 变化，当略去 `format` 中的某部分时，浮层中对应的列也会消失。

```html
<template>
  <h-time-picker :default-value="moment('12:08', 'HH:mm')" format="HH:mm" />
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
  },
};
</script>
```

##### 三种大小
三种大小的输入框，大的用在表单中，中的为默认。

```html
<template>
  <div>
    <h-time-picker :default-value="moment('12:08:23', 'HH:mm:ss')" size="large" />
    <h-time-picker :default-value="moment('12:08:23', 'HH:mm:ss')" />
    <h-time-picker :default-value="moment('12:08:23', 'HH:mm:ss')" size="small" />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
  },
};
</script>
```

##### 后缀图标 
点击 TimePicker，然后可以在浮层中选择或者输入某一时间。

```html
<template>
  <h-time-picker :default-open-value="moment('00:00:00', 'HH:mm:ss')" @change="onChange">
    <h-icon slot="suffixIcon" type="smile" />
  </h-time-picker>
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
    onChange(time, timeString) {
      console.log(time, timeString);
    },
  },
};
</script>
```

##### 附加内容
在 TimePicker 选择框底部显示自定义的内容。

```html
<template>
  <div>
    <h-time-picker :open="open" @openChange="handleOpenChange">
      <h-button slot="addon" slot-scope="panel" size="small" type="primary" @click="handleClose">
        Ok {{ panel.prefixCls }}
      </h-button>
    </h-time-picker>
    <h-time-picker :open.sync="open2">
      <h-button slot="addon" size="small" type="primary" @click="handleClose">
        Ok
      </h-button>
    </h-time-picker>
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      open: false,
      open2: false,
    };
  },
  methods: {
    handleOpenChange(open) {
      console.log('open', open);
      this.open = open;
    },
    handleClose() {
      this.open = false;
      this.open2 = false;
    },
  },
};
</script>
```

##### 禁用 
禁用时间选择。

```html
<template>
  <h-time-picker :default-value="moment('12:08:23', 'HH:mm:ss')" disabled />
</template>
<script>
import moment from 'moment';
export default {
  methods: {
    moment,
  },
};
</script>
```

##### 步长选项 
可以使用 `hourStep` `minuteStep` `secondStep` 按步长展示可选的时分秒。

```html
<template>
  <h-time-picker :minute-step="15" :second-step="10" />
</template>
```

##### 受控组件
value 和 onChange 需要配合使用。也可以直接使用v-model。

```html
<template>
  <div>
    <p>use value and @change</p>
    <h-time-picker :value="value" @change="onChange" />
    <br />
    <br />
    <p>v-model</p>
    <h-time-picker v-model="value" />
    <br />
    <br />
    <p>Do not change</p>
    <h-time-picker :value="value2" />
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      value: null,
      value2: moment(),
    };
  },
  methods: {
    onChange(time) {
      console.log(time);
      this.value = time;
    },
  },
};
</script>
```

### API 
| 参数                | 说明                                                         | 类型                                                         | 默认值       | 版本  |
| :------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------- | :---- |
| addon               | 选择框底部显示自定义的内容                                   | slot \| slot-scope                                           | 无           |       |
| allowClear          | 是否展示清除按钮                                             | boolean                                                      | true         |       |
| autoFocus           | 自动获取焦点                                                 | boolean                                                      | false        |       |
| clearText           | 清除按钮的提示文案                                           | string                                                       | clear        |       |
| defaultOpenValue    | 当 defaultValue/value 不存在时，可以设置面板打开时默认选中的值 | [moment](http://momentjs.com/)                               | moment()     |       |
| defaultValue        | 默认时间                                                     | [moment](http://momentjs.com/)                               | 无           |       |
| disabled            | 禁用全部操作                                                 | boolean                                                      | false        |       |
| disabledHours       | 禁止选择部分小时选项                                         | function()                                                   | 无           |       |
| disabledMinutes     | 禁止选择部分分钟选项                                         | function(selectedHour)                                       | 无           |       |
| disabledSeconds     | 禁止选择部分秒选项                                           | function(selectedHour, selectedMinute)                       | 无           |       |
| format              | 展示的时间格式                                               | string                                                       | "HH:mm:ss"   |       |
| getPopupContainer   | 定义浮层的容器，默认为 body 上新建 div                       | function(trigger)                                            | 无           |       |
| hideDisabledOptions | 隐藏禁止选择的选项                                           | boolean                                                      | false        |       |
| hourStep            | 小时选项间隔                                                 | number                                                       | 1            |       |
| inputReadOnly       | 设置输入框为只读（避免在移动设备上打开虚拟键盘）             | boolean                                                      | false        |       |
| minuteStep          | 分钟选项间隔                                                 | number                                                       | 1            |       |
| open(.sync)         | 面板是否打开                                                 | boolean                                                      | false        |       |
| placeholder         | 没有值的时候显示的内容                                       | string                                                       | "请选择时间" |       |
| popupClassName      | 弹出层类名                                                   | string                                                       | ''           |       |
| popupStyle          | 弹出层样式对象                                               | object                                                       | -            |       |
| secondStep          | 秒选项间隔                                                   | number                                                       | 1            |       |
| suffixIcon          | 自定义的选择框后缀图标                                       | string \| VNode \| slot                                      | -            |       |
| clearIcon           | 自定义的清除图标                                             | string \| VNode \| slot                                      | -            | 1.5.0 |
| use12Hours          | 使用 12 小时制，为 true 时 `format` 默认为 `h:mm:ss a`       | boolean                                                      | false        |       |
| value(v-model)      | 当前时间                                                     | [moment](http://momentjs.com/)                               | 无           |       |
| align               | 该值将合并到 placement 的配置中，设置参考 [dom-align](https://github.com/yiminghe/dom-align) | Object                                                       | 无           | 1.5.4 |
| valueFormat         | 可选，绑定值的格式，对 value、defaultValue 起作用。不指定则绑定值为 moment 对象 | string，[具体格式](https://momentjs.com/docs/#/displaying/format/) | -            | 1.5.4 |

#### 事件
| 事件名称   | 说明                  | 回调参数                                                   |
| :--------- | :-------------------- | :--------------------------------------------------------- |
| change     | 时间发生变化的回调    | function(time: moment \| string, timeString: string): void |
| openChange | 面板打开/关闭时的回调 | (open: boolean): void                                      |

### 方法
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

## 穿梭框
双栏穿梭选择框。

### 何时使用
- 需要在多个可选项中进行多选时。
- 比起 Select 和 TreeSelect，穿梭框占据更大的空间，可以展示可选项的更多信息。

穿梭选择框用直观的方式在两栏中移动元素，完成选择行为。

选择一个或以上的选项后，点击对应的方向键，可以把选中的选项移动到另一栏。
其中，左边一栏为 `source`，右边一栏为 `target`，API 的设计也反映了这两个概念。

### 代码演示
##### 基本用法 
最基本的用法，展示了 `dataSource`、`targetKeys`、每行的渲染函数 `render` 以及回调函数 `change` `selectChange` `scroll` 的用法。

```html
<template>
  <div>
    <h-transfer
      :dath-source="mockData"
      :titles="['Source', 'Target']"
      :target-keys="targetKeys"
      :selected-keys="selectedKeys"
      :render="item => item.title"
      :disabled="disabled"
      @change="handleChange"
      @selectChange="handleSelectChange"
      @scroll="handleScroll"
    />
    <h-switch
      un-checked-children="enabled"
      checked-children="disabled"
      :checked="disabled"
      style="margin-top: 16px"
      @change="handleDisable"
    />
  </div>
</template>
<script>
export default {
  data() {
    const mockData = [];
    for (let i = 0; i < 20; i++) {
      mockData.push({
        key: i.toString(),
        title: `content${i + 1}`,
        description: `description of content${i + 1}`,
        disabled: i % 3 < 1,
      });
    }

    const oriTargetKeys = mockData.filter(item => +item.key % 3 > 1).map(item => item.key);
    return {
      mockData,
      targetKeys: oriTargetKeys,
      selectedKeys: ['1', '4'],
      disabled: false,
    };
  },
  methods: {
    handleChange(nextTargetKeys, direction, moveKeys) {
      this.targetKeys = nextTargetKeys;

      console.log('targetKeys: ', nextTargetKeys);
      console.log('direction: ', direction);
      console.log('moveKeys: ', moveKeys);
    },
    handleSelectChange(sourceSelectedKeys, targetSelectedKeys) {
      this.selectedKeys = [...sourceSelectedKeys, ...targetSelectedKeys];

      console.log('sourceSelectedKeys: ', sourceSelectedKeys);
      console.log('targetSelectedKeys: ', targetSelectedKeys);
    },
    handleScroll(direction, e) {
      console.log('direction:', direction);
      console.log('target:', e.target);
    },
    handleDisable(disabled) {
      this.disabled = disabled;
    },
  },
};
</script>
```

##### 带搜索框 
带搜索框的穿梭框，可以自定义搜索函数。

```html
<template>
  <h-transfer
    :dath-source="mockData"
    show-search
    :filter-option="filterOption"
    :target-keys="targetKeys"
    :render="item => item.title"
    @change="handleChange"
    @search="handleSearch"
  />
</template>
<script>
export default {
  data() {
    return {
      mockData: [],
      targetKeys: [],
    };
  },
  mounted() {
    this.getMock();
  },
  methods: {
    getMock() {
      const targetKeys = [];
      const mockData = [];
      for (let i = 0; i < 20; i++) {
        const data = {
          key: i.toString(),
          title: `content${i + 1}`,
          description: `description of content${i + 1}`,
          chosen: Math.random() * 2 > 1,
        };
        if (data.chosen) {
          targetKeys.push(data.key);
        }
        mockData.push(data);
      }
      this.mockData = mockData;
      this.targetKeys = targetKeys;
    },
    filterOption(inputValue, option) {
      return option.description.indexOf(inputValue) > -1;
    },
    handleChange(targetKeys, direction, moveKeys) {
      console.log(targetKeys, direction, moveKeys);
      this.targetKeys = targetKeys;
    },
    handleSearch(dir, value) {
      console.log('search:', dir, value);
    },
  },
};
</script>
```

##### 高级用法 
穿梭框高级用法，可配置操作文案，可定制宽高，可对底部进行自定义渲染。

```html
<template>
  <h-transfer
    :dath-source="mockData"
    show-search
    :list-style="{
      width: '250px',
      height: '300px',
    }"
    :operations="['to right', 'to left']"
    :target-keys="targetKeys"
    :render="item => `${item.title}-${item.description}`"
    @change="handleChange"
  >
    <h-button
      slot="footer"
      slot-scope="props"
      size="small"
      style="float:right;margin: 5px"
      @click="getMock"
    >
      reload
    </h-button>
    <span slot="notFoundContent">
      没数据
    </span>
  </h-transfer>
</template>
<script>
export default {
  data() {
    return {
      mockData: [],
      targetKeys: [],
    };
  },
  mounted() {
    this.getMock();
  },
  methods: {
    getMock() {
      const targetKeys = [];
      const mockData = [];
      for (let i = 0; i < 20; i++) {
        const data = {
          key: i.toString(),
          title: `content${i + 1}`,
          description: `description of content${i + 1}`,
          chosen: Math.random() * 2 > 1,
        };
        if (data.chosen) {
          targetKeys.push(data.key);
        }
        mockData.push(data);
      }
      this.mockData = mockData;
      this.targetKeys = targetKeys;
    },
    handleChange(targetKeys, direction, moveKeys) {
      console.log(targetKeys, direction, moveKeys);
      this.targetKeys = targetKeys;
    },
  },
};
</script>
```

##### 自定义渲染行数据
自定义渲染每一个 Transfer Item，可用于渲染复杂数据。

```html
<template>
  <h-transfer
    :dath-source="mockData"
    :list-style="{
      width: '300px',
      height: '300px',
    }"
    :target-keys="targetKeys"
    :render="renderItem"
    @change="handleChange"
  />
</template>
<script>
export default {
  data() {
    return {
      mockData: [],
      targetKeys: [],
    };
  },
  mounted() {
    this.getMock();
  },
  methods: {
    getMock() {
      const targetKeys = [];
      const mockData = [];
      for (let i = 0; i < 20; i++) {
        const data = {
          key: i.toString(),
          title: `content${i + 1}`,
          description: `description of content${i + 1}`,
          chosen: Math.random() * 2 > 1,
        };
        if (data.chosen) {
          targetKeys.push(data.key);
        }
        mockData.push(data);
      }
      this.mockData = mockData;
      this.targetKeys = targetKeys;
    },
    renderItem(item) {
      const customLabel = (
        <span class="custom-item">
          {item.title} - {item.description}
        </span>
      );

      return {
        label: customLabel, // for displayed item
        value: item.title, // for title and filter matching
      };
    },
    handleChange(targetKeys, direction, moveKeys) {
      console.log(targetKeys, direction, moveKeys);
      this.targetKeys = targetKeys;
    },
  },
};
</script>
```

##### 表格穿梭框 
使用 Table 组件作为自定义渲染列表。

```html
<template>
  <div>
    <h-transfer
      :dath-source="mockData"
      :target-keys="targetKeys"
      :disabled="disabled"
      :show-search="showSearch"
      :filter-option="(inputValue, item) => item.title.indexOf(inputValue) !== -1"
      :show-select-all="false"
      @change="onChange"
    >
      <template
        slot="children"
        slot-scope="{
          props: { direction, filteredItems, selectedKeys, disabled: listDisabled },
          on: { itemSelectAll, itemSelect },
        }"
      >
        <h-table
          :row-selection="
            getRowSelection({ disabled: listDisabled, selectedKeys, itemSelectAll, itemSelect })
          "
          :columns="direction === 'left' ? leftColumns : rightColumns"
          :dath-source="filteredItems"
          size="small"
          :style="{ pointerEvents: listDisabled ? 'none' : null }"
          :custom-row="
            ({ key, disabled: itemDisabled }) => ({
              on: {
                click: () => {
                  if (itemDisabled || listDisabled) return;
                  itemSelect(key, !selectedKeys.includes(key));
                },
              },
            })
          "
        />
      </template>
    </h-transfer>
    <h-switch
      un-checked-children="disabled"
      checked-children="disabled"
      :checked="disabled"
      style="margin-top: 16px"
      @change="triggerDisable"
    />
    <h-switch
      un-checked-children="showSearch"
      checked-children="showSearch"
      :checked="showSearch"
      style="margin-top: 16px"
      @change="triggerShowSearch"
    />
  </div>
</template>
<script>
import difference from 'lodash/difference';
const mockData = [];
for (let i = 0; i < 20; i++) {
  mockData.push({
    key: i.toString(),
    title: `content${i + 1}`,
    description: `description of content${i + 1}`,
    disabled: i % 4 === 0,
  });
}

const originTargetKeys = mockData.filter(item => +item.key % 3 > 1).map(item => item.key);

const leftTableColumns = [
  {
    dataIndex: 'title',
    title: 'Name',
  },
  {
    dataIndex: 'description',
    title: 'Description',
  },
];
const rightTableColumns = [
  {
    dataIndex: 'title',
    title: 'Name',
  },
];

export default {
  data() {
    return {
      mockData,
      targetKeys: originTargetKeys,
      disabled: false,
      showSearch: false,
      leftColumns: leftTableColumns,
      rightColumns: rightTableColumns,
    };
  },
  methods: {
    onChange(nextTargetKeys) {
      this.targetKeys = nextTargetKeys;
    },

    triggerDisable(disabled) {
      this.disabled = disabled;
    },

    triggerShowSearch(showSearch) {
      this.showSearch = showSearch;
    },
    getRowSelection({ disabled, selectedKeys, itemSelectAll, itemSelect }) {
      return {
        getCheckboxProps: item => ({ props: { disabled: disabled || item.disabled } }),
        onSelectAll(selected, selectedRows) {
          const treeSelectedKeys = selectedRows
            .filter(item => !item.disabled)
            .map(({ key }) => key);
          const diffKeys = selected
            ? difference(treeSelectedKeys, selectedKeys)
            : difference(selectedKeys, treeSelectedKeys);
          itemSelectAll(diffKeys, selected);
        },
        onSelect({ key }, selected) {
          itemSelect(key, selected);
        },
        selectedRowKeys: selectedKeys,
      };
    },
  },
};
</script>
```

##### 树穿梭框 
使用 Tree 组件作为自定义渲染列表。

```html
<template>
  <div>
    <h-transfer
      class="tree-transfer"
      :dath-source="dataSource"
      :target-keys="targetKeys"
      :render="item => item.title"
      :show-select-all="false"
      @change="onChange"
    >
      <template
        slot="children"
        slot-scope="{ props: { direction, selectedKeys }, on: { itemSelect } }"
      >
        <h-tree
          v-if="direction === 'left'"
          blockNode
          checkable
          checkStrictly
          defaultExpandAll
          :checkedKeys="[...selectedKeys, ...targetKeys]"
          :treeData="treeData"
          @check="
            (_, props) => {
              onChecked(_, props, [...selectedKeys, ...targetKeys], itemSelect);
            }
          "
          @select="
            (_, props) => {
              onChecked(_, props, [...selectedKeys, ...targetKeys], itemSelect);
            }
          "
        />
      </template>
    </h-transfer>
  </div>
</template>
<script>
const treeData = [
  { key: '0-0', title: '0-0' },
  {
    key: '0-1',
    title: '0-1',
    children: [
      { key: '0-1-0', title: '0-1-0' },
      { key: '0-1-1', title: '0-1-1' },
    ],
  },
  { key: '0-2', title: '0-3' },
];

const transferDataSource = [];
function flatten(list = []) {
  list.forEach(item => {
    transferDataSource.push(item);
    flatten(item.children);
  });
}
flatten(JSON.parse(JSON.stringify(treeData)));

function isChecked(selectedKeys, eventKey) {
  return selectedKeys.indexOf(eventKey) !== -1;
}

function handleTreeData(data, targetKeys = []) {
  data.forEach(item => {
    item['disabled'] = targetKeys.includes(item.key);
    if (item.children) {
      handleTreeData(item.children, targetKeys);
    }
  });
  return data;
}

export default {
  data() {
    return {
      targetKeys: [],
      dataSource: transferDataSource,
    };
  },
  computed: {
    treeData() {
      return handleTreeData(treeData, this.targetKeys);
    },
  },
  methods: {
    onChange(targetKeys) {
      console.log('Target Keys:', targetKeys);
      this.targetKeys = targetKeys;
    },
    onChecked(_, e, checkedKeys, itemSelect) {
      const { eventKey } = e.node;
      itemSelect(eventKey, !isChecked(checkedKeys, eventKey));
    },
  },
};
</script>
<style scoped>
.tree-transfer .ant-transfer-list:first-child {
  width: 50%;
  flex: none;
}
</style>
```

### API 
| 参数          | 说明                                                         | 类型                                                         | 默认值                                                       | 版本  |
| :------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---- |
| dataSource    | 数据源，其中的数据将会被渲染到左边一栏中，`targetKeys` 中指定的除外。 | [{key: string.isRequired,title: string.isRequired,description: string,disabled: bool}][] | []                                                           |       |
| disabled      | 是否禁用                                                     | boolean                                                      | false                                                        |       |
| filterOption  | 接收 `inputValue` `option` 两个参数，当 `option` 符合筛选条件时，应返回 `true`，反之则返回 `false`。 | (inputValue, option): boolean                                |                                                              |       |
| footer        | 可以设置为一个 作用域插槽                                    | slot="footer" slot-scope="props"                             |                                                              |       |
| lazy          | Transfer 使用了 [vc-lazy-load]优化性能，这里可以设置相关参数。设为 `false` 可以关闭懒加载。 | object\|boolean                                              | `{ height: 32, offset: 32 }`                                 |       |
| listStyle     | 两个穿梭框的自定义样式                                       | object                                                       |                                                              |       |
| locale        | 各种语言                                                     | object                                                       | `{ itemUnit: '项', itemsUnit: '项', notFoundContent: '列表为空', searchPlaceholder: '请输入搜索内容' }` |       |
| operations    | 操作文案集合，顺序从上至下                                   | string[]                                                     | ['>', '<']                                                   |       |
| render        | 每行数据渲染函数，该函数的入参为 `dataSource` 中的项，返回值为 element。或者返回一个普通对象，其中 `label` 字段为 element，`value` 字段为 title | Function(record)                                             |                                                              |       |
| selectedKeys  | 设置哪些项应该被选中                                         | string[]                                                     | []                                                           |       |
| showSearch    | 是否显示搜索框                                               | boolean                                                      | false                                                        |       |
| showSelectAll | 是否展示全选勾选框                                           | boolean                                                      | true                                                         | 1.5.0 |
| targetKeys    | 显示在右侧框数据的 key 集合                                  | string[]                                                     | []                                                           |       |
| titles        | 标题集合，顺序从左至右                                       | string[]                                                     | ['', '']                                                     |       |

#### 事件
| 事件名称     | 说明                           | 回调参数                                          |
| :----------- | :----------------------------- | :------------------------------------------------ |
| change       | 选项在两栏之间转移时的回调函数 | (targetKeys, direction, moveKeys): void           |
| scroll       | 选项列表滚动时的回调函数       | (direction, event): void                          |
| search       | 搜索框内容时改变时的回调函数   | (direction: 'left'\|'right', value: string): void |
| selectChange | 选中项发生改变时的回调函数     | (sourceSelectedKeys, targetSelectedKeys): void    |

#### Render Props
1.5.0 新增。Transfer 支持接收 `children` 自定义渲染列表，并返回以下参数：

```json
{
  "props": {
    "direction": String,
    "disabled": Boolean,
    "filteredItems": Array,
    "selectedKeys": Array
  },
  "on": {
    "itemSelect": Function,
    "itemSelectAll": Function
  }
}
```

| 参数          | 说明           | 类型                                | 版本  |
| :------------ | :------------- | :---------------------------------- | :---- |
| direction     | 渲染列表的方向 | 'left' \| 'right'                   | 1.5.0 |
| disabled      | 是否禁用列表   | boolean                             | 1.5.0 |
| filteredItems | 过滤后的数据   | TransferItem[]                      | 1.5.0 |
| selectedKeys  | 选中的条目     | string[]                            | 1.5.0 |
| itemSelect    | 勾选条目       | (key: string, selected: boolean)    | 1.5.0 |
| itemSelectAll | 勾选一组条目   | (keys: string[], selected: boolean) | 1.5.0 |

##### 参考示例 
```html
<h-transfer>
  <template
    slot="children"
    slot-scope="{
      props: {
        direction,
        filteredItems,
        selectedKeys,
        disabled: listDisabled
      }, on: {
        itemSelectAll,
        itemSelect,
      }
    }"
  >
    <your-component />
  <template>
</h-transfer>
```

### 注意 
按照 Vue 最新的规范，所有的组件数组最好绑定 key。在 Transfer 中，`dataSource`里的数据值需要指定 `key` 值。对于 `dataSource` 默认将每列数据的 `key` 属性作为唯一的标识。

如果你的数据没有这个属性，务必使用 `rowKey` 来指定数据列的主键。

```jsx
// 比如你的数据主键是 uid
return <Transfer :rowKey="record => record.uid" />;
```

## 树型选择控件
### 何时使用
类似 Select 的选择控件，可选择的数据结构是一个树形结构时，可以使用 TreeSelect，例如公司层级、学科系统、分类目录等等。

### 代码演示
##### 基本用法
最简单的用法。

```html
<template>
  <h-tree-select
    v-model="value"
    show-search
    style="width: 100%"
    :dropdown-style="{ maxHeight: '400px', overflow: 'auto' }"
    placeholder="Please select"
    allow-clear
    tree-default-expand-all
  >
    <h-tree-select-node key="0-1" value="parent 1" title="parent 1">
      <h-tree-select-node key="0-1-1" value="parent 1-0" title="parent 1-0">
        <h-tree-select-node key="random" :selectable="false" value="leaf1" title="my leaf" />
        <h-tree-select-node key="random1" value="leaf2" title="your leaf" />
      </h-tree-select-node>
      <h-tree-select-node key="random2" value="parent 1-1" title="parent 1-1">
        <h-tree-select-node key="random3" value="sss">
          <b slot="title" style="color: #08c">sss</b>
        </h-tree-select-node>
      </h-tree-select-node>
    </h-tree-select-node>
  </h-tree-select>
</template>

<script>
export default {
  data() {
    return {
      treeExpandedKeys: [],
      value: undefined,
    };
  },
};
</script>
```

##### 多选
多选的树选择。

```html
<template>
  <h-tree-select
    show-search
    style="width: 100%"
    :value="value"
    :dropdown-style="{ maxHeight: '400px', overflow: 'auto' }"
    placeholder="Please select"
    allow-clear
    multiple
    tree-default-expand-all
    @change="onChange"
    @search="onSearch"
    @select="onSelect"
  >
    <h-tree-select-node key="0-1" value="parent 1" title="parent 1">
      <h-tree-select-node key="0-1-1" value="parent 1-0" title="parent 1-0">
        <h-tree-select-node key="random" value="leaf1" title="my leaf" />
        <h-tree-select-node key="random1" value="leaf2" title="your leaf" />
      </h-tree-select-node>
      <h-tree-select-node key="random2" value="parent 1-1" title="parent 1-1">
        <h-tree-select-node key="random3" value="sss">
          <b slot="title" style="color: #08c">sss</b>
        </h-tree-select-node>
      </h-tree-select-node>
    </h-tree-select-node>
  </h-tree-select>
</template>

<script>
export default {
  data() {
    return {
      value: undefined,
    };
  },
  methods: {
    onChange(value) {
      console.log(value);
      this.value = value;
    },
    onSearch() {
      console.log(...arguments);
    },
    onSelect() {
      console.log(...arguments);
    },
  },
};
</script>
```

##### 后缀图标
最简单的用法。

```html
<template>
  <h-tree-select
    v-model="value"
    show-search
    style="width: 100%"
    :dropdown-style="{ maxHeight: '400px', overflow: 'auto' }"
    placeholder="Please select"
    allow-clear
    tree-default-expand-all
  >
    <h-icon slot="suffixIcon" type="smile" />
    <h-tree-select-node key="0-1" value="parent 1" title="parent 1">
      <h-tree-select-node key="0-1-1" value="parent 1-0" title="parent 1-0">
        <h-tree-select-node key="random" value="leaf1" title="my leaf" />
        <h-tree-select-node key="random1" value="leaf2" title="your leaf" />
      </h-tree-select-node>
      <h-tree-select-node key="random2" value="parent 1-1" title="parent 1-1">
        <h-tree-select-node key="random3" value="sss">
          <b slot="title" style="color: #08c">sss</b>
        </h-tree-select-node>
      </h-tree-select-node>
    </h-tree-select-node>
  </h-tree-select>
</template>

<script>
export default {
  data() {
    return {
      value: undefined,
    };
  },
};
</script>
```

##### 可勾选 
使用勾选框实现多选功能。

```html
<template>
  <h-tree-select
    v-model="value"
    style="width: 100%"
    :tree-data="treeData"
    tree-checkable
    :show-checked-strategy="SHOW_PARENT"
    search-placeholder="Please select"
  />
</template>

<script>
import { TreeSelect } from 'ant-design-vue';
const SHOW_PARENT = TreeSelect.SHOW_PARENT;

const treeData = [
  {
    title: 'Node1',
    value: '0-0',
    key: '0-0',
    children: [
      {
        title: 'Child Node1',
        value: '0-0-0',
        key: '0-0-0',
      },
    ],
  },
  {
    title: 'Node2',
    value: '0-1',
    key: '0-1',
    children: [
      {
        title: 'Child Node3',
        value: '0-1-0',
        key: '0-1-0',
        disabled: true,
      },
      {
        title: 'Child Node4',
        value: '0-1-1',
        key: '0-1-1',
      },
      {
        title: 'Child Node5',
        value: '0-1-2',
        key: '0-1-2',
      },
    ],
  },
];
export default {
  data() {
    return {
      value: ['0-0-0'],
      treeData,
      SHOW_PARENT,
    };
  },
};
</script>
```

##### 从数据直接生成 
使用 `treeData` 把 JSON 数据直接生成树结构。

```html
<template>
  <h-tree-select
    v-model="value"
    style="width: 100%"
    :dropdown-style="{ maxHeight: '400px', overflow: 'auto' }"
    :tree-data="treeData"
    placeholder="Please select"
    tree-default-expand-all
  >
    <span v-if="key === '0-0-1'" slot="title" slot-scope="{ key, value }" style="color: #08c">
      Child Node1 {{ value }}
    </span>
  </h-tree-select>
</template>

<script>
const treeData = [
  {
    title: 'Node1',
    value: '0-0',
    key: '0-0',
    children: [
      {
        value: '0-0-1',
        key: '0-0-1',
        scopedSlots: {
          // custom title
          title: 'title',
        },
      },
      {
        title: 'Child Node2',
        value: '0-0-2',
        key: '0-0-2',
      },
    ],
  },
  {
    title: 'Node2',
    value: '0-1',
    key: '0-1',
  },
];
export default {
  data() {
    return {
      value: undefined,
      treeData,
    };
  },
  watch: {
    value(value) {
      console.log(value);
    },
  },
};
</script>
```

##### 异步加载
异步加载树节点。

```html
<template>
  <h-tree-select
    v-model="value"
    tree-dath-simple-mode
    style="width: 100%"
    :dropdown-style="{ maxHeight: '400px', overflow: 'auto' }"
    :tree-data="treeData"
    placeholder="Please select"
    :load-data="onLoadData"
  />
</template>

<script>
export default {
  data() {
    return {
      value: undefined,
      treeData: [
        { id: 1, pId: 0, value: '1', title: 'Expand to load' },
        { id: 2, pId: 0, value: '2', title: 'Expand to load' },
        { id: 3, pId: 0, value: '3', title: 'Tree Node', isLeaf: true },
      ],
    };
  },
  watch: {
    value(value) {
      console.log(value);
    },
  },
  methods: {
    genTreeNode(parentId, isLeaf = false) {
      const random = Math.random()
        .toString(36)
        .substring(2, 6);
      return {
        id: random,
        pId: parentId,
        value: random,
        title: isLeaf ? 'Tree Node' : 'Expand to load',
        isLeaf,
      };
    },
    onLoadData(treeNode) {
      return new Promise(resolve => {
        const { id } = treeNode.dataRef;
        setTimeout(() => {
          this.treeData = this.treeData.concat([
            this.genTreeNode(id, false),
            this.genTreeNode(id, true),
          ]);
          resolve();
        }, 300);
      });
    },
  },
};
</script>
```

### API 
#### Tree props
| 参数                     | 说明                                                         | 类型                                                         | 默认值                                                       | 版本 |
| :----------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
| allowClear               | 显示清除按钮                                                 | boolean                                                      | false                                                        |      |
| defaultValue             | 指定默认选中的条目                                           | string/string[]                                              | -                                                            |      |
| disabled                 | 是否禁用                                                     | boolean                                                      | false                                                        |      |
| dropdownClassName        | 下拉菜单的 className 属性                                    | string                                                       | -                                                            |      |
| dropdownMatchSelectWidth | 下拉菜单和选择器同宽                                         | boolean                                                      | true                                                         |      |
| dropdownStyle            | 下拉菜单的样式                                               | object                                                       | -                                                            |      |
| filterTreeNode           | 是否根据输入项进行筛选，默认用 treeNodeFilterProp 的值作为要筛选的 TreeNode 的属性值 | boolean\|Function(inputValue: string, treeNode: TreeNode) (函数需要返回 bool 值) | Function                                                     |      |
| getPopupContainer        | 菜单渲染父节点。默认渲染到 body 上，如果你遇到菜单滚动定位问题，试试修改为滚动的区域，并相对其定位。 | Function(triggerNode)                                        | () => document.body                                          |      |
| labelInValue             | 是否把每个选项的 label 包装到 value 中，会把 value 类型从 `string` 变为 `{value: string, label: VNode, halfChecked(treeCheckStrictly 时有效): string[] }` 的格式 | boolean                                                      | false                                                        |      |
| loadData                 | 异步加载数据                                                 | function(node)                                               | -                                                            |      |
| maxTagCount              | 最多显示多少个 tag                                           | number                                                       | -                                                            |      |
| maxTagPlaceholder        | 隐藏 tag 时显示的内容                                        | slot/function(omittedValues)                                 | -                                                            |      |
| multiple                 | 支持多选（当设置 treeCheckable 时自动变为 true）             | boolean                                                      | false                                                        |      |
| placeholder              | 选择框默认文字                                               | string\|slot                                                 | -                                                            |      |
| searchPlaceholder        | 搜索框默认文字                                               | string\|slot                                                 | -                                                            |      |
| searchValue(.sync)       | 搜索框的值，可以通过 `search` 事件获取用户输入               | string                                                       | -                                                            |      |
| treeIcon                 | 是否展示 TreeNode title 前的图标，没有默认样式，如设置为 true，需要自行定义图标相关样式 | boolean                                                      | false                                                        |      |
| showCheckedStrategy      | 定义选中项回填的方式。`TreeSelect.SHOW_ALL`: 显示所有选中节点(包括父节点). `TreeSelect.SHOW_PARENT`: 只显示父节点(当父节点下所有子节点都选中时). 默认只显示子节点. | enum{TreeSelect.SHOW_ALL, TreeSelect.SHOW_PARENT, TreeSelect.SHOW_CHILD } | TreeSelect.SHOW_CHILD                                        |      |
| showSearch               | 在下拉中显示搜索框(仅在单选模式下生效)                       | boolean                                                      | false                                                        |      |
| size                     | 选择框大小，可选 `large` `small`                             | string                                                       | 'default'                                                    |      |
| suffixIcon               | 自定义的选择框后缀图标                                       | VNode \| slot                                                | -                                                            |      |
| treeCheckable            | 显示 checkbox                                                | boolean                                                      | false                                                        |      |
| treeCheckStrictly        | checkable 状态下节点选择完全受控（父子节点选中状态不再关联），会使得 `labelInValue` 强制为 true | boolean                                                      | false                                                        |      |
| treeData                 | treeNodes 数据，如果设置则不需要手动构造 TreeNode 节点（value 在整个树范围内唯一） | array<{value, label, children, [disabled, disableCheckbox, selectable]}> | []                                                           |      |
| replaceFields            | 替换 treeNode 中 title,value,key,children 字段为 treeData 中对应的字段 | object                                                       | {children:'children', title:'title', key:'key', value: 'value' } |      |
| treeDataSimpleMode       | 使用简单格式的 treeData，具体设置参考可设置的类型 (此时 treeData 应变为这样的数据结构: [{id:1, pId:0, value:'1', label:"test1",...},...], `pId` 是父节点的 id) | false\|Array<{ id: string, pId: string, rootPId: null }>     | false                                                        |      |
| treeDefaultExpandAll     | 默认展开所有树节点                                           | boolean                                                      | false                                                        |      |
| treeDefaultExpandedKeys  | 默认展开的树节点                                             | string[] \| number[]                                         | -                                                            |      |
| treeExpandedKeys(.sync)  | 设置展开的树节点                                             | string[] \| number[]                                         | -                                                            |      |
| treeNodeFilterProp       | 输入项过滤对应的 treeNode 属性                               | string                                                       | 'value'                                                      |      |
| treeNodeLabelProp        | 作为显示的 prop 设置                                         | string                                                       | 'title'                                                      |      |
| value(v-model)           | 指定当前选中的条目                                           | string/string[]                                              | -                                                            |      |

#### 事件
| 事件名称   | 说明                   | 回调参数                      |
| :--------- | :--------------------- | :---------------------------- |
| change     | 选中树节点时调用此函数 | function(value, label, extra) |
| search     | 文本框值变化时回调     | function(value: string)       |
| select     | 被选中时调用           | function(value, node, extra)  |
| treeExpand | 展开节点时调用         | function(expandedKeys)        |

#### Tree 方法 
| 名称    | 描述     |
| :------ | :------- |
| blur()  | 移除焦点 |
| focus() | 获取焦点 |

#### TreeNode props 
> 建议使用 treeData 来代替 TreeNode，免去手工构造麻烦

| 参数            | 说明                                                         | 类型             | 默认值 | 版本  |
| :-------------- | :----------------------------------------------------------- | :--------------- | :----- | :---- |
| selectable      | 是否可选                                                     | boolean          | true   |       |
| checkable       | 当树为 checkable 时，设置独立节点是否展示 Checkbox           | boolean          | -      | 1.5.0 |
| disableCheckbox | 禁掉 checkbox                                                | boolean          | false  |       |
| disabled        | 是否禁用                                                     | boolean          | false  |       |
| isLeaf          | 是否是叶子节点                                               | boolean          | false  |       |
| key             | 此项必须设置（其值在整个树范围内唯一）                       | string \| number | -      |       |
| title           | 树节点显示的内容                                             | string\|slot     | '---'  |       |
| value           | 默认根据此属性值进行筛选（其值在整个树范围内唯一）           | string           | -      |       |
| scopedSlots     | 使用 treeData 时，可以通过该属性配置支持 slot 的属性，如 `scopedSlots: { title: 'XXX'}` | object           | -      |       |

## 徽标数
图标右上角的圆形徽标数字。

### 何时使用
一般出现在通知图标或头像的右上角，用于显示需要处理的消息条数，通过醒目视觉形式吸引用户处理。

### 代码演示
##### 基本 
简单的徽章展示，当 `count` 为 `0` 时，默认不显示，但是可以使用 `showZero` 修改为显示。

```html
<template>
  <div>
    <h-badge count="5">
      <a href="#" class="head-example" />
    </h-badge>
    <h-badge count="0" show-zero>
      <a href="#" class="head-example" />
    </h-badge>
    <h-badge>
      <h-icon slot="count" type="clock-circle" style="color: #f5222d" />
      <a href="#" class="head-example" />
    </h-badge>
  </div>
</template>
```

##### 封顶数字
超过 `overflowCount` 的会显示为 `${overflowCount}+`，默认的 `overflowCount` 为 `99`。

```html
<template>
  <div>
    <h-badge :count="99">
      <a href="#" class="head-example" />
    </h-badge>
    <h-badge :count="100">
      <a href="#" class="head-example" />
    </h-badge>
    <h-badge :count="99" :overflow-count="10">
      <a href="#" class="head-example" />
    </h-badge>
    <h-badge :count="1000" :overflow-count="999">
      <a href="#" class="head-example" />
    </h-badge>
  </div>
</template>
```

##### 状态点
用于表示状态的小圆点。

```html
<template>
  <div>
    <h-badge status="success" />
    <h-badge status="error" />
    <h-badge status="default" />
    <h-badge status="processing" />
    <h-badge status="warning" />
    <br />
    <h-badge status="success" text="Success" />
    <br />
    <h-badge status="error" text="Error" />
    <br />
    <h-badge status="default" text="Default" />
    <br />
    <h-badge status="processing" text="Processing" />
    <br />
    <h-badge status="warning" text="warning" />
  </div>
</template>
```

##### 自定义标题
设置鼠标放在状态点上时显示的文字

```html
<template>
  <div id="components-badge-demo-title">
    <h-badge :count="5" title="Custom hover text">
      <a href="#" class="head-example" />
    </h-badge>
  </div>
</template>
<style scoped>
#components-badge-demo-title .ant-badge:not(.ant-badge-status) {
  margin-right: 20px;
}
.head-example {
  width: 42px;
  height: 42px;
  border-radius: 4px;
  background: #eee;
  display: inline-block;
}
</style>
```

##### 独立使用
不包裹任何元素即是独立使用，可自定样式展现。
在右上角的 badge 则限定为红色。

```html
<template>
  <div>
    <h-badge count="25" />
    <h-badge
      count="4"
      :number-style="{
        backgroundColor: '#fff',
        color: '#999',
        boxShadow: '0 0 0 1px #d9d9d9 inset',
      }"
    />
    <h-badge count="109" :number-style="{ backgroundColor: '#52c41a' }" />
  </div>
</template>
```

##### 讨嫌的小红点 
没有具体的数字。

```html
<template>
  <div id="components-badge-demo-dot">
    <h-badge dot>
      <h-icon type="notification" />
    </h-badge>
    <h-badge :count="0" dot>
      <h-icon type="notification" />
    </h-badge>
    <h-badge dot>
      <a href="#">Link something</a>
    </h-badge>
  </div>
</template>
<style scoped>
#components-badge-demo-dot .anticon-notification {
  width: 16px;
  height: 16px;
  line-height: 16px;
  font-size: 16px;
}
</style>
```

##### 动态 
展示动态变化的效果。

```html
<template>
  <div>
    <div>
      <h-badge :count="count">
        <a href="#" class="head-example" />
      </h-badge>
      <h-button-group>
        <h-button @click="decline">
          <h-icon type="minus" />
        </h-button>
        <h-button @click="increase">
          <h-icon type="plus" />
        </h-button>
      </h-button-group>
    </div>
    <div style="margin-top: 10px">
      <h-badge :dot="show">
        <a href="#" class="head-example" />
      </h-badge>
      <h-switch v-model="show" />
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      count: 5,
      show: true,
    };
  },
  methods: {
    decline() {
      let count = this.count - 1;
      if (count < 0) {
        count = 0;
      }
      this.count = count;
    },
    increase() {
      this.count++;
    },
  },
};
</script>
```

##### 多彩徽标
1.5.0 后新增。我们添加了多种预设色彩的徽标样式，用作不同场景使用。如果预设值不能满足你的需求，可以设置为具体的色值。

```html
<template>
  <div>
    <h4 style="margin-bottom: 16px">
      Presets:
    </h4>
    <div>
      <div v-for="color in colors" :key="color">
        <h-badge :color="color" :text="color" />
      </div>
    </div>
    <h4 style="margin: 16px 0">
      Custom:
    </h4>
    <div>
      <h-badge color="#f50" text="#f50" />
      <br />
      <h-badge color="#2db7f5" text="#2db7f5" />
      <br />
      <h-badge color="#87d068" text="#87d068" />
      <br />
      <h-badge color="#108ee9" text="#108ee9" />
    </div>
  </div>
</template>
<script>
const colors = [
  'pink',
  'red',
  'yellow',
  'orange',
  'cyan',
  'green',
  'blue',
  'purple',
  'geekblue',
  'magenta',
  'volcano',
  'gold',
  'lime',
];
export default {
  data() {
    return {
      colors,
    };
  },
};
</script>
```

### API
```html
<h-badge :count="5">
  <a href="#" class="head-example" />
</h-badge>
<h-badge :count="5" />
```

| 参数          | 说明                                                         | 类型                                                         | 默认值  | 版本  |
| :------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :------ | :---- |
| color         | 自定义小圆点的颜色                                           | string                                                       | -       | 1.5.0 |
| count         | 展示的数字，大于 overflowCount 时显示为 `${overflowCount}+`，为 0 时隐藏 | number \| string \| slot                                     |         |       |
| dot           | 不展示数字，只有一个小红点                                   | boolean                                                      | false   |       |
| offset        | 设置状态点的位置偏移，格式为 [x, y]                          | [number\|string, number\|string]                             | -       |       |
| overflowCount | 展示封顶的数字值                                             | number                                                       | 99      |       |
| showZero      | 当数值为 0 时，是否展示 Badge                                | boolean                                                      | false   |       |
| status        | 设置 Badge 为状态点                                          | Enum{ 'success', 'processing, 'default', 'error', 'warning' } | ''      |       |
| text          | 在设置了 `status` 的前提下有效，设置状态点的文本             | string                                                       | ''      |       |
| numberStyle   | 设置状态点的样式                                             | object                                                       | ''      |       |
| title         | 设置鼠标放在状态点上时显示的文字                             | string                                                       | `count` |       |

## 日历
按照日历形式展示数据的容器。

### 何时使用
当数据是日期或按照日期划分时，例如日程、课表、价格日历等，农历等。目前支持年/月切换。

### 代码演示
##### 基本 
一个通用的日历面板，支持年/月切换。

```html
<template>
  <h-calendar @panelChange="onPanelChange" />
</template>
<script>
export default {
  methods: {
    onPanelChange(value, mode) {
      console.log(value, mode);
    },
  },
};
</script>
```

##### 卡片模式 
用于嵌套在空间有限的容器中。

```html
<template>
  <div :style="{ width: '300px', border: '1px solid #d9d9d9', borderRadius: '4px' }">
    <h-calendar :fullscreen="false" @panelChange="onPanelChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onPanelChange(value, mode) {
      console.log(value, mode);
    },
  },
};
</script>
```

##### 通知事项日历 
一个复杂的应用示例，用 `dateCellRender` 和 `monthCellRender` 函数来自定义需要渲染的数据。

```html
<template>
  <h-calendar>
    <ul slot="dateCellRender" slot-scope="value" class="events">
      <li v-for="item in getListData(value)" :key="item.content">
        <h-badge :status="item.type" :text="item.content" />
      </li>
    </ul>
    <template slot="monthCellRender" slot-scope="value">
      <div v-if="getMonthData(value)" class="notes-month">
        <section>{{ getMonthData(value) }}</section>
        <span>Backlog number</span>
      </div>
    </template>
  </h-calendar>
</template>
<script>
export default {
  methods: {
    getListData(value) {
      let listData;
      switch (value.date()) {
        case 8:
          listData = [
            { type: 'warning', content: 'This is warning event.' },
            { type: 'success', content: 'This is usual event.' },
          ];
          break;
        case 10:
          listData = [
            { type: 'warning', content: 'This is warning event.' },
            { type: 'success', content: 'This is usual event.' },
            { type: 'error', content: 'This is error event.' },
          ];
          break;
        case 15:
          listData = [
            { type: 'warning', content: 'This is warning event' },
            { type: 'success', content: 'This is very long usual event。。....' },
            { type: 'error', content: 'This is error event 1.' },
            { type: 'error', content: 'This is error event 2.' },
            { type: 'error', content: 'This is error event 3.' },
            { type: 'error', content: 'This is error event 4.' },
          ];
          break;
        default:
      }
      return listData || [];
    },

    getMonthData(value) {
      if (value.month() === 8) {
        return 1394;
      }
    },
  },
};
</script>
<style scoped>
.events {
  list-style: none;
  margin: 0;
  padding: 0;
}
.events .ant-badge-status {
  overflow: hidden;
  white-space: nowrap;
  width: 100%;
  text-overflow: ellipsis;
  font-size: 12px;
}
.notes-month {
  text-align: center;
  font-size: 28px;
}
.notes-month section {
  font-size: 28px;
}
</style>
```

##### 选择功能 
一个通用的日历面板，支持年/月切换。

```html
<template>
  <div>
    <h-alert
      :message="`You selected date: ${selectedValue && selectedValue.format('YYYY-MM-DD')}`"
    />
    <div
      :style="{
        display: 'inline-block',
        width: '500px',
        border: '1px solid #d9d9d9',
        borderRadius: '4px',
      }"
    >
      <h-calendar :value="value" @select="onSelect" @panelChange="onPanelChange" />
    </div>
    <div
      :style="{
        display: 'inline-block',
        width: '500px',
        marginLeft: '20px',
        border: '1px solid #d9d9d9',
        borderRadius: '4px',
      }"
    >
      <h-calendar v-model="value1" />
    </div>
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      value: moment('2017-01-25'),
      selectedValue: moment('2017-01-25'),
      value1: moment('2017-01-25'),
    };
  },
  methods: {
    onSelect(value) {
      this.value = value;
      this.selectedValue = value;
    },
    onPanelChange(value) {
      this.value = value;
    },
  },
};
</script>
```

##### 自定义头部
自定义日历头部内容。

```html
<template>
  <div style="width: 300px; border: 1px solid #d9d9d9; border-radius: 4px">
    <h-calendar :fullscreen="false" :header-render="headerRender" @panelChange="onPanelChange" />
  </div>
</template>
<script>
export default {
  methods: {
    onPanelChange(value, mode) {
      // eslint-disable-next-line no-console
      console.log(value, mode);
    },
    headerRender({ value, type, onChange, onTypeChange }) {
      const start = 0;
      const end = 12;
      const monthOptions = [];

      const current = value.clone();
      const localeData = value.localeData();
      const months = [];
      for (let i = 0; i < 12; i++) {
        current.month(i);
        months.push(localeData.monthsShort(current));
      }

      for (let index = start; index < end; index++) {
        monthOptions.push(
          <h-select-option class="month-item" key={`${index}`}>
            {months[index]}
          </h-select-option>,
        );
      }
      const month = value.month();

      const year = value.year();
      const options = [];
      for (let i = year - 10; i < year + 10; i += 1) {
        options.push(
          <h-select-option key={i} value={i} class="year-item">
            {i}
          </h-select-option>,
        );
      }
      return (
        <div style={{ padding: '10px' }}>
          <div style={{ marginBottom: '10px' }}>Custom header </div>
          <h-row type="flex" justify="space-between">
            <h-col>
              <h-radio-group size="small" onChange={e => onTypeChange(e.target.value)} value={type}>
                <h-radio-button value="month">Month</h-radio-button>
                <h-radio-button value="year">Year</h-radio-button>
              </h-radio-group>
            </h-col>
            <h-col>
              <h-select
                size="small"
                dropdownMatchSelectWidth={false}
                class="my-year-select"
                onChange={newYear => {
                  const now = value.clone().year(newYear);
                  onChange(now);
                }}
                value={String(year)}
              >
                {options}
              </h-select>
            </h-col>
            <h-col>
              <h-select
                size="small"
                dropdownMatchSelectWidth={false}
                value={String(month)}
                onChange={selectedMonth => {
                  const newValue = value.clone();
                  newValue.month(parseInt(selectedMonth, 10));
                  onChange(newValue);
                }}
              >
                {monthOptions}
              </h-select>
            </h-col>
          </h-row>
        </div>
      );
    },
  },
};
</script>
```

### API 
**注意：**Calendar 部分 locale 是从 value 中读取，所以请先正确设置 moment 的 locale。

```html
// 默认语言为 en-US，所以如果需要使用其他语言，推荐在入口文件全局设置 locale // import moment from
'moment'; // import 'moment/locale/zh-cn'; // moment.locale('zh-cn');

<h-calendar @panelChange="onPanelChange" @select="onSelect">
  <template slot="dateCellRender" slot-scope="value"></template>
  <template slot="monthCellRender" slot-scope="value"></template>
</h-calendar>
```

| 参数                | 说明                                                         | 类型                                                         | 默认值                                                       | 版本  |
| :------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---- |
| dateCellRender      | 作用域插槽，用来自定义渲染日期单元格，返回内容会被追加到单元格, | function(date: moment)                                       | 无                                                           |       |
| dateFullCellRender  | 作用域插槽，自定义渲染日期单元格，返回内容覆盖单元格         | function(date: moment)                                       | 无                                                           |       |
| defaultValue        | 默认展示的日期                                               | [moment](http://momentjs.com/)                               | 默认日期                                                     |       |
| disabledDate        | 不可选择的日期                                               | (currentDate: moment) => boolean                             | 无                                                           |       |
| fullscreen          | 是否全屏显示                                                 | boolean                                                      | true                                                         |       |
| locale              | 国际化配置                                                   | object                                                       | [默认配置](https://github.com/vueComponent/ant-design-vue/blob/master/components/date-picker/locale/example.json) |       |
| mode                | 初始模式，`month/year`                                       | string                                                       | month                                                        |       |
| monthCellRender     | 作用域插槽，自定义渲染月单元格，返回内容会被追加到单元格     | function(date: moment)                                       | 无                                                           |       |
| monthFullCellRender | 作用域插槽，自定义渲染月单元格，返回内容覆盖单元格           | function(date: moment)                                       | 无                                                           |       |
| validRange          | 设置可以显示的日期                                           | [[moment](http://momentjs.com/), [moment](http://momentjs.com/)] | 无                                                           |       |
| value(v-model)      | 展示日期                                                     | [moment](http://momentjs.com/)                               | 当前日期                                                     |       |
| headerRender        | 自定义头部内容                                               | function(object:{value: moment, type: string, onChange: f(), onTypeChange: f()}) \| slot-scope | -                                                            | 1.5.0 |
| valueFormat         | 可选，绑定值的格式，对 value、defaultValue 起作用。不指定则绑定值为 moment 对象 | string，[具体格式](https://momentjs.com/docs/#/displaying/format/) | -                                                            | 1.5.4 |

#### 事件 
| 事件名称    | 说明                                         | 回调参数                                       |
| :---------- | :------------------------------------------- | :--------------------------------------------- |
| panelChange | 日期面板变化回调                             | function(date: moment \| string, mode: string) |
| select      | 点击选择日期回调                             | function(date: moment \| string）              |
| change      | 日期变化时的回调, 面板变化有可能导致日期变化 | function(date: moment \| string）              |

## 卡片
通用卡片容器

### 何时使用
最基础的卡片容器，可承载文字、列表、图片、段落，常用于后台概览页面。

### 代码演示
##### 典型卡片 
包含标题、内容、操作区域。
可通过设置size为`default`或者`small`，控制尺寸

```html
<template>
  <div>
    <h-card title="Default size card" style="width: 300px">
      <a slot="extra" href="#">more</a>
      <p>card content</p>
      <p>card content</p>
      <p>card content</p>
    </h-card>
    <br />
    <h-card size="small" title="Small size card" style="width: 300px">
      <a slot="extra" href="#">more</a>
      <p>card content</p>
      <p>card content</p>
      <p>card content</p>
    </h-card>
  </div>
</template>
```

##### 更灵活的内容展示
可以利用 `Card.Meta` 支持更灵活的内容

```html
<template>
  <h-card hoverable style="width: 240px">
    <img
      slot="cover"
      alt="example"
      src="https://os.alipayobjects.com/rmsportal/QBnOOoLaAfKPirc.png"
    />
    <h-card-meta title="Europe Street beat">
      <template slot="description">
        www.instagram.com
      </template>
    </h-card-meta>
  </h-card>
</template>
```

##### 栅格卡片 
在系统概览页面常常和栅格进行配合。

```html
<template>
  <div style="background-color: #ececec; padding: 20px;">
    <h-row :gutter="16">
      <h-col :span="8">
        <h-card title="Card title" :bordered="false">
          <p>card content</p>
        </h-card>
      </h-col>
      <h-col :span="8">
        <h-card title="Card title" :bordered="false">
          <p>card content</p>
        </h-card>
      </h-col>
      <h-col :span="8">
        <h-card title="Card title" :bordered="false">
          <p>card content</p>
        </h-card>
      </h-col>
    </h-row>
  </div>
</template>
```

##### 预加载的卡片 
数据读入前会有文本块样式

```html
<template>
  <div>
    <h-card :loading="loading" title="Card title">
      whatever content
    </h-card>
    <h-button style="marginTop: 16px" @click="handleClick">
      Toggle loading
    </h-button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      loading: true,
    };
  },
  methods: {
    handleClick() {
      this.loading = !this.loading;
    },
  },
};
</script>
```

##### 简洁卡片 
只包含内容区域。

```html
<template>
  <h-card style="width: 300px">
    <p>Card content</p>
    <p>Card content</p>
    <p>Card content</p>
  </h-card>
</template>
```

##### 无边框
在灰色背景上使用无边框的卡片

```html
<template>
  <div style="background:#ECECEC; padding:30px">
    <h-card title="Card title" :bordered="false" style="width: 300px">
      <p>Card content</p>
      <p>Card content</p>
      <p>Card content</p>
    </h-card>
  </div>
</template>
```

##### 网格型内嵌卡片
一种常见的卡片内容区隔模式。

```html
<template>
  <h-card title="Card Title">
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center" :hoverable="false">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
    <h-card-grid style="width:25%;text-align:center">
      Content
    </h-card-grid>
  </h-card>
</template>
```

##### 内部卡片 
可以放在普通卡片内部，展示多层级结构的信息

```html
<template>
  <h-card title="Card title">
    <p style="fontSize: 14px;color: rgba(0, 0, 0, 0.85); marginBottom: 16px;fontWeight: 500">
      Group title
    </p>
    <h-card title="Inner card title">
      <a slot="extra" href="#">More</a>
      Inner Card content
    </h-card>
    <h-card title="Inner card title" :style="{ marginTop: '16px' }">
      <a slot="extra" href="#">More</a>
      Inner Card content
    </h-card>
  </h-card>
</template>
```

##### 支持更多内容配置
一种支持封面、头像、标题和描述信息的卡片。

```html
<template>
  <h-card hoverable style="width: 300px">
    <img
      slot="cover"
      alt="example"
      src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"
    />
    <template slot="actions" class="ant-card-actions">
      <h-icon key="setting" type="setting" />
      <h-icon key="edit" type="edit" />
      <h-icon key="ellipsis" type="ellipsis" />
    </template>
    <h-card-meta title="Card title" description="This is the description">
      <h-avatar
        slot="avatar"
        src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
      />
    </h-card-meta>
  </h-card>
</template>
```

##### 带页签的卡片
可承载更多内容

```html
<template>
  <div>
    <h-card
      style="width:100%"
      title="Card title"
      :tab-list="tabList"
      :active-tab-key="key"
      @tabChange="key => onTabChange(key, 'key')"
    >
      <span slot="customRender" slot-scope="item"> <h-icon type="home" />{{ item.key }} </span>
      <a slot="extra" href="#">More</a>
      {{ contentList[key] }}
    </h-card>
    <br /><br />
    <h-card
      style="width:100%"
      :tab-list="tabListNoTitle"
      :active-tab-key="noTitleKey"
      @tabChange="key => onTabChange(key, 'noTitleKey')"
    >
      <p v-if="noTitleKey === 'article'">
        article content
      </p>
      <p v-else-if="noTitleKey === 'app'">
        app content
      </p>
      <p v-else="noTitleKey === 'project'">
        project content
      </p>
      <a slot="tabBarExtraContent" href="#">More</a>
    </h-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tabList: [
        {
          key: 'tab1',
          // tab: 'tab1',
          scopedSlots: { tab: 'customRender' },
        },
        {
          key: 'tab2',
          tab: 'tab2',
        },
      ],
      contentList: {
        tab1: 'content1',
        tab2: 'content2',
      },
      tabListNoTitle: [
        {
          key: 'article',
          tab: 'article',
        },
        {
          key: 'app',
          tab: 'app',
        },
        {
          key: 'project',
          tab: 'project',
        },
      ],
      key: 'tab1',
      noTitleKey: 'app',
    };
  },
  methods: {
    onTabChange(key, type) {
      console.log(key, type);
      this[type] = key;
    },
  },
};
</script>
```

### API 
#### Card 
| 参数                | 说明                                                | 类型                                                      | 默认值     | 版本      |
| :------------------ | :-------------------------------------------------- | :-------------------------------------------------------- | :--------- | :-------- |
| actions             | 卡片操作组，位置在卡片底部                          | slots                                                     | -          |           |
| activeTabKey        | 当前激活页签的 key                                  | string                                                    | -          |           |
| headStyle           | 自定义标题区域样式                                  | object                                                    | -          |           |
| bodyStyle           | 内容区域自定义样式                                  | object                                                    | -          |           |
| bordered            | 是否有边框                                          | boolean                                                   | true       |           |
| cover               | 卡片封面                                            | slot                                                      | -          |           |
| defaultActiveTabKey | 初始化选中页签的 key，如果没有设置 activeTabKey     | string                                                    | 第一个页签 |           |
| extra               | 卡片右上角的操作区域                                | string\|slot                                              | -          |           |
| hoverable           | 鼠标移过时可浮起                                    | boolean                                                   | false      |           |
| loading             | 当卡片内容还在加载中时，可以用 loading 展示一个占位 | boolean                                                   | false      |           |
| tabList             | 页签标题列表, 可以通过 scopedSlots 属性自定义 tab   | Array<{key: string, tab: any, scopedSlots: {tab: 'XXX'}}> | -          |           |
| tabBarExtraContent  | tab bar 上额外的元素                                | slot                                                      | 无         | 1.5.0     |
| size                | card 的尺寸                                         | `default`                                                 | `small`    | `default` |
| title               | 卡片标题                                            | string\|slot                                              | -          |           |
| type                | 卡片类型，可设置为 `inner` 或 不设置                | string                                                    | -          |           |

#### 事件
| 事件名称  | 说明           | 回调参数      | 版本 |
| :-------- | :------------- | :------------ | :--- |
| tabChange | 页签切换的回调 | (key) => void | -    |

#### Card.Grid
#### Card.Meta 
| 参数        | 说明      | 类型         | 默认值 | 版本 |
| :---------- | :-------- | :----------- | :----- | :--- |
| avatar      | 头像/图标 | slot         | -      |      |
| description | 描述内容  | string\|slot | -      |      |
| title       | 标题内容  | string\|slot | -      |      |

## 走马灯
旋转木马，一组轮播的区域。

### 何时使用
- 当有一组平级的内容。

- 当内容空间不足时，可以用走马灯的形式进行收纳，进行轮播展现。

- 常用于一组图片或卡片轮播。

### 代码演示
##### 基本
最简单的用法。

```html
<template>
  <h-carousel :after-change="onChange">
    <div><h3>1</h3></div>
    <div><h3>2</h3></div>
    <div><h3>3</h3></div>
    <div><h3>4</h3></div>
  </h-carousel>
</template>
<script>
export default {
  methods: {
    onChange(a, b, c) {
      console.log(a, b, c);
    },
  },
};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-slide {
  text-align: center;
  height: 160px;
  line-height: 160px;
  background: #364d79;
  overflow: hidden;
}

.ant-carousel >>> .slick-slide h3 {
  color: #fff;
}
</style>
```

##### 位置
位置有 4 个方向。

```html
<template>
  <div>
    <h-radio-group v-model="dotPosition" style="margin-bottom: 8px">
      <h-radio-button value="top">
        Top
      </h-radio-button>
      <h-radio-button value="bottom">
        Bottom
      </h-radio-button>
      <h-radio-button value="left">
        Left
      </h-radio-button>
      <h-radio-button value="right">
        Right
      </h-radio-button>
    </h-radio-group>
    <h-carousel :dot-position="dotPosition">
      <div><h3>1</h3></div>
      <div><h3>2</h3></div>
      <div><h3>3</h3></div>
      <div><h3>4</h3></div>
    </h-carousel>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dotPosition: 'top',
    };
  },
};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-slide {
  text-align: center;
  height: 160px;
  line-height: 160px;
  background: #364d79;
  overflow: hidden;
}

.ant-carousel >>> .slick-slide h3 {
  color: #fff;
}
</style>
```

##### 渐显
切换效果为渐显。

```html
<template>
  <h-carousel effect="fade">
    <div><h3>1</h3></div>
    <div><h3>2</h3></div>
    <div><h3>3</h3></div>
    <div><h3>4</h3></div>
  </h-carousel>
</template>
<script>
export default {};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-slide {
  text-align: center;
  height: 160px;
  line-height: 160px;
  background: #364d79;
  overflow: hidden;
}

.ant-carousel >>> .slick-slide h3 {
  color: #fff;
}
</style>
```

##### 自动切换 
定时切换下一张。

```html
<template>
  <h-carousel autoplay>
    <div><h3>1</h3></div>
    <div><h3>2</h3></div>
    <div><h3>3</h3></div>
    <div><h3>4</h3></div>
  </h-carousel>
</template>
<script>
export default {};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-slide {
  text-align: center;
  height: 160px;
  line-height: 160px;
  background: #364d79;
  overflow: hidden;
}

.ant-carousel >>> .slick-slide h3 {
  color: #fff;
}
</style>
```

##### 自定义分页 
自定义分页展示。

```html
<template>
  <h-carousel arrows dots-class="slick-dots slick-thumb">
    <a slot="customPaging" slot-scope="props">
      <img :src="getImgUrl(props.i)" />
    </a>
    <div v-for="item in 4">
      <img :src="baseUrl + 'abstract0' + item + '.jpg'" />
    </div>
  </h-carousel>
</template>
<script>
const baseUrl =
  'https://raw.githubusercontent.com/vueComponent/ant-design-vue/master/components/vc-slick/assets/img/react-slick/';
export default {
  data() {
    return {
      baseUrl,
    };
  },
  methods: {
    getImgUrl(i) {
      return `${baseUrl}abstract0${i + 1}.jpg`;
    },
  },
};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-dots {
  height: auto;
}
.ant-carousel >>> .slick-slide img {
  border: 5px solid #fff;
  display: block;
  margin: auto;
  max-width: 80%;
}
.ant-carousel >>> .slick-thumb {
  bottom: -45px;
}
.ant-carousel >>> .slick-thumb li {
  width: 60px;
  height: 45px;
}
.ant-carousel >>> .slick-thumb li img {
  width: 100%;
  height: 100%;
  filter: grayscale(100%);
}
.ant-carousel >>> .slick-thumb li.slick-active img {
  filter: grayscale(0%);
}
</style>
```

##### 自定义箭头 
自定义箭头展示。

```html
<template>
  <h-carousel arrows>
    <div
      slot="prevArrow"
      slot-scope="props"
      class="custom-slick-arrow"
      style="left: 10px;zIndex: 1"
    >
      <h-icon type="left-circle" />
    </div>
    <div slot="nextArrow" slot-scope="props" class="custom-slick-arrow" style="right: 10px">
      <h-icon type="right-circle" />
    </div>
    <div><h3>1</h3></div>
    <div><h3>2</h3></div>
    <div><h3>3</h3></div>
    <div><h3>4</h3></div>
  </h-carousel>
</template>
<script>
export default {};
</script>
<style scoped>
/* For demo */
.ant-carousel >>> .slick-slide {
  text-align: center;
  height: 160px;
  line-height: 160px;
  background: #364d79;
  overflow: hidden;
}

.ant-carousel >>> .custom-slick-arrow {
  width: 25px;
  height: 25px;
  font-size: 25px;
  color: #fff;
  background-color: rgba(31, 45, 61, 0.11);
  opacity: 0.3;
}
.ant-carousel >>> .custom-slick-arrow:before {
  display: none;
}
.ant-carousel >>> .custom-slick-arrow:hover {
  opacity: 0.5;
}

.ant-carousel >>> .slick-slide h3 {
  color: #fff;
}
</style>
```

### API
| 参数         | 说明                                               | 类型               | 默认值       | 版本  |
| :----------- | :------------------------------------------------- | :----------------- | :----------- | :---- |
| afterChange  | 切换面板的回调                                     | function(current)  | 无           |       |
| autoplay     | 是否自动切换                                       | boolean            | false        |       |
| beforeChange | 切换面板的回调                                     | function(from, to) | 无           |       |
| dotPosition  | 面板指示点位置，可选 `top` `bottom` `left` `right` | string             | bottom       | 1.5.0 |
| dots         | 是否显示面板指示点                                 | boolean            | true         |       |
| dotsClass    | 面板指示点类名                                     | string             | `slick-dots` |       |
| easing       | 动画效果                                           | string             | linear       |       |
| effect       | 动画效果函数，可取 scrollx, fade                   | string             | scrollx      |       |

### 方法
| 名称                           | 描述                                              | 版本 |
| :----------------------------- | :------------------------------------------------ | :--- |
| goTo(slideNumber, dontAnimate) | 切换到指定面板, dontAnimate = true 时，不使用动画 |      |
| next()                         | 切换到下一面板                                    |      |
| prev()                         | 切换到上一面板                                    |      |

更多参数可参考：[vc-slick props](https://github.com/vueComponent/ant-design-vue/blob/master/components/vc-slick/src/default-props.js#L3)

## 折叠面板
可以折叠/展开的内容区域。

### 何时使用
- 对复杂区域进行分组和隐藏，保持页面的整洁。
- ‘手风琴’ 是一种特殊的折叠面板，只允许单个内容区域展开。

### 代码演示
##### 折叠面板
可以同时展开多个面板，这个例子默认展开了第一个。

```html
<template>
  <div>
    <h-collapse v-model="activeKey">
      <h-collapse-panel key="1" header="This is panel header 1">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :disabled="false">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3" disabled>
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
      activeKey: ['1'],
    };
  },
  watch: {
    activeKey(key) {
      console.log(key);
    },
  },
};
</script>
```

##### 手风琴
手风琴，每次只打开一个 tab。

```html
<template>
  <div>
    <h-collapse accordion>
      <h-collapse-panel key="1" header="This is panel header 1">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :disabled="false">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3">
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
    };
  },
};
</script>
```

##### 面板嵌套 
嵌套折叠面板。

```html
<template>
  <div>
    <h-collapse @change="changeActivekey">
      <h-collapse-panel key="1" header="This is panel header 1">
        <h-collapse default-active-key="4">
          <h-collapse-panel key="4" header="This is panel nest panel">
            <p>{{ text }}</p>
          </h-collapse-panel>
        </h-collapse>
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :disabled="false">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3">
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
    };
  },
  methods: {
    changeActivekey(key) {
      console.log(key);
    },
  },
};
</script>
```

##### 简洁风格
一套没有边框的简洁样式。

```html
<template>
  <div>
    <h-collapse default-active-key="1" :bordered="false">
      <h-collapse-panel key="1" header="This is panel header 1">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :disabled="false">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3">
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal. Known for its loyalty and faithfulness, it can be found as a welcome guest in many households across the world.`,
    };
  },
};
</script>
```

##### 自定义面板 
自定义各个面板的背景色、圆角、边距和图标。

```html
<template>
  <div>
    <h-collapse default-active-key="1" :bordered="false">
      <template #expandIcon="props">
        <h-icon type="caret-right" :rotate="props.isActive ? 90 : 0" />
      </template>
      <h-collapse-panel key="1" header="This is panel header 1" :style="customStyle">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :style="customStyle">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3" :style="customStyle">
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
      customStyle:
        'background: #f7f7f7;border-radius: 4px;margin-bottom: 24px;border: 0;overflow: hidden',
    };
  },
};
</script>
```

##### 隐藏箭头 
你可以通过 `:showArrow="false"` 隐藏 `h-collapse-panel` 组件的箭头图标。

```html
<template>
  <div>
    <h-collapse default-active-key="1" @change="changeActivekey">
      <h-collapse-panel key="1" header="This is panel header with arrow icon">
        <p>{{ text }}</p>
      </h-collapse-panel>
      <h-collapse-panel
        key="2"
        header="This is panel header with no arrow icon"
        :show-arrow="false"
      >
        <p>{{ text }}</p>
      </h-collapse-panel>
    </h-collapse>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
    };
  },
  methods: {
    changeActivekey(key) {
      console.log(key);
    },
  },
};
</script>
```

##### 额外节点
可以同时展开多个面板，这个例子默认展开了第一个。

```html
<template>
  <div>
    <h-collapse v-model="activeKey" :expand-icon-position="expandIconPosition">
      <h-collapse-panel key="1" header="This is panel header 1">
        <p>{{ text }}</p>
        <h-icon slot="extra" type="setting" @click="handleClick" />
      </h-collapse-panel>
      <h-collapse-panel key="2" header="This is panel header 2" :disabled="false">
        <p>{{ text }}</p>
        <h-icon slot="extra" type="setting" @click="handleClick" />
      </h-collapse-panel>
      <h-collapse-panel key="3" header="This is panel header 3" disabled>
        <p>{{ text }}</p>
        <h-icon slot="extra" type="setting" @click="handleClick" />
      </h-collapse-panel>
    </h-collapse>
    <br />
    <span>Expand Icon Position: </span>
    <h-select v-model="expandIconPosition">
      <h-select-option value="left">
        left
      </h-select-option>
      <h-select-option value="right">
        right
      </h-select-option>
    </h-select>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: `A dog is a type of domesticated animal.Known for its loyalty and faithfulness,it can be found as a welcome guest in many households across the world.`,
      activeKey: ['1'],
      expandIconPosition: 'left',
    };
  },
  watch: {
    activeKey(key) {
      console.log(key);
    },
  },
  methods: {
    handleClick(event) {
      // If you don't want click extra trigger collapse, you can prevent this:
      event.stopPropagation();
    },
  },
};
</script>
```

### API 
#### Collapse 
| 参数                 | 说明                           | 类型                                                         | 默认值                                 | 版本  |
| :------------------- | :----------------------------- | :----------------------------------------------------------- | :------------------------------------- | :---- |
| activeKey(v-model)   | 当前激活 tab 面板的 key        | string[]\|string                                             | 默认无，accordion 模式下默认第一个元素 |       |
| defaultActiveKey     | 初始化选中面板的 key           | string                                                       | 无                                     |       |
| bordered             | 带边框风格的折叠面板           | boolean                                                      | `true`                                 |       |
| accordion            | 手风琴模式                     | boolean                                                      | `false`                                |       |
| expandIcon           | 自定义切换图标                 | Function(props):VNode \| slot="expandIcon" slot-scope="props"\|v-slot:expandIcon="props" |                                        |       |
| expandIconPosition   | 设置图标位置： `left`, `right` | `left`                                                       | -                                      | 1.5.0 |
| destroyInactivePanel | 销毁折叠隐藏的面板             | boolean                                                      | `false`                                |       |

#### 事件 
| 事件名称 | 说明           | 回调参数      | 版本 |
| :------- | :------------- | :------------ | :--- |
| change   | 切换面板的回调 | function(key) |      |

#### Collapse.Panel
| 参数        | 说明                                       | 类型          | 默认值 | 版本  |
| :---------- | :----------------------------------------- | :------------ | :----- | :---- |
| disabled    | 禁用后的面板展开与否将无法通过用户交互改变 | boolean       | false  |       |
| forceRender | 被隐藏时是否渲染 DOM 结构                  | boolean       | false  |       |
| header      | 面板头内容                                 | string\|slot  | 无     |       |
| key         | 对应 activeKey                             | string        | 无     |       |
| showArrow   | 是否展示当前面板上的箭头                   | boolean       | `true` |       |
| extra       | 自定义渲染每个面板右上角的内容             | VNode \| slot | -      | 1.5.0 |

## 评论
对网站内容的反馈、评价和讨论。

### 何时使用
评论组件可用于对事物的讨论，例如页面、博客文章、问题等等。

##### 基本评论
一个基本的评论组件，带有作者、头像、时间和操作。

```html
<template>
  <h-comment>
    <template slot="actions">
      <span key="comment-basic-like">
        <h-tooltip title="Like">
          <h-icon type="like" :theme="action === 'liked' ? 'filled' : 'outlined'" @click="like" />
        </h-tooltip>
        <span style="padding-left: '8px';cursor: 'auto'">
          {{ likes }}
        </span>
      </span>
      <span key="comment-basic-dislike">
        <h-tooltip title="Dislike">
          <h-icon
            type="dislike"
            :theme="action === 'disliked' ? 'filled' : 'outlined'"
            @click="dislike"
          />
        </h-tooltip>
        <span style="padding-left: '8px';cursor: 'auto'">
          {{ dislikes }}
        </span>
      </span>
      <span key="comment-basic-reply-to">Reply to</span>
    </template>
    <a slot="author">Han Solo</a>
    <h-avatar
      slot="avatar"
      src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
      alt="Han Solo"
    />
    <p slot="content">
      We supply a series of design principles, practical patterns and high quality design resources
      (Sketch and Axure), to help people create their product prototypes beautifully and
      efficiently.
    </p>
    <h-tooltip slot="datetime" :title="moment().format('YYYY-MM-DD HH:mm:ss')">
      <span>{{ moment().fromNow() }}</span>
    </h-tooltip>
  </h-comment>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
      action: null,
      moment,
    };
  },
  methods: {
    like() {
      this.likes = 1;
      this.dislikes = 0;
      this.action = 'liked';
    },
    dislike() {
      this.likes = 0;
      this.dislikes = 1;
      this.action = 'disliked';
    },
  },
};
</script>
```

##### 配合 List 组件
配合 List 组件展现评论列表。

```html
<template>
  <h-list
    class="comment-list"
    :header="`${data.length} replies`"
    item-layout="horizontal"
    :dath-source="data"
  >
    <h-list-item slot="renderItem" slot-scope="item, index">
      <h-comment :author="item.author" :avatar="item.avatar">
        <template slot="actions">
          <span v-for="action in item.actions">{{ action }}</span>
        </template>
        <p slot="content">
          {{ item.content }}
        </p>
        <h-tooltip slot="datetime" :title="item.datetime.format('YYYY-MM-DD HH:mm:ss')">
          <span>{{ item.datetime.fromNow() }}</span>
        </h-tooltip>
      </h-comment>
    </h-list-item>
  </h-list>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      data: [
        {
          actions: ['Reply to'],
          author: 'Han Solo',
          avatar: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
          content:
            'We supply a series of design principles, practical patterns and high quality design resources (Sketch and Axure), to help people create their product prototypes beautifully and efficiently.',
          datetime: moment().subtract(1, 'days'),
        },
        {
          actions: ['Reply to'],
          author: 'Han Solo',
          avatar: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
          content:
            'We supply a series of design principles, practical patterns and high quality design resources (Sketch and Axure), to help people create their product prototypes beautifully and efficiently.',
          datetime: moment().subtract(2, 'days'),
        },
      ],
      moment,
    };
  },
};
</script>
```

##### 嵌套评论 
评论可以嵌套。

```html
<template>
  <h-comment>
    <span slot="actions" key="comment-nested-reply-to">Reply to</span>
    <a slot="author">Han Solo</a>
    <h-avatar
      slot="avatar"
      src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
      alt="Han Solo"
    />
    <p slot="content">
      We supply a series of design principles, practical patterns and high quality design resources
      (Sketch and Axure).
    </p>
    <h-comment>
      <span slot="actions">Reply to</span>
      <a slot="author">Han Solo</a>
      <h-avatar
        slot="avatar"
        src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
        alt="Han Solo"
      />
      <p slot="content">
        We supply a series of design principles, practical patterns and high quality design
        resources (Sketch and Axure).
      </p>
      <h-comment>
        <span slot="actions">Reply to</span>
        <a slot="author">Han Solo</a>
        <h-avatar
          slot="avatar"
          src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
          alt="Han Solo"
        />
        <p slot="content">
          We supply a series of design principles, practical patterns and high quality design
          resources (Sketch and Axure).
        </p>
      </h-comment>
      <h-comment>
        <span slot="actions">Reply to</span>
        <a slot="author">Han Solo</a>
        <h-avatar
          slot="avatar"
          src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
          alt="Han Solo"
        />
        <p slot="content">
          We supply a series of design principles, practical patterns and high quality design
          resources (Sketch and Axure).
        </p>
      </h-comment>
    </h-comment>
  </h-comment>
</template>
```

##### 回复框 
评论编辑器组件提供了相同样式的封装以支持自定义评论编辑器。

```html
<template>
  <div>
    <h-list
      v-if="comments.length"
      :dath-source="comments"
      :header="`${comments.length} ${comments.length > 1 ? 'replies' : 'reply'}`"
      item-layout="horizontal"
    >
      <h-list-item slot="renderItem" slot-scope="item, index">
        <h-comment
          :author="item.author"
          :avatar="item.avatar"
          :content="item.content"
          :datetime="item.datetime"
        />
      </h-list-item>
    </h-list>
    <h-comment>
      <h-avatar
        slot="avatar"
        src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
        alt="Han Solo"
      />
      <div slot="content">
        <h-form-item>
          <h-textarea :rows="4" :value="value" @change="handleChange" />
        </h-form-item>
        <h-form-item>
          <h-button html-type="submit" :loading="submitting" type="primary" @click="handleSubmit">
            Add Comment
          </h-button>
        </h-form-item>
      </div>
    </h-comment>
  </div>
</template>
<script>
import moment from 'moment';
export default {
  data() {
    return {
      comments: [],
      submitting: false,
      value: '',
      moment,
    };
  },
  methods: {
    handleSubmit() {
      if (!this.value) {
        return;
      }

      this.submitting = true;

      setTimeout(() => {
        this.submitting = false;
        this.comments = [
          {
            author: 'Han Solo',
            avatar: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
            content: this.value,
            datetime: moment().fromNow(),
          },
          ...this.comments,
        ];
        this.value = '';
      }, 1000);
    },
    handleChange(e) {
      this.value = e.target.value;
    },
  },
};
</script>
```

### API 
| Property | Description                                            | Type         | Default |
| :------- | :----------------------------------------------------- | :----------- | :------ |
| actions  | 在评论内容下面呈现的操作项列表                         | Array\|slot  | -       |
| author   | 要显示为注释作者的元素                                 | string\|slot | -       |
| avatar   | 要显示为评论头像的元素 - 通常是 antd `Avatar` 或者 src | string\|slot | -       |
| content  | 评论的主要内容                                         | string\|slot | -       |
| datetime | 展示时间描述                                           | string\|slot | -       |

## 描述列表
成组展示多个只读字段。

### 何时使用
常见于详情页的信息展示。

### 代码演示
##### 基本 
简单的展示。

```html
<template>
  <h-descriptions title="User Info">
    <h-descriptions-item label="UserName">
      Zhou Maomao
    </h-descriptions-item>
    <h-descriptions-item label="Telephone">
      1810000000
    </h-descriptions-item>
    <h-descriptions-item label="Live">
      Hangzhou, Zhejiang
    </h-descriptions-item>
    <h-descriptions-item label="Remark">
      empty
    </h-descriptions-item>
    <h-descriptions-item label="Address">
      No. 18, Wantang Road, Xihu District, Hangzhou, Zhejiang, China
    </h-descriptions-item>
  </h-descriptions>
</template>
```

##### 带边框的 
```html
<template>
  <h-descriptions title="User Info" bordered>
    <h-descriptions-item label="Product">
      Cloud Database
    </h-descriptions-item>
    <h-descriptions-item label="Billing Mode">
      Prepaid
    </h-descriptions-item>
    <h-descriptions-item label="Automatic Renewal">
      YES
    </h-descriptions-item>
    <h-descriptions-item label="Order time">
      2018-04-24 18:00:00
    </h-descriptions-item>
    <h-descriptions-item label="Usage Time" :span="2">
      2019-04-24 18:00:00
    </h-descriptions-item>
    <h-descriptions-item label="Status" :span="3">
      <h-badge status="processing" text="Running" />
    </h-descriptions-item>
    <h-descriptions-item label="Negotiated Amount">
      $80.00
    </h-descriptions-item>
    <h-descriptions-item label="Discount">
      $20.00
    </h-descriptions-item>
    <h-descriptions-item label="Official Receipts">
      $60.00
    </h-descriptions-item>
    <h-descriptions-item label="Config Info">
      Data disk type: MongoDB
      <br />
      Database version: 3.4
      <br />
      Package: dds.mongo.mid
      <br />
      Storage space: 10 GB
      <br />
      Replication factor: 3
      <br />
      Region: East China 1<br />
    </h-descriptions-item>
  </h-descriptions>
</template>
```

##### 自定义尺寸 
自定义尺寸，适应在各种容器中展示。

```html
<template>
  <div>
    <h-radio-group v-model="size" @change="onChange">
      <h-radio value="default">
        default
      </h-radio>
      <h-radio value="middle">
        middle
      </h-radio>
      <h-radio value="small">
        small
      </h-radio>
    </h-radio-group>
    <br />
    <br />
    <h-descriptions bordered title="Custom Size" :size="size">
      <h-descriptions-item label="Product">
        Cloud Database
      </h-descriptions-item>
      <h-descriptions-item label="Billing">
        Prepaid
      </h-descriptions-item>
      <h-descriptions-item label="Time">
        18:00:00
      </h-descriptions-item>
      <h-descriptions-item label="Amount">
        $80.00
      </h-descriptions-item>
      <h-descriptions-item label="Discount">
        $20.00
      </h-descriptions-item>
      <h-descriptions-item label="Official">
        $60.00
      </h-descriptions-item>
      <h-descriptions-item label="Config Info">
        Data disk type: MongoDB
        <br />
        Database version: 3.4
        <br />
        Package: dds.mongo.mid
        <br />
        Storage space: 10 GB
        <br />
        Replication factor: 3
        <br />
        Region: East China 1<br />
      </h-descriptions-item>
    </h-descriptions>
    <br />
    <br />
    <h-descriptions title="Custom Size" :size="size">
      <h-descriptions-item label="Product">
        Cloud Database
      </h-descriptions-item>
      <h-descriptions-item label="Billing">
        Prepaid
      </h-descriptions-item>
      <h-descriptions-item label="Time">
        18:00:00
      </h-descriptions-item>
      <h-descriptions-item label="Amount">
        $80.00
      </h-descriptions-item>
      <h-descriptions-item label="Discount">
        $20.00
      </h-descriptions-item>
      <h-descriptions-item label="Official">
        $60.00
      </h-descriptions-item>
    </h-descriptions>
  </div>
</template>
<script>
export default {
  data() {
    return {
      size: 'default',
    };
  },
  methods: {
    onChange(e) {
      console.log('size checked', e.target.value);
      this.size = e.target.value;
    },
  },
};
</script>
```

##### 响应式 
通过响应式的配置可以实现在小屏幕设备上的完美呈现。

```html
<template>
  <div>
    <h-descriptions
      title="Responsive Descriptions"
      bordered
      :column="{ xxl: 4, xl: 3, lg: 3, md: 3, sm: 2, xs: 1 }"
    >
      <h-descriptions-item label="Product">
        Cloud Database
      </h-descriptions-item>
      <h-descriptions-item label="Billing">
        Prepaid
      </h-descriptions-item>
      <h-descriptions-item label="Time">
        18:00:00
      </h-descriptions-item>
      <h-descriptions-item label="Amount">
        $80.00
      </h-descriptions-item>
      <h-descriptions-item label="Discount">
        $20.00
      </h-descriptions-item>
      <h-descriptions-item label="Official">
        $60.00
      </h-descriptions-item>
      <h-descriptions-item label="Config Info">
        Data disk type: MongoDB
        <br />
        Database version: 3.4
        <br />
        Package: dds.mongo.mid
        <br />
        Storage space: 10 GB
        <br />
        Replication factor: 3
        <br />
        Region: East China 1
      </h-descriptions-item>
    </h-descriptions>
  </div>
</template>
```

##### 垂直 
垂直的列表。

```html
<template>
  <h-descriptions title="User Info" layout="vertical">
    <h-descriptions-item label="UserName">
      Zhou Maomao
    </h-descriptions-item>
    <h-descriptions-item label="Telephone">
      1810000000
    </h-descriptions-item>
    <h-descriptions-item label="Live">
      Hangzhou, Zhejiang
    </h-descriptions-item>
    <h-descriptions-item label="Address" span="2">
      No. 18, Wantang Road, Xihu District, Hangzhou, Zhejiang, China
    </h-descriptions-item>
    <h-descriptions-item label="Remark">
      empty
    </h-descriptions-item>
  </h-descriptions>
</template>
```

##### 垂直带边框的 
垂直带边框和背景颜色的列表。

```html
<template>
  <h-descriptions title="User Info" layout="vertical" bordered>
    <h-descriptions-item label="Product">
      Cloud Database
    </h-descriptions-item>
    <h-descriptions-item label="Billing Mode">
      Prepaid
    </h-descriptions-item>
    <h-descriptions-item label="Automatic Renewal">
      YES
    </h-descriptions-item>
    <h-descriptions-item label="Order time">
      2018-04-24 18:00:00
    </h-descriptions-item>
    <h-descriptions-item label="Usage Time" :span="2">
      2019-04-24 18:00:00
    </h-descriptions-item>
    <h-descriptions-item label="Status" :span="3">
      <h-badge status="processing" text="Running" />
    </h-descriptions-item>
    <h-descriptions-item label="Negotiated Amount">
      $80.00
    </h-descriptions-item>
    <h-descriptions-item label="Discount">
      $20.00
    </h-descriptions-item>
    <h-descriptions-item label="Official Receipts">
      $60.00
    </h-descriptions-item>
    <h-descriptions-item label="Config Info">
      Data disk type: MongoDB
      <br />
      Database version: 3.4
      <br />
      Package: dds.mongo.mid
      <br />
      Storage space: 10 GB
      <br />
      Replication factor: 3
      <br />
      Region: East China 1<br />
    </h-descriptions-item>
  </h-descriptions>
</template>
```

### API 
#### Descriptions props 
| 参数     | 说明                                                         | 类型                            | 默认值       |
| :------- | :----------------------------------------------------------- | :------------------------------ | :----------- |
| title    | 描述列表的标题，显示在最顶部                                 | string \| VNode \| v-slot:title | -            |
| bordered | 是否展示边框                                                 | boolean                         | false        |
| column   | 一行的 `DescriptionItems` 数量，可以写成像素值或支持响应式的对象写法 `{ xs: 8, sm: 16, md: 24}` | number                          | 3            |
| size     | 设置列表的大小。可以设置为 `middle` 、`small`, 或不填（只有设置 `bordered={true}` 生效） | `default | middle | small`      | `default`    |
| layout   | 描述布局                                                     | `horizontal | vertical`         | `horizontal` |
| colon    | 配置 `Descriptions.Item` 的 `colon` 的默认值                 | boolean                         | true         |

#### Item props 
| 参数  | 说明         | 类型                            | 默认值 |
| :---- | :----------- | :------------------------------ | :----- |
| label | 内容的描述   | string \| VNode \| v-slot:label | -      |
| span  | 包含列的数量 | number                          | 1      |

> span 是 Descriptions.Item 的数量。 span={2} 会占用两个 DescriptionsItem 的宽度。

## 空状态
空状态时的展示占位图。

### 何时使用
- 当目前没有数据时，用于显式的用户提示。
- 初始化场景时的引导创建流程。

### 代码演示
##### 基本 
简单的展示。

```html
<template>
  <h-empty />
</template>
```

##### 全局化配置 
自定义全局组件的 Empty 样式。

```html
<template>
  <div>
    <h-switch
      un-checked-children="default"
      checked-children="customize"
      :checked="customize"
      @change="val => (customize = val)"
    />

    <h-divider />
    <h-config-provider>
      <template v-if="customize" #renderEmpty>
        <div style="text-align: center">
          <h-icon type="smile" style="font-size: 20px" />
          <p>Data Not Found</p>
        </div>
      </template>
      <div class="config-provider">
        <h3>Select</h3>
        <h-select :style="style" :options="[]" />

        <h3>TreeSelect</h3>
        <h-tree-select :style="style" :tree-data="[]" />

        <h3>Cascader</h3>
        <h-cascader :style="style" :options="[]" :show-search="true" />

        <h3>Transfer</h3>
        <h-transfer :dath-source="[]" />

        <h3>Table</h3>
        <h-table style="margin-top: 8px" :columns="columns" :dath-source="[]" />
        <h3>List</h3>
        <h-list :dath-source="[]" />
      </div>
    </h-config-provider>
  </div>
</template>
<script>
export default {
  data() {
    return {
      customize: false,
      style: { width: '200px' },
      columns: [
        {
          title: 'Name',
          dataIndex: 'name',
          key: 'name',
        },
        {
          title: 'Age',
          dataIndex: 'age',
          key: 'age',
        },
      ],
    };
  },
};
</script>
<style>
.code-box-demo .config-provider h3 {
  font-size: inherit;
  margin: 16px 0 8px 0;
}
</style>
```

##### 自定义
自定义图片、描述、附属内容。

```html
<template>
  <h-empty
    image="https://gw.alipayobjects.com/mdn/miniapp_social/afts/img/A*pevERLJC9v0AAAAAAAAAAABjAQAAAQ/original"
    :image-style="{
      height: '60px',
    }"
  >
    <span slot="description"> Customize <a href="#API">Description</a> </span>
    <h-button type="primary">
      Create Now
    </h-button>
  </h-empty>
</template>
```

##### 无描述
无描述展示。

```html
<template>
  <h-empty :description="false" />
</template>
```

##### 选择图片
可以通过设置 `image` 为 `Empty.PRESENTED_IMAGE_SIMPLE` 选择另一种风格的图片。

```html
<template>
  <h-empty :image="simpleImage" />
</template>
<script>
import { Empty } from 'ant-design-vue';
export default {
  beforeCreate() {
    this.simpleImage = Empty.PRESENTED_IMAGE_SIMPLE;
  },
};
</script>
```

### API 
```jsx
<Empty>
  <Button>创建</Button>
</Empty>
```

| 参数        | 说明                                         | 类型             | 默认值 | 版本  |
| :---------- | :------------------------------------------- | :--------------- | :----- | :---- |
| description | 自定义描述内容                               | string \| v-slot | -      |       |
| imageStyle  | 图片样式                                     | CSSProperties    | -      | 1.5.0 |
| image       | 设置显示图片，为 string 时表示自定义图片地址 | string \| v-slot | false  |       |

### 内置图片
- Empty.PRESENTED_IMAGE_SIMPLE
- Empty.PRESENTED_IMAGE_DEFAULT

## 列表
通用列表。

### 何时使用
最基础的列表展示，可承载文字、列表、图片、段落，常用于后台数据展示页面。

### 代码演示
##### 基础列表
基础列表。

```html
<template>
  <h-list item-layout="horizontal" :dath-source="data">
    <h-list-item slot="renderItem" slot-scope="item, index">
      <h-list-item-meta
        description="Ant Design, a design language for background applications, is refined by Ant UED Team"
      >
        <a slot="title" href="https://www.antdv.com/">{{ item.title }}</a>
        <h-avatar
          slot="avatar"
          src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
        />
      </h-list-item-meta>
    </h-list-item>
  </h-list>
</template>
<script>
const data = [
  {
    title: 'Ant Design Title 1',
  },
  {
    title: 'Ant Design Title 2',
  },
  {
    title: 'Ant Design Title 3',
  },
  {
    title: 'Ant Design Title 4',
  },
];
export default {
  data() {
    return {
      data,
    };
  },
};
</script>
<style></style>
```

##### 栅格列表
可以通过设置 `List` 的 `grid` 属性来实现栅格列表，`column` 可设置期望显示的列数。

```html
<template>
  <h-list :grid="{ gutter: 16, column: 4 }" :dath-source="data">
    <h-list-item slot="renderItem" slot-scope="item, index">
      <h-card :title="item.title">
        Card content
      </h-card>
    </h-list-item>
  </h-list>
</template>
<script>
const data = [
  {
    title: 'Title 1',
  },
  {
    title: 'Title 2',
  },
  {
    title: 'Title 3',
  },
  {
    title: 'Title 4',
  },
];
export default {
  data() {
    return {
      data,
    };
  },
};
</script>
<style></style>
```

##### 加载更多
可通过 `loadMore` 属性实现加载更多功能。

```html
<template>
  <h-list
    class="demo-loadmore-list"
    :loading="loading"
    item-layout="horizontal"
    :dath-source="data"
  >
    <div
      v-if="showLoadingMore"
      slot="loadMore"
      :style="{ textAlign: 'center', marginTop: '12px', height: '32px', lineHeight: '32px' }"
    >
      <h-spin v-if="loadingMore" />
      <h-button v-else @click="onLoadMore">
        loading more
      </h-button>
    </div>
    <h-list-item slot="renderItem" slot-scope="item, index">
      <a slot="actions">edit</a>
      <a slot="actions">more</a>
      <h-list-item-meta
        description="Ant Design, a design language for background applications, is refined by Ant UED Team"
      >
        <a slot="title" href="https://www.antdv.com/">{{ item.name.last }}</a>
        <h-avatar
          slot="avatar"
          src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
        />
      </h-list-item-meta>
      <div>content</div>
    </h-list-item>
  </h-list>
</template>
<script>
import reqwest from 'reqwest';

const fakeDataUrl = 'https://randomuser.me/api/?results=5&inc=name,gender,email,nat&noinfo';

export default {
  data() {
    return {
      loading: true,
      loadingMore: false,
      showLoadingMore: true,
      data: [],
    };
  },
  mounted() {
    this.getData(res => {
      this.loading = false;
      this.data = res.results;
    });
  },
  methods: {
    getData(callback) {
      reqwest({
        url: fakeDataUrl,
        type: 'json',
        method: 'get',
        contentType: 'application/json',
        success: res => {
          callback(res);
        },
      });
    },
    onLoadMore() {
      this.loadingMore = true;
      this.getData(res => {
        this.data = this.data.concat(res.results);
        this.loadingMore = false;
        this.$nextTick(() => {
          window.dispatchEvent(new Event('resize'));
        });
      });
    },
  },
};
</script>
<style>
.demo-loadmore-list {
  min-height: 350px;
}
</style>
```

##### 响应式的栅格列表 
响应式的栅格列表。尺寸与 [Layout Grid](https://www.antdv.com/components/grid-cn/#Col) 保持一致。

```html
<template>
  <h-list :grid="{ gutter: 16, xs: 1, sm: 2, md: 4, lg: 4, xl: 6, xxl: 3 }" :dath-source="data">
    <h-list-item slot="renderItem" slot-scope="item, index">
      <h-card :title="item.title">
        Card content
      </h-card>
    </h-list-item>
  </h-list>
</template>
<script>
const data = [
  {
    title: 'Title 1',
  },
  {
    title: 'Title 2',
  },
  {
    title: 'Title 3',
  },
  {
    title: 'Title 4',
  },
  {
    title: 'Title 5',
  },
  {
    title: 'Title 6',
  },
];

export default {
  data() {
    return {
      data,
    };
  },
};
</script>
<style></style>
```

##### 简单列表 
列表拥有大、中、小三种尺寸。
通过设置 `size` 为 `large` `small` 分别把按钮设为大、小尺寸。若不设置 `size`，则尺寸为中。
可通过设置 `header` 和 `footer`，来自定义列表头部和尾部。

```html
<template>
  <div>
    <h3 :style="{ marginBottom: '16px' }">
      Default Size
    </h3>
    <h-list bordered :dath-source="data">
      <h-list-item slot="renderItem" slot-scope="item, index">
        {{ item }}
      </h-list-item>
      <div slot="header">
        Header
      </div>
      <div slot="footer">
        Footer
      </div>
    </h-list>
    <h3 :style="{ margin: '16px 0' }">
      Small Size
    </h3>
    <h-list size="small" bordered :dath-source="data">
      <h-list-item slot="renderItem" slot-scope="item, index">
        {{ item }}
      </h-list-item>
      <div slot="header">
        Header
      </div>
      <div slot="footer">
        Footer
      </div>
    </h-list>
    <h3 :style="{ margin: '16px 0' }">
      Large Size
    </h3>
    <h-list size="large" bordered :dath-source="data">
      <h-list-item slot="renderItem" slot-scope="item, index">
        {{ item }}
      </h-list-item>
      <div slot="header">
        Header
      </div>
      <div slot="footer">
        Footer
      </div>
    </h-list>
  </div>
</template>
<script>
const data = [
  'Racing car sprays burning fuel into crowd.',
  'Japanese princess to wed commoner.',
  'Australian walks 100km after outback crash.',
  'Man charged over missing wedding girl.',
  'Los Angeles battles huge wildfires.',
];

export default {
  data() {
    return {
      data,
    };
  },
};
</script>
<style></style>
```

##### 竖排列表样式
通过设置 `itemLayout` 属性为 `vertical` 可实现竖排列表样式。

```html
<template>
  <h-list item-layout="vertical" size="large" :pagination="pagination" :dath-source="listData">
    <div slot="footer"><b>ant design vue</b> footer part</div>
    <h-list-item slot="renderItem" key="item.title" slot-scope="item, index">
      <template v-for="{ type, text } in actions" slot="actions">
        <span :key="type">
          <h-icon :type="type" style="margin-right: 8px" />
          {{ text }}
        </span>
      </template>
      <img
        slot="extra"
        width="272"
        alt="logo"
        src="https://gw.alipayobjects.com/zos/rmsportal/mqaQswcyDLcXyDKnZfES.png"
      />
      <h-list-item-meta :description="item.description">
        <a slot="title" :href="item.href">{{ item.title }}</a>
        <h-avatar slot="avatar" :src="item.avatar" />
      </h-list-item-meta>
      {{ item.content }}
    </h-list-item>
  </h-list>
</template>
<script>
const listData = [];
for (let i = 0; i < 23; i++) {
  listData.push({
    href: 'https://www.antdv.com/',
    title: `ant design vue part ${i}`,
    avatar: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
    description:
      'Ant Design, a design language for background applications, is refined by Ant UED Team.',
    content:
      'We supply a series of design principles, practical patterns and high quality design resources (Sketch and Axure), to help people create their product prototypes beautifully and efficiently.',
  });
}

export default {
  data() {
    return {
      listData,
      pagination: {
        onChange: page => {
          console.log(page);
        },
        pageSize: 3,
      },
      actions: [
        { type: 'star-o', text: '156' },
        { type: 'like-o', text: '156' },
        { type: 'message', text: '2' },
      ],
    };
  },
};
</script>
<style></style>
```

##### 滚动加载
结合 [vue-infinite-scroll](https://github.com/ElemeFE/vue-infinite-scroll) 实现滚动自动加载列表。

```html
<template>
  <div
    v-infinite-scroll="handleInfiniteOnLoad"
    class="demo-infinite-container"
    :infinite-scroll-disabled="busy"
    :infinite-scroll-distance="10"
  >
    <h-list :dath-source="data">
      <h-list-item slot="renderItem" slot-scope="item, index">
        <h-list-item-meta :description="item.email">
          <a slot="title" :href="item.href">{{ item.name.last }}</a>
          <h-avatar
            slot="avatar"
            src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
          />
        </h-list-item-meta>
        <div>Content</div>
      </h-list-item>
      <div v-if="loading && !busy" class="demo-loading-container">
        <h-spin />
      </div>
    </h-list>
  </div>
</template>
<script>
import reqwest from 'reqwest';
import infiniteScroll from 'vue-infinite-scroll';
const fakeDataUrl = 'https://randomuser.me/api/?results=5&inc=name,gender,email,nat&noinfo';
export default {
  directives: { infiniteScroll },
  data() {
    return {
      data: [],
      loading: false,
      busy: false,
    };
  },
  beforeMount() {
    this.fetchData(res => {
      this.data = res.results;
    });
  },
  methods: {
    fetchData(callback) {
      reqwest({
        url: fakeDataUrl,
        type: 'json',
        method: 'get',
        contentType: 'application/json',
        success: res => {
          callback(res);
        },
      });
    },
    handleInfiniteOnLoad() {
      const data = this.data;
      this.loading = true;
      if (data.length > 14) {
        this.$message.warning('Infinite List loaded all');
        this.busy = true;
        this.loading = false;
        return;
      }
      this.fetchData(res => {
        this.data = data.concat(res.results);
        this.loading = false;
      });
    },
  },
};
</script>
<style>
.demo-infinite-container {
  border: 1px solid #e8e8e8;
  border-radius: 4px;
  overflow: auto;
  padding: 8px 24px;
  height: 300px;
}
.demo-loading-container {
  position: absolute;
  bottom: 40px;
  width: 100%;
  text-align: center;
}
</style>
```

##### 滚动加载无限长列表 
结合 [vue-virtual-scroller](https://github.com/Akryum/vue-virtual-scroller) 实现滚动加载无限长列表，带有虚拟化（[virtualization](https://blog.jscrambler.com/optimizing-react-rendering-through-virtualization/)）功能，能够提高数据量大时候长列表的性能。
可以结合 [vue-infinite-scroll](https://github.com/ElemeFE/vue-infinite-scroll) 实现滚动自动加载无限长列表。
`virtualized` 是在大数据列表中应用的一种技术，主要是为了减少不可见区域不必要的渲染从而提高性能，特别是数据量在成千上万条效果尤为明显。

```html
<template>
  <h-list>
    <RecycleScroller
      v-infinite-scroll="handleInfiniteOnLoad"
      style="height: 400px"
      :items="data"
      :item-size="73"
      key-field="email"
      :infinite-scroll-disabled="busy"
      :infinite-scroll-distance="10"
    >
      <h-list-item slot-scope="{ item }">
        <h-list-item-meta :description="item.email">
          <a slot="title" :href="item.href">{{ item.name.last }}</a>
          <h-avatar
            slot="avatar"
            src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
          />
        </h-list-item-meta>
        <div>Content {{ item.index }}</div>
      </h-list-item>
    </RecycleScroller>
    <h-spin v-if="loading" class="demo-loading" />
  </h-list>
</template>
<script>
import reqwest from 'reqwest';
import infiniteScroll from 'vue-infinite-scroll';
import { RecycleScroller } from 'vue-virtual-scroller';
import 'vue-virtual-scroller/dist/vue-virtual-scroller.css';
const fakeDataUrl = 'https://randomuser.me/api/?results=10&inc=name,gender,email,nat&noinfo';
export default {
  directives: { infiniteScroll },
  components: {
    RecycleScroller,
  },
  data() {
    return {
      data: [],
      loading: false,
      busy: false,
    };
  },
  beforeMount() {
    this.fetchData(res => {
      this.data = res.results.map((item, index) => ({ ...item, index }));
    });
  },
  methods: {
    fetchData(callback) {
      reqwest({
        url: fakeDataUrl,
        type: 'json',
        method: 'get',
        contentType: 'application/json',
        success: res => {
          callback(res);
        },
      });
    },
    handleInfiniteOnLoad() {
      const data = this.data;
      this.loading = true;
      if (data.length > 100) {
        this.$message.warning('Infinite List loaded all');
        this.busy = true;
        this.loading = false;
        return;
      }
      this.fetchData(res => {
        this.data = data.concat(res.results).map((item, index) => ({ ...item, index }));
        this.loading = false;
      });
    },
  },
};
</script>
<style>
.demo-loading {
  position: absolute;
  bottom: 40px;
  width: 100%;
  text-align: center;
}
</style>
```

### API 
#### List 
| 参数       | 说明                                                         | 类型                                                         | 默认值                | 版本    |
| :--------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------------- | :------ |
| bordered   | 是否展示边框                                                 | boolean                                                      | false                 |         |
| footer     | 列表底部                                                     | string\|slot                                                 | -                     |         |
| grid       | 列表栅格配置                                                 | object                                                       | -                     |         |
| header     | 列表头部                                                     | string\|slot                                                 | -                     |         |
| itemLayout | 设置 `List.Item` 布局, 设置成 `vertical` 则竖直样式显示, 默认横排 | string                                                       | -                     |         |
| loading    | 当卡片内容还在加载中时，可以用 `loading` 展示一个占位        | boolean\|[object](https://www.antdv.com/components/spin-cn/#API) | false                 |         |
| loadMore   | 加载更多                                                     | string\|slot                                                 | -                     |         |
| locale     | 默认文案设置，目前包括空数据文案                             | object                                                       | emptyText: '暂无数据' |         |
| pagination | 对应的 `pagination` [配置](https://www.antdv.com/components/pagination-cn/#API), 设置 `false` 不显示 | boolean\|object                                              | false                 |         |
| size       | list 的尺寸                                                  | `default`                                                    | `middle`              | `small` |
| split      | 是否展示分割线                                               | boolean                                                      | true                  |         |
| dataSource | 列表数据源                                                   | any[]                                                        | -                     | 1.5.0   |
| renderItem | 自定义`Item`函数，也可使用 slot="renderItem" 和 slot-scope="item, index" | (item, index) => vNode                                       |                       | -       |
| rowKey     | 各项 key 的取值，可以是字符串或一个函数                      | item => string\|number                                       |                       |         |

#### pagination 
分页的配置项。

| 参数     | 说明               | 类型                        | 默认值   |
| :------- | :----------------- | :-------------------------- | :------- |
| position | 指定分页显示的位置 | 'top' \| 'bottom' \| 'both' | 'bottom' |

更多配置项，请查看 [`Pagination`](https://www.antdv.com/components/pagination-cn/#API)。

#### List grid props
| 参数   | 说明                 | 类型                                     | 默认值 |
| :----- | :------------------- | :--------------------------------------- | :----- |
| column | 列数                 | number oneOf [ 1, 2, 3, 4, 6, 8, 12, 24] | -      |
| gutter | 栅格间隔             | number                                   | 0      |
| xs     | `<576px` 展示的列数  | number                                   | -      |
| sm     | `≥576px` 展示的列数  | number                                   | -      |
| md     | `≥768px` 展示的列数  | number                                   | -      |
| lg     | `≥992px` 展示的列数  | number                                   | -      |
| xl     | `≥1200px` 展示的列数 | number                                   | -      |
| xxl    | `≥1600px` 展示的列数 | number                                   | -      |

#### List.Item 
| 参数    | 说明                                                         | 类型          | 默认值 |
| :------ | :----------------------------------------------------------- | :------------ | :----- |
| actions | 列表操作组，根据 `itemLayout` 的不同, 位置在卡片底部或者最右侧 | Array<vNode>/ | slot   |
| extra   | 额外内容, 通常用在 `itemLayout` 为 `vertical` 的情况下, 展示右侧内容; `horizontal` 展示在列表元素最右侧 | string\|slot  | -      |

#### List.Item.Meta 
| 参数        | 说明               | 类型         | 默认值 |
| :---------- | :----------------- | :----------- | :----- |
| avatar      | 列表元素的图标     | slot         | -      |
| description | 列表元素的描述内容 | string\|slot | -      |
| title       | 列表元素的标题     | string\|slot | -      |

## 气泡卡片
点击/鼠标移入元素，弹出气泡式的卡片浮层。

### 何时使用
当目标元素有进一步的描述和相关操作时，可以收纳到卡片中，根据用户的操作行为进行展现。

和 `Tooltip` 的区别是，用户可以对浮层上的元素进行操作，因此它可以承载更复杂的内容，比如链接或按钮等。

### 代码演示
##### 基本 
最简单的用法，浮层的大小由内容区域决定。

```html
<template>
  <h-popover title="Title">
    <template slot="content">
      <p>Content</p>
      <p>Content</p>
    </template>
    <h-button type="primary">
      Hover me
    </h-button>
  </h-popover>
</template>
```

##### 从浮层内关闭 
使用 `visible` 属性控制浮层显示。

```html
<template>
  <h-popover v-model="visible" title="Title" trigger="click">
    <a slot="content" @click="hide">Close</a>
    <h-button type="primary">
      Click me
    </h-button>
  </h-popover>
</template>

<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    hide() {
      console.log(111);
      this.visible = false;
    },
  },
};
</script>
```

##### 三种触发方式
鼠标移入、聚集、点击。

```html
<template>
  <div>
    <h-popover title="Title" trigger="hover">
      <template slot="content">
        <p>Content</p>
        <p>Content</p>
      </template>
      <h-button type="primary">
        Hover me
      </h-button>
    </h-popover>
    <h-popover title="Title" trigger="focus">
      <template slot="content">
        <p>Content</p>
        <p>Content</p>
      </template>
      <h-button type="primary">
        Focus me
      </h-button>
    </h-popover>
    <h-popover title="Title" trigger="click">
      <template slot="content">
        <p>Content</p>
        <p>Content</p>
      </template>
      <h-button type="primary">
        Click me
      </h-button>
    </h-popover>
  </div>
</template>
```

##### 箭头指向 
设置了 `arrowPointAtCenter` 后，箭头将指向目标元素的中心。

```html
<template>
  <div>
    <h-popover placement="topLeft">
      <template slot="content">
        <p>Content</p>
        <p>Content</p>
      </template>
      <span slot="title">Title</span>
      <h-button>Align edge / 边缘对齐</h-button>
    </h-popover>
    <h-popover placement="topLeft" arrow-point-at-center>
      <template slot="content">
        <p>Content</p>
        <p>Content</p>
      </template>
      <span slot="title">Title</span>
      <h-button>Arrow points to center / 箭头指向中心</h-button>
    </h-popover>
  </div>
</template>
```

##### 位置 
位置有十二个方向。

```html
<template>
  <div id="components-popover-demo-placement">
    <div :style="{ marginLeft: `${buttonWidth}px`, whiteSpace: 'nowrap' }">
      <h-popover placement="topLeft">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>TL</h-button>
      </h-popover>
      <h-popover placement="top">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>Top</h-button>
      </h-popover>
      <h-popover placement="topRight">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>TR</h-button>
      </h-popover>
    </div>
    <div :style="{ width: `${buttonWidth}px`, float: 'left' }">
      <h-popover placement="leftTop">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>LT</h-button>
      </h-popover>
      <h-popover placement="left">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>Left</h-button>
      </h-popover>
      <h-popover placement="leftBottom">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>LB</h-button>
      </h-popover>
    </div>
    <div :style="{ width: `${buttonWidth}px`, marginLeft: `${buttonWidth * 4 + 24}px` }">
      <h-popover placement="rightTop">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>RT</h-button>
      </h-popover>
      <h-popover placement="right">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>Right</h-button>
      </h-popover>
      <h-popover placement="rightBottom">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>RB</h-button>
      </h-popover>
    </div>
    <div :style="{ marginLeft: `${buttonWidth}px`, clear: 'both', whiteSpace: 'nowrap' }">
      <h-popover placement="bottomLeft">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>BL</h-button>
      </h-popover>
      <h-popover placement="bottom">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>Bottom</h-button>
      </h-popover>
      <h-popover placement="bottomRight">
        <template slot="content">
          <p>Content</p>
          <p>Content</p>
        </template>
        <template slot="title">
          <span>Title</span>
        </template>
        <h-button>BR</h-button>
      </h-popover>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      buttonWidth: 70,
    };
  },
};
</script>
<style>
#components-popover-demo-placement .ant-btn {
  width: 70px;
  text-align: center;
  padding: 0;
  margin-right: 8px;
  margin-bottom: 8px;
}
</style>
```

##### 悬停点击弹出窗口 
以下示例显示如何创建可悬停和单击的弹出窗口。

```html
<template>
  <h-popover
    title="Hover title"
    trigger="hover"
    :visible="hovered"
    @visibleChange="handleHoverChange"
  >
    <div slot="content">
      This is hover content.
    </div>
    <h-popover
      title="Click title"
      trigger="click"
      :visible="clicked"
      @visibleChange="handleClickChange"
    >
      <div slot="content">
        <div>This is click content.</div>
        <a @click="hide">Close</a>
      </div>
      <h-button>Hover and click / 悬停并单击</h-button>
    </h-popover>
  </h-popover>
</template>
<script>
export default {
  data() {
    return {
      clicked: false,
      hovered: false,
    };
  },
  methods: {
    hide() {
      this.clicked = false;
      this.hovered = false;
    },
    handleHoverChange(visible) {
      this.clicked = false;
      this.hovered = visible;
    },
    handleClickChange(visible) {
      this.clicked = visible;
      this.hovered = false;
    },
  },
};
</script>
```

### API 
| 参数    | 说明     | 类型                | 默认值 |
| :------ | :------- | :------------------ | :----- |
| content | 卡片内容 | string\|slot\|VNode | 无     |
| title   | 卡片标题 | string\|slot\|VNode | 无     |

更多属性请参考 [Tooltip](https://1x.antdv.com/components/tooltip-cn/#API)。

### 注意 
请确保 `Popover` 的子元素能接受 `mouseenter`、`mouseleave`、`focus`、`click` 事件。

## 统计数值
展示统计数值。

### 何时使用
- 当需要突出某个或某组数字时
- 当需要展示带描述的统计类数据时使用

### 代码演示
##### 基本 
简单展示

```html
<template>
  <div>
    <h-statistic title="Active Users" :value="112893" style="margin-right: 50px" />
    <h-statistic title="Account Balance (CNY)" :precision="2" :value="112893" />
  </div>
</template>
```

##### 在卡片中使用
在卡片中展示统计数值。

```html
<template>
  <div style="background: #ECECEC; padding: 30px">
    <h-row :gutter="16">
      <h-col :span="12">
        <h-card>
          <h-statistic
            title="Feedback"
            :value="11.28"
            :precision="2"
            suffix="%"
            :value-style="{ color: '#3f8600' }"
            style="margin-right: 50px"
          >
            <template #prefix>
              <h-icon type="arrow-up" />
            </template>
          </h-statistic>
        </h-card>
      </h-col>
      <h-col :span="12">
        <h-card>
          <h-statistic
            title="Idle"
            :value="9.3"
            :precision="2"
            suffix="%"
            class="demo-class"
            :value-style="{ color: '#cf1322' }"
          >
            <template #prefix>
              <h-icon type="arrow-down" />
            </template>
          </h-statistic>
        </h-card>
      </h-col>
    </h-row>
  </div>
</template>
```

##### 单位
通过前缀和后缀添加单位。

```html
<template>
  <h-row :gutter="16">
    <h-col :span="12">
      <h-statistic title="Feedback" :value="1128" style="margin-right: 50px">
        <template #suffix>
          <h-icon type="like" />
        </template>
      </h-statistic>
    </h-col>
    <h-col :span="12">
      <h-statistic title="Unmerged" :value="93" class="demo-class">
        <template #suffix>
          <span> / 100</span>
        </template>
      </h-statistic>
    </h-col>
  </h-row>
</template>
```

##### 倒计时 
倒计时组件。

```html
<template>
  <h-row :gutter="16">
    <h-col :span="12">
      <h-statistic-countdown
        title="Countdown"
        :value="deadline"
        style="margin-right: 50px"
        @finish="onFinish"
      />
    </h-col>
    <h-col :span="12">
      <h-statistic-countdown
        title="Million Seconds"
        :value="deadline"
        format="HH:mm:ss:SSS"
        style="margin-right: 50px"
      />
    </h-col>
    <h-col :span="24" style="margin-top: 32px;">
      <h-statistic-countdown title="Day Level" :value="deadline" format="D 天 H 时 m 分 s 秒" />
    </h-col>
  </h-row>
</template>
<script>
export default {
  data() {
    return {
      deadline: Date.now() + 1000 * 60 * 60 * 24 * 2 + 1000 * 30,
    };
  },
  methods: {
    onFinish() {
      console.log('finished!');
    },
  },
};
</script>
```

### API 
#### Statistic
| 参数             | 说明             | 类型                            | 默认值 |
| :--------------- | :--------------- | :------------------------------ | :----- |
| decimalSeparator | 设置小数点       | string                          | .      |
| formatter        | 自定义数值展示   | v-slot \| ({h, value}) => VNode | -      |
| groupSeparator   | 设置千分位标识符 | string                          | ,      |
| precision        | 数值精度         | number                          | -      |
| prefix           | 设置数值的前缀   | string \| v-slot                | -      |
| suffix           | 设置数值的后缀   | string \| v-slot                | -      |
| title            | 数值的标题       | string \| v-slot                | -      |
| value            | 数值内容         | string \| number                | -      |
| valueStyle       | 设置数值的样式   | style                           | -      |

#### Statistic.Countdown 
| 参数       | 说明                                                  | 类型             | 默认值     |
| :--------- | :---------------------------------------------------- | :--------------- | :--------- |
| format     | 格式化倒计时展示，参考 [moment](http://momentjs.com/) | string           | 'HH:mm:ss' |
| prefix     | 设置数值的前缀                                        | string \| v-slot | -          |
| suffix     | 设置数值的后缀                                        | string \| v-slot | -          |
| title      | 数值的标题                                            | string \| v-slot | -          |
| value      | 数值内容                                              | number \| moment | -          |
| valueStyle | 设置数值的样式                                        | style            | -          |

##### Statistic.Countdown 事件 
| 事件名称 | 说明             | 回调参数   |
| :------- | :--------------- | :--------- |
| finish   | 倒计时完成时触发 | () => void |

## 标签页
选项卡切换组件。

### 何时使用
提供平级的区域将大块内容进行收纳和展现，保持界面整洁。

Ant Design 依次提供了三级选项卡，分别用于不同的场景。

- 卡片式的页签，提供可关闭的样式，常用于容器顶部。
- 标准线条式页签，用于容器内部的主功能切换，这是最常用的 Tabs。
- [RadioButton](https://1x.antdv.com/ant-design/components/radio-cn/) 可作为更次级的页签来使用。

### 代码演示
##### 基本用法 
默认选中第一项。

```html
<template>
  <div>
    <h-tabs default-active-key="1" @change="callback">
      <h-tab-pane key="1" tab="Tab 1">
        Content of Tab Pane 1
      </h-tab-pane>
      <h-tab-pane key="2" tab="Tab 2" force-render>
        Content of Tab Pane 2
      </h-tab-pane>
      <h-tab-pane key="3" tab="Tab 3">
        Content of Tab Pane 3
      </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    callback(key) {
      console.log(key);
    },
  },
};
</script>
```

##### 禁用
禁用某一项。

```html
<template>
  <h-tabs default-active-key="1">
    <h-tab-pane key="1" tab="Tab 1">
      Tab 1
    </h-tab-pane>
    <h-tab-pane key="2" tab="Tab 2" disabled>
      Tab 2
    </h-tab-pane>
    <h-tab-pane key="3" tab="Tab 3">
      Tab 3
    </h-tab-pane>
  </h-tabs>
</template>
```

##### 图标 
有图标的标签。

```html
<template>
  <h-tabs default-active-key="2">
    <h-tab-pane key="1">
      <span slot="tab">
        <h-icon type="apple" />
        Tab 1
      </span>
      Tab 1
    </h-tab-pane>
    <h-tab-pane key="2">
      <span slot="tab">
        <h-icon type="android" />
        Tab 2
      </span>
      Tab 2
    </h-tab-pane>
  </h-tabs>
</template>
```

##### 滑动 
可以左右、上下滑动，容纳更多标签。

```html
<template>
  <div style="width: 500px">
    <h-radio-group v-model="mode" :style="{ marginBottom: '8px' }">
      <h-radio-button value="top">
        Horizontal
      </h-radio-button>
      <h-radio-button value="left">
        Vertical
      </h-radio-button>
    </h-radio-group>
    <h-tabs
      default-active-key="1"
      :tab-position="mode"
      :style="{ height: '200px' }"
      @prevClick="callback"
      @nextClick="callback"
    >
      <h-tab-pane v-for="i in 30" :key="i" :tab="`Tab-${i}`"> Content of tab {{ i }} </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    return {
      mode: 'top',
    };
  },
  methods: {
    callback(val) {
      console.log(val);
    },
  },
};
</script>
```

##### 附加内容 
可以在页签右边添加附加操作。

```html
<template>
  <h-tabs>
    <h-tab-pane key="1" tab="Tab 1">
      Content of tab 1
    </h-tab-pane>
    <h-tab-pane key="2" tab="Tab 2">
      Content of tab 2
    </h-tab-pane>
    <h-tab-pane key="3" tab="Tab 3">
      Content of tab 3
    </h-tab-pane>
    <h-button slot="tabBarExtraContent">
      Extra Action
    </h-button>
  </h-tabs>
</template>
```

##### 大小 
大号页签用在页头区域，小号用在弹出框等较狭窄的容器内。

```html
<template>
  <div>
    <h-radio-group v-model="size" style="margin-bottom: 16px">
      <h-radio-button value="small">
        Small
      </h-radio-button>
      <h-radio-button value="default">
        Default
      </h-radio-button>
      <h-radio-button value="large">
        Large
      </h-radio-button>
    </h-radio-group>
    <h-tabs default-active-key="2" :size="size">
      <h-tab-pane key="1" tab="Tab 1">
        Content of tab 1
      </h-tab-pane>
      <h-tab-pane key="2" tab="Tab 2">
        Content of tab 2
      </h-tab-pane>
      <h-tab-pane key="3" tab="Tab 3">
        Content of tab 3
      </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    return {
      size: 'small',
    };
  },
};
</script>
```

##### 位置
有四个位置，`tabPosition="left|right|top|bottom"`。

```html
<template>
  <div style="width: 500px">
    <h-radio-group v-model="tabPosition" style="margin:8px">
      <h-radio-button value="top">
        top
      </h-radio-button>
      <h-radio-button value="bottom">
        bottom
      </h-radio-button>
      <h-radio-button value="left">
        left
      </h-radio-button>
      <h-radio-button value="right">
        right
      </h-radio-button>
    </h-radio-group>
    <h-tabs default-active-key="1" :tab-position="tabPosition">
      <h-tab-pane key="1" tab="Tab 1">
        Content of Tab 1
      </h-tab-pane>
      <h-tab-pane key="2" tab="Tab 2">
        Content of Tab 2
      </h-tab-pane>
      <h-tab-pane key="3" tab="Tab 3">
        Content of Tab 3
      </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tabPosition: 'top',
    };
  },
  methods: {
    callback(val) {
      console.log(val);
    },
  },
};
</script>
```

##### 卡片式页签 
另一种样式的页签，不提供对应的垂直样式。

```html
<template>
  <h-tabs type="card" @change="callback">
    <h-tab-pane key="1" tab="Tab 1">
      Content of Tab Pane 1
    </h-tab-pane>
    <h-tab-pane key="2" tab="Tab 2">
      Content of Tab Pane 2
    </h-tab-pane>
    <h-tab-pane key="3" tab="Tab 3">
      Content of Tab Pane 3
    </h-tab-pane>
  </h-tabs>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    callback(key) {
      console.log(key);
    },
  },
};
</script>
```

##### 新增和关闭页签
只有卡片样式的页签支持新增和关闭选项。
使用 `closable={false}` 禁止关闭。

```html
<template>
  <h-tabs v-model="activeKey" type="editable-card" @edit="onEdit">
    <h-tab-pane v-for="pane in panes" :key="pane.key" :tab="pane.title" :closable="pane.closable">
      {{ pane.content }}
    </h-tab-pane>
  </h-tabs>
</template>
<script>
export default {
  data() {
    const panes = [
      { title: 'Tab 1', content: 'Content of Tab 1', key: '1' },
      { title: 'Tab 2', content: 'Content of Tab 2', key: '2' },
      { title: 'Tab 3', content: 'Content of Tab 3', key: '3', closable: false },
    ];
    return {
      activeKey: panes[0].key,
      panes,
      newTabIndex: 0,
    };
  },
  methods: {
    callback(key) {
      console.log(key);
    },
    onEdit(targetKey, action) {
      this[action](targetKey);
    },
    add() {
      const panes = this.panes;
      const activeKey = `newTab${this.newTabIndex++}`;
      panes.push({ title: 'New Tab', content: 'Content of new Tab', key: activeKey });
      this.panes = panes;
      this.activeKey = activeKey;
    },
    remove(targetKey) {
      let activeKey = this.activeKey;
      let lastIndex;
      this.panes.forEach((pane, i) => {
        if (pane.key === targetKey) {
          lastIndex = i - 1;
        }
      });
      const panes = this.panes.filter(pane => pane.key !== targetKey);
      if (panes.length && activeKey === targetKey) {
        if (lastIndex >= 0) {
          activeKey = panes[lastIndex].key;
        } else {
          activeKey = panes[0].key;
        }
      }
      this.panes = panes;
      this.activeKey = activeKey;
    },
  },
};
</script>
```

##### 卡片式页签容器
用于容器顶部，需要一点额外的样式覆盖。

```html
<template>
  <div class="card-container">
    <h-tabs type="card">
      <h-tab-pane key="1" tab="Tab Title 1">
        <p>Content of Tab Pane 1</p>
        <p>Content of Tab Pane 1</p>
        <p>Content of Tab Pane 1</p>
      </h-tab-pane>
      <h-tab-pane key="2" tab="Tab Title 2">
        <p>Content of Tab Pane 2</p>
        <p>Content of Tab Pane 2</p>
        <p>Content of Tab Pane 2</p>
      </h-tab-pane>
      <h-tab-pane key="3" tab="Tab Title 3">
        <p>Content of Tab Pane 3</p>
        <p>Content of Tab Pane 3</p>
        <p>Content of Tab Pane 3</p>
      </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    callback(key) {
      console.log(key);
    },
  },
};
</script>
<style>
.card-container {
  background: #f5f5f5;
  overflow: hidden;
  padding: 24px;
}
.card-container > .ant-tabs-card > .ant-tabs-content {
  height: 120px;
  margin-top: -16px;
}

.card-container > .ant-tabs-card > .ant-tabs-content > .ant-tabs-tabpane {
  background: #fff;
  padding: 16px;
}

.card-container > .ant-tabs-card > .ant-tabs-bar {
  border-color: #fff;
}

.card-container > .ant-tabs-card > .ant-tabs-bar .ant-tabs-tab {
  border-color: transparent;
  background: transparent;
}

.card-container > .ant-tabs-card > .ant-tabs-bar .ant-tabs-tab-active {
  border-color: #fff;
  background: #fff;
}
</style>
```

##### 自定义新增页签触发器
隐藏默认的页签增加图标，给自定义触[#](https://1x.antdv.com/components/tabs-cn/#Tabs.TabPane)发器绑定事件。

```html
<template>
  <div>
    <div :style="{ marginBottom: '16px' }">
      <h-button @click="add">
        ADD
      </h-button>
    </div>
    <h-tabs v-model="activeKey" hide-add type="editable-card" @edit="onEdit">
      <h-tab-pane v-for="pane in panes" :key="pane.key" :tab="pane.title" :closable="pane.closable">
        {{ pane.content }}
      </h-tab-pane>
    </h-tabs>
  </div>
</template>
<script>
export default {
  data() {
    const panes = [
      { title: 'Tab 1', content: 'Content of Tab 1', key: '1' },
      { title: 'Tab 2', content: 'Content of Tab 2', key: '2' },
    ];
    return {
      activeKey: panes[0].key,
      panes,
      newTabIndex: 0,
    };
  },
  methods: {
    callback(key) {
      console.log(key);
    },
    onEdit(targetKey, action) {
      this[action](targetKey);
    },
    add() {
      const panes = this.panes;
      const activeKey = `newTab${this.newTabIndex++}`;
      panes.push({
        title: `New Tab ${activeKey}`,
        content: `Content of new Tab ${activeKey}`,
        key: activeKey,
      });
      this.panes = panes;
      this.activeKey = activeKey;
    },
    remove(targetKey) {
      let activeKey = this.activeKey;
      let lastIndex;
      this.panes.forEach((pane, i) => {
        if (pane.key === targetKey) {
          lastIndex = i - 1;
        }
      });
      const panes = this.panes.filter(pane => pane.key !== targetKey);
      if (panes.length && activeKey === targetKey) {
        if (lastIndex >= 0) {
          activeKey = panes[lastIndex].key;
        } else {
          activeKey = panes[0].key;
        }
      }
      this.panes = panes;
      this.activeKey = activeKey;
    },
  },
};
</script>
```

### API 
#### Tabs 
| 参数               | 说明                                                      | 类型                                         | 默认值                          |
| :----------------- | :-------------------------------------------------------- | :------------------------------------------- | :------------------------------ |
| activeKey(v-model) | 当前激活 tab 面板的 key                                   | string                                       | 无                              |
| animated           | 是否使用动画切换 Tabs，在 `tabPosition=top|bottom` 时有效 | boolean \| {inkBar:boolean, tabPane:boolean} | true, 当 type="card" 时为 false |
| defaultActiveKey   | 初始化选中面板的 key，如果没有设置 activeKey              | string                                       | 第一个面板                      |
| hideAdd            | 是否隐藏加号图标，在 `type="editable-card"` 时有效        | boolean                                      | false                           |
| size               | 大小，提供 `large` `default` 和 `small` 三种大小          | string                                       | 'default'                       |
| tabBarExtraContent | tab bar 上额外的元素                                      | slot                                         | 无                              |
| tabBarStyle        | tab bar 的样式对象                                        | object                                       | -                               |
| tabPosition        | 页签位置，可选值有 `top` `right` `bottom` `left`          | string                                       | 'top'                           |
| type               | 页签的基本样式，可选 `line`、`card` `editable-card` 类型  | string                                       | 'line'                          |
| tabBarGutter       | tabs 之间的间隙                                           | number                                       | 无                              |

#### 事件 
| 事件名称  | 说明                                                   | 回调参数                  |
| :-------- | :----------------------------------------------------- | :------------------------ |
| change    | 切换面板的回调                                         | Function(activeKey) {}    |
| edit      | 新增和删除页签的回调，在 `type="editable-card"` 时有效 | (targetKey, action): void |
| nextClick | next 按钮被点击的回调                                  | Function                  |
| prevClick | prev 按钮被点击的回调                                  | Function                  |
| tabClick  | tab 被点击的回调                                       | Function                  |

#### Tabs.TabPane 
| 参数        | 说明                      | 类型         | 默认值 |
| :---------- | :------------------------ | :----------- | :----- |
| forceRender | 被隐藏时是否渲染 DOM 结构 | boolean      | false  |
| key         | 对应 activeKey            | string       | 无     |
| tab         | 选项卡头显示文字          | string\|slot | 无     |

## 标签
进行标记和分类的小标签。

### 何时使用
- 用于标记事物的属性和维度。
- 进行分类。

### 代码演示
##### 基本用法
基本标签的用法，可以通过添加 `closable` 变为可关闭标签。可关闭标签具有 `close` 两个事件。

```html
<template>
  <div>
    <h-tag>Tag 1</h-tag>
    <h-tag><a href="https://github.com/vueComponent/ant-design">Link</a></h-tag>
    <h-tag closable @close="log">
      Tag 2
    </h-tag>
    <h-tag closable @close="preventDefault">
      Prevent Default
    </h-tag>
  </div>
</template>
<script>
export default {
  methods: {
    log(e) {
      console.log(e);
    },
    preventDefault(e) {
      e.preventDefault();
      console.log('Clicked! But prevent default.');
    },
  },
};
</script>
```

##### 多彩标签 
我们添加了多种预设色彩的标签样式，用作不同场景使用。如果预设值不能满足你的需求，可以设置为具体的色值。

```html
<template>
  <div>
    <h4 style="margin-bottom: 16px">
      Presets:
    </h4>
    <div>
      <h-tag color="pink">
        pink
      </h-tag>
      <h-tag color="red">
        red
      </h-tag>
      <h-tag color="orange">
        orange
      </h-tag>
      <h-tag color="green">
        green
      </h-tag>
      <h-tag color="cyan">
        cyan
      </h-tag>
      <h-tag color="blue">
        blue
      </h-tag>
      <h-tag color="purple">
        purple
      </h-tag>
    </div>
    <h4 style="margin: '16px 0'">
      Custom:
    </h4>
    <div>
      <h-tag color="#f50">
        #f50
      </h-tag>
      <h-tag color="#2db7f5">
        #2db7f5
      </h-tag>
      <h-tag color="#87d068">
        #87d068
      </h-tag>
      <h-tag color="#108ee9">
        #108ee9
      </h-tag>
    </div>
  </div>
</template>
```

##### 热门标签
选择你感兴趣的话题。

```html
<template>
  <div>
    <span :style="{ marginRight: 8 }">Categories:</span>
    <template v-for="tag in tags">
      <h-checkable-tag
        :key="tag"
        :checked="selectedTags.indexOf(tag) > -1"
        @change="checked => handleChange(tag, checked)"
      >
        {{ tag }}
      </h-checkable-tag>
    </template>
  </div>
</template>
<script>
export default {
  data() {
    return {
      checked1: false,
      checked2: false,
      checked3: false,
      tags: ['Movies', 'Books', 'Music', 'Sports'],
      selectedTags: [],
    };
  },
  methods: {
    handleChange(tag, checked) {
      const { selectedTags } = this;
      const nextSelectedTags = checked
        ? [...selectedTags, tag]
        : selectedTags.filter(t => t !== tag);
      console.log('You are interested in: ', nextSelectedTags);
      this.selectedTags = nextSelectedTags;
    },
  },
};
</script>
```

##### 可选择 
可通过 `CheckableTag` 实现类似 Checkbox 的效果，点击切换选中效果。

> 该组件为完全受控组件，不支持非受控用法。

```html
<template>
  <div>
    <h-checkable-tag v-model="checked1" @change="handleChange">
      Tag1
    </h-checkable-tag>
    <h-checkable-tag v-model="checked2" @change="handleChange">
      Tag2
    </h-checkable-tag>
    <h-checkable-tag v-model="checked3" @change="handleChange">
      Tag3
    </h-checkable-tag>
  </div>
</template>
<script>
export default {
  data() {
    return {
      checked1: false,
      checked2: false,
      checked3: false,
    };
  },
  methods: {
    handleChange(checked) {
      console.log(checked);
    },
  },
};
</script>
```

##### 动态添加和删除 
用数组生成一组标签，可以动态添加和删除。

```html
<template>
  <div>
    <template v-for="(tag, index) in tags">
      <h-tooltip v-if="tag.length > 20" :key="tag" :title="tag">
        <h-tag :key="tag" :closable="index !== 0" @close="() => handleClose(tag)">
          {{ `${tag.slice(0, 20)}...` }}
        </h-tag>
      </h-tooltip>
      <h-tag v-else :key="tag" :closable="index !== 0" @close="() => handleClose(tag)">
        {{ tag }}
      </h-tag>
    </template>
    <h-input
      v-if="inputVisible"
      ref="input"
      type="text"
      size="small"
      :style="{ width: '78px' }"
      :value="inputValue"
      @change="handleInputChange"
      @blur="handleInputConfirm"
      @keyup.enter="handleInputConfirm"
    />
    <h-tag v-else style="background: #fff; borderStyle: dashed;" @click="showInput">
      <h-icon type="plus" /> New Tag
    </h-tag>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tags: ['Unremovable', 'Tag 2', 'Tag 3Tag 3Tag 3Tag 3Tag 3Tag 3Tag 3'],
      inputVisible: false,
      inputValue: '',
    };
  },
  methods: {
    handleClose(removedTag) {
      const tags = this.tags.filter(tag => tag !== removedTag);
      console.log(tags);
      this.tags = tags;
    },

    showInput() {
      this.inputVisible = true;
      this.$nextTick(function() {
        this.$refs.input.focus();
      });
    },

    handleInputChange(e) {
      this.inputValue = e.target.value;
    },

    handleInputConfirm() {
      const inputValue = this.inputValue;
      let tags = this.tags;
      if (inputValue && tags.indexOf(inputValue) === -1) {
        tags = [...tags, inputValue];
      }
      console.log(tags);
      Object.assign(this, {
        tags,
        inputVisible: false,
        inputValue: '',
      });
    },
  },
};
</script>
```

##### 控制关闭状态 
通过 `visible` 属性控制关闭状态。

```html
<template>
  <div>
    <h-tag v-model="visible" closable>
      Movies
    </h-tag>
    <br />
    <h-button size="small" @click="visible = !visible">
      Toggle
    </h-button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: true,
    };
  },
};
</script>
```

### API 
#### Tag 
| 参数             | 说明                                                         | 类型       | 默认值 |
| :--------------- | :----------------------------------------------------------- | :--------- | :----- |
| afterClose       | 关闭动画完成后的回调，请使用 `close` 事件, 我们将在下个版本删除此项 | () => void | -      |
| afterClose       | 关闭动画完成后的回调                                         | () => void | -      |
| closable         | 标签是否可以关闭                                             | boolean    | false  |
| color            | 标签色                                                       | string     | -      |
| visible(v-model) | 是否显示标签                                                 | boolean    | `true` |

#### 事件
| 事件名称 | 说明         | 回调参数    |
| :------- | :----------- | :---------- |
| close    | 关闭时的回调 | (e) => void |

#### Tag.CheckableTag 
| 参数             | 说明               | 类型    | 默认值 |
| :--------------- | :----------------- | :------ | :----- |
| checked(v-model) | 设置标签的选中状态 | boolean | false  |

#### 事件 
| 事件名称 | 说明                 | 回调参数          |
| :------- | :------------------- | :---------------- |
| change   | 点击标签时触发的回调 | (checked) => void |

## 时间轴
垂直展示的时间流信息。

### 何时使用
- 当有一系列信息需按时间排列时，可正序和倒序。

- 需要有一条时间轴进行视觉上的串联时。

### 代码演示
##### 基本用法
基本的时间轴。

```html
<template>
  <h-timeline>
    <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
    <h-timeline-item>Solve initial network problems 2015-09-01</h-timeline-item>
    <h-timeline-item>Technical testing 2015-09-01</h-timeline-item>
    <h-timeline-item>Network problems being solved 2015-09-01</h-timeline-item>
  </h-timeline>
</template>
```

##### 最后一个及排序
当任务状态正在发生，还在记录过程中，可用幽灵节点来表示当前的时间节点，当 pending 为真值时展示幽灵节点，如果 pending 是 React 元素可用于定制该节点内容，同时 pendingDot 将可以用于定制其轴点。reverse 属性用于控制节点排序，为 false 时按正序排列，为 true 时按倒序排列。

```html
<template>
  <div>
    <h-timeline pending="Recording..." :reverse="reverse">
      <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
      <h-timeline-item>Solve initial network problems 2015-09-01</h-timeline-item>
      <h-timeline-item>Technical testing 2015-09-01</h-timeline-item>
    </h-timeline>
    <h-button type="primary" style="margin-top: 16px" @click="handleClick">
      Toggle Reverse
    </h-button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      reverse: false,
    };
  },
  methods: {
    handleClick() {
      this.reverse = !this.reverse;
    },
  },
};
</script>
```

##### 交替展现 
内容在时间轴两侧轮流出现。

```html
<template>
  <h-timeline mode="alternate">
    <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
    <h-timeline-item color="green">
      Solve initial network problems 2015-09-01
    </h-timeline-item>
    <h-timeline-item>
      <h-icon slot="dot" type="clock-circle-o" style="font-size: 16px;" />
      Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque
      laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto
      beatae vitae dicta sunt explicabo.[#](https://1x.antdv.com/components/timeline-cn/#Timeline.Item)
    </h-timeline-item>
    <h-timeline-item color="red">
      Network problems being solved 2015-09-01
    </h-timeline-item>
    <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
    <h-timeline-item>
      <h-icon slot="dot" type="clock-circle-o" style="font-size: 16px;" />
      Technical testing 2015-09-01
    </h-timeline-item>
  </h-timeline>
</template>
```

##### 圆圈颜色
圆圈颜色，绿色用于已完成、成功状态，红色表示告警或错误状态，蓝色可表示正在进行或其他默认状态。

```html
<template>
  <h-timeline>
    <h-timeline-item color="green">
      Create a services site 2015-09-01
    </h-timeline-item>
    <h-timeline-item color="green">
      Create a services site 2015-09-01
    </h-timeline-item>
    <h-timeline-item color="red">
      <p>Solve initial network problems 1</p>
      <p>Solve initial network problems 2</p>
      <p>Solve initial network problems 3 2015-09-01</p>
    </h-timeline-item>
    <h-timeline-item>
      <p>Technical testing 1</p>
      <p>Technical testing 2</p>
      <p>Technical testing 3 2015-09-01</p>
    </h-timeline-item>
    <h-timeline-item color="gray">
      <p>Technical testing 1</p>
      <p>Technical testing 2</p>
      <p>Technical testing 3 2015-09-01</p>
    </h-timeline-item>
    <h-timeline-item color="gray">
      <p>Technical testing 1</p>
      <p>Technical testing 2</p>
      <p>Technical testing 3 2015-09-01</p>
    </h-timeline-item>
  </h-timeline>
</template>
```

##### 自定义时间轴点 
基本的时间轴。

```html
<template>
  <h-timeline>
    <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
    <h-timeline-item>Solve initial network problems 2015-09-01</h-timeline-item>
    <h-timeline-item color="red">
      <h-icon slot="dot" type="clock-circle-o" style="font-size: 16px;" />
      Technical testing 2015-09-01
    </h-timeline-item>
    <h-timeline-item>Network problems being solved 2015-09-01</h-timeline-item>
  </h-timeline>
</template>
```

##### 右侧时间轴点
时间轴点可以在内容的右边。

```html
<template>
  <h-timeline mode="right">
    <h-timeline-item>Create a services site 2015-09-01</h-timeline-item>
    <h-timeline-item>Solve initial network problems 2015-09-01</h-timeline-item>
    <h-timeline-item>
      <h-icon slot="dot" type="clock-circle-o" style="font-size: 16px;" />
      Technical testing 2015-09-01
    </h-timeline-item>
    <h-timeline-item>Network problems being solved 2015-09-01</h-timeline-item>
  </h-timeline>
</template>
```

### API 
```html
<h-timeline>
  <h-timeline-item>创建服务现场 2015-09-01</h-timeline-item>
  <h-timeline-item>初步排除网络异常 2015-09-01</h-timeline-item>
  <h-timeline-item>技术测试异常 2015-09-01</h-timeline-item>
  <h-timeline-item>网络异常正在修复 2015-09-01</h-timeline-item>
</h-timeline>
```

#### Timeline 
时间轴。

| 参数       | 说明                                           | 类型                  | 默认值                    |
| :--------- | :--------------------------------------------- | :-------------------- | :------------------------ |
| pending    | 指定最后一个幽灵节点是否存在或内容             | boolean\|string\|slot | false                     |
| pendingDot | 当最后一个幽灵节点存在時，指定其时间图点       | string\|slot          | `<Icon type="loading" />` |
| reverse    | 节点排序                                       | boolean               | false                     |
| mode       | 通过设置 `mode` 可以改变时间轴和内容的相对位置 | `left`                | `alternate`               |

#### Timeline.Item 
时间轴的每一个节点。

| 参数     | 说明                                            | 类型         | 默认值  | 版本 |
| :------- | :---------------------------------------------- | :----------- | :------ | :--- |
| color    | 指定圆圈颜色 `blue, red, green`，或自定义的色值 | string       | blue    |      |
| dot      | 自定义时间轴点                                  | string\|slot | -       |      |
| position | 自定义节点位置                                  | `left`       | `right` | -    |

## 文字提示
简单的文字提示气泡框。

### 何时使用
鼠标移入则显示提示，移出消失，气泡浮层不承载复杂文本和操作。

可用来代替系统默认的 ‘title’ 提示，提供一个’按钮/文字/操作’的文案解释。

### 代码演示
##### 基本 
最简单的用法。

```html
<template>
  <h-tooltip>
    <template slot="title">
      prompt text
    </template>
    Tooltip will show when mouse enter.
  </h-tooltip>
</template>
```

##### 箭头指向
设置了 `arrowPointAtCenter` 后，箭头将指向目标元素的中心。

```html
<template>
  <div>
    <h-tooltip placement="topLeft" title="Prompt Text">
      <h-button>Align edge / 边缘对齐</h-button>
    </h-tooltip>
    <h-tooltip placement="topLeft" title="Prompt Text" arrow-point-at-center>
      <h-button>Arrow points to center / 箭头指向中心</h-button>
    </h-tooltip>
  </div>
</template>
```

##### 位置 
位置有 12 个方向。

```html
<template>
  <div id="components-h-tooltip-demo-placement">
    <div :style="{ marginLeft: `${buttonWidth}px`, whiteSpace: 'nowrap' }">
      <h-tooltip placement="topLeft">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>TL</h-button>
      </h-tooltip>
      <h-tooltip placement="top">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>Top</h-button>
      </h-tooltip>
      <h-tooltip placement="topRight">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>TR</h-button>
      </h-tooltip>
    </div>
    <div :style="{ width: `${buttonWidth}px`, float: 'left' }">
      <h-tooltip placement="leftTop">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>LT</h-button>
      </h-tooltip>
      <h-tooltip placement="left">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>Left</h-button>
      </h-tooltip>
      <h-tooltip placement="leftBottom">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>LB</h-button>
      </h-tooltip>
    </div>
    <div :style="{ width: `${buttonWidth}px`, marginLeft: `${buttonWidth * 4 + 24}px` }">
      <h-tooltip placement="rightTop">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>RT</h-button>
      </h-tooltip>
      <h-tooltip placement="right">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>Right</h-button>
      </h-tooltip>
      <h-tooltip placement="rightBottom">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>RB</h-button>
      </h-tooltip>
    </div>
    <div :style="{ marginLeft: `${buttonWidth}px`, clear: 'both', whiteSpace: 'nowrap' }">
      <h-tooltip placement="bottomLeft">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>BL</h-button>
      </h-tooltip>
      <h-tooltip placement="bottom">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>Bottom</h-button>
      </h-tooltip>
      <h-tooltip placement="bottomRight">
        <template slot="title">
          <span>prompt text</span>
        </template>
        <h-button>BR</h-button>
      </h-tooltip>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      buttonWidth: 70,
    };
  },
};
</script>
<style scoped>
#components-h-tooltip-demo-placement .ant-btn {
  width: 70px;
  text-align: center;
  padding: 0;
  margin-right: 8px;
  margin-bottom: 8px;
}
</style>
```

##### 自动调整位置 
气泡框不可见时自动调整位置

```html
<template>
  <div :style="wrapStyles">
    <h-tooltip placement="left" title="Prompt Text" :get-popup-containe[#](https://1x.antdv.com/components/tooltip-cn/#注意)r="getPopupContainer">
      <h-button>Adjust automatically / 自动调整</h-button>
    </h-tooltip>
    <br />
    <h-tooltip
      style="marginTop: 10px"
      placement="left"
      title="Prompt Text"
      :get-popup-container="getPopupContainer"
      :auto-adjust-overflow="false"
    >
      <h-button>Ingore / 不处理</h-button>
    </h-tooltip>
  </div>
</template>
<script>
const wrapStyles = {
  overflow: 'hidden',
  position: 'relative',
  padding: '24px',
  border: '1px solid #e9e9e9',
};
export default {
  data() {
    return {
      wrapStyles,
    };
  },
  methods: {
    getPopupContainer(trigger) {
      return trigger.parentElement;
    },
  },
};
</script>
```

### API 
| 参数  | 说明     | 类型         | 默认值 |
| :---- | :------- | :----------- | :----- |
| title | 提示文字 | string\|slot | 无     |

#### 共同的 API 
以下 API 为 Tooltip、Popconfirm、Popover 共享的 API。

| 参数                 | 说明                                                         | 类型                  | 默认值              |
| :------------------- | :----------------------------------------------------------- | :-------------------- | :------------------ |
| arrowPointAtCenter   | 箭头是否指向目标元素中心                                     | boolean               | `false`             |
| autoAdjustOverflow   | 气泡被遮挡时自动调整位置                                     | boolean               | `true`              |
| defaultVisible       | 默认是否显隐                                                 | boolean               | false               |
| getPopupContainer    | 浮层渲染父节点，默认渲染到 body 上                           | Function(triggerNode) | () => document.body |
| mouseEnterDelay      | 鼠标移入后延时多少才显示 Tooltip，单位：秒                   | number                | 0                   |
| mouseLeaveDelay      | 鼠标移出后延时多少才隐藏 Tooltip，单位：秒                   | number                | 0.1                 |
| overlayClassName     | 卡片类名                                                     | string                | 无                  |
| overlayStyle         | 卡片样式                                                     | object                | 无                  |
| placement            | 气泡框位置，可选 `top` `left` `right` `bottom` `topLeft` `topRight` `bottomLeft` `bottomRight` `leftTop` `leftBottom` `rightTop` `rightBottom` | string                | top                 |
| trigger              | 触发行为，可选 `hover/focus/click/contextmenu`               | string                | hover               |
| visible(v-model)     | 用于手动控制浮层显隐                                         | boolean               | false               |
| destroyTooltipOnHide | 隐藏后是否销毁 tooltip                                       | boolean               | false               |
| align                | 该值将合并到 placement 的配置中，设置参考 [dom-align](https://github.com/yiminghe/dom-align) | Object                | 无                  |

#### 事件 
| 事件名称      | 说明           | 回调参数          |
| :------------ | :------------- | :---------------- |
| visibleChange | 显示隐藏的回调 | (visible) => void |

### 注意 
请确保 `Tooltip` 的子元素能接受 `mouseenter`、`mouseleave`、`focus`、`click` 事件。

## 警告提示
警告提示，展现需要关注的信息。

### 何时使用
- 当某个页面需要向用户显示警告的信息时。

- 非浮层的静态展现形式，始终展现，不会自动消失，用户可以点击关闭。

### 代码演示
##### 顶部公告
页面顶部通告形式，默认有图标且`type` 为 'warning'。

```html
<template>
  <div>
    <h-alert message="Warning text" banner />
    <br />
    <h-alert
      message="Very long warning text warning text text text text text text text"
      banner
      closable
    />
    <br />
    <h-alert :show-icon="false" message="Warning text without icon" banner />
    <br />
    <h-alert type="error" message="Error text" banner />
  </div>
</template>
```

##### 可关闭的警告提示 
显示关闭按钮，点击可关闭警告提示。

```html
<template>
  <div>
    <h-alert
      message="Warning Text Warning Text Warning TextW arning Text Warning Text Warning TextWarning Text"
      type="warning"
      closable
      @close="onClose"
    />
    <h-alert
      message="Error Text"
      description="Error Description Error Description Error Description Error Description Error Description Error Description"
      type="error"
      closable
      @close="onClose"
    />
  </div>
</template>
<script>
export default {
  methods: {
    onClose(e) {
      console.log(e, 'I was closed.');
    },
  },
};
</script>
```

##### 含有辅助性文字介绍
含有辅助性文字介绍的警告提示。

```html
<template>
  <div>
    <h-alert message="Success Text" type="success">
      <p slot="description">
        Success Description <span style="color: red">Success</span> Description Success Description
      </p>
    </h-alert>
    <h-alert
      message="Info Text"
      description="Info Description Info Description Info Description Info Description"
      type="info"
    />
    <h-alert
      message="Warning Text"
      description="Warning Description Warning Description Warning Description Warning Description"
      type="warning"
    />
    <h-alert
      message="Error Text"
      description="Error Description Error Description Error Description Error Description"
      type="error"
    />
  </div>
</template>
```

##### 四种样式
共有四种样式 `success`、`info`、`warning`、`error`。

```html
<template>
  <div>
    <h-alert message="Success Text" type="success" />
    <h-alert message="Info Text" type="info" />
    <h-alert message="Warning Text" type="warning" />
    <h-alert message="Error Text" type="error" />
  </div>
</template>
```

##### 基本 
最简单的用法，适用于简短的警告提示。

```html
<template>
  <h-alert message="Success Text" type="success" />
</template>
```

##### 自定义关闭
可以自定义关闭，自定义的文字会替换原先的关闭 `Icon`。

```html
<template>
  <h-alert message="Info Text" type="info" close-text="Close Now" />
</template>
```

##### 图标 
可口的图标让信息类型更加醒目。

```html
<template>
  <div>
    <h-alert message="Success Tips" type="success" show-icon />
    <h-alert message="Informational Notes" type="info" show-icon />
    <h-alert message="Warning" type="warning" show-icon />
    <h-alert message="Error" type="error" show-icon />
    <h-alert
      message="Success Tips"
      description="Detailed description and advices about successful copywriting."
      type="success"
      show-icon
    />
    <h-alert
      message="Informational Notes"
      description="Additional description and informations about copywriting."
      type="info"
      show-icon
    />
    <h-alert
      message="Warning"
      description="This is a warning notice about copywriting."
      type="warning"
      show-icon
    />
    <h-alert
      message="Error"
      description="This is an error message about copywriting."
      type="error"
      show-icon
    />
  </div>
</template>
```

##### 平滑地卸载 
平滑、自然的卸载提示。

```html
<template>
  <div>
    <h-alert
      v-if="visible"
      message="Alert Message Text"
      type="success"
      closable
      :after-close="handleClose"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: true,
    };
  },
  methods: {
    handleClose() {
      this.visible = false;
    },
  },
};
</script>
```

### API 
| 参数        | 说明                                                         | 类型          | 默认值                                    | 版本 |
| :---------- | :----------------------------------------------------------- | :------------ | :---------------------------------------- | :--- |
| afterClose  | 关闭动画结束后触发的回调函数                                 | () => void    | -                                         | -    |
| banner      | 是否用作顶部公告                                             | boolean       | false                                     | -    |
| closable    | 默认不显示关闭按钮                                           | boolean       | 无                                        | -    |
| closeText   | 自定义关闭按钮                                               | string\|slot  | 无                                        | -    |
| description | 警告提示的辅助性文字介绍                                     | string\|slot  | 无                                        | -    |
| icon        | 自定义图标，`showIcon` 为 `true` 时有效                      | vnode \| slot | -                                         | -    |
| message     | 警告提示内容                                                 | string\|slot  | 无                                        | -    |
| showIcon    | 是否显示辅助图标                                             | boolean       | false，`banner` 模式下默认值为 true       | -    |
| type        | 指定警告提示的样式，有四种选择 `success`、`info`、`warning`、`error` | string        | `info`，`banner` 模式下默认值为 `warning` | -    |

#### 事件 
| 事件名称 | 说明                 | 回调参数                | 版本 |
| :------- | :------------------- | :---------------------- | :--- |
| close    | 关闭时触发的回调函数 | (e: MouseEvent) => void | -    |

## 抽屉
屏幕边缘滑出的浮层面板。

### 何时使用
抽屉从父窗体边缘滑入，覆盖住部分父窗体内容。用户在抽屉内操作时不必离开当前任务，操作完成后，可以平滑地回到到原任务。

- 当需要一个附加的面板来控制父窗体内容，这个面板在需要时呼出。比如，控制界面展示样式，往界面中添加内容。
- 当需要在当前任务流中插入临时任务，创建或预览附加内容。比如展示协议条款，创建子对象。

### 代码演示
##### 基础抽屉
基础抽屉，点击触发按钮抽屉从右滑出，点击遮罩区关闭

```html
<template>
  <div>
    <h-button type="primary" @click="showDrawer">
      Open
    </h-button>
    <h-drawer
      title="Basic Drawer"
      placement="right"
      :closable="false"
      :visible="visible"
      :after-visible-change="afterVisibleChange"
      @close="onClose"
    >
      <p>Some contents...</p>
      <p>Some contents...</p>
      <p>Some contents...</p>
    </h-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    afterVisibleChange(val) {
      console.log('visible', val);
    },
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
  },
};
</script>
```

##### 抽屉表单
在抽屉中使用表单。

```html
<template>
  <div>
    <h-button type="primary" @click="showDrawer"> <h-icon type="plus" /> New account </h-button>
    <h-drawer
      title="Create a new account"
      :width="720"
      :visible="visible"
      :body-style="{ paddingBottom: '80px' }"
      @close="onClose"
    >
      <h-form :form="form" layout="vertical" hide-required-mark>
        <h-row :gutter="16">
          <h-col :span="12">
            <h-form-item label="Name">
              <h-input
                v-decorator="[
                  'name',
                  {
                    rules: [{ required: true, message: 'Please enter user name' }],
                  },
                ]"
                placeholder="Please enter user name"
              />
            </h-form-item>
          </h-col>
          <h-col :span="12">
            <h-form-item label="Url">
              <h-input
                v-decorator="[
                  'url',
                  {
                    rules: [{ required: true, message: 'please enter url' }],
                  },
                ]"
                style="width: 100%"
                addon-before="http://"
                addon-after=".com"
                placeholder="please enter url"
              />
            </h-form-item>
          </h-col>
        </h-row>
        <h-row :gutter="16">
          <h-col :span="12">
            <h-form-item label="Owner">
              <h-select
                v-decorator="[
                  'owner',
                  {
                    rules: [{ required: true, message: 'Please select an owner' }],
                  },
                ]"
                placeholder="Please h-s an owner"
              >
                <h-select-option value="xiao">
                  Xiaoxiao Fu
                </h-select-option>
                <h-select-option value="mao">
                  Maomao Zhou
                </h-select-option>
              </h-select>
            </h-form-item>
          </h-col>
          <h-col :span="12">
            <h-form-item label="Type">
              <h-select
                v-decorator="[
                  'type',
                  {
                    rules: [{ required: true, message: 'Please choose the type' }],
                  },
                ]"
                placeholder="Please choose the type"
              >
                <h-select-option value="private">
                  Private
                </h-select-option>
                <h-select-option value="public">
                  Public
                </h-select-option>
              </h-select>
            </h-form-item>
          </h-col>
        </h-row>
        <h-row :gutter="16">
          <h-col :span="12">
            <h-form-item label="Approver">
              <h-select
                v-decorator="[
                  'approver',
                  {
                    rules: [{ required: true, message: 'Please choose the approver' }],
                  },
                ]"
                placeholder="Please choose the approver"
              >
                <h-select-option value="jack">
                  Jack Ma
                </h-select-option>
                <h-select-option value="tom">
                  Tom Liu
                </h-select-option>
              </h-select>
            </h-form-item>
          </h-col>
          <h-col :span="12">
            <h-form-item label="DateTime">
              <h-date-picker
                v-decorator="[
                  'dateTime',
                  {
                    rules: [{ required: true, message: 'Please choose the dateTime' }],
                  },
                ]"
                style="width: 100%"
                :get-popup-container="trigger => trigger.parentNode"
              />
            </h-form-item>
          </h-col>
        </h-row>
        <h-row :gutter="16">
          <h-col :span="24">
            <h-form-item label="Description">
              <h-textarea
                v-decorator="[
                  'description',
                  {
                    rules: [{ required: true, message: 'Please enter url description' }],
                  },
                ]"
                :rows="4"
                placeholder="please enter url description"
              />
            </h-form-item>
          </h-col>
        </h-row>
      </h-form>
      <div
        :style="{
          position: 'absolute',
          right: 0,
          bottom: 0,
          width: '100%',
          borderTop: '1px solid #e9e9e9',
          padding: '10px 16px',
          background: '#fff',
          textAlign: 'right',
          zIndex: 1,
        }"
      >
        <h-button :style="{ marginRight: '8px' }" @click="onClose">
          Cancel
        </h-button>
        <h-button type="primary" @click="onClose">
          Submit
        </h-button>
      </div>
    </h-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      form: this.$form.createForm(this),
      visible: false,
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
  },
};
</script>
```

##### 多层抽屉
在抽屉内打开新的抽屉，用以解决多分支任务的复杂状况。

```html
<template>
  <div>
    <h-button type="primary" @click="showDrawer">
      Open
    </h-button>
    <h-drawer
      title="Multi-level drawer"
      width="520"
      :closable="false"
      :visible="visible"
      @close="onClose"
    >
      <h-button type="primary" @click="showChildrenDrawer">
        Two-level drawer
      </h-button>
      <h-drawer
        title="Two-level Drawer"
        width="320"
        :closable="false"
        :visible="childrenDrawer"
        @close="onChildrenDrawerClose"
      >
        <h-button type="primary" @click="showChildrenDrawer">
          This is two-level drawer
        </h-button>
      </h-drawer>
      <div
        :style="{
          position: 'absolute',
          bottom: 0,
          width: '100%',
          borderTop: '1px solid #e8e8e8',
          padding: '10px 16px',
          textAlign: 'right',
          left: 0,
          background: '#fff',
          borderRadius: '0 0 4px 4px',
        }"
      >
        <h-button style="marginRight: 8px" @click="onClose">
          Cancel
        </h-button>
        <h-button type="primary" @click="onClose">
          Submit
        </h-button>
      </div>
    </h-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false,
      childrenDrawer: false,
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
    showChildrenDrawer() {
      this.childrenDrawer = true;
    },
    onChildrenDrawerClose() {
      this.childrenDrawer = false;
    },
  },
};
</script>
```

##### 自定义位置
自定义位置，点击触发按钮抽屉从相应的位置滑出，点击遮罩区关闭

```html
<template>
  <div>
    <h-radio-group style="margin-right: 8px" :default-value="placement" @change="onChange">
      <h-radio value="top">
        top
      </h-radio>
      <h-radio value="right">
        right
      </h-radio>
      <h-radio value="bottom">
        bottom
      </h-radio>
      <h-radio value="left">
        left
      </h-radio>
    </h-radio-group>
    <h-button type="primary" @click="showDrawer">
      Open
    </h-button>
    <h-drawer
      title="Basic Drawer"
      :placement="placement"
      :closable="false"
      :visible="visible"
      @close="onClose"
    >
      <p>Some contents...</p>
      <p>Some contents...</p>
      <p>Some contents...</p>
    </h-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false,
      placement: 'left',
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
    onChange(e) {
      this.placement = e.target.value;
    },
  },
};
</script>
```

##### 信息预览抽屉 
需要快速预览对象概要时使用，点击遮罩区关闭。

```html
<template>
  <div>
    <h-list
      :dath-source="[
        {
          name: 'Lily',
        },
        {
          name: 'Lily',
        },
      ]"
      bordered
    >
      <h-list-item slot="renderItem" :key="`h-${item.id}`" slot-scope="item, index">
        <a slot="actions" @click="showDrawer">View Profile</a>
        <h-list-item-meta description="Progresser XTech">
          <a slot="title" href="https://www.antdv.com/">{{ item.name }}</a>
          <h-avatar
            slot="avatar"
            src="https://gw.alipayobjects.com/zos/rmsportal/BiazfanxmamNRoxxVxka.png"
          />
        </h-list-item-meta>
      </h-list-item>
    </h-list>
    <h-drawer width="640" placement="right" :closable="false" :visible="visible" @close="onClose">
      <p :style="[pStyle, pStyle2]">
        User Profile
      </p>
      <p :style="pStyle">
        Personal
      </p>
      <h-row>
        <h-col :span="12">
          <description-item title="Full Name" content="Lily" />
        </h-col>
        <h-col :span="12">
          <description-item title="Account" content="AntDesign@example.com" />
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="12">
          <description-item title="City" content="HangZhou" />
        </h-col>
        <h-col :span="12">
          <description-item title="Country" content="China🇨🇳" />
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="12">
          <description-item title="Birthday" content="February 2,1900" />
        </h-col>
        <h-col :span="12">
          <description-item title="Website" content="-" />
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="12">
          <description-item
            title="Message"
            content="Make things as simple as possible but no simpler."
          />
        </h-col>
      </h-row>
      <h-divider />
      <p :style="pStyle">
        Company
      </p>
      <h-row>
        <h-col :span="12">
          <description-item title="Position" content="Programmer" />
        </h-col>
        <h-col :span="12">
          <description-item title="Responsibilities" content="Coding" />
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="12">
          <description-item title="Department" content="XTech" />
        </h-col>
        <h-col :span="12">
          <description-item title="Supervisor">
            <a slot="content">Lin</a>
          </description-item>
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="24">
          <description-item
            title="Skills"
            content="C / C + +, data structures, software engineering, operating systems, computer networks, databases, compiler theory, computer architecture, Microcomputer Principle and Interface Technology, Computer English, Java, ASP, etc."
          />
        </h-col>
      </h-row>
      <h-divider />
      <p :style="pStyle">
        Contacts
      </p>
      <h-row>
        <h-col :span="12">
          <description-item title="Email" content="ant-design-vue@example.com" />
        </h-col>
        <h-col :span="12">
          <description-item title="Phone Number" content="+86 181 0000 0000" />
        </h-col>
      </h-row>
      <h-row>
        <h-col :span="24">
          <description-item title="Github">
            <a slot="content" href="https://github.com/vueComponent/ant-design-vue">
              github.com/vueComponent/ant-design-vue
            </a>
          </description-item>
        </h-col>
      </h-row>
    </h-drawer>
  </div>
</template>
<script>
import descriptionItem from './descriptionItem';

export default {
  components: {
    descriptionItem,
  },
  data() {
    return {
      visible: false,
      pStyle: {
        fontSize: '16px',
        color: 'rgba(0,0,0,0.85)',
        lineHeight: '24px',
        display: 'block',
        marginBottom: '16px',
      },
      pStyle2: {
        marginBottom: '24px',
      },
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
  },
};
</script>
```

##### 渲染在当前 DOM 
渲染在当前 dom 里。自定义容器，查看 getContainer。

```html
<template>
  <div
    :style="{
      height: '200px',
      overflow: 'hidden',
      position: 'relative',
      border: '1px solid #ebedf0',
      borderRadius: '2px',
      padding: '48px',
      textAlign: 'center',
      background: '#fafafa',
    }"
  >
    Render in this
    <div style="margin-top: 16px">
      <h-button type="primary" @click="showDrawer">
        Open
      </h-button>
    </div>
    <h-drawer
      title="Basic Drawer"
      placement="right"
      :closable="false"
      :visible="visible"
      :get-container="false"
      :wrap-style="{ position: 'absolute' }"
      @close="onClose"
    >
      <p>Some contents...</p>
    </h-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    afterVisibleChange(val) {
      console.log('visible', val);
    },
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
  },
};
</script>
```

### API 
| 参数               | 说明                                                         | 类型                                            | 默认值  | 版本   |
| :----------------- | :----------------------------------------------------------- | :---------------------------------------------- | :------ | :----- |
| closable           | 是否显示右上角的关闭按钮                                     | boolean                                         | true    |        |
| destroyOnClose     | 关闭时销毁 Drawer 里的子元素                                 | boolean                                         | false   |        |
| getContainer       | 指定 Drawer 挂载的 HTML 节点                                 | HTMLElement \| `() => HTMLElement` \| Selectors | 'body'  |        |
| maskClosable       | 点击蒙层是否允许关闭                                         | boolean                                         | true    |        |
| mask               | 是否展示遮罩                                                 | Boolean                                         | true    |        |
| maskStyle          | 遮罩样式                                                     | object                                          | {}      |        |
| title              | 标题                                                         | string \| slot                                  | -       |        |
| visible            | Drawer 是否可见                                              | boolean                                         | -       |        |
| wrapClassName      | 对话框外层容器的类名                                         | string                                          | -       |        |
| wrapStyle          | 可用于设置 Drawer 最外层容器的样式，和 `drawerStyle` 的区别是作用节点包括 `mask` | object                                          | -       |        |
| drawerStyle        | 用于设置 Drawer 弹出层的样式                                 | object                                          | -       | 1.4.11 |
| headerStyle        | 用于设置 Drawer 头部的样式                                   | object                                          | -       | 1.5.0  |
| bodyStyle          | 可用于设置 Drawer 内容部分的样式                             | object                                          | -       |        |
| width              | 宽度                                                         | string \| number                                | 256     |        |
| height             | 高度, 在 `placement` 为 `top` 或 `bottom` 时使用             | string \| number                                | 256     |        |
| zIndex             | 设置 Drawer 的 `z-index`                                     | Number                                          | 1000    |        |
| placement          | 抽屉的方向                                                   | 'top' \| 'right' \| 'bottom' \| 'left'          | 'right' |        |
| handle             | 设置后抽屉直接挂载到 DOM 上，你可以通过该 handle 控制抽屉打开关闭 | VNode \| slot                                   | -       |        |
| afterVisibleChange | 切换抽屉时动画结束后的回调                                   | function(visible)                               | 无      | 1.5.0  |
| keyboard           | 是否支持键盘 esc 关闭                                        | boolean                                         | true    | 1.5.0  |

### 方法 
| 名称  | 描述                                 | 类型        | 默认值 | 版本 |
| :---- | :----------------------------------- | :---------- | :----- | :--- |
| close | 点击遮罩层或右上角叉或取消按钮的回调 | function(e) | 无     |      |

## 全局提示
全局展示操作反馈信息。

### 何时使用
- 可提供成功、警告和错误等反馈信息。
- 顶部居中显示并自动消失，是一种不打断用户操作的轻量级提示方式。

### 代码演示
##### 普通提示 
信息提醒反馈。

```html
<template>
  <h-button type="primary" @click="info">
    Display normal message
  </h-button>
</template>
<script>
export default {
  methods: {
    info() {
      this.$message.info('This is a normal message');
    },
  },
};
</script>
```

##### 加载中 
进行全局 loading，异步自行移除。

```html
<template>
  <h-button @click="success">
    Display a loading indicator
  </h-button>
</template>
<script>
export default {
  methods: {
    success() {
      const hide = this.$message.loading('Action in progress..', 0);
      setTimeout(hide, 2500);
    },
  },
};
</script>
```

##### Promise 接口 
可以通过 then 接口在关闭后运行 callback 。以上用例将在每个 message 将要结束时通过 then 显示新的 message 。

```html
<template>
  <h-button @click="success">
    Display a sequence of message
  </h-button>
</template>
<script>
export default {
  methods: {
    success() {
      this.$message
        .loading('Action in progress..', 2.5)
        .then(() => this.$message.success('Loading finished', 2.5))
        .then(() => this.$message.info('Loading finished is finished', 2.5));
    },
  },
};
</script>
```

##### 修改延时
自定义时长 `10s`，默认时长为 `3s`。

```html
<template>
  <h-button @click="success">
    Customized display duration
  </h-button>
</template>
<script>
export default {
  methods: {
    success() {
      this.$message.success(
        'This is a prompt message for success, and it will disappear in 10 seconds',
        10,
      );
    },
  },
};
</script>
```

##### 其他提示类型 
包括成功、失败、警告。

```html
<template>
  <div>
    <h-button @click="success">
      Success
    </h-button>
    <h-button @click="error">
      Error
    </h-button>
    <h-button @click="warning">
      Warning
    </h-button>
  </div>
</template>
<script>
export default {
  methods: {
    success() {
      this.$message.success('This is a success message');
    },
    error() {
      this.$message.error('This is an error message');
    },
    warning() {
      this.$message.warning('This is a warning message');
    },
  },
};
</script>
```

##### 更新消息内容
可以通过唯一的 `key` 来更新内容。

```html
<template>
  <h-button type="primary" @click="openMessage">
    Open the message box
  </h-button>
</template>
<script>
const key = 'updatable';
export default {
  methods: {
    openMessage() {
      this.$message.loading({ content: 'Loading...', key });
      setTimeout(() => {
        this.$message.success({ content: 'Loaded!', key, duration: 2 });
      }, 1000);
    },
  },
};
</script>
```

### API 
组件提供了一些静态方法，使用方式和参数如下：

- `message.success(content, [duration], onClose)`
- `message.error(content, [duration], onClose)`
- `message.info(content, [duration], onClose)`
- `message.warning(content, [duration], onClose)`
- `message.warn(content, [duration], onClose)` // alias of warning
- `message.loading(content, [duration], onClose)`

| 参数     | 说明                                          | 类型                          | 默认值 |
| :------- | :-------------------------------------------- | :---------------------------- | :----- |
| content  | 提示内容                                      | string\| VNode \|(h) => VNode | -      |
| duration | 自动关闭的延时，单位秒。设为 0 时不自动关闭。 | number                        | 3      |
| onClose  | 关闭时触发的回调函数                          | Function                      | -      |

组件同时提供 promise 接口

- `message[level](content, [duration]).then(afterClose)`
- `message[level](content, [duration], onClose).then(afterClose)`

其中`message[level]` 是组件已经提供的静态方法。`then` 接口返回值是 Promise 。

也可以对象的形式传递参数：

- `message.open(config)`
- `message.success(config)`
- `message.error(config)`
- `message.info(config)`
- `message.warning(config)`
- `message.warn(config)` // alias of warning
- `message.loading(config)`

| 参数     | 说明                                          | 类型                          | 默认值 | 版本  |
| :------- | :-------------------------------------------- | :---------------------------- | :----- | :---- |
| content  | 提示内容                                      | string\| VNode \|(h) => VNode | -      |       |
| duration | 自动关闭的延时，单位秒。设为 0 时不自动关闭。 | number                        | 3      |       |
| onClose  | 关闭时触发的回调函数                          | Function                      | -      |       |
| icon     | 自定义图标                                    | string\| VNode \|(h) => VNode | -      |       |
| key      | 当前提示的唯一标志                            | string\|number                | -      | 1.5.0 |

#### 全局方法
还提供了全局配置和全局销毁方法：

- `message.config(options)`
- `message.destroy()`

##### message.config 
```js
message.config({
  top: `100px`,
  duration: 2,
  maxCount: 3,
});
```

| 参数         | 说明                                           | 类型              | 默认值              |
| :----------- | :--------------------------------------------- | :---------------- | :------------------ |
| duration     | 默认自动关闭延时，单位秒                       | number            | 3                   |
| getContainer | 配置渲染节点的输出位置                         | () => HTMLElement | () => document.body |
| maxCount     | 最大显示数, 超过限制时，最早的消息会被自动关闭 | number            | -                   |
| top          | 消息距离顶部的位置                             | string            | `24px`              |

## 通知提醒框
全局展示通知提醒信息。

### 何时使用
在系统四个角显示通知提醒信息。经常用于以下情况：

- 较为复杂的通知内容。
- 带有交互的通知，给出用户下一步的行动点。
- 系统主动推送。

### 代码演示
##### 基本
最简单的用法，4.5 秒后自动关闭。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
export default {
  methods: {
    openNotification() {
      this.$notification.open({
        message: 'Notification Title',
        description:
          'This is the content of the notification. This is the content of the notification. This is the content of the notification.',
        onClick: () => {
          console.log('Notification Clicked!');
        },
      });
    },
  },
};
</script>
```

##### 自定义样式 
使用 style 和 className 来定义样式。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
export default {
  methods: {
    openNotification() {
      this.$notification.open({
        message: 'Notification Title',
        description:
          'This is the content of the notification. This is the content of the notification. This is the content of the notification.',
        style: {
          width: '600px',
          marginLeft: `${335 - 600}px`,
        },
      });
    },
  },
};
</script>
```

##### 位置
可以设置通知从右上角、右下角、左下角、左上角弹出。

```html
<template>
  <div>
    <h-button type="primary" @click="openNotification('topLeft')">
      <h-icon type="radius-upleft" />
      topLeft
    </h-button>
    <h-button type="primary" @click="openNotification('topRight')">
      <h-icon type="radius-upright" />
      topRight
    </h-button>
    <h-divider />
    <h-button type="primary" @click="openNotification('bottomLeft')">
      <h-icon type="radius-bottomleft" />
      bottomLeft
    </h-button>
    <h-button type="primary" @click="openNotification('bottomRight')">
      <h-icon type="radius-bottomright" />
      bottomRight
    </h-button>
  </div>
</template>
<script>
export default {
  methods: {
    openNotification(placement) {
      this.$notification.open({
        message: `Notification ${placement}`,
        description:
          'This is the content of the notification. This is the content of the notification. This is the content of the notification.',
        placement,
      });
    },
  },
};
</script>
```

##### 带有图标的通知提醒框 
通知提醒框左侧有图标。

```html
<template>
  <div>
    <h-button @click="() => openNotificationWithIcon('success')">
      Success
    </h-button>
    <h-button @click="() => openNotificationWithIcon('info')">
      Info
    </h-button>
    <h-button @click="() => openNotificationWithIcon('warning')">
      Warning
    </h-button>
    <h-button @click="() => openNotificationWithIcon('error')">
      Error
    </h-button>
  </div>
</template>
<script>
export default {
  methods: {
    openNotificationWithIcon(type) {
      this.$notification[type]({
        message: 'Notification Title',
        description:
          'This is the content of the notification. This is the content of the notification. This is the content of the notification.',
      });
    },
  },
};
</script>
```

##### 自定义图标
图标可以被自定义。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
export default {
  methods: {
    openNotification() {
      this.$notification.open({
        message: 'Notification Title',
        description:
          'This is the content of the notification. This is the content of the notification. This is the content of the notification.',
        icon: <h-icon type="smile" style="color: #108ee9" />,
      });
    },
  },
};
</script>
```

##### 自动关闭的延时 
自定义通知框自动关闭的延时，默认`4.5s`，取消自动关闭只要将该值设为 `0` 即可。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
export default {
  methods: {
    openNotification() {
      this.$notification.open({
        message: 'Notification Title',
        description:
          'I will never close automatically. I will be close automatically. I will never close automatically.',
        duration: 0,
      });
    },
  },
};
</script>
```

##### 自定义按钮 
自定义关闭按钮的样式和文字。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
const close = () => {
  console.log(
    'Notification was closed. Either the close button was clicked or duration time elapsed.',
  );
};
export default {
  methods: {
    openNotification() {
      const key = `open${Date.now()}`;
      this.$notification.open({
        message: 'Notification Title',
        description:
          'A function will be be called after the notification is closed (automatically after the "duration" time of manually).',
        btn: h => {
          return h(
            'h-button',
            {
              props: {
                type: 'primary',
                size: 'small',
              },
              on: {
                click: () => this.$notification.close(key),
              },
            },
            'Confirm',
          );
        },
        key,
        onClose: close,
      });
    },
  },
};
</script>
```

##### 更新消息内容 
可以通过唯一的 key 来更新内容。

```html
<template>
  <h-button type="primary" @click="openNotification">
    Open the notification box
  </h-button>
</template>
<script>
const key = 'updatable';
export default {
  methods: {
    openNotification() {
      this.$notification.open({
        key,
        message: 'Notification Title',
        description: 'description.',
      });
      setTimeout(() => {
        this.$notification.open({
          key,
          message: 'New Title',
          description: 'New description.',
        });
      }, 1000);
    },
  },
};
</script>
```

### 何时使用 
在系统四个角显示通知提醒信息。经常用于以下情况：

- 较为复杂的通知内容。
- 带有交互的通知，给出用户下一步的行动点。
- 系统主动推送。

### API 
- `notification.success(config)`
- `notification.error(config)`
- `notification.info(config)`
- `notification.warning(config)`
- `notification.warn(config)`
- `notification.open(config)`
- `notification.close(key: String)`
- `notification.destroy()`

config 参数如下：

| 参数         | 说明                                                         | 类型                           | 默认值              | 版本  |
| :----------- | :----------------------------------------------------------- | :----------------------------- | :------------------ | :---- |
| btn          | 自定义关闭按钮                                               | vueNode \|function(h)          | -                   |       |
| bottom       | 消息从底部弹出时，距离底部的位置，单位像素。                 | string                         | `24px`              | 1.5.0 |
| class        | 自定义 CSS class                                             | string                         | -                   |       |
| description  | 通知提醒内容，必选                                           | string \|vueNode \|function(h) | -                   |       |
| duration     | 默认 4.5 秒后自动关闭，配置为 null 则不自动关闭              | number                         | 4.5                 |       |
| getContainer | 配置渲染节点的输出位置                                       | () => HTMLNode                 | () => document.body |       |
| icon         | 自定义图标                                                   | vueNode \|function(h)          | -                   |       |
| key          | 当前通知唯一标志                                             | string                         | -                   |       |
| message      | 通知提醒标题，必选                                           | string \|vueNode \|function(h) | -                   |       |
| placement    | 弹出位置，可选 `topLeft` `topRight` `bottomLeft` `bottomRight` | string                         | topRight            |       |
| style        | 自定义内联样式                                               | Object \| string               | -                   |       |
| onClose      | 点击默认关闭按钮时触发的回调函数                             | Function                       | -                   |       |
| onClick      | 点击通知时触发的回调函数                                     | Function                       | -                   |       |
| top          | 消息从顶部弹出时，距离顶部的位置，单位像素。                 | string                         | `24px`              | 1.5.0 |
| closeIcon    | 自定义关闭图标                                               | VNode \| function(h)           | -                   | 1.5.0 |

还提供了一个全局配置方法，在调用前提前配置，全局一次生效。

- `notification.config(options)`

```js
notification.config({
  placement: 'bottomRight',
  bottom: '50px',
  duration: 3,
});
```

| 参数         | 说明                                                         | 类型                 | 默认值              | 版本  |
| :----------- | :----------------------------------------------------------- | :------------------- | :------------------ | :---- |
| bottom       | 消息从底部弹出时，距离底部的位置，单位像素。                 | string               | `24px`              |       |
| duration     | 默认自动关闭延时，单位秒                                     | number               | 4.5                 |       |
| getContainer | 配置渲染节点的输出位置                                       | () => HTMLNode       | () => document.body |       |
| placement    | 弹出位置，可选 `topLeft` `topRight` `bottomLeft` `bottomRight` | string               | topRight            |       |
| top          | 消息从顶部弹出时，距离顶部的位置，单位像素。                 | string               | `24px`              |       |
| closeIcon    | 自定义关闭图标                                               | VNode \| function(h) | -                   | 1.5.0 |

## 气泡确认框
点击元素，弹出气泡式的确认框。

### 何时使用
目标元素的操作需要用户进一步的确认时，在目标元素附近弹出浮层提示，询问用户。

和 ‘confirm’ 弹出的全屏居中模态对话框相比，交互形式更轻量。

### 代码演示
##### 基本 
最简单的用法。

```html
<template>
  <h-popconfirm
    title="Are you sure delete this task?"
    ok-text="Yes"
    cancel-text="No"
    @confirm="confirm"
    @cancel="cancel"
  >
    <a href="#">Delete</a>
  </h-popconfirm>
</template>
<script>
export default {
  methods: {
    confirm(e) {
      console.log(e);
      this.$message.success('Click on Yes');
    },
    cancel(e) {
      console.log(e);
      this.$message.error('Click on No');
    },
  },
};
</script>
```

##### 位置 
位置有十二个方向。如需箭头指向目标元素中心，可以设置 `arrowPointAtCenter`。

```html
<template>
  <div id="components-h-popconfirm-demo-placement">
    <div :style="{ marginLeft: `${buttonWidth}px`, whiteSpace: 'nowrap' }">
      <h-popconfirm placement="topLeft" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>TL</h-button>
      </h-popconfirm>
      <h-popconfirm placement="top" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>Top</h-button>
      </h-popconfirm>
      <h-popconfirm placement="topRight" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>TR</h-button>
      </h-popconfirm>
    </div>
    <div :style="{ width: `${buttonWidth}px`, float: 'left' }">
      <h-popconfirm placement="leftTop" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>LT</h-button>
      </h-popconfirm>
      <h-popconfirm placement="left" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>Left</h-button>
      </h-popconfirm>
      <h-popconfirm placement="leftBottom" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>LB</h-button>
      </h-popconfirm>
    </div>
    <div :style="{ width: `${buttonWidth}px`, marginLeft: `${buttonWidth * 4 + 24}px` }">
      <h-popconfirm placement="rightTop" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>RT</h-button>
      </h-popconfirm>
      <h-popconfirm placement="right" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>Right</h-button>
      </h-popconfirm>
      <h-popconfirm placement="rightBottom" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>RB</h-button>
      </h-popconfirm>
    </div>
    <div :style="{ marginLeft: `${buttonWidth}px`, clear: 'both', whiteSpace: 'nowrap' }">
      <h-popconfirm placement="bottomLeft" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>BL</h-button>
      </h-popconfirm>
      <h-popconfirm placement="bottom" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>Bottom</h-button>
      </h-popconfirm>
      <h-popconfirm placement="bottomRight" ok-text="Yes" cancel-text="No" @confirm="confirm">
        <template slot="title">
          <p>{{ text }}</p>
          <p>{{ text }}</p>
        </template>
        <h-button>BR</h-button>
      </h-popconfirm>
    </div>
  </div>
</template>
<script>
import { message } from 'ant-design-vue';

export default {
  data() {
    return {
      buttonWidth: 70,
      text: 'Are you sure to delete this task?',
    };
  },
  methods: {
    confirm() {
      message.info('Clicked on Yes.');
    },
  },
};
</script>
<style scoped>
#components-h-popconfirm-demo-placement .ant-btn {
  width: 70px;
  text-align: center;
  padding: 0;
  margin-right: 8px;
  margin-bottom: 8px;
}
</style>
```

##### 自定义 Icon 图标
使用 `icon` 自定义提示 `icon`。

```html
<template>
  <h-popconfirm title="Are you sure？">
    <h-icon slot="icon" type="question-circle-o" style="color: red" />
    <a href="#">Delete</a>
  </h-popconfirm>
</template>
```

##### 国际化 
使用 `okText` 和 `cancelText` 自定义按钮文字。

```html
<template>
  <h-popconfirm title="Are you sure？" ok-text="Yes" cancel-text="No">
    <a href="#">Delete</a>
  </h-popconfirm>
</template>
```

##### 条件触发
可以判断是否需要弹出。

```html
<template>
  <div>
    <h-popconfirm
      title="Are you sure delete this task?"
      :visible="visible"
      ok-text="Yes"
      cancel-text="No"
      @visibleChange="handleVisibleChange"
      @confirm="confirm"
      @cancel="cancel"
    >
      <a href="#">Delete a task</a>
    </h-popconfirm>
    <br />
    <br />
    Whether directly execute：<h-checkbox default-checked @change="changeCondition" />
  </div>
</template>
<script>
import { message } from 'ant-design-vue';

export default {
  data() {
    return {
      visible: false,
      condition: true,
    };
  },
  methods: {
    changeCondition(e) {
      this.condition = e.target.checked;
    },
    confirm() {
      this.visible = false;
      message.success('Next step.');
    },
    cancel() {
      this.visible = false;
      message.error('Click on cancel.');
    },
    handleVisibleChange(visible) {
      if (!visible) {
        this.visible = false;
        return;
      }
      // Determining condition before show the popconfirm.
      console.log(this.condition);
      if (this.condition) {
        this.confirm(); // next step
      } else {
        this.visible = true;
      }
    },
  },
};
</script>
```

### API 
| 参数       | 说明                                     | 类型         | 默认值                             | 版本  |
| :--------- | :--------------------------------------- | :----------- | :--------------------------------- | :---- |
| cancelText | 取消按钮文字                             | string\|slot | 取消                               |       |
| okText     | 确认按钮文字                             | string\|slot | 确定                               |       |
| okType     | 确认按钮类型                             | string       | primary                            |       |
| title      | 确认框的描述                             | string\|slot | 无                                 |       |
| icon       | 自定义弹出气泡 Icon 图标                 | vNode        | <Icon type="exclamation-circle" /> |       |
| disabled   | 点击 Popconfirm 子元素是否弹出气泡确认框 | boolean      | false                              | 1.5.0 |

#### 事件
| 事件名称      | 说明           | 回调参数          |
| :------------ | :------------- | :---------------- |
| cancel        | 点击取消的回调 | function(e)       |
| confirm       | 点击确认的回调 | function(e)       |
| visibleChange | 显示隐藏的回调 | function(visible) |

更多属性请参考 [Tooltip](https://1x.antdv.com/components/tooltip-cn/#API)。

### 注意
请确保 `Popconfirm` 的子元素能接受 `mouseenter`、`mouseleave`、`focus`、`click` 事件。

## 进度条
展示操作的当前进度。

### 何时使用
在操作需要较长时间才能完成时，为用户显示该操作的当前进度和状态。

- 当一个操作会打断当前界面，或者需要在后台运行，且耗时可能超过2秒时；

- 当需要显示一个操作完成的百分比时。

### 代码演示
##### 进度条
标准的进度条。

```html
<template>
  <div>
    <h-progress :percent="30" />
    <h-progress :percent="50" status="active" />
    <h-progress :percent="70" status="exception" />
    <h-progress :percent="100" />
    <h-progress :percent="50" :show-info="false" />
  </div>
</template>
```

##### 小型进度条 
适合放在较狭窄的区域内。

```html
<template>
  <div style="width: 170px">
    <h-progress :percent="30" size="small" />
    <h-progress :percent="50" size="small" status="active" />
    <h-progress :percent="70" size="small" status="exception" />
    <h-progress :percent="100" size="small" />
  </div>
</template>
```

##### 进度圈动态展示 
会动的进度条才是好进度条。

```html
<template>
  <div>
    <h-progress type="circle" :percent="percent" />
    <h-button-group>
      <h-button icon="minus" @click="decline" />
      <h-button icon="plus" @click="increase" />
    </h-button-group>
  </div>
</template>
<script>
export default {
  data() {
    return {
      percent: 0,
    };
  },
  methods: {
    increase() {
      let percent = this.percent + 10;
      if (percent > 100) {
        percent = 100;
      }
      this.percent = percent;
    },
    decline() {
      let percent = this.percent - 10;
      if (percent < 0) {
        percent = 0;
      }
      this.percent = percent;
    },
  },
};
</script>
```

##### 动态展示 
会动的进度条才是好进度条。

```html
<template>
  <div>
    <h-progress :percent="percent" />
    <h-button-group>
      <h-button icon="minus" @click="decline" />
      <h-button icon="plus" @click="increase" />
    </h-button-group>
  </div>
</template>
<script>
export default {
  data() {
    return {
      percent: 0,
    };
  },
  methods: {
    increase() {
      let percent = this.percent + 10;
      if (percent > 100) {
        percent = 100;
      }
      this.percent = percent;
    },
    decline() {
      let percent = this.percent - 10;
      if (percent < 0) {
        percent = 0;
      }
      this.percent = percent;
    },
  },
};
</script>
```

##### 分段进度条 
标准的进度条。

```html
<template>
  <div>
    <h-tooltip title="3 done / 3 in progress / 4 to do">
      <h-progress :percent="60" :success-percent="30" />
    </h-tooltip>
    <h-tooltip title="3 done / 3 in progress / 4 to do">
      <h-progress :percent="60" :success-percent="30" type="circle" />
    </h-tooltip>
    <h-tooltip title="3 done / 3 in progress / 4 to do">
      <h-progress :percent="60" :success-percent="30" type="dashboard" />
    </h-tooltip>
  </div>
</template>
```

##### 自定义进度条渐变色
`linear-gradient` 的封装。推荐只传两种颜色。

```html
<template>
  <div>
    <h-progress
      :stroke-color="{
        '0%': '#108ee9',
        '100%': '#87d068',
      }"
      :percent="99.9"
    />
    <h-progress
      :stroke-color="{
        from: '#108ee9',
        to: '#87d068',
      }"
      :percent="99.9"
      status="active"
    />
    <h-progress
      type="circle"
      :stroke-color="{
        '0%': '#108ee9',
        '100%': '#87d068',
      }"
      :percent="90"
    />
    <h-progress
      type="circle"
      :stroke-color="{
        '0%': '#108ee9',
        '100%': '#87d068',
      }"
      :percent="100"
    />
  </div>
</template>
```

##### 进度圈 
圈形的进度。

```html
<template>
  <div>
    <h-progress type="circle" :percent="75" />
    <h-progress type="circle" :percent="70" status="exception" />
    <h-progress type="circle" :percent="100" />
  </div>
</template>
<style scoped>
.ant-progress-circle-wrap,
.ant-progress-line-wrap {
  margin-right: 8px;
  margin-bottom: 5px;
}
</style>
```

##### 小型进度圈 
小一号的圈形进度。

```html
<template>
  <div>
    <h-progress type="circle" :percent="30" :width="80" />
    <h-progress type="circle" :percent="70" :width="80" status="exception" />
    <h-progress type="circle" :percent="100" :width="80" />
  </div>
</template>
<style scoped>
.ant-progress-circle-wrap,
.ant-progress-line-wrap {
  margin-right: 8px;
  margin-bottom: 5px;
}
</style>
```

##### 自定义文字格式
`format` 属性指定格式。

```html
<template>
  <div>
    <h-progress type="circle" :percent="75" :format="percent => `${percent} Days`" />
    <h-progress type="circle" :percent="100" :format="() => 'Done'" />
    <h-progress type="circle" :percent="75">
      <template #format="percent">
        <span style="color: red">{{ percent }}</span>
      </template>
    </h-progress>
  </div>
</template>
<style scoped>
div.ant-progress-circle,
div.ant-progress-line {
  margin-right: 8px;
  margin-bottom: 8px;
}
</style>
```

##### 仪表盘 
By setting `type=dashboard`, you can get a dashboard style of progress easily.

```html
<template>
  <div>
    <h-progress type="dashboard" :percent="75" />
  </div>
</template>
```

##### 圆角/方角边缘
`strokeLinecap="square|round"` 可以调整进度条边缘的形状。

```html
<template>
  <div>
    <h-progress stroke-linecap="square" :percent="75" />
    <h-progress stroke-linecap="square" :percent="75" type="circle" />
    <h-progress stroke-linecap="square" :percent="75" type="dashboard" />
  </div>
</template>
```

### API 
各类型共用的属性。

| 属性           | 说明                                                         | 类型                                                         | 默认值                     |
| :------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------------- |
| type           | 类型，可选 `line` `circle` `dashboard`                       | string                                                       | `line`                     |
| format         | 内容的模板函数                                               | function(percent, successPercent) \| v-slot:format="percent, successPercent" | `percent => percent + '%'` |
| percent        | 百分比                                                       | number                                                       | 0                          |
| showInfo       | 是否显示进度数值或状态图标                                   | boolean                                                      | true                       |
| status         | 状态，可选：`success` `exception` `normal` `active`(仅限 line) | string                                                       | -                          |
| strokeLinecap  |                                                              | Enum{ 'round', 'square' }                                    | `round`                    |
| strokeColor    | 进度条的色彩                                                 | string                                                       | -                          |
| successPercent | 已完成的分段百分比                                           | number                                                       | 0                          |

#### `type="line"` 
| 属性        | 说明                               | 类型                                                      | 默认值 | 版本  |
| :---------- | :--------------------------------- | :-------------------------------------------------------- | :----- | :---- |
| strokeWidth | 进度条线的宽度，单位 px            | number                                                    | 10     |       |
| strokeColor | 进度条的色彩，传入 object 时为渐变 | string \| { from: string; to: string; direction: string } | -      | 1.5.0 |

#### `type="circle"`
| 属性        | 说明                                             | 类型             | 默认值 | 版本  |
| :---------- | :----------------------------------------------- | :--------------- | :----- | :---- |
| width       | 圆形进度条画布宽度，单位 px                      | number           | 132    |       |
| strokeWidth | 圆形进度条线的宽度，单位是进度条画布宽度的百分比 | number           | 6      |       |
| strokeColor | 圆形进度条线的色彩，传入 object 时为渐变         | string \| object | -      | 1.5.0 |

#### `type="dashboard"` 
| 属性        | 说明                                               | 类型                                     | 默认值 |
| :---------- | :------------------------------------------------- | :--------------------------------------- | :----- |
| width       | 仪表盘进度条画布宽度，单位 px                      | number                                   | 132    |
| strokeWidth | 仪表盘进度条线的宽度，单位是进度条画布宽度的百分比 | number                                   | 6      |
| gapDegree   | 仪表盘进度条缺口角度，可取值 0 ~ 360               | number                                   | 0      |
| gapPosition | 仪表盘进度条缺口位置                               | Enum{ 'top', 'bottom', 'left', 'right' } | `top`  |

## 结果 
用于反馈一系列操作任务的处理结果。

### 何时使用
当有重要操作需告知用户处理结果，且反馈内容较为复杂时使用。

### 代码演示
##### Success
成功的结果。

```html
<template>
  <h-result
    status="success"
    title="Successfully Purchased Cloud Server ECS!"
    sub-title="Order number: 2017182818828182881 Cloud server configuration takes 1-5 minutes, please wait."
  >
    <template #extra>
      <h-button key="console" type="primary">
        Go Console
      </h-button>
      <h-button key="buy">
        Buy Again
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### Warning 
警告类型的结果。

```html
<template>
  <h-result status="warning" title="There are some problems with your operation.">
    <template #extra>
      <h-button key="console" type="primary">
        Go Console
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### 404 
此页面未找到。

```html
<template>
  <h-result status="404" title="404" sub-title="Sorry, the page you visited does not exist.">
    <template #extra>
      <h-button type="primary">
        Back Home
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### Error 
复杂的错误反馈。

```html
<template>
  <h-result
    status="error"
    title="Submission Failed"
    sub-title="Please check and modify the following information before resubmitting."
  >
    <template #extra>
      <h-button key="console" type="primary">
        Go Console
      </h-button>
      <h-button key="buy">
        Buy Again
      </h-button>
    </template>

    <div class="desc">
      <p style="font-size: 16px;">
        <strong>The content you submitted has the following error:</strong>
      </p>
      <p>
        <h-icon :style="{ color: 'red' }" type="close-circle" /> Your account has been frozen
        <a>Thaw immediately &gt;</a>
      </p>
      <p>
        <h-icon :style="{ color: 'red' }" type="close-circle" /> Your account is not yet eligible to
        apply <a>Apply Unlock &gt;</a>
      </p>
    </div>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
<style scoped>
.desc p {
  margin-bottom: 1em;
}
</style>
```

##### Info 
展示处理结果。

```html
<template>
  <h-result title="Your operation has been executed">
    <template #extra>
      <h-button key="console" type="primary">
        Go Console
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### 403 
你没有此页面的访问权限。

```html
<template>
  <h-result status="403" title="403" sub-title="Sorry, you are not authorized to access this page.">
    <template #extra>
      <h-button type="primary">
        Back Home
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### 500 
服务器发生了错误。

```html
<template>
  <h-result status="500" title="500" sub-title="Sorry, the server is wrong.">
    <template #extra>
      <h-button type="primary">
        Back Home
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

##### 自定义 icon 
自定义 icon。

```html
<template>
  <h-result title="Great, we have done all the operations!">
    <template #icon>
      <h-icon type="smile" theme="twoTone" />
    </template>
    <template #extra>
      <h-button type="primary">
        Next
      </h-button>
    </template>
  </h-result>
</template>
<script>
export default {
  data() {
    return {};
  },
};
</script>
```

### API 
| 参数     | 说明                      | 类型                                                         | 默认值 |
| :------- | :------------------------ | :----------------------------------------------------------- | :----- |
| title    | title 文字                | string \| VNode \| v-slot:title                              | -      |
| subTitle | subTitle 文字             | string \| VNode \| v-slot:subTitle                           | -      |
| status   | 结果的状态,决定图标和颜色 | `'success' | 'error' | 'info' | 'warning'| '404' | '403' | '500'` | 'info' |
| icon     | 自定义 icon               | v-slot:icon                                                  | -      |
| extra    | 操作区                    | v-slot:extra                                                 | -      |

## 加载占位图/骨架屏
在需要等待加载内容的位置提供一个占位图。

### 何时使用
- 网络较慢，需要长时间等待加载处理的情况下。
- 图文信息内容较多的列表/卡片中。
- 只在第一次加载数据的时候使用。
- 可以被 Spin 完全代替，但是在可用的场景下可以比 Spin 提供更好的视觉效果和用户体验。

### 代码演示
##### 基本
最简单的占位效果。

```html
<template>
  <h-skeleton />
</template>
```

##### 复杂的组合 
更复杂的组合。

```html
<template>
  <h-skeleton avatar :paragraph="{ rows: 4 }" />
</template>
```

##### 动画效果 
显示动画效果。

```html
<template>
  <h-skeleton active />
</template>
```

##### 包含子组件 
加载占位图包含子组件。

```html
<template>
  <div class="article">
    <h-skeleton :loading="loading">
      <div>
        <h4>Ant Design Vue, a design language</h4>
        <p>
          We supply a series of design principles, practical patterns and high quality design
          resources (Sketch and Axure), to help people create their product prototypes beautifully
          and efficiently.
        </p>
      </div>
    </h-skeleton>
    <h-button :disabled="loading" @click="showSkeleton">
      Show Skeleton
    </h-button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      loading: false,
    };
  },
  methods: {
    showSkeleton() {
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 3000);
    },
  },
};
</script>
<style>
.article h4 {
  margin-bottom: 16px;
}
.article button {
  margin-top: 16px;
}
</style>
```

##### 列表
在列表组件中使用加载占位符。

```html
<template>
  <div>
    <h-switch :checked="!loading" @change="onChange" />

    <h-list item-layout="vertical" size="large" :dath-source="listData">
      <h-list-item slot="renderItem" key="item.title" slot-scope="item, index">
        <template v-for="{ type, text } in actions" v-if="!loading" slot="actions">
          <span :key="type">
            <h-icon :type="type" style="margin-right: 8px" />
            {{ text }}
          </span>
        </template>
        <img
          v-if="!loading"
          slot="extra"
          width="272"
          alt="logo"
          src="https://gw.alipayobjects.com/zos/rmsportal/mqaQswcyDLcXyDKnZfES.png"
        />
        <h-skeleton :loading="loading" active avatar>
          <h-list-item-meta :description="item.description">
            <a slot="title" :href="item.href">{{ item.title }}</a>
            <h-avatar slot="avatar" :src="item.avatar" />
          </h-list-item-meta>
          {{ item.content }}
        </h-skeleton>
      </h-list-item>
    </h-list>
  </div>
</template>
<script>
const listData = [];
for (let i = 0; i < 3; i++) {
  listData.push({
    href: 'https://www.antdv.com/',
    title: `ant design vue part ${i}`,
    avatar: 'https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png',
    description:
      'Ant Design, a design language for background applications, is refined by Ant UED Team.',
    content:
      'We supply a series of design principles, practical patterns and high quality design resources (Sketch and Axure), to help people create their product prototypes beautifully and efficiently.',
  });
}
export default {
  data() {
    return {
      loading: true,
      listData,
      actions: [
        { type: 'star-o', text: '156' },
        { type: 'like-o', text: '156' },
        { type: 'message', text: '2' },
      ],
    };
  },
  methods: {
    onChange(checked) {
      this.loading = !checked;
    },
  },
};
</script>
<style>
.skeleton-demo {
  border: 1px solid #f4f4f4;
}
</style>
```

### API 
#### Skeleton 
| 属性      | 说明                                           | 类型                                                         | 默认值 |
| :-------- | :--------------------------------------------- | :----------------------------------------------------------- | :----- |
| active    | 是否展示动画效果                               | boolean                                                      | false  |
| avatar    | 是否显示头像占位图                             | boolean \| [SkeletonAvatarProps](https://1x.antdv.com/components/skeleton-cn/#SkeletonAvatarProps) | false  |
| loading   | 为 `true` 时，显示占位图。反之则直接展示子组件 | boolean                                                      | -      |
| paragraph | 是否显示段落占位图                             | boolean \| [SkeletonParagraphProps](https://1x.antdv.com/components/skeleton-cn/#SkeletonParagraphProps) | true   |
| title     | 是否显示标题占位图                             | boolean \| [SkeletonTitleProps](https://1x.antdv.com/components/skeleton-cn/#SkeletonTitleProps) | true   |

#### SkeletonAvatarProps 
| 属性  | 说明                 | 类型                                          | 默认值 |
| :---- | :------------------- | :-------------------------------------------- | :----- |
| size  | 设置头像占位图的大小 | number \| Enum{ 'large', 'small', 'default' } | -      |
| shape | 指定头像的形状       | Enum{ 'circle', 'square' }                    | -      |

#### SkeletonTitleProps 
| 属性  | 说明                 | 类型             | 默认值 |
| :---- | :------------------- | :--------------- | :----- |
| width | 设置标题占位图的宽度 | number \| string | -      |

#### SkeletonParagraphProps 
| 属性  | 说明                                                         | 类型                                        | 默认值 |
| :---- | :----------------------------------------------------------- | :------------------------------------------ | :----- |
| rows  | 设置段落占位图的行数                                         | number                                      | -      |
| width | 设置段落占位图的宽度，若为数组时则为对应的每行宽度，反之则是最后一行的宽度 | number \| string \| Array<number \| string> | -      |

## 加载中
用于页面和区块的加载中状态。

### 何时使用
页面局部处于等待异步数据或正在渲染过程时，合适的加载动效会有效缓解用户的焦虑。

### 代码演示
##### 基本用法 
一个简单的 loading 状态。

```html
<template>
  <div>
    <h-spin />
  </div>
</template>
```

##### 容器 
放入一个容器中。

```html
<style scoped>
.example {
  text-align: center;
  background: rgba(0, 0, 0, 0.05);
  border-radius: 4px;
  margin-bottom: 20px;
  padding: 30px 50px;
  margin: 20px 0;
}
</style>
<template>
  <div class="example">
    <h-spin />
  </div>
</template>
```

##### 自定义描述文案
自定义描述文案。

```html
<style scoped>
.spin-content {
  border: 1px solid #91d5ff;
  background-color: #e6f7ff;
  padding: 30px;
}
</style>
<template>
  <div>
    <h-spin tip="Loading...">
      <div class="spin-content">
        我的描述文案是自定义的。。。
      </div>
    </h-spin>
  </div>
</template>
```

##### 自定义指示符 
使用自定义指示符。

```html
<template>
  <div>
    <h-spin>
      <h-icon slot="indicator" type="loading" style="font-size: 24px" spin />
    </h-spin>
    <h-spin :indicator="indicator" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      indicator: <h-icon type="loading" style="font-size: 24px" spin />,
    };
  },
};
</script>
```

##### 各种大小 
小的用于文本加载，默认用于卡片容器级加载，大的用于**页面级**加载。

```html
<template>
  <div>
    <h-spin size="small" />
    <h-spin />
    <h-spin size="large" />
  </div>
</template>
```

##### 卡片加载中 
可以直接把内容内嵌到 `Spin` 中，将现有容器变为加载状态。

```html
<style scoped>
.spin-content {
  border: 1px solid #91d5ff;
  background-color: #e6f7ff;
  padding: 30px;
}
</style>
<template>
  <div>
    <h-spin :spinning="spinning">
      <div class="spin-content">
        可以点击‘切换’按钮，控制本区域的spin展示。
      </div>
    </h-spin>
    Loading state：<h-switch v-model="spinning" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      spinning: false,
    };
  },
  methods: {
    changeSpinning() {
      this.spinning = !this.spinning;
    },
  },
};
</script>
```

##### 延迟 
延迟显示 loading 效果。当 spinning 状态在 `delay` 时间内结束，则不显示 loading 状态。

```html
<style scoped>
.spin-content {
  border: 1px solid #91d5ff;
  background-color: #e6f7ff;
  padding: 30px;
}
</style>
<template>
  <div>
    <h-spin :spinning="spinning" :delay="delayTime">
      <div class="spin-content">
        可以点击‘切换’按钮，延迟显示 loading 效果。当 spinning 状态在 `delay` 时间内结束，则不显示
        loading 状态。
      </div>
    </h-spin>
    Loading state：<h-switch v-model="spinning" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      spinning: false,
      delayTime: 500,
    };
  },
  methods: {
    changeSpinning() {
      this.spinning = !this.spinning;
    },
  },
};
</script>
```

### API 
| 参数             | 说明                                         | 类型          | 默认值    |
| :--------------- | :------------------------------------------- | :------------ | :-------- |
| delay            | 延迟显示加载效果的时间（防止闪烁）           | number (毫秒) | -         |
| indicator        | 加载指示符                                   | vNode \| slot | -         |
| size             | 组件大小，可选值为 `small` `default` `large` | string        | 'default' |
| spinning         | 是否为加载中状态                             | boolean       | true      |
| tip              | 当作为包裹元素时，可以自定义描述文案         | string        | -         |
| wrapperClassName | 包装器的类属性                               | string        | -         |

#### 静态方法 
- `Spin.setDefaultIndicator({indicator})` 同上 `indicator`，你可以自定义全局默认元素

  ```jsx
  Spin.setDefaultIndicator({
    indicator: h => {
      return <i class="anticon anticon-loading anticon-spin ant-spin-dot"></i>;
    },
  });
  或者;
  Spin.setDefaultIndicator({
    indicator: {
      render() {
        return <i class="anticon anticon-loading anticon-spin ant-spin-dot"></i>;
      },
    },
  });
  ```

## 锚点
用于跳转到页面指定位置。

### 何时使用
需要展现当前页面上可供跳转的锚点链接，以及快速在锚点之间跳转。

### 代码演示
##### 基本
最简单的用法。

```html
<template>
  <h-anchor>
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link
      href="#components-anchor-demo-basic"
      title="Basic demo with Target"
      target="_blank"
    />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
```

##### 自定义 click 事件 
点击锚点不记录历史。

```html
<template>
  <h-anchor :affix="false" @click="handleClick">
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
<script>
export default {
  methods: {
    handleClick(e, link) {
      e.preventDefault();
      console.log(link);
    },
  },
};
</script>
```

##### 监听锚点链接改变 
监听锚点链接改变

```html
<template>
  <h-anchor :affix="false" @change="onChange">
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
<script>
export default {
  methods: {
    onChange(link) {
      console.log('Anchor:OnChange', link);
    },
  },
};
</script>
```

##### 静态位置
不浮动，状态不随页面滚动变化。

```html
<template>
  <h-anchor :affix="false">
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
```

##### 自定义锚点高亮 
自定义锚点高亮。

```html
<template>
  <h-anchor :affix="false" :get-current-anchor="getCurrentAnchor">
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
<script>
export default {
  methods: {
    getCurrentAnchor() {
      return '#components-anchor-demo-static';
    },
  },
};
</script>
```

##### 设置锚点滚动偏移量 
锚点目标滚动到屏幕正中间。

```html
<template>
  <h-anchor :target-offset="targetOffset">
    <h-anchor-link href="#components-anchor-demo-basic" title="Basic demo" />
    <h-anchor-link href="#components-anchor-demo-static" title="Static demo" />
    <h-anchor-link href="#API" title="API">
      <h-anchor-link href="#Anchor-Props" title="Anchor Props" />
      <h-anchor-link href="#Link-Props" title="Link Props" />
    </h-anchor-link>
  </h-anchor>
</template>
<script>
export default {
  data() {
    return {
      targetOffset: undefined,
    };
  },
  mounted() {
    this.targetOffset = window.innerHeight / 2;
  },
};
</script>
```

### API
#### Anchor Props 
| 成员             | 说明                                                         | 类型              | 默认值       | 版本  |
| :--------------- | :----------------------------------------------------------- | :---------------- | :----------- | :---- |
| affix            | 固定模式                                                     | boolean           | true         |       |
| bounds           | 锚点区域边界                                                 | number            | 5(px)        |       |
| getContainer     | 指定滚动的容器                                               | () => HTMLElement | () => window |       |
| offsetBottom     | 距离窗口底部达到指定偏移量后触发                             | number            |              |       |
| offsetTop        | 距离窗口顶部达到指定偏移量后触发                             | number            |              |       |
| showInkInFixed   | 固定模式是否显示小圆点                                       | boolean           | false        |       |
| wrapperClass     | 容器的类名                                                   | string            | -            |       |
| wrapperStyle     | 容器样式                                                     | object            | -            |       |
| getCurrentAnchor | 自定义高亮的锚点                                             | () => string      | -            | 1.5.0 |
| targetOffset     | 锚点滚动偏移量，默认与 offsetTop 相同，[例子](https://1x.antdv.com/components/anchor-cn/#components-anchor-demo-targetOffset) | number            | `offsetTop`  | 1.5.0 |

#### 事件 
| 事件名称 | 说明                   | 回调参数                            | 版本 |
| :------- | :--------------------- | :---------------------------------- | :--- |
| click    | `click` 事件的 handler | Function(e: Event, link: Object)    |      |
| change   | 监听锚点链接改变       | (currentActiveLink: string) => void |      |

#### Link Props
| 成员   | 说明                             | 类型         | 默认值 | 版本  |
| :----- | :------------------------------- | :----------- | :----- | :---- |
| href   | 锚点链接                         | string       |        |       |
| title  | 文字内容                         | string\|slot |        |       |
| target | 该属性指定在何处显示链接的资源。 | string       |        | 1.5.0 |

## 回到顶部
返回页面顶部的操作按钮。

### 何时使用
- 当页面内容区域比较长时；

- 当用户需要频繁返回顶部查看相关内容时。

### 代码演示
##### 基本 
最简单的用法。

```html
<template>
  <div>
    <h-back-top />
    Scroll down to see the bottom-right
    <strong style="color: rgba(64, 64, 64, 0.6)"> gray </strong>
    button.
  </div>
</template>
```

##### 自定义样式
可以自定义回到顶部按钮的样式，限制宽高：`40px * 40px`。

```html
<template>
  <div id="components-back-top-demo-custom">
    <h-back-top>
      <div class="ant-back-top-inner">
        UP
      </div>
    </h-back-top>
    Scroll down to see the bottom-right
    <strong style="color: #1088e9"> blue </strong>
    button.
  </div>
</template>
<style scoped>
#components-back-top-demo-custom .ant-back-top {
  bottom: 100px;
}
#components-back-top-demo-custom .ant-back-top-inner {
  height: 40px;
  width: 40px;
  line-height: 40px;
  border-radius: 4px;
  background-color: #1088e9;
  color: #fff;
  text-align: center;
  font-size: 20px;
}
</style>
```

### API 
> 有默认样式，距离底部 `50px`，可覆盖。
>
> 自定义样式宽高不大于 40px * 40px。

| 参数             | 说明                                                         | 类型     | 默认值       | 版本 |
| :--------------- | :----------------------------------------------------------- | :------- | :----------- | :--- |
| target           | 设置需要监听其滚动事件的元素，值为一个返回对应 DOM 元素的函数 | Function | () => window |      |
| visibilityHeight | 滚动高度达到此参数值才出现 `BackTop`                         | number   | 400          |      |

#### 事件 
| 事件名称 | 说明               | 回调参数 | 版本 |
| :------- | :----------------- | :------- | :--- |
| click    | 点击按钮的回调函数 | Function |      |

## 全局化配置
为组件提供统一的全局化配置。

##### 国际化 
此处列出 Ant Design Vue 中需要国际化支持的组件，你可以在演示里切换语言。

```html
<template>
  <div>
    <div class="change-locale">
      <span style="margin-right: 16px">Change locale of components: </span>
      <h-radio-group :value="locale" @change="changeLocale">
        <h-radio-button key="en" :value="enUS">
          English
        </h-radio-button>
        <h-radio-button key="cn" :value="zhCN">
          中文
        </h-radio-button>
      </h-radio-group>
    </div>
    <h-config-provider :locale="locale">
      <div :key="locale ? locale.locale : 'en'" class="locale-components">
        <div class="example">
          <h-pagination :default-current="1" :total="50" show-size-changer />
        </div>
        <div class="example">
          <h-select show-search style="width: 200px">
            <h-select-option value="jack">
              jack
            </h-select-option>
            <h-select-option value="lucy">
              lucy
            </h-select-option>
          </h-select>
          <h-date-picker />
          <h-time-picker />
          <h-range-picker style="width: 200px" />
        </div>
        <div class="example">
          <h-button type="primary" @click="visible = true">
            Show Modal
          </h-button>
          <h-button @click="info">
            Show info
          </h-button>
          <h-button @click="confirm">
            Show confirm
          </h-button>
          <h-popconfirm title="Question?">
            <a href="#">Click to confirm</a>
          </h-popconfirm>
        </div>
        <div class="example">
          <h-transfer
            :dath-source="[]"
            show-search
            :target-keys="[]"
            :render="item => item.title"
          />
        </div>
        <div style="width: 319px; border: 1px solid #d9d9d9; border-radius: 4px">
          <h-calendar :fullscreen="false" :value="moment()" />
        </div>
        <div class="example">
          <h-table :dath-source="[]" :columns="columns" />
        </div>
        <h-modal v-model="visible" title="Locale Modal">
          <p>Locale Modal</p>
        </h-modal>
      </div>
    </h-config-provider>
  </div>
</template>
<script>
import enUS from 'ant-design-vue/es/locale/en_US';
import zhCN from 'ant-design-vue/es/locale/zh_CN';
import moment from 'moment';
import 'moment/locale/zh-cn';

moment.locale('en');

const columns = [
  {
    title: 'Name',
    dataIndex: 'name',
    filters: [
      {
        text: 'filter1',
        value: 'filter1',
      },
    ],
  },
  {
    title: 'Age',
    dataIndex: 'age',
  },
];
export default {
  data() {
    return {
      columns,
      visible: false,
      locale: enUS,
      moment,
      enUS,
      zhCN,
    };
  },
  methods: {
    changeLocale(e) {
      const localeValue = e.target.value;
      this.locale = localeValue;
      if (!localeValue) {
        moment.locale('en');
      } else {
        moment.locale('zh-cn');
      }
    },
    info() {
      this.$info({
        title: 'some info',
        content: 'some info',
      });
    },
    confirm() {
      this.$confirm({
        title: 'some info',
        content: 'some info',
      });
    },
  },
};
</script>
<style scoped>
.locale-components {
  border-top: 1px solid #d9d9d9;
  padding-top: 16px;
}

.example {
  margin: 16px 0;
}

.example > * {
  margin-right: 8px;
}

.change-locale {
  margin-bottom: 16px;
}
</style>
```

### 使用 
ConfigProvider 使用 Vue 的 [provide / inject](https://vuejs.org/v2/api/#provide-inject) 特性，只需在应用外围包裹一次即可全局生效。

```html
<template>
  <h-config-provider :getPopupContainer="getPopupContainer">
    <app />
  </h-config-provider>
</template>
<script>
  export default {
    methods: {
      getPopupContainer(el, dialogContext) {
        if (dialogContext) {
          return dialogContext.getDialogWrap();
        } else {
          return document.body;
        }
      },
    },
  };
</script>
```

#### Content Security Policy 
部分组件为了支持波纹效果，使用了动态样式。如果开启了 Content Security Policy (CSP)，你可以通过 `csp` 属性来进行配置：

```html
<h-config-provider :csp="{ nonce: 'YourNonceCode' }">
  <h-button>My Button</h-button>
</h-config-provider>
```

### API 
| 参数                    | 说明                                                         | 类型                                                 | 默认值              | 版本     |
| :---------------------- | :----------------------------------------------------------- | :--------------------------------------------------- | :------------------ | :------- |
| autoInsertSpaceInButton | 设置为 `false` 时，移除按钮中 2 个汉字之间的空格             | boolean                                              | true                |          |
| csp                     | 设置 [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) 配置 | { nonce: string }                                    | -                   |          |
| renderEmpty             | 自定义组件空状态。参考 [空状态](https://1x.antdv.com/components/empty/) | slot-scope \| Function(componentName: string): VNode | -                   |          |
| getPopupContainer       | 弹出框（Select, Tooltip, Menu 等等）渲染父节点，默认渲染到 body 上。 | Function(triggerNode, dialogContext)                 | () => document.body |          |
| locale                  | 语言包配置，语言包可到 [ant-design-vue/es/locale](http://unpkg.com/ant-design-vue/es/locale/) 目录下寻找 | object                                               | -                   | 1.5.0    |
| pageHeader              | 统一设置 pageHeader 的 ghost，参考 [pageHeader](https://1x.antdv.com/components/config-provider-cn/(/components/page-header)) | { ghost: boolean }                                   | 'true'              | 1.5.0    |
| transformCellText       | Table 数据渲染前可以再次改变，一般用户空数据的默认配置       | Function({ text, column, record, index }) => any     | -                   | 1.5.4 ｜ |

### FAQ 
##### 为什么我使用了 ConfigProvider `locale`，时间类组件的国际化还有问题？ 
请检查是否设置了 `moment.locale('zh-cn')`，或者是否有两个版本的 moment 共存。

##### 配置 `getPopupContainer` 导致 Modal 报错？ 
当如下全局设置 `getPopupContainer` 为触发节点的 parentNode 时，由于 Modal 的用法不存在 `triggerNode`，这样会导致 `triggerNode is undefined` 的报错，需要增加一个判断条件。

```diff
 <ConfigProvider
-  getPopupContainer={triggerNode => triggerNode.parentNode}
+  getPopupContainer={node => {
+    if (node) {
+      return node.parentNode;
+    }
+    return document.body;
+  }}
 >
   <App />
 </ConfigProvider>
```

## 分割线
区隔内容的分割线。

### 何时使用
- 对不同章节的文本段落进行分割。
- 对行内文字/链接进行分割，例如表格的操作列。

### 代码演示
##### 垂直分割线
使用 `type="vertical"` 设置为行内的垂直分割线。

```html
<template>
  <div>
    Text
    <h-divider type="vertical" />
    <a href="#">Link</a>
    <h-divider type="vertical" />
    <a href="#">Link</a>
  </div>
</template>
```

##### 水平分割线 
默认为水平分割线，可在中间加入文字。

```html
<template>
  <div>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider />
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider>With Text</h-divider>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider dashed />
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
  </div>
</template>
```

##### 带文字的分割线
分割线中带有文字，可以用 `orientation` 指定文字位置。

```html
<template>
  <div>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider>Text</h-divider>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider orientation="left">
      Left Text
    </h-divider>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
    <h-divider orientation="right">
      Right Text
    </h-divider>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nonne merninisti licere mihi ista
      probare, quae sunt a te dicta? Refert tamen, quo modo.
    </p>
  </div>
</template>
```

### API 
| 参数        | 说明             | 类型                          | 默认值       |
| :---------- | :--------------- | :---------------------------- | :----------- |
| dashed      | 是否虚线         | Boolean                       | false        |
| orientation | 分割线标题的位置 | enum: `left` `right`          | `center`     |
| type        | 水平还是垂直类型 | enum: `horizontal` `vertical` | `horizontal` |

## 国际化
为组件内建文案提供统一的国际化支持。

### 使用 
LocaleProvider 使用 Vue 的 [provide/inject](https://cn.vuejs.org/v2/api/#provide-inject) 特性，只需在应用外围包裹一次即可全局生效。

```html
<template>
  <h-locale-provider :locale="zh_CN">
    <App />
  </h-locale-provider>
</template>
<script>
  import zh_CN from 'ant-design-vue/lib/locale-provider/zh_CN';
  import moment from 'moment';
  import 'moment/locale/zh-cn';

  moment.locale('zh-cn');
  export default {
    data() {
      return {
        zh_CN,
      };
    },
  };
</script>
```

我们提供了英语，中文，俄语，法语，德语等多种语言支持，所有语言包可以在 [这里](https://github.com/vueComponent/ant-design-vue/tree/master/components/locale-provider) 找到。

注意：如果你需要使用 UMD 版的 dist 文件，应该引入 `ant-design-vue/dist/antd-with-locales.js`，同时引入 moment 对应的 locale，然后按以下方式使用：

```html
<template>
  <h-locale-provider :locale="locales.en_US">
    <App />
  </h-locale-provider>
</template>
<script>
  const { LocaleProvider, locales } = window.antd;
</script>
```

#### 增加语言包 
如果你找不到你需要的语言包，欢迎你在 [英文语言包](https://github.com/vueComponent/ant-design-vue/blob/master/components/locale-provider/en_US.js) 的基础上创建一个新的语言包，并给我们 Pull Request。

#### 其他国际化需求 
本模块仅用于组件的内建文案，若有业务文案的国际化需求，建议使用 [vue-i18n](https://github.com/kazupon/vue-i18n)

### 代码演示 
##### 国际化 
用 `LocaleProvider` 包裹你的应用，并引用对应的语言包。

```html
<template>
  <h-locale-provider :locale="zhCN">
    <h-pagination :default-current="1" :total="50" show-size-changer />
  </h-locale-provider>
</template>
<script>
// you should use import zhCN from 'ant-design-vue/es/locale-provider/zh_CN';
import zhCN from 'ant-design-vue/es/locale-provider/zh_CN';
export default {
  data() {
    return {
      zhCN,
    };
  },
};
</script>
```

##### 所有组件
此处列出 Ant Design 中需要国际化支持的组件，你可以在演示里切换语言。

```html
<template>
  <div>
    <div class="change-locale">
      <span :style="{ marginRight: '16px' }">Change locale of components: </span>
      <h-radio-group :default-value="null" @change="changeLocale">
        <h-radio-button key="en" :value="null">
          English
        </h-radio-button>
        <h-radio-button key="cn" :value="zhCN">
          中文
        </h-radio-button>
      </h-radio-group>
    </div>
    <h-locale-provider :locale="locale">
      <div :key="(!!locale).toString()" class="locale-components">
        <!-- HACK: just refresh in production environment-->
        <div class="example">
          <h-pagination :default-current="1" :total="50" show-size-changer />
        </div>
        <div class="example">
          <h-select show-search style="width: 200px">
            <h-select-option value="jack">
              jack
            </h-select-option>
            <h-select-option value="lucy">
              lucy
            </h-select-option>
          </h-select>
          <h-date-picker />
          <h-time-picker />
          <h-range-picker style=" width: 200px " />
        </div>
        <div class="example">
          <h-button type="primary" @click="showModal">
            Show Modal
          </h-button>
          <h-button @click="info">
            Show info
          </h-button>
          <h-button @click="confirm">
            Show confirm
          </h-button>
          <h-popconfirm title="Question?">
            <a href="#">Click to confirm</a>
          </h-popconfirm>
        </div>
        <div className="example">
          <h-transfer
            :dath-source="[]"
            show-search
            :target-keys="[]"
            :render="item => item.title"
          />
        </div>
        <div :style="{ width: '319px', border: '1px solid #d9d9d9', borderRadius: '4px' }">
          <h-calendar :fullscreen="false" :value="moment()" />
        </div>
        <h-modal v-model="visible" title="Locale Modal">
          <p>Locale Modal</p>
        </h-modal>
      </div>
    </h-locale-provider>
  </div>
</template>
<script>
// you should use import zhCN from 'ant-design-vue/es/locale-provider/zh_CN'
import zhCN from 'ant-design-vue/es/locale-provider/zh_CN';
import { Modal } from 'ant-design-vue';
import moment from 'moment';
import 'moment/locale/zh-cn';
moment.locale('en');
const columns = [
  {
    title: 'Name',
    dataIndex: 'name',
    filters: [
      {
        text: 'filter1',
        value: 'filter1',
      },
    ],
  },
  {
    title: 'Age',
    dataIndex: 'age',
  },
];
export default {
  data() {
    return {
      visible: false,
      locale: null,
      zhCN,
    };
  },
  methods: {
    moment,
    showModal() {
      this.visible = true;
    },
    hideModal() {
      this.visible = false;
    },
    info() {
      Modal.info({
        title: 'some info',
        content: 'some info',
      });
    },
    confirm() {
      Modal.confirm({
        title: 'some info',
        content: 'some info',
      });
    },
    changeLocale(e) {
      const localeValue = e.target.value;
      this.locale = localeValue;
      if (!localeValue) {
        moment.locale('en');
      } else {
        moment.locale('zh-cn');
      }
    },
  },
};
</script>

<style scoped>
.locale-components {
  border-top: 1px solid #d9d9d9;
  padding-top: 16px;
}

.example {
  margin: 16px 0;
}

.example > * {
  margin-right: 8px;
}

.change-locale {
  margin-bottom: 16px;
}
</style>
```

### API
| 参数   | 说明                                                         | 类型   | 默认值 |
| :----- | :----------------------------------------------------------- | :----- | :----- |
| locale | 语言包配置，语言包可到 `ant-design-vue/lib/locale-provider/` 目录下寻找 | object | -      |
