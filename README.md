\# Chromium 141 指纹浏览器阶段性成果介绍（FingerPrintJS / Pro 全通过）



\# https://fingerprintjs.github.io/fingerprintjs/



本版本是基于 Chromium 141 深度定制的 Anti-Fingerprinting 浏览器，专门针对 FingerprintJS 与其 Pro 版本的检测逻辑进行对抗研发。

本项目支持对浏览器中几乎全部指纹字段进行重写、伪造和自定义，运行 FingerprintJS 官方测试站点可实现全量通过。


\# 下载地址
通过网盘分享的文件：chrome.7z
链接: https://pan.baidu.com/s/1Qqt3dAEm3F1I_Ntm0XpnWQ?pwd=vv9e 提取码: vv9e 



\## 启动方式



安装完成后，可通过脚本或 CMD 执行以下命令启动浏览器，并加载自定义指纹文件：



```

chrome.exe --ruyi="{\\"ruyiFile\\":\\"C:\\\\chromiun141\\\\fp.txt\\"}" --enable-webgl --ignore-gpu-blocklist --enable-unsafe-webgl --no-sandbox https://fingerprintjs.github.io/fingerprintjs/

```



其中：



\* ruyiFile 用于指定你的自定义指纹脚本路径

\* 全部指纹参数会从该文件读取并覆盖浏览器真实指纹

\* 支持 WebGL、Audio、Canvas、GPU、Hardware、WebRTC 等多维度指纹伪造



\## 指纹脚本示例（fp.txt）



以下为示例指纹配置文件，可直接创建为 fp.txt 使用：



```

webdriver:0

useragent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36

platform:win646

fonts:ZWAdobeF,TRAJAN PRO

monospacePreferences:87.375

sansPreferences:90.66667175292969

serifPreferences:90.66667175292969

webaudio:0.0001

screenHeight:906

screenWidth:1707

avaiscreenHeight:866

avaiscreenWidth:1707

colorDepth:24

canvas:39

langugages:zh-CN,en-US

timezone:Asia/Shanghai

deviceMemory:8

hardwareConcurrency:32

unmaskedRenderer:Google Inc. (NVIDIA)

unmaskedVendor:ANGLE (NVIDIA, NVIDIA GeForce RTX 3080 Laptop GPU (0x0000249C) Direct3D11 vs\_5\_0 ps\_5\_0, D3D11)

gl\_version:WebGL 1.0

gl\_vendor:WebKit

gl\_renderer:WebKit WebGL

gl\_shading:WebGL GLSL ES 1.0 (1.0)

preserveDrawingBuffer:true

xrCompatible:true

premultipliedAlpha:true

stencil:true

desynchronized:true

powerPreference:high-performance

failIfMajorPerformanceCaveat:true

alpha:true

antialias:true

depth:true

ALIASED\_POINT\_SIZE\_RANGE:1,1024

SHADER\_LOW\_FLOAT:127,127,24

supportedExt:ANGLE\_instanced\_arrays,EXT\_blend\_minmax,EXT\_clip\_control,EXT\_color\_buffer\_half\_float,EXT\_depth\_clamp,EXT\_disjoint\_timer\_query,EXT\_float\_blend,EXT\_frag\_depth,EXT\_polygon\_offset\_clamp,EXT\_shader\_texture\_lod,EXT\_texture\_compression\_bptc,EXT\_texture\_compression\_rgtc,EXT\_texture\_filter\_anisotropic,EXT\_texture\_mirror\_clamp\_to\_edge,EXT\_sRGB,KHR\_parallel\_shader\_compile,OES\_element\_index\_uint,OES\_fbo\_render\_mipmap,OES\_standard\_derivatives,OES\_texture\_float,OES\_texture\_float\_linear,OES\_texture\_half\_float,OES\_texture\_half\_float\_linear,OES\_vertex\_array\_object,WEBGL\_blend\_func\_extended,WEBGL\_color\_buffer\_float,WEBGL\_compressed\_texture\_s3tc,WEBGL\_compressed\_texture\_s3tc\_srgb,WEBGL\_debug\_renderer\_info,WEBGL\_debug\_shaders,WEBGL\_depth\_texture,WEBGL\_draw\_buffers,WEBGL\_lose\_context,WEBGL\_multi\_draw,WEBGL\_polygon\_mode

CLIP\_DEPTH\_MODE\_EXT:true

```



你可以按照需要继续新增任意指纹字段，本浏览器会自动解析并覆写。



\## 课程与源码学习



如需学习 FingerprintJS 指纹识别原理、浏览器指纹伪造体系、Chromium 源码修改、Canvas/WebGL/Audio/GPU 指纹定制等内容，请查看课程文档：



\[https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp](https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp)



