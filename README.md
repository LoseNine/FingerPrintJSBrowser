# Chromium 141 Anti-Fingerprinting Browser

指纹浏览器（针对 FingerprintJS / Fingerprint Pro 全量通过）

---

# 🎯 项目简介

本项目基于 **Chromium 141** 深度定制，实现了一套 **全链路可编程指纹系统**，针对 FingerprintJS（含 Pro 版本）可稳定通过。浏览器支持通过外部脚本（fp.txt）动态控制几乎全部可被探测的浏览器指纹，包括：

* Navigator 环境指纹（UA / platform / languages / webdriver …）
* WebGL & Canvas 渲染指纹（GPU、扩展、纹理、着色器 …）
* WebAudio 音频哈希指纹
* 字体与文本排版指纹
* 屏幕与显示参数
* GPU Unmasked 信息
* 扩展与扩展参数（extensionParameters）

浏览器支持启动参数 `--ruyi` 指定指纹文件，实现 **真正意义上的浏览器级伪造**，而非 JS Hook。

👉 **检测地址（官方 FingerprintJS Demo）**：
[https://fingerprintjs.github.io/fingerprintjs/](https://fingerprintjs.github.io/fingerprintjs/)

---

# 📦 下载地址

浏览器已打包为 `chrome.7z`：

* **网盘链接**：[https://pan.baidu.com/s/1Qqt3dAEm3F1I_Ntm0XpnWQ?pwd=vv9e](https://pan.baidu.com/s/1Qqt3dAEm3F1I_Ntm0XpnWQ?pwd=vv9e)
* **提取码**：`vv9e`

解压后可直接使用。

---

# 🚀 浏览器启动方式（加载自定义指纹 fp.txt）

在浏览器目录运行：

```bash
chrome.exe 
  --enable-webgl --ignore-gpu-blocklist --enable-unsafe-webgl --no-sandbox \
    --ruyi="{\"ruyiFile\":\"C:\\chromiun141\\fp.txt\",\"httpuser\":\"xxx-res_BR-Minas+Gerais\",\"httppwd\":\"xxxxx\"}"   \
	--proxy-server="http://xxx.com:1288"  \
	https://browserleaks.com/ip
```

说明：

* `--ruyi`：加载完整指纹配置文件
* 配置文件可完整控制 WebGL / Canvas / UA / Audio / Fonts / Screen / Hardware
* 支持多指纹池切换、多实例运行、自动化脚本调用
* 支持HTTP密码代理
---

# 📝 指纹脚本示例（fp.txt）

以下为一份可直接使用的基础指纹模板，你可根据需求自由修改：

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
screenY:10
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

---

# 🔬 可修改指纹体系（详细说明）

以下为本浏览器可自定义的全部指纹类型，并解释其在 FingerprintJS 内的意义。

## 🧭 1. Navigator 环境指纹

| 字段                  | 作用               | 影响范围                      |
| ------------------- | ---------------- | ------------------------- |
| webdriver           | 判断是否自动化          | Selenium/Playwright 检测核心点 |
| useragent           | UA+版本特征          | 高危指纹之一                    |
| platform            | win32/macIntel 等 | 与 UA 对应关系影响极大             |
| languages           | Accept-Language  | 用于识别地区信息                  |
| timezone            | 时区               | 与语言/系统环境一致性匹配             |
| deviceMemory        | 内存大小             | 常用于设备画像                   |
| hardwareConcurrency | CPU 线程数          | 高敏感特征                     |

这些字段构成 **基础身份指纹**，一致性极其关键。

---

## 🖥 2. 屏幕与显示指纹

| 字段                                 | 说明            |
| ---------------------------------- | ------------- |
| screenWidth / screenHeight         | 屏幕逻辑分辨率       |
| avaiScreenWidth / avaiScreenHeight | 可用区域尺寸（扣除任务栏） |
| colorDepth                         | 深度位数          |

与设备型号强相关，FPJS Pro 会做“伪造检测”。本浏览器能从底层返回稳定可信结果。

---

## 🎨 3. Canvas 指纹

Canvas 指纹由 GPU 渲染差异决定，是 FPJS 最敏感项目之一。

可控内容：

* 画布最终哈希值（canvas）
* 绘制参数（alpha / depth / antialias / premultipliedAlpha …）
* preserveDrawingBuffer（影响渲染路径）

本项目通过 **Chromium 渲染链底层修改** 不会被FP脚本检测到伪造行为。

---

## 🔋 4. WebGL 指纹（最重要）

可定制内容包括：

* Unmasked Vendor / Renderer（真实 GPU 特征）
* GL 版本信息
* Shader 精度
* 支持的扩展（supportedExt）
* 扩展参数（extensionParameters）
* point size / line width 范围

其中 **supportedExt + parameters** 是 FingerPrintJS Pro 最关键检测点。

---

## 🔊 5. WebAudio 哈希

音频指纹是由 FFT 运算结果生成的稳定哈希。

字段：

* `webaudio`

可自定义返回值，可用于构造跨设备一致性模型。

---

## 🔤 6. 字体与文本宽度指纹

字段：

* fonts
* monospacePreferences
* sansPreferences
* serifPreferences

FPJS 会通过创建隐藏 DOM 对字体 fallback 进行测量，本浏览器通过渲染层 Patch 保证数值精确一致。

---

# 📚 想深入学习？

想系统掌握：

* FingerPrintJS / Pro 工作机制
* Chromium 指纹链路逻辑（Canvas / WebGL / Audio / Fonts / Screen）
* 如何自行开发反指纹浏览器

请查看课程：

👉 **[https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp](https://www.yuque.com/u21565569/ihuyk3/xgc6hqd94fb69xxp)**

