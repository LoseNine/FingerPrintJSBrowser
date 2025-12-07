# Chromium 141 指纹浏览器阶段成果展示

以下为可直接复制使用的 **原始 Markdown 文本**，用于介绍你针对 **FingerprintJS / Pro 全通过** 的定制版 Chromium 141 指纹浏览器，包括下载方式、启动方式、指纹脚本示例与课程链接。

---

# 🚀 Chromium 141 指纹浏览器（专为 FingerprintJS / Pro 定制）

本项目是基于 **Chromium 141 深度定制的 Anti-Fingerprinting 浏览器**，核心目标是：

* 对抗 **FingerprintJS / Fingerprint Pro** 全量指纹检测
* 支持伪造、覆写、定制 **全部关键指纹**（Canvas / WebGL / Audio / GPU / UA / Fonts 等）
* 采用独立参数 `--ruyi` 加载外部指纹脚本，使浏览器成为“可编程指纹容器”
* 基线版本验证可通过 FingerprintJS 官方站点

👉 **检测地址：** [https://fingerprintjs.github.io/fingerprintjs/](https://fingerprintjs.github.io/fingerprintjs/)

---

# 📦 浏览器下载

通过百度网盘分享的文件：`chrome.7z`

**下载链接：** [https://pan.baidu.com/s/1Qqt3dAEm3F1I_Ntm0XpnWQ?pwd=vv9e](https://pan.baidu.com/s/1Qqt3dAEm3F1I_Ntm0XpnWQ?pwd=vv9e)
**提取码：** `vv9e`

下载后解压，可直接双击使用。

---

# 🧩 浏览器启动方式（加载你的指纹脚本）

在浏览器目录执行以下命令：

```
chrome.exe --ruyi="{\"ruyiFile\":\"C:\\chromiun141\\fp.txt\"}" \
  --enable-webgl --ignore-gpu-blocklist --enable-unsafe-webgl --no-sandbox \
  https://fingerprintjs.github.io/fingerprintjs/
```

解释：

* `--ruyi`: 加载外部指纹脚本
* 指纹脚本可根据需要完全自定义

---

# 📝 指纹脚本示例（fp.txt）

以下为一个完整可用的示例，可直接保存为：`C:\chromiun141\fp.txt`

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
unmaskedVendor:ANGLE (NVIDIA, NVIDIA GeForce RTX 3080 Laptop GPU (0x0000249C) Direct3D11 vs_5_0 ps_5_0, D3D11)
gl_version:WebGL 1.0
gl_vendor:WebKit
gl_renderer:WebKit WebGL
gl_shading:WebGL GLSL ES 1.0 (1.0)
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
ALIASED_POINT_SIZE_RANGE:1,1024
SHADER_LOW_FLOAT:127,127,24
supportedExt:ANGLE_instanced_arrays,EXT_blend_minmax,EXT_clip_control,EXT_color_buffer_half_float,EXT_depth_clamp,EXT_disjoint_timer_query,EXT_float_blend,EXT_frag_depth,EXT_polygon_offset_clamp,EXT_shader_texture_lod,EXT_texture_compression_bptc,EXT_texture_compression_rgtc,EXT_texture_filter_anisotropic,EXT_texture_mirror_clamp_to_edge,EXT_sRGB,KHR_parallel_shader_compile,OES_element_index_uint,OES_fbo_render_mipmap,OES_standard_derivatives,OES_texture_float,OES_texture_float_linear,OES_texture_half_float,OES_texture_half_float_linear,OES_vertex_array_object,WEBGL_blend_func_extended,WEBGL_color_buffer_float,WEBGL_compressed_texture_s3tc,WEBGL_compressed_texture_s3tc_srgb,WEBGL_debug_renderer_info,WEBGL_debug_shaders,WEBGL_depth_texture,WEBGL_draw_buffers,WEBGL_lose_context,WEBGL_multi_draw,WEBGL_polygon_mode
CLIP_DEPTH_MODE_EXT:true
```

你可以新增/修改任意字段，本浏览器会在底层完成指纹注入。

---

# 📚 想深入学习？

如果你希望掌握：

* 浏览器指纹检测原理
* FingerprintJS / Pro 的全部指纹来源
* 如何在 Chromium 中修改 WebGL / Canvas / Audio / GPU 指纹
* 如何构建自己的定制反指纹浏览器

请查看课程文档：

👉 **[https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp](https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp)**

如需我继续为你：

* 制作 README 的图片版本
* 生成视频教授文案
* 扩展更高级的指纹脚本模板
* 补充指纹字段说明

随时告诉我即可。
