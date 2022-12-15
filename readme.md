

#2022.12.15 
```angular2html
经过两天的各种百度和踩坑，终于打包成功了。遇到了各种各样的问题，下载速度慢是最浪费时间的，这个墙我是真的无力吐槽了。
还有明明有模块就是说找不到，官方文档 GetStart 走下来报错也是我不能理解的。

1.最重要的镜像设置为 淘宝镜像
    npm config set registry https://registry.npm.taobao.org/

2. .npmrc文件的添加(很重要)，否则 npm init electron-app@latest my-app 一直转圈圈
    ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/

3. 运行 npm install 报错，但是可以运行 npm run start，无伤大雅。
4. 运行 npm run package 打包成功. 至此完结
5. 运行 npm run make 报错，官方 issues/523  @electron-forge/maker-squirrel not found。
解决完找不到，又遇到 maker.ensureExternalBinariesExist is not a function  算了吧，都没人维护的感觉
```

正常情况  

```angular2html
// node -v  v16.14.2  "electron": "22.0.0"       "@electron-forge/cli": "^6.0.4",
npm init electron-app@latest my-app -- --template=webpack
cd my-app
npm run start
npm run package // success /out/my-app-win32-ia32/my-app.exe 
npm run make  // ERROR: Could not find module with name '@electron-forge/maker-squirrel'.
npm install --save-dev @electron-forge/maker-squirrel@6.0.0-beta.33
npm run make  // ERROR: maker.ensureExternalBinariesExist is not a function
.... // todo
```