## gh-uploader 基于GitHub的文件上传插件

### 安装

``` 

npm i gh-uploader
```

### Token加密

- 初始化传入GitHub项目信息（需要Base64加密，GitHub提交代码时，如果代码中存在明文access_token，此access_token会被自动删除）

``` 

var gh;
gh = {
    owner: '',
    repo: '',
    access_token: ''
}
gh = window.btoa && btoa(JSON.stringify(gh));
console.log(gh);
```

* 需要在提交前删除加密代码，只保留加密后的Base64字符串

### 使用

* 引入

``` 

import GhUploader from 'gh-uploader';
```
或者
```
<script src="https://unpkg.com/gh-uploader@0.0.4/index.js"></script>
```

* 初始化

``` 

var gh = 'eyJvd25lciI6IkFc3**************ZWZjRjZWUyZGVhIn0=';//加密获得的Base64字符串
var ghUpload = new GhUploader(gh);

```

* 上传字符串

``` 

ghUpload.put({
    path: '1.txt',
    content: '测试',
}).then(function (res) {
    console.log(res);
}).catch(function (error) {
    console.log(error);
});

```

* 上传文件

``` 

var files = e.target.files || e.dataTransfer.files;
ghUpload.put({
    path: files[0].name,
    content: files[0],
}).then(function (res) {
    console.log(res);
}).catch(function (error) {
    console.log(error);
});

```
