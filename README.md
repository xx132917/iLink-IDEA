1.项目管理和综合工具:maven<br>
(1)Maven安装和配置:参考https://www.yiibai.com/maven/maven_environment_setup.html<br>
(2)Eclipse和IDEA配置Maven<br>

2.Spring版本：5.0.7<br>
3.MVC：Spring MVC配置<br>
(1)jar包:spring-webmvc.jar<br>
(2)web.xml配置SpringMVC监听类：org.springframework.web.context.ContextLoaderListener<br>
(3)SpringMVC核心配置文件：spring-mvc.xml  配置自动扫描的包、配置视图解析器 如何把 handler方法返回值解析为实际的物理视图、配置静态资源映射静态资源交给默认的Servlet、配置 mvc:annotation-driven标签开启注解<br>
(4)@RestController =@Controller+@ResponseBody<br>
(5)@RequestMapping("/")<br>
(6)页面跳转使用 ModelAndView<br>

4.实现文件上传下载：参考：https://blog.csdn.net/jronzhang/article/details/61210700<br>
(1)相关jar包：commons-fileupload、commons-io、commons-codec<br>
(2)Spring核心文件配置：bean  multipartResolver   maxUploadSize设置最大上传文件大小       defaultEncoding设置编码<br>
(3)下载测试url：http://localhost:8080/iLink/file/down<br>

5.IDEA开发出现java.lang.ClassNotFoundException:org.springframework.web.context.ContextLoaderListener错误解决方法<br>
解決方法：在IDEA中点击File > Project Structure > Artifacts > 在右侧Output Layout右击项目名，选择Put into Output Root。
执行后，在WEB-INF在增加了lib目录，里面是项目引用的jar包。<br>
参考：https://blog.csdn.net/du_23tiyanwang/article/details/80654313  <br>

6.实现文件上传功能，在浏览器中上传文件报错：HTML+Jquery+ajax post提交SpringMVC服务端 <br>
报错信息：java.io.EOFException: Unexpected EOF read on the socket  <br>
解决方法：使用ajax异步传输的问题，换了用jsp页面直接form表单post方式提交解决了问题 <br>
html使用jquery-form.js异步提交解决了问题。<br>
参考：https://www.jb51.net/article/112440.htm   <br>

7.git工具<br>
(1)annotate:如何项目中有一行代码不知道是什么意思，在当前代码行右击，然后点击annotate查看当前行的作者<br>
(2)移动所有改动之处    Previous Change 快捷键<br>
(3)撤销，包括单个和项目改动之处    Revert快捷键<br>
(4)提交代码遇到问题：Push rejected: Push to origin/master was rejected  <br>

8.实现多文件同时上传，Controller接受参数使用MultipartFile[]数组，循环遍历上传 <br>

9.jquery实现上传文件进度监听及进度条的实现<br>
(1)原理:给XMLHttpRequest对象的upload属性绑定onprogress方法监听上传过程<br>
(2)因为jQuery默认使用的XMLHttpRequest对象是内部生成的无法直接给jq的xhr绑定onprogress方法
   所以只要给jQuery重新生成一个绑定了onprogress的XMLHttpRequest对象即可实现<br>
(3)首先封装一个方法 传入一个监听函数 返回一个绑定了监听函数的XMLHttpRequest对象<br>
(4)ajax请求时加：<br> xhr:xhrOnProgress(function(e){<br>
                    var percent=e.loaded / e.total;//计算百分比   <br>
                })<br>
(5)参考：https://blog.csdn.net/qq_21119773/article/details/52796375   <br>

10.java执行shell命令行 <br>
  (1)主要方法：Runtime.getRuntime().exec(args, envps, new File(dir)) <br>
  (2)参数： <br>
         args： 命令行数组 例如：cmd.exe /c  startup.bat <br>
         envps: 环境变量 <br>
         dir: 执行文件路径 <br>
  (3)参考：http://zohan.iteye.com/blog/1709136  <br>
  
11.文件解压  <br>
  (1)依赖jar包：ant(.zip)、junrar(.rar)  <br> 
  (2)参考工具类：com.iLink.utils.CompressFileUtils <br>
  (3)参考：https://blog.csdn.net/ljheee/ar ticle/details/52736091 <br>

12.文件使用DES加密解密 <br>
  (1)密钥，密钥长64位，实际参与运算的是56位 <br>
  (2)在自定义配置文件DesKey.txt配置文件中配置：例如byte[]={-1,20,-13,90,70,50,-111,39} <br>
  (3)获取文件路径方法（解决路径中带中文字符和空格问题）：DesUtil.class.getClassLoader().getResource("DesKey.txt").toURI().getPath() <br>
     ---问题解决参考：https://www.cnblogs.com/tv151579/p/6220443.html  <br>
  (4)参考：https://blog.csdn.net/feng______/article/details/40782347  <br>
  
13.功能实现及描述： <br>
  (1)流程：上传加密的压缩文件-->解密-->解压-->执行文件中的.sh文件或.bat文件 <br>
  (2)上传文件：POST方式提交，服务端使用SpringMVC的MultipartFile <br>
     ---参考文章：https://blog.csdn.net/jronzhang/article/details/61210700 <br>
  (3)解压：使用jar包：ant(.zip)、junrar(.rar) <br>
     ---参考文章： https://blog.csdn.net/ljheee/ar ticle/details/52736091 <br>
  (4)java执行shell命令行：主要方法Runtime.getRuntime().exec(args, envps, new File(dir))<br>
     ---参考文章：http://zohan.iteye.com/blog/1709136<br>
  (5)文件加密解密  <br>
     -加密  <br>
     ---生成密钥Key：<br><br>
     ![Image text](https://github.com/xx132917/iLink-IDEA/blob/master/readme-img/autokey.png) <br><br>
     ![Image text](https://github.com/xx132917/iLink-IDEA/blob/master/readme-img/getkey.png) <br><br>
     ---文件加密方法：<br>
     ![Image text](https://github.com/xx132917/iLink-IDEA/blob/master/readme-img/jiami.png) <br><br>
     ---文件解密方法：<br>
     ![Image text](https://github.com/xx132917/iLink-IDEA/blob/master/readme-img/jiemi.png) <br><br>
  (6)总结至Github  README.md文件：https://github.com/xx132917/iLink-IDEA <br>
  (7)功能实现代码尚未完善，只考虑每个实现步骤实现成功的情况，可能出现的异常和操作失败的情况还未完善 <br>


