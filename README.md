# wall-e-flasher

**WALL-E AI 桌宠固件的一键刷机页**（GitHub Pages 托管）。

👉 打开刷机页：**https://nirvanaslash.github.io/wall-e-flasher/**

## 这个仓库是什么

只放**编译好的固件**和一张刷机网页，方便不装任何开发工具的人（造物主）直接刷。

- **源码在私有仓库**：`nirvanaslash/wall-e-firmware_OV5640_flash`（基于 MIT 的 [78/xiaozhi-esp32](https://github.com/78/xiaozhi-esp32)）
- 这里公开的只有编译产物 `wall-e-factory.bin`，不含源码

## 文件

| 文件 | 作用 |
|---|---|
| `index.html` | 刷机页（ESP Web Tools / Web Serial API，Chrome、Edge 可用） |
| `manifest.json` | 告诉刷机页「刷哪个文件、什么芯片、偏移多少」 |
| `wall-e-factory.bin` | 全量 factory 镜像，offset 0，7,955,625 字节 |
| `.nojekyll` | 关掉 Jekyll 处理，保证静态文件原样发布 |

## 目标硬件

| 项 | 值 |
|---|---|
| 主板 | Seeed XIAO **ESP32-S3 Sense**（8MB Flash / 8MB PSRAM） |
| 摄像头 | **OV5640**（DVP，自动对焦）—— 同一镜像也兼容 OV3660 / OV2640 |
| 屏幕 | ST7789 1.54" 240×240 |
| 功放 | MAX98357（I2S） |
| 电机 | DRV8833 × 双路，左右履带 |
| 分区表 | `partitions/v2/8m.csv`（OTA 双槽 + 2MB assets） |

## 更新固件（发版流程）

在私有仓库里 push 后 CI 会产出 `merged-binary.bin`，然后：

```bash
# 1) 下载最新构建产物
gh run download -R nirvanaslash/wall-e-firmware_OV5640_flash \
  -n "wall-e-firmware-<sha>" -D /tmp/wall-e

# 2) 覆盖到本仓库
cp /tmp/wall-e/merged-binary.bin wall-e-factory.bin

# 3) 更新 manifest.json 里的 version（建议带上构建 sha，便于确认刷的是哪一版）

# 4) 提交并推送，GitHub Pages 会自动重新部署（约 1 分钟）
git commit -am "firmware: <version>"
git push
```

> ⚠️ 刷机会整片擦除（`new_install_prompt_erase: true`），包括 WiFi 配置，刷完需要重新配网。
> 这样做是因为自研固件的分区表与原厂 2.4.0 不同，必须整片重写。

## 为什么不用原厂那个安装页

原厂的 `huyvector.github.io/wall-e-ai-installer` 只会刷它自己的 bin。
自研固件必须有自己的 manifest + bin，所以另起一个页面。

## 许可

固件基于 MIT 许可的 xiaozhi-esp32；本仓库的 `wall-e-factory.bin` 是该工程的编译产物。
