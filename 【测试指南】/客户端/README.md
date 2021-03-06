# 客户端测试指南

## 基础模块测试

设计验收 （只针对基础模块）（可选）
- [] 【代码质量】通读与建议（通读暴露的接口文件，提出设计的坏味道）
- [] 【模块设计】设计概要（建议做测试的人来做一下整理吧，模块开发者也可以输出初版）

测试验收
- [] 单元测试（只针对暴露出来的类）（可选）
	* 可测试性：
		1. 每个方法是一个行为，行为必须有反馈
			* 直接反馈：返回值、实参变化
			* 间接反馈：日志模块的文件管理，如setFilename, filepath, 然后检查，if file exist.
- [] 功能测试（必须）
- [] 性能测试（必须）
	* 时间占用（体验负载），横向比较
	* 线程占用（系统负载）
- [] 压力测试（可选）
	* 多线程高并发测试
	* 数据流高IO测试

流程执行
- [] 【团队协作】测试工程维护 （尽快完善，同时大家一致执行）
	* design, test放在一起，依赖XXKit
	* XXKit 放在pod 远端
- [] 【开发流程】完成流程整合：基础模块的 开发流程、测试流程（测试集成）、发布流程（发布集成）
