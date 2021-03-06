# ChinaAQIData

## 中国城市AQI数据
我们从[中国环境总站](http://www.cnemc.cn/)采集实时的空气质量数据。数据API是`http://106.37.208.233:20035/emcpublish/ClientBin/Env-CnemcPublish-RiaServices-EnvCnemcPublishDomainService.svc/binary/GetAQIDataPublishLives`。这个API提供了一个WCF二进制数据流，使用`wget`命令可以下载一个二进制数据文件，然后使用[`python-wcfbin`](https://github.com/ernw/python-wcfbin) 对该二进制文件进行解码得到XML文本格式的数据。

这个项目，我们使用`data_from_cepm.sh`这个shell脚本完成整个数据获取和解码的工作。我们在Linux机器上设置了一个`cron`任务，每个小时定时执行两次该脚本，并将获得的XML文件存储到`xml`目录中，json文件存储到`archives`目录中。同时，我们也保存一个`airnow.json`的文件存储当前小时的空气质量数据。

## 免责声明
我们不对使用此方法采集到的数据的真实性负责。使用此方法获取的数据出现的任何后果由使用方法者自己负责。


## AQI Data of Cities in China

We collect real-time air quality data from [China National Environmental Monitoring Centre](http://www.cnemc.cn/). The data API is `http://106.37.208.233:20035/emcpublish/ClientBin/Env-CnemcPublish-RiaServices-EnvCnemcPublishDomainService.svc/binary/GetAQIDataPublishLives`. This API provides a WCF binary data stream. We can use `wget` to get the data, and use [`python-wcfbin`](https://github.com/ernw/python-wcfbin) to decode this binary data to XML text format.

In this project, we use the shell `data_from_cepm.sh` to do the whole process of data crawling and decoding. We set up a `cron` job on linux system to execute this shell twice every hour. XML files are stored in the `xml` directory and json files in the `archives` directory. We also keep a `airnow.json` file which contains the air quality data of current hour. 

## Disclaimer
We are not responsible for the truth of the data collected by this method. Anyone who uses the data by this method should be responsible for any consequence caused by using the data.