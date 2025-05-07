常用页面案例

## api接口

描述：这是一个api接口文件的代码案例

注意：

1、axios必须从jpaas-component/utils/request导入，不允许修改；

2、api必须有按下面代码案例的格式输出。

```js
/**
 * 示例Api
 */
import { axios } from 'jpaas-component/utils/request' // 不允许修改

const api = {
  apiList: '/demo/api/list',// 列表
  apiRemove: '/demo/api/remove',// 删除
}

// 必须按下面代码案例的风格
export const demoAPI = {
  apiList (parameter) {
    return axios({
      url: api.apiList,
      method: 'get',
      params: parameter
    })
  },
  apiRemove (parameter) {
    return axios({
      url: api.apiRemove,
      method: 'post',
      data: parameter
    })
  }
}
```

## router路由

描述：这是一个router路由的代码案例。

注意：

1、BasicLayout、HRouterView必须从jpaas-component/layouts导入，不允许修改；

2、svg图标导入，除了文件名，其他路径不允许修改，必须按下面案例输出；

```js
import { BasicLayout, HRouterView } from 'jpaas-component/layouts'
import FileText from 'jpaas-component/icons/svg/outline/file-text.svg?inline'
export default [
  {
    path: '/',
    name: 'index',
    component: BasicLayout,
    redirect: '/default',
    meta: {
      title: '管理系统'
    },
    children: [
      {
        path: '/markManage',
        name: 'markManage',
        redirect: '/markManage/pageManage',
        component: HRouterView,
        meta: {
          icon: FileText,
          keepAlive: false,
          title: '管理页面',
          permission: ['server:signManage:*']
        },
        children: [
          {
            path: '/markManage/pageManage',
            name: 'pageManage',
            hideChildrenInMenu: true,
            component: () => import('@/views/demo/markManage/pageManage/pageManageList.vue'),
            meta: {
              keepAlive: false,
              title: '管理页面1'
            }
          },
        ]
      }
    ]
  }
]
```

## 表格

描述：这是一个表格页面的示例代码，具有批量操作、删除、导入、导出、数据检索功能。

注意：

1、在使用组件时，组件的使用和导入是配套的，所以在import导入和template模版重用的组件要对应；

2、如果使用api接口的话，必须要import { demoAPI } from '@/api/demo'；

3、表格页面中的loadData的数据获取必须按照下面代码的格式，必须在data中调用api获取；

4、如果表格有按钮、搜索框等功能，必须将其放在toolbarLeft或toolbarRight的template插槽内；

5、表格项的字段columns，必须要有，必须在computed中；

6、表格页面最外层必须用<h-card>组件包裹；

7、toolbarLeft或toolbarRight的template插槽必须放在<h-table>组件内部，例如：

<template>
​    <h-table

​      ref="table"

​      :columns="columns"

​      :data="loadData"

​      :rowKey="(record) => record.iid">

​      <template #toolbarLeft>

​      </template>

​      <template #toolbarRight>

​      </template>

​    </h-table>

</template>

