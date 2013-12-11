# Project #

**H.264视频流的web播放插件**

# 特点 #

- 接收遵循RTSP协议的流

- HTML嵌入

- Javascript wrapper

- 基于本地解码库解码，浏览器插件形式，不增加浏览器负担

- 灵活调用

# 依赖项 #

> 本插件采用本地解码库依赖，故需要安装VLC播放器以及插件，测试在VLC 2.1.1版本实现

> VLC2.1.1安装过程中默认勾选了基于浏览器的插件安装，请保持

> VLC的最新发行版请移步 [http://www.videolan.org/](http://www.videolan.org/)

# HTML嵌入 #

> 你需要在HTML的head标签里面嵌入对styles.css的引用
	
	<!--For Player style-->
	<link  href="css/styles.css" rel="stylesheet"/>
>为了更加快速的加载页面内容，我们建议将js的引用放置在文档底部

	<!--Player core js-->
    <script language="javascript" src="js/jquery.min.js"></script>
    <script language="javascript" src="js/jquery-vlc.js"></script>
> 然后你需要在body标签内放置一个容器，并有一个id标示，如下：

	<div class="player-group">
	     <div id="vlc" class="col-lg-12"></vlc>
	</div>
>然后你使用如下方法初始化播放器，即ready函数：

	<script type="text/javascript">
      function play(instance, uri) {
			//...
        }
        var player = null;
        $(document).ready(function() {
            player = VLCobject.embedPlayer('vlc', 800, 480, true);
        });
	</script>
> 你需要传递给对象VLCobject的VLCobject方法**四个参数**，分别是播放器放置容器的id，播放器宽度和高度以及是否需要额外的播放器控制面板（VLC插件控制不集成时间戳）

# API 方法#
## embedPlayer() ##



- 参数表——(replaceElemIdStr, widthStr, heightStr, add_toolbar)

	> replaceElemIdStr(String)——目标容器的id
	
	> widthStr(Int)——播放器宽度
	
	> heightStr(Int)——播放器高度
	
	> add_toolbar(Boolean)——播放器面板
- 调用方法
	
    	var player = VLCobject.embedPlayer('containerId', widthStr, heightStr, addToolBar);
## play() ##

- 参数表——(uri)

	>uri(String)——代表一个rtsp地址
- 调用方法

	    //你需要使用返回的player实例调用play方法
	    player.play('rtsp://Ur rtsp path');

## stop() ##

- 无参数表

- 调用方法
	    
		// stop playing
	    player.stop(); 
## toggleFullscreen() ##

- 无参数表

- 调用方法
	    
		// toggleFullScreen 
	    player.toggleFullscreen(); 
## add() ##
- 参数表——(uri)

	>uri(String)——代表一个rtsp地址
- 调用方法
	    
		//添加uri
		var id = Object.playlist.add(uri);
		//切换至新的uri播放
	    plugin.playlist.playItem(id);
	
## options选项 ##
- 子方法
	
    	//设置开始播放时间
    	set("start-time", 50);
    	// 重置 VLC options
    	clear()
