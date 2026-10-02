# 方舟 STM32 开发板工程

本仓库保存 CubeMX 与 Keil MDK 工程，可在 Studio 中与独立 ark_sdk、App 和 Keil 组合使用。SDK 引用采用直接路径，不创建软链接。

## 工程与输入文件

包含 c8t6_demo、c8t6_microcar_soil、c8t6_usb_cdc、c8t6_xiaoyan_net。保留 IOC、.mxproject、Core、Drivers、Middlewares、USB_DEVICE、启动汇编、uvprojx、uvoptx、RTE 与调试配置。

uvoptx 是探针和烧录工具的必要输入。CMSIS 的预编译 lib/a 是厂商输入，不是本地构建产物；保留原授权。

## 开发

在 Rust Studio 选择该仓库中的工程文件，再明确选择 Target。可单独编译工程；同步 SDK/App 时还需要选择 SDK 与 DTS，并验证芯片兼容性。同步仅修改所选 Target，新建工程保持统一名称。

完整构建需要 Keil、对应设备包和 ARM 编译器。编译输出、固件、日志和个人 IDE 会话不提交；CubeMX 生成的 C/H 为构建输入，不手改。

## 验证

网络板完整构建通过。土壤车超过 Flash，两个历史 JSON 示例需要 DTS/API 迁移。详细记录见 [验证说明](SOURCE-VERIFICATION.md)。
