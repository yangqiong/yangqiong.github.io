---
title: 管理后台确认对话框最佳实践
date: 2019-09-22 15:34:03
tags:
---

管理后台开发中如上图所示的一种对话框，比如说驳回审核，添加评论，审核确定等。其中涉及：
1. 点击按钮弹出对话框
2. 显示信息，并可能需要填入原因或者评论
3. 点击确认向后台发送请求，确认按钮处于loading状态，成功后对话框消失；错误则弹出提示
4. 或者点击取消
![](/images/admin-confirm-modal.png)

涉及页面的状态有：
1. visible 对话框是否显示
2. value 原因或者评论内容
3. loading 确认按钮的状态

如果有涉及大量此类操作，并在外部维护上面三种状态以及请求前后行为，还是一件很重复的工作。

其实此类操作的不同点在于两点
1. 请求的接口不同（请求的前后行为是一致的）
2. 对话框的内容不同（Input的行为是相同的）

**总结下就是把visible, value, loading状态都放在组件内部，只暴露出请求接口**。

## ConfirmModal组件代码
主要暴露出两个函数：
1. body: 把`{value, setValue}`给到外部用于Input的处理，需返回对话框主题显示的UI
2. onOk: 回调函数包含`value`，用于请求发送；函数返回true则表示成功隐藏对话框，否则不隐藏

``` [javascript] [title] [url] [link text]
import React, { useState } from 'react';
import { Modal } from 'antd';
import ReactDOM from 'react-dom'

const ConfirmModal = props => {
  let [visible, setVisible] = useState(true);
  let [loading, setLoading] = useState(false);
  let [value, setValue] = useState(null);

  const confirm = async () => {
    setLoading(true);
    let result = await props.onOk({value});
    if (result !== true){
      setVisible(true);
    } else {
      setVisible(false);
    }
    setLoading(false);
  }
  const close = () => setVisible(false);

  return (
    <Modal
      title="驳回原因"
      visible={visible}
      onOk={confirm}
      onCancel={close}
      confirmLoading={loading}
    >
      {props.body({value, setValue})}
    </Modal>
  )
}

ConfirmModal.open = options => {
  let el = document.createElement("div");
  ReactDOM.render(<ConfirmModal {...options}/>, el);
  document.body.appendChild(el);
}

ConfirmModal.defaultProps = {
  body: ({value, setValue}) => {}, // 返回对话框body显示内容
  onOk: ({value}) => {},           // 返回处理结果
}

export default ConfirmModal;
```

## 调用ConfirmModal
```
export default () => {
  let formItemLayout = {
    labelCol: { span: 4 },
    wrapperCol: { span: 14 },
  }

  let confirmModalOption = {
    body: ({ value, setValue }) => {
      return (
        <Form >
          <Form.Item label="申请企业" {...formItemLayout}>
            <span className="ant-form-text">深圳腾讯科技有限公司</span>
          </Form.Item>
          <Form.Item label="驳回原因" {...formItemLayout} required={true}>
            <Input.TextArea value={value} onChange={(event) => setValue(event.target.value)}/>
          </Form.Item>
        </Form>
      )
    },
    onOk: async ({value}) => {
      console.log(value);
      await sleep(3000) // 模拟请求
      return true; // 成功
    }
  }

  return (
    <div>
      <Button onClick={() => ConfirmModal.open(confirmModalOption)}>驳回</Button>
    </div>
  )
}
```