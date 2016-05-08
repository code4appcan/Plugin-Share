#AppCan应用开发之插件实践篇-分享插件
本节教程将介绍如何利用插件完成一个分享的页面。

页面效果图

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/1.png)

1、首先编写UI页面布局。新建一个appcan页面，命名为lvdetail.html，同时IDE会自动根据lvdetail.html页面生成一个浮动窗口lvdetail_content.html页面。
lvdetail.html主窗口头部header部分布局代码：

	    <div id="header" class="uh bc-text-head ub bc-head" style="height: 2.8em">
    <div class="nav-btn" id="nav-left">
        <div class="fa fa-angle-left fa-2x" id="aa"></div>
    </div>
    <h1 class="ut ub-f1 ulev-3 ut-s tx-c" tabindex="0" id="bar"></h1>
    <div class="nav-btn nav-bt ub" style="margin-right: 0.7em">
        <div class="ub ub-f1 fa fa-comment-o " style="margin-right: 0.8em" id="comment"></div>
        <div class="ub ub-f1 fa fa-heart-o" style="margin-right: 0.8em;" id="conlect" ></div>
        <div class="ub ub-f1 image uhide " style="margin-right: 0.8em;" id="delete" ></div>
        <div class="ub ub-f1 fa fa-external-link " id="share"></div>    
    </div>
</div>

效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/2.png)

2、其次在lvdetail.html页面js脚本区内编写javascript代码，用于实现点击右上角分享图标按钮后弹出分享窗口。

	   appcan.button("#share", "btn-act", function() {
   			appcan.frame.open('share_content', 'share_content.html', 0);
		}

效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/3.png)

3、其次在lvdetail_content.html浮动窗口编写页面UI布局代码

	    <div class="ub ub-ver" style="border-bottom:0.7em solid #DDDDDE">
            <div class="ub header-image" style="background-size:100% 100%;height:14em;width:100%;background-repeat: no-repeat;" id="img"></div>
            <div class="ub ulev1 ub-ac" style="margin-top: 0.5em">
                相关图片
            </div>
            <div style="width:100%;height:7em; overflow-x:auto;margin-top: 0.2em;" class="ub ">
                <table>
                    <tr id="imgList">
                        <td id="img0"></td>
                    </tr>
                </table>
            </div>
            <div class="ub ub-ac ulev1" style="height:2em;margin:0.6em 0;color:black; ">
                简介
            </div>
            <div class="ub ub-ver" style="border-bottom: 1px solid #DDDDDE ;">
                <div id="test" class="ub ub-ver " style="color:#6B6B6B ;padding-bottom: 1em;line-height: 1.5em">
                    <div class="ub ub-f1 aa" id="box" style="padding: 0 1em;text-indent: 1em"></div>
                    <div class="ub ub-f1  ub-pc" id="down">
                        <img src="images/xiangxia.png" style="width: 1.5em" />
                    </div>
                </div>
            </div>
        </div>
        <div class="ub ub-ac ulev1 " style="height:2em;margin:0.6em 0 0.6em 1em">
            营业时间
        </div>
        <div class="ub" style="color:#6B6B6B;padding: 0 1em;" id="time"></div>
        <div class="ub ub-ver " style="margin:1em 0;padding: 0 0 1em 1em;border-bottom: 1px solid #DDDDDE;">
            <div class="ulev1 " style=" ">
                电话
            </div>
            <div style="color:#6B6B6B;margin-top: 1em" id="phone"></div>
        </div>
        <div class="ub ">
            <div class="ub ub-f1 ub-ver" style="padding: 0 1em;">
                <div class="ulev1" style="color: black">
                    门票
                </div>
                <div style="color:#6B6B6B;margin-left: 0.1em;margin-top: 1em;margin-bottom: 1em" id="price"></div>
            </div>
            <div class="ub ub-ac ub-pc ulev1" style="color:red;margin:-2em 2em 0 0;font-weight: bold;" id="callToOrder">
                我要订票
            </div>
        </div>
        </div>
        <div class="ub ub-ver" style="border-bottom: 0.7em solid #DDDDDE">
            <div class="ub ub-hor" style="">
                <div class="ub ub-f1 ub-ver"  >
                    <div class="ub ub-hor">
                        <div class="ub ub-f1 ub-ac ulev1" style="height:2em;color:black">
                            地址
                        </div>
                        <img src="images/map.png" class="ub " style="width:1.1em;height:1.3em;margin-right: 0.6em" id="map"/>
                    </div>
                    <div class="ub ulev-1" style="color:#6B6B6B;border-bottom: 1px solid #DDDDDE;padding: 0 0 0.8em 0.8em;margin-top: 0.3em ;line-height: 1.4em" id="address"></div>
                </div>
            </div>
            <div class="ub ub-ver" style="border-bottom: 1px solid #DDDDDE ;">
                <div id="test" class="ub ub-ver " style="color:#6B6B6B ;padding-bottom: 1em;line-height: 1.5em">
                    <div class="ub ub-ac ulev1" style="height:2em;color:black">
                        如何到达
                    </div>
                    <div class="ub ub-f1 aa ulev-1" id="box_2" style="padding: 0.5em 1em;" ></div>
                </div>
                <div class="ub ub-f1  ub-pc" id="down_2">
                    <img src="images/xiangxia.png" style="width: 1.5em" />
                </div>
            </div>
        </div>
        <div class="ub ub-ver " style="">
            <div class="ub ub-ac ulev1" style="height:2em;color:#00A1EA">
                小贴士
            </div>
            <div class="ub ulev-1" style="color:#6B6B6B;padding:0 1em 1em;text-indent: 1em" id="tips"></div>
        </div>

效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/4.png)
![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/5.png)
![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/6.png)

