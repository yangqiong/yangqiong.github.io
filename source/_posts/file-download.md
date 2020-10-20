---
title: 文件下载的几种方式
date: 2020-10-20 15:10
tags: Linux
---

## 服务端下载
前端
```
<a href="<FILE_URL>">下载</a>
```
当HTTP的响应头包含如下，浏览器会当做文件下载处理。
```
Content-Disposition: attachment; filename=<file name.ext>
```

## 前端下载
### download属性标签点击
[适合移动端，IE不支持，后续可能禁止跨域下载](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAnchorElement/download)
```
<a href="<FILE_URL>" download="<FILE_NAME>">
```

### download属性触发点击
```
function forceDownload(url, fileName){
    var xhr = new XMLHttpRequest();
    xhr.open("GET", url, true);
    xhr.responseType = "blob";
    xhr.onload = function(){
        var urlCreator = window.URL || window.webkitURL;
        var imageUrl = urlCreator.createObjectURL(this.response);
        var tag = document.createElement('a');
        tag.href = imageUrl;
        tag.download = fileName;
        document.body.appendChild(tag);
        tag.click();
        document.body.removeChild(tag);
    }
    xhr.send();
}
```

## 参考
* [Force browser to download image files on click
](https://stackoverflow.com/questions/17527713/force-browser-to-download-image-files-on-click)