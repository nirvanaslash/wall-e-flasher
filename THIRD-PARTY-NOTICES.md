# 第三方组件声明 / Third-Party Notices

`wall-e-factory-*.bin` 是本项目固件的编译产物。该固件由多个开源项目构建而成，
按各自许可证的要求，在此列出主要组件与版权声明。

## 主要组件

| 组件 | 许可证 | 上游 |
|---|---|---|
| xiaozhi-esp32（固件基座） | MIT | https://github.com/78/xiaozhi-esp32 |
| esp32-camera（摄像头驱动） | Apache-2.0 | https://github.com/espressif/esp32-camera |
| ESP-IDF（SDK） | Apache-2.0 | https://github.com/espressif/esp-idf |
| LVGL（图形库） | MIT | https://github.com/lvgl/lvgl |
| ESP-SR（语音识别 / 唤醒词） | Espressif 组件许可 | https://github.com/espressif/esp-sr |

> ESP-SR 为乐鑫（Espressif）提供的语音识别组件，随 ESP-IDF 组件管理器分发，
> 其使用受该组件自身许可条款约束，不适用下文 MIT 条款。

## 关于本项目新增的代码

固件在 `xiaozhi-esp32` 基础上新增了本项目的板型支持（`main/boards/wall-e/`），
包括引脚配置、摄像头自动对焦初始化、DRV8833 电机控制与 `self.wall_e.*` 设备端工具。
这部分代码的版权归其作者所有，**源码未随本二进制公开**。

## xiaozhi-esp32 的 MIT 许可证全文

```
MIT License

Copyright (c) 2025 Shenzhen Xinzhi Future Technology Co., Ltd.
Copyright (c) 2025 Project Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Apache-2.0 组件

esp32-camera 与 ESP-IDF 采用 Apache License 2.0。
许可证全文见 https://www.apache.org/licenses/LICENSE-2.0 。
按该许可证要求，如需要完整的 NOTICE 内容或对应源码，
可在上述上游仓库获取；本项目未对这两个组件做修改。
