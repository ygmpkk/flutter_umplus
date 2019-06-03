# flutter_umplus

一个简单的友盟 umeng app+ 统计，其他几个库的坑都踩过了，吸收了它们的优点，建议大家有这个库。

**目前遇到的问题：**

- dispose 在Android有点问题，需要再测试一下，友盟必须在beginPageView和endPageView配对才算有效。如果有人知道如何解决欢迎fork。

## Getting Started

| Init        |                                                              |
| ----------- | ------------------------------------------------------------ |
| key         | 友盟AppKey                                                   |
| channel     | 渠道；空字符串或者null，iOS默认为AppStore，Android字段从AnroidMainfest.xml的UMENG_CHANNEL读取 |
| reportCrash | 是否报告错误                                                 |
| logEnable   | 是否启用日志                                                 |
| encrypt     | 是否启用加密                                                 |

### Usage

初始化

```
FlutterUmplus.init(
    'Your umeng appkey',
    channel: 'Your channel',
    reportCrash: false,
    logEnable: true,
    encrypt: true,
);
```

页面开始

```
@override
void initState() {
	super.initState();
	
	FlutterUmplus.beginPageView('demo');

}
```

页面结束

```
@override
void dispose() {
	FlutterUmplus.endPageView('demo');
	// FIXME 这个最好放在最后，iOS有效，Android无论如何都无效。
	super.dispose();
}
```

事件埋点

```
FlutterUmplus.event('eventName', label: 'eventLabel');
```

[仓库地址](https://github.com/ygmpkk/flutter_umplus)

## LICENSE

MIT