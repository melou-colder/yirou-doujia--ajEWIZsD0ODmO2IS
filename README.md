
小程序录制视频；10\-30秒；需要拍摄人脸，大声朗读数字（123456）这种。


## 1\.camera组件


camera页面内嵌的区域相机组件。注意这不是点击后全屏打开的相机


camera只支持小程序使用；[官网链接](https://github.com)


![](https://img2024.cnblogs.com/blog/2237618/202408/2237618-20240830150416743-1945450748.png)


### 1\.2 效果图


![](https://img2024.cnblogs.com/blog/2237618/202408/2237618-20240830151336818-874263568.png)


 


### 1\.3 页面布局


camera 设置宽100%，高度通过uni.getSystemInfo获取，全屏展示。在通过定位把提示文字等信息放上去；


录制完毕，遮罩提示,完成录制,确认返回；


![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

copy
```
<template>
    <view class="camera-position">
        <camera device-position="front" flash="auto" @error="onCameraError"
            :style="'width: 100%; height: '+ screenHeight +'px;'">
            
            <image src="../../static/face/face-avater.png" style="width: 100%; height: 55vh; margin:22vh 0 0 0;"
                v-if="!achieveShow">image>
        camera>

        
        <view class="camera-top text-center" v-show="!achieveShow">
            <view class="text-lg text-red">
                请面向屏幕
            view>
            <view class="text-xl text-white margin-tb-xs">
                <text class="text-lg">用普通话大声读text>
                <text class="text-red text-bold margin-left-xs">123456text>
            view>
            <view class="text-xxl text-red">
                <text class="text-df text-white">倒计时text>
                <text class="text-red text-bold margin-lr-xs">{{totalSeconds}}text>
                <text class="text-df text-white">Stext>
            view>
        view>

        
        <view class="achieve-shade" :style="'width: 100%; height: '+ screenHeight +'px;'" v-if="achieveShow">
            <view class="" style="font-size: 120rpx;color: #1977FF;">
                <text class="cuIcon-roundcheck">text>
            view>
            <view class="text-xl text-white margin-tb-sm">
                已完成人脸识别
            view>
            <button class="cu-btn line-blue round lg" @click="confirmBut">确定button>
        view>
    view>
template>
```


View
注：行内css `text-xl text-white margin-tb-xs`使用了 [ColorUI\-UniApp](https://link.juejin.cn/?target=https%3A%2F%2Fext.dcloud.net.cn%2Fplugin%3Fid%3D239 "https://ext.dcloud.net.cn/plugin?id=239") 插件内容


css样式


![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

copy

css
js代码


![](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif)![](https://images.cnblogs.com/OutliningIndicators/ExpandedBlockStart.gif)

copy

js
注：第一次进入页面，有时候摄像头会启动失败，需要重新点击打开；


案例地址： [https://gitee.com/jielov/uni\-app\-tabbar](https://github.com):[西部世界官网](https://tianchuang88.com)


## 2\.微信官方api


**微信小程序**中需要使用手机**拍摄照片以及视频**;使用`wx.chooseMedia`API来实现;


该API用于拍摄或从手机相册中选择图片或视频，官网链接为：[wx.chooseMedia\-微信开放文档](https://github.com)



[?](https://github.com)

| 12345678910111213141516171819 | `wx.chooseMedia({``//数量 1-9``count: 1,``//时长``maxDuration:` `'10'``,``// 文件类型  image 图片  video视频   mix同时选择图片和视频``mediaType: [``'video'``],``// 图片和视频选择的来源: album 相册  camera相机拍摄``sourceType: [``'camera'``],``//摄像头: back 前置  front 后置摄像头` `camera:` `'back'``,``success(res) {``console.log(res)``console.log(res.tempFiles[0].tempFilePath)``},``fail(err) {``console.log(err)``}``})` |
| --- | --- |



　　