```vue
<template>
    <!-- 表格table -->
    <h-table
      ref="table"
      :columns="columns"
      :data="loadData"
      :rowKey="(record) => record.iid">
      <!-- 组件内头部有按钮、搜索框等组件，必须放在toolbarLeft或toolbarRight插槽中，这种插槽必须放在h-table组件内部 -->
      <template #toolbarLeft>
        <h-button
          type="primary"
          @click="handleAdd"
        >新增</h-button
        >
        <h-button
          type="link"
          @click="importFile"
        >导入</h-button
        >
        <h-button
          type="link"
          @click="exportFile"
        >导出</h-button
        >
      </template>
	  <!-- 组件内头部有按钮、搜索框等组件，必须放在toolbarLeft或toolbarRight插槽中，这种插槽必须放在h-table组件内部 -->
      <template #toolbarRight>
        <h-search
          v-model="queryParam.searchText"
          :maxLength="80"
          :placeholder="'请输入名称'"
          @clean="$refs.table.refresh()"
          @search="$refs.table.refresh()" />
      </template>
      <template #demoAttribute="text, record">
        <span>{{ record.demoAttribute || '-' }}</span>
      </template>
      <template #createTime="text, record">
        {{ record.createTime }}
      </template>
      <template #action="text, record">
        <a @click="handleEdit(record)">编辑</a>
        <h-popconfirm
          title="你确定要删除这行内容吗？"
          @confirm="removeSingle(record.iid)">
          <a>删除</a>
        </h-popconfirm>
      </template>
    </h-table>
    <!-- <import-modal
      ref="importModalRef"
      @importSuccess="$refs.table.refresh()"></import-modal> -->
</template>
<script>
import { HCard, HButton, HSearch, HDownload, HTable, HPopconfirm } from 'jpaas-component'
import { demoAPI } from '@/api/demo/' // 必须要引入api文件
// import ImportModal from './demoImport.vue'
export default {
  name: 'DemoManageList',
  components: {
    HCard,
    HTable,
    HButton,
    HSearch,
    HDownload,
    // ImportModal,
    HPopconfirm
  },
  data() {
    return {
      queryParam: {
        searchText: ''
      },
      // 表格的数据，必须在data中，不允许写在其他位置
      loadData: (parameter) => {
        return demoAPI
          .list({ searchText: this.queryParam.searchText, ...parameter })
          .then((res) => {
            if (res.success) {
              return res.data
            }
          })
      }
    }
  },
  watch: {},
  computed: {
    columns() {
      const columns = [
        {
          title: '名称',
          dataIndex: 'demoName',
          // width: '35%',
          scopedSlots: { customRender: 'demoName' }
        },
        {
          title: '属性',
          dataIndex: 'demoAttribute',
          scopedSlots: { customRender: 'demoAttribute' }
        },
        {
          title: '编辑人',
          dataIndex: 'creatorName'
        },
        {
          title: '时间',
          dataIndex: 'createTime',
          width: '15%',
          scopedSlots: { customRender: 'createTime' }
        },
        {
          title: '操作',
          dataIndex: 'action',
          align: 'center',
          key: 'action',
          // width: '20%',
          scopedSlots: { customRender: 'action' }
        }
      ]
      return columns
    }
  },
  methods: {
    // 新增
    handleAdd() {
      console.log('新增')
    },
    // 编辑
    handleEdit(record) {
      console.log('编辑', record)
    },
    // 删除函数
    handleRemove(data) {
      demoAPI.demoRemove({ ids: data.join(',') }).then((res) => {
        if (res.success) {
          this.$message.success('删除成功')
          this.$refs.table.refresh()
        }
      })
    },
    // 单个删除
    removeSingle(iid) {
      this.handleRemove([iid])
    },
    // 导入
    importFile() {
      this.$refs.importModalRef.visible = true
    },
    // 导出
    exportFile() {
      this.exportuids = this.selectedRowKeys.join(',')
      this.hrefUrl =
        '/api-gateway/jpaas-demo-server/demo/demo/export?ids=' + this.exportuids
      this.fileName = 'demo.xlsx'
      this.$refs.download.download()
    }
  }
}
</script>

```

## 表单

描述：这是一个表单的示例代码，可以实现数据录入的功能。

注意：

1、在使用表单时，优先使用h-form-model和h-form-model-item组件，他们是配套使用和导入的，所以在import导入的时候，也要同时导入hFormModel和hFormModelItem。

2、如果使用api接口的话，必须要import { demoAPI } from '@/api/demo'；

3、必须生成单独的Vue文件代码、API调用函数文件代码、路由配置文件代码；

4、表单页面最外层必须用<h-card>组件包裹；

```vue
<template>
  <h-card>
    <h-form-model
      ref="ruleForm"
      :model="form"
      :rules="rules"
      layout="vertical">
      <h-form-model-item
        label="用户名"
        prop="username">
        <h-input
          v-model="form.username"
          placeholder="请输入用户名" />
      </h-form-model-item>
      <h-form-model-item
        label="密码"
        prop="password">
        <h-input-password
          v-model="form.password"
          placeholder="请输入密码" />
      </h-form-model-item>
      <h-form-model-item
        label="邮箱"
        prop="email">
        <h-input
          v-model="form.email"
          placeholder="请输入邮箱" />
      </h-form-model-item>
      <h-form-model-item>
        <h-button
          type="primary"
          @click="submitForm"
          :loading="loading"
        >提交</h-button
        >
      </h-form-model-item>
    </h-form-model>
  </h-card>
</template>

<script>
import { HCard, HFormModel, HFormModelItem, HInput, HInputPassword, HButton } from 'jpaas-component'
import { demoAPI } from '@/api/demo'

export default {
  components: {
    HCard,
    HFormModel,
    HFormModelItem,
    HInput,
    HInputPassword,
    HButton
  },
  data() {
    return {
      form: {
        username: '',
        password: '',
        email: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' }
        ],
        password: [{ required: true, message: '请输入密码', trigger: 'blur' }],
        email: [
          { required: true, message: '请输入邮箱', trigger: 'blur' },
          {
            type: 'email',
            message: '请输入正确的邮箱地址',
            trigger: ['blur', 'change']
          }
        ]
      },
      loading: false
    }
  },
  methods: {
    submitForm() {
      this.$refs.ruleForm.validate((valid) => {
        if (valid) {
          this.loading = true
          // 调用API接口提交表单数据
          demoAPI
            .addForm(this.form)
            .then(() => {
              this.$message.success('提交成功!')
              this.resetForm()
            })
            .finally(() => {
              this.loading = false
            })
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm() {
      this.$refs.ruleForm.resetFields()
    }
  }
}
</script>

```

