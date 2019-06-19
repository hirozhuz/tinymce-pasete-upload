# paste-upload TinyMCE Plugin

为tinymce富文本编辑器开发的插件。

支持 Ctrl+C/Ctrl+V 上传，支持拖拽上传，也支持 QQ/微信截图上传。

# quick start （开始使用）

## 1.clone本项目到本地
## 2.npm install / yarn install
## 3.npm run build / yarn run build
    打包好的插件plugin.js在dist目录
## 4.在tinymce/plugins目录下新建文件夹paste-upload。将上一步打包好的plugin.js复制到paste-upload文件夹内。
## 5.tinymce.init 方法中，plugins的值新增 paste-upload

# 配置项

## tinymce.init 方法中可添加如下的自定义配置内容
    pasteUploadConfig: {
            url: 'http://api.qdqcwy.cn/upload',
            headers: [
              {
                name: 'token',
                value: '123'
              }
            ],
            diyExtractUrl: true,
            extractUrlFun: function (json) {
              return json.msg;
            }
          }

### url: 图片上传接口
### headers： 请求头集合
### diyExtractUrl：图片上传到服务器之后，服务器把上传的图片地址返回，但插件其实并不知道接口返回的json数据格式，无法自动获取到返回结果中的图片地址，因为开放一个配置开关。
### extractUrlFun：自定义获取接口返回结果中的图片地址字段。

# 具体代码示例可参考static目录下的index.html
