**pixabay**，非常不错的图片网站

![](http://i.imgur.com/EQ3DXDf.jpg)

[https://pixabay.com/zh/editors_choice/?media_type=photo&pagi=](https://pixabay.com/zh/editors_choice/?media_type=photo&pagi=)

图片下载地址：

 链接：http://pan.baidu.com/s/1skBtfJZ 密码：q82g

源码：

	import requests
	from lxml import etree
	import time
	import urllib
	
	def Download(url):
	    s = requests.Session()
	    header = {
	        'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36'}
	    r = s.get(url, headers=header).text
	    s = etree.HTML(r)
	    r = s.xpath('//img/@data-lazy')
	    for i in r:
	        imglist = i.replace('__340', '_960_720')
	        name = imglist.split('/')[-1]
	        urllib.request.urlretrieve(imglist,name)
	        time.sleep(1)
	
	
	def FullUrl():
	    full_link = []
	    for i in range(2,165):
	        #print(i)
	        full_link.append( 'https://pixabay.com/zh/editors_choice/?media_type=photo&pagi='+ str(i))
	        #print(full)
	    return full_link
	
	if __name__ == '__main__':
	    urls = FullUrl()
	    for url in urls:
	        Download(url)