## 侧边栏

描述：这是一个侧边栏页面的示例代码。

注意：

1、在使用侧边栏页面组件时，h-sider-panel和h-menu是同时使用的，这是一个完整搭配的组件；

2、侧边栏顶部标题必须放在leftSiderTitle插槽中，必须要有；

3、侧边栏左侧切菜单必须放在leftSiderContent插槽中，必须要有，h-menu组件必须写在这个插槽里；

4、侧边栏右边展示内容必须放在content插槽中，必须要有，内部必须是元素标签或者自定义组件；

5、表格项的字段columns，必须要有，必须在computed中；

6、菜单数据源用orgTreeData，数据格式是固定的，不允许修改，特别是params属性必须要有；

```vue
<template>
  <!-- 在使用侧边栏时，h-sider-panel和h-menu是同时使用的，这是一个完整搭配的组件 -->
  <h-sider-panel>
    <!-- 侧边栏顶部标题插槽，必须要有，这个插槽只允许放入文本 -->
    <template #leftSiderTitle>侧边栏案例</template>
    <!-- 侧边栏左侧菜单插槽，必须要有，这个插槽里必须放入h-menu组件 -->
    <template #leftSiderContent>
      <h-menu
        ref="hMenu"
        :dataSource="orgTreeData"
        :selectedKeys="selectedKeys"
        @click="handleClick">
      </h-menu>
    </template>
    <!-- 侧边栏右边展示内容插槽，必须要有，内部必须是元素标签或者自定义组件 -->
    <template #content>
      <!-- 页面1 -->
      <div v-if="selectedKeys[0] === '1'">页面1</div>
      <!-- 页面2 -->
      <div v-if="selectedKeys[0] === '2'">页面2</div>
    </template>
  </h-sider-panel>
</template>

<script>
import { HSiderPanel, HMenu } from 'jpaas-component'

export default {
  name: 'DemoSiderPanel',
  components: {
    HSiderPanel,
    HMenu
  },
  data() {
    return {
      selectedKeys: ['1']
    }
  },
  computed: {
    // orgTreeData是菜单数据源，数据格式是固定的，不允许修改
    orgTreeData() {
      const orgTreeData = [ // 数据内的数据格式是固定的，不允许修改
        {
          params: { type: 0 }, // params属性必须要有
          key: '1',
          title: '页面1'
        },
        {
          params: { type: 0 }, // params属性必须要有
          key: '2',
          title: '页面2'
        }
      ]
      return orgTreeData
    }
  },
  methods: {
    // 点击后切换的必须是元素标签或者自定义组件
    handleClick(e) {
      this.selectedKeys = [e.key] || ['1']
    }
  }
}
</script>

```

## 导入

描述：这是一个导入弹窗的示例代码。

注意：

1、如果使用api接口的话，必须要import { demoAPI } from '@/api/demo'；

2、在使用组件时，组件的使用和导入是配套的，所以在import导入和template模版重用的组件要对应；

