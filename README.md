#
python实现简单语音识别
1.用到speech模块  用pip安装即可
2.pywin32
我用的是anconda的IDE，已经安装好。如果没有安装的可以在网上下载一下，注意一定要与python版本相对应
3.windows的语音模块
Microsoft Speech SDK 5.1在网上下载好就可以了
4.贴代码
import speech
import win32api
import os
import win32com
import subprocess
##while True:
##    words=raw_input("Please input some words:")   
##    if words.lower()=='stop':
##        break
##    speech.say(words)

##contents=speech.input("Say something,please.")
##speech.say(contents)
##print(contents)

if __name__=='__main__':
    Start='你在哪'
    Hello='你好'
    Control='关闭语音控制'
    openPython='我要写代码'
    openMusic='我要听音乐'
    stormPlayer='我要看电影'
    tencentQQ='我要'
    listenMusic='我累了'
    Hawk='你是谁'
    Users='你知道我是谁么'
    Love='你喜欢我么'  


#    judge=speech.input()
#    while True:
#        if(judge == Start):
#            speech.say("我在这呢，你说吧")
#            break我要听音乐
       
    while True:
        words=speech.input("Say you want to do.")
        print(words)
        if(words == Control):
            speech.say("已关闭语音控制")
            break
        elif(words==Start):
            speech.say("我在这呢，你说吧")
        elif(words == Hello):
            speech.say("你也好，今天过得怎么样")
        elif(words == openPython):
            subprocess.Popen(r'D:\PyCharm 2017.2.4\bin\pycharm64.exe')
##            win32.api.ShellExecute(0,'open','D:\Python\python.exe','','',0)
##            win32.api.ShellExecute(0,'open','D:\Python\python.exe','','',1)
        elif(words == openMusic):
           subprocess.Popen(r'C:\Program Files (x86)\Netease\CloudMusic\cloudmusic.exe')
##            win32.api.ShellExecute(0,'open','D:\QQ音乐\QQMusic\QQMusic.exe','','',0)
##            win32.api.ShellExecute(0,'open','D:\QQ音乐\QQMusic\QQMusic.exe','','',1)
        elif(words == stormPlayer):
            subprocess.Popen(r'D:\360安全浏览器下载\QQLive\QQLive.exe')
        elif(words == tencentQQ):
           subprocess.Popen(r'C:\Program Files (x86)\Tencent\QQ\Bin\QQScLauncher.exe')
        elif(words == listenMusic):
            speech.say("那就听会儿音乐吧")
            subprocess.Popen(r'C:\Program Files (x86)\Netease\CloudMusic\cloudmusic.exe')
        elif(words == Hawk):
            speech.say("我叫Hawk")
        elif(words == Users):
            speech.say("我是谁，我也不知道")
        elif(words == Love):
            speech.say("不喜欢，下一个")
        else:
            speech.say("暂时不支持此功能")

##words=speech.input("Say you want to do.")
##words=str(words)
##print(words)
可以根据自己的需要写自己想要控制的位置
5.注：
	这个运行起来真的好慢，可能是代码太简单，也可能是我电脑太差......
6.遇到的问题
（1）.我在网上看到的文档是可以用os.system或者os.popen打开程序，后来怎么都不能实现，于是在网上各种查询资料，发现可以用
 subprocess.Popen代替
（2）.之前使用的是C:\\Users\\Administrator\\Downloads\\网易云音乐.exe')类似这种路径方式，因为我刚开始的时候是使用
\的形式不可以，然后又尝试使用u的形式还是不能使用，最后在网上文档张看到可以用\\的强制类型，试了下果然可以...Buf在请教学长的
过程张发现可以用r 的形式...涨姿势
（3）.刚开始的时候一直使用decode的编码然后发现总是有问题，改为encode编码可以运行可是在运行中总是出现暂不能识别的问题
后来请教了学长后发现可能是编码的问题于是删除各种编码形式果然可以了