4、然后新建一个share_content.html页面，并编写UI布局代码。

	    <div class="ub" id="close"></div>
        <div class="ub ub-ver " style="background-color: #D7D7D7;width:100%;padding-bottom: 2em;position: absolute;bottom: 0">
            <div class="ub " style="margin-top: 2em;margin-bottom: 1em">
                <div class="ub ub-f1 ub-ver" onclick="wx_share(0)">
                    <div id="view" class="ub ub-ac ub-pc"><img src="images/weixinFriend.png" style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        微信好友
                    </div>
                </div>
                <div class="ub ub-f1 ub-ver" onclick="wx_share(1)">
                    <div id="food" class="ub ub-ac ub-pc"><img src="images/weixinQuan.png"  style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        朋友圈
                    </div>
                </div>
                <div class="ub  ub-f1 ub-ver" id="QQ">
                    <div id="hotel" class="ub ub-ac ub-pc"><img src="images/QQ.png"  style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        QQ
                    </div>
                </div>
            </div>
            <div class="ub " style="margin-bottom: 1em">
                <div class="ub ub-f1 ub-ver" id="QQk">
                    <div id="view" class="ub ub-ac ub-pc"><img src="images/QQk.png" style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        QQ空间
                    </div>
                </div>
                <div class="ub ub-f1 ub-ver" id="message">
                    <div id="food" class="ub ub-ac ub-pc"><img src="images/message.png" style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        短信
                    </div>
                </div>
                <div class="ub  ub-f1 ub-ver" id="copy">
                    <div id="hotel" class="ub ub-ac ub-pc"><img src="images/copy.png" style="height:4em;width:4em" >
                    </div>
                    <div class="ub ub-ac ub-pc text" style="margin-top: 0.5em">
                        复制
                    </div>
                </div>
            </div>
            <div class="ub ub-f1 ub-ac ub-pc ulev" style="background-color: white;height:3em;margin-top: 1em" id="cancle">
                取消
            </div>
        </div>

效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/7.png)

5、最后在share_content.html页面js脚本区内编写javascript代码，实现微信分享到好友，微信分享到朋友圈，QQ分享到好友，QQ分享到空间，以及手机短信发送和复制信息到剪帖板功能。

（1）微信分享使用之前需要到微信官网申请注册开发者账号并获取appID和appScret，详情可参考http://newdocx.appcan.cn/newdocx/docx?type=1449_975

（2）QQ分享使用之前需要到QQ互联开放平台为应用申请相应的AppID,并将AppID配置到应用中。详情可参考http://newdocx.appcan.cn/newdocx/docx?type=1329_975

当分别获取了微信appID和QQ的appID之后，接下来在share_content.html页面js脚本区编写代码

	    var weixin_appId = "wxd7ff3acbfbb05ff0";
        var weixin_app_serect = "d4624c36b6795d1d99dcf0547af5443d";
        var qq_appId = '1104873173';
        var shareImg = appcan.locStorage.getVal("shareImg");
        var shareImg = ipVal + shareImg.split("WEB-INF/")[1];
        appcan.ready(function() {
        });

>微信分享文本给指定好友

	    function wx_share(type)//0是发送好友，1是分享到朋友圈
        {
            uexWeiXin.registerApp(weixin_appId);
            uexWeiXin.cbRegisterApp = function(opCode, dataType, data) {
                if (data == 0)//授权成功
                {
                    uexWeiXin.isWXAppInstalled();
                    uexWeiXin.cbIsWXAppInstalled = function(opCode, dataType, data) {
                        alert(data);
                        if (data == 0) {
                            var con = {
                                "thumbImg" : shareImg,
                                "wedpageUrl" : "http://www.badongtour.com/",
                                "scene" : type,
                                "title" : "秘境巴东",
                                "description" : "秘境巴东一日游！"
                            };

                            uexWeiXin.shareLinkContent(JsonData);
                        } else if (data == 1) {
                            appcan.window.alert({
                                title : "提示",
                                content : "检测到您未安装微信",
                                button : ["确定"]
                            })
                        }
                    }
                } else {
                    appcan.window.alert({
                        title : "提示",
                        content : "授权失败",
                        button : ["确定"]
                    })
                }
            }
        }

>qq分享图文到qq好友

	    function shareWebImgTextToQQ() {
            var json = '{"title":"图文分享标题","summary":"图文分享消息摘要","targetUrl":"http://appcan.cn","imageUrl":"res://aa.jpg","appName":"uexQQ", "cflag":"2"}';
            uexQQ.shareWebImgTextToQQ(qq_appId, json);
        }

	    appcan.button("#close", "btn-act", function() {
            appcan.window.close(-1);
        })

>分享到qq好友

	    appcan.button("#QQ", "btn-act", function() {
            uexQQ.login(qq_appId);
            shareWebImgTextToQQ();
        })

>分享到qq空间

	    appcan.button("#QQk", "btn-act", function() {
            uexQQ.login(qq_appId);
            shareWebImgTextToQQK();
        })
        appcan.button("#copy", "btn-act", function() {
            uexClipboard.copy("中国最大的移动中间键平台AppCan对剪贴板的测试");
        })
        appcan.button("#message", "btn-act", function() {
            uexSMS.open("10086", "中国最大的移动中间键平台AppCan对剪短信的测试");
        })

>取消分享

	     appcan.button("#cancle", "btn-act", function() {
            appcan.window.close(-1);
        })

点击分享到微信好友按钮效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/8.png)

点击分享到微信朋友圈按钮效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/9.png)

点击分享到QQ效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/10.png)

点击分享到QQ空间效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/11.png)

点击短信按钮弹出手机短信发送界面效果如下：

![](https://raw.githubusercontent.com/code4appcan/Plugin-Share/master/12.png)