```vue
<template>
  <div>
    <h-modal
      title="导入"
      :visible="visible"
      :destroyOnClose="true"
      width="760px"
      @cancel="handleCancel">
      <div>
        <div style="margin: 0 20px 0 20px">
          <div v-if="showImport">
            <ul style="line-height: 30px">
              <li>
                点击下载
                <a
                  href="javascript:;"
                  @click="downloadTemplate">
                  导入模版
                </a>
              </li>
              <li>填写须知：</li>
              <p style="margin: 0">1.文件格式支持.xlsx；</p>
            </ul>
            <!-- 拖拽框 -->
            <h-upload-dragger
              name="file"
              :accept="accept"
              :multiple="false"
              @change="handleChange"
              :remove="handleFileRemove"
              :fileList="tempFileList"
              :beforeUpload="beforeUpload">
              <p class="ant-upload-text">点击或将文件拖拽到这里上传</p>
              <p class="ant-upload-hint">支持扩展名：.xlsx</p>
            </h-upload-dragger>
          </div>
          <div v-else>
            <!-- 导入结果 -->
            <h-result
              :status="importSuccess ? 'success' : 'error'"
              :title="importSuccess ? '导入完成！' : '导入失败！'"></h-result>
            <ul>
              <li>
                本次共成功导入{{ importRes.successFileCount }}个文件，失败{{
                  importRes.failureFileCount
                }}个！包含成功导入数据{{ importRes.successRowCount }}条，失败{{
                  importRes.failureRowCount
                }}条！
              </li>
              <li v-if="!importRes.flag"><a href="javascript:;" @click="downloadError">错误详情</a></li>
            </ul>
          </div>
        </div>
      </div>
      <template slot="footer">
        <h-button
          key="back"
          @click="handleCancel"
        >取消</h-button
        >
        <h-button
          type="primary"
          v-if="showImport"
          :loading="okLoading"
          @click="handleImport">
          导入
        </h-button>
      </template>
    </h-modal>
    <h-download
      :hrefUrl="hrefUrl"
      ref="download"></h-download>
  </div>
</template>

<script>
import { HButton, HModal, HDownload, HUploadDragger, HResult } from 'jpaas-component'
import { demoAPI } from '@/api/demo'

export default {
  name: 'demoImport',
  components: {
    HButton,
    HModal,
    HDownload,
    HUploadDragger,
    HResult
  },
  data () {
    return {
      visible: false,
      okLoading: false,
      tempFileList: [],
      fileList: [],
      hrefUrl: '',
      accept: '.xlsx,.xls',
      steps: [
        {
          title: '上传数据文件'
        },
        {
          title: '文件格式检查'
        },
        {
          title: '导入'
        }
      ],
      showImport: true,
      importRes: {},
      importSuccess: true
    }
  },
  methods: {
    // 取消
    handleCancel () {
      this.visible = false
      this.tempFileList = []
      this.fileList = []
      this.okLoading = false
      this.showImport = true
      this.importRes = {}
      this.importSuccess = true
    },
    // 导入
    handleImport () {
      if (this.tempFileList.length === 0) {
        this.$notification['error']({
          message: '请选择要导入的文件',
          duration: 2
        })
        return
      }
      this.okLoading = true
      this.tempFileList = this.tempFileList.filter(
        (fileObj) => fileObj.status !== 'error'
      )
      const formData = new FormData()
      this.tempFileList.forEach(function (file) {
        formData.append('fileList', file)
      })

      demoAPI.importQualityData(formData).then((res) => {
        if (res.success) {
          this.importOk(res.data)
        }
      })
    },
    // 导入完成
    importOk (data) {
      this.tempFileList = []
      this.fileList = []
      this.okLoading = false
      this.showImport = false
      this.importRes = data
      this.importSuccess = data.flag
      this.$emit('importSuccess') // 刷新数据
    },
    // 下载模版
    downloadTemplate () {
      this.hrefUrl =
        '/api-gateway/jpaas-demo-server/demo/demo/demo'
      this.$refs.download.download()
    },
    // 下载错误
    downloadError () {
      this.hrefUrl = '/api-gateway/jpaas-demo-server/demo/demo/demo?errorMsgFilePath=' + this.importRes.errorMsgFilePath
      this.$refs.download.download()
    },
    // 上传改变
    handleChange (info) {
      this.fileList = info.fileList.filter((file) => {
        return file.status === 'done'
      })
    },
    // 删除文件
    handleFileRemove (file) {
      this.tempFileList.forEach((item, index) => {
        if (item.iid === file.iid) {
          this.tempFileList.splice(index, 1)
        }
      })
      this.fileList.forEach((item, index) => {
        if (item.iid === file.iid) {
          this.fileList.splice(index, 1)
        }
      })
    },
    // 上传前校验
    beforeUpload (file) {
      let flag = true
      if (file && file.size === 0) {
        this.$message.warn('文件大小不能为0!')
        flag = false
      }
      let isTrue = false
      this.tempFileList.some((item) => {
        if (file.name === item.name) {
          file.status = 'error'
          isTrue = true
        }
      })
      // 文件数量超过1个
      if (this.tempFileList.length === 1) {
        this.$notification['error']({
          message: '文件数量超过1个！'
        })
        flag = false
      }
      // 文件名称重复
      if (isTrue) {
        this.$notification['error']({
          message: '文件名称重复！'
        })
        flag = false
      }
      if (flag) {
        this.tempFileList.push(file)
        // 优先去掉上传出错的文件
        while (
          this.tempFileList.length > 10 &&
          this.tempFileList.some((fileObj) => fileObj.status === 'error')
        ) {
          const findIndex = this.tempFileList.findIndex(
            (fileObj) => fileObj.status === 'error'
          )
          this.tempFileList.splice(findIndex, 1)
        }
        // 如果仍然超出，则删除较早上传的文件
        if (this.tempFileList.length > 10) {
          this.tempFileList = this.tempFileList.slice(-10)
        }
      }
      return false
    }
  }
}
</script>

<style scoped lang="less">
::v-deep .ant-checkbox-wrapper {
  margin: 10px 12px 0 0;
}

::v-deep .ant-result {
  padding: 28px 32px;
}
</style>

```

