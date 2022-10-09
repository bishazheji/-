mixed-port: 7890
allow-lan: true
bind-address: '*'
mode: rule
log-level: info
external-controller: '127.0.0.1:9090'
dns:
    enable: true
    ipv6: false
    default-nameserver: [223.5.5.5, 119.29.29.29]
    enhanced-mode: redir-host
    fake-ip-range: 198.18.0.1/16
    use-hosts: true
    nameserver: ['https://doh.pub/dns-query', 'https://dns.alidns.com/dns-query']
    fallback: ['https://doh.dns.sb/dns-query', 'https://dns.cloudflare.com/dns-query', 'https://dns.twnic.tw/dns-query', 'tls://8.8.4.4:853']
    fallback-filter: { geoip: true, ipcidr: [240.0.0.0/4, 0.0.0.0/32] }
proxies:
    - { name: 香港, type: ss, server: 20.187.126.152, port: 38443, cipher: aes-256-gcm, password: bf28accc-d721-4558-b6a8-f689b6cd446f, udp: true }
proxy-groups:
    - { name: 免费机场, type: select, proxies: [自动选择, 故障转移, 香港] }
    - { name: 自动选择, type: url-test, proxies: [香港], url: 'http://www.gstatic.com/generate_204', interval: 86400 }
    - { name: 故障转移, type: fallback, proxies: [香港], url: 'http://www.gstatic.com/generate_204', interval: 7200 }
rules:
    - 'DOMAIN,,DIRECT'
    - 'DOMAIN-SUFFIX,services.googleapis.cn,免费机场'
    - 'DOMAIN-SUFFIX,xn--ngstr-lra8j.com,免费机场'
    - 'DOMAIN,safebrowsing.urlsec.qq.com,DIRECT'
    - 'DOMAIN,safebrowsing.googleapis.com,DIRECT'
    - 'DOMAIN,developer.apple.com,免费机场'
    - 'DOMAIN-SUFFIX,digicert.com,免费机场'
    - 'DOMAIN,ocsp.apple.com,免费机场'
    - 'DOMAIN,ocsp.comodoca.com,免费机场'
    - 'DOMAIN,ocsp.usertrust.com,免费机场'
    - 'DOMAIN,ocsp.sectigo.com,免费机场'
    - 'DOMAIN,ocsp.verisign.net,免费机场'
    - 'DOMAIN-SUFFIX,apple-dns.net,免费机场'
    - 'DOMAIN,testflight.apple.com,免费机场'
    - 'DOMAIN,sandbox.itunes.apple.com,免费机场'
    - 'DOMAIN,itunes.apple.com,免费机场'
    - 'DOMAIN-SUFFIX,apps.apple.com,免费机场'
    - 'DOMAIN-SUFFIX,blobstore.apple.com,免费机场'
    - 'DOMAIN,cvws.icloud-content.com,免费机场'
    - 'DOMAIN-SUFFIX,mzstatic.com,DIRECT'
    - 'DOMAIN-SUFFIX,itunes.apple.com,DIRECT'
    - 'DOMAIN-SUFFIX,icloud.com,DIRECT'
    - 'DOMAIN-SUFFIX,icloud-content.com,DIRECT'
    - 'DOMAIN-SUFFIX,me.com,DIRECT'
    - 'DOMAIN-SUFFIX,aaplimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,cdn20.com,DIRECT'
    - 'DOMAIN-SUFFIX,cdn-apple.com,DIRECT'
    - 'DOMAIN-SUFFIX,akadns.net,DIRECT'
    - 'DOMAIN-SUFFIX,akamaiedge.net,DIRECT'
    - 'DOMAIN-SUFFIX,edgekey.net,DIRECT'
    - 'DOMAIN-SUFFIX,mwcloudcdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,mwcname.com,DIRECT'
    - 'DOMAIN-SUFFIX,apple.com,DIRECT'
    - 'DOMAIN-SUFFIX,apple-cloudkit.com,DIRECT'
    - 'DOMAIN-SUFFIX,apple-mapkit.com,DIRECT'
    - 'DOMAIN-SUFFIX,xn--94q57lcvpw50b.com,DIRECT'
    - 'DOMAIN-SUFFIX,126.com,DIRECT'
    - 'DOMAIN-SUFFIX,126.net,DIRECT'
    - 'DOMAIN-SUFFIX,127.net,DIRECT'
    - 'DOMAIN-SUFFIX,163.com,DIRECT'
    - 'DOMAIN-SUFFIX,360buyimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,36kr.com,DIRECT'
    - 'DOMAIN-SUFFIX,acfun.tv,DIRECT'
    - 'DOMAIN-SUFFIX,air-matters.com,DIRECT'
    - 'DOMAIN-SUFFIX,aixifan.com,DIRECT'
    - 'DOMAIN-KEYWORD,alicdn,DIRECT'
    - 'DOMAIN-KEYWORD,alipay,DIRECT'
    - 'DOMAIN-KEYWORD,taobao,DIRECT'
    - 'DOMAIN-SUFFIX,amap.com,DIRECT'
    - 'DOMAIN-SUFFIX,autonavi.com,DIRECT'
    - 'DOMAIN-KEYWORD,baidu,DIRECT'
    - 'DOMAIN-SUFFIX,bdimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,bdstatic.com,DIRECT'
    - 'DOMAIN-SUFFIX,bilibili.com,DIRECT'
    - 'DOMAIN-SUFFIX,bilivideo.com,DIRECT'
    - 'DOMAIN-SUFFIX,caiyunapp.com,DIRECT'
    - 'DOMAIN-SUFFIX,clouddn.com,DIRECT'
    - 'DOMAIN-SUFFIX,cnbeta.com,DIRECT'
    - 'DOMAIN-SUFFIX,cnbetacdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,cootekservice.com,DIRECT'
    - 'DOMAIN-SUFFIX,csdn.net,DIRECT'
    - 'DOMAIN-SUFFIX,ctrip.com,DIRECT'
    - 'DOMAIN-SUFFIX,dgtle.com,DIRECT'
    - 'DOMAIN-SUFFIX,dianping.com,DIRECT'
    - 'DOMAIN-SUFFIX,douban.com,DIRECT'
    - 'DOMAIN-SUFFIX,doubanio.com,DIRECT'
    - 'DOMAIN-SUFFIX,duokan.com,DIRECT'
    - 'DOMAIN-SUFFIX,easou.com,DIRECT'
    - 'DOMAIN-SUFFIX,ele.me,DIRECT'
    - 'DOMAIN-SUFFIX,feng.com,DIRECT'
    - 'DOMAIN-SUFFIX,fir.im,DIRECT'
    - 'DOMAIN-SUFFIX,frdic.com,DIRECT'
    - 'DOMAIN-SUFFIX,g-cores.com,DIRECT'
    - 'DOMAIN-SUFFIX,godic.net,DIRECT'
    - 'DOMAIN-SUFFIX,gtimg.com,DIRECT'
    - 'DOMAIN,cdn.hockeyapp.net,DIRECT'
    - 'DOMAIN-SUFFIX,hongxiu.com,DIRECT'
    - 'DOMAIN-SUFFIX,hxcdn.net,DIRECT'
    - 'DOMAIN-SUFFIX,iciba.com,DIRECT'
    - 'DOMAIN-SUFFIX,ifeng.com,DIRECT'
    - 'DOMAIN-SUFFIX,ifengimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,ipip.net,DIRECT'
    - 'DOMAIN-SUFFIX,iqiyi.com,DIRECT'
    - 'DOMAIN-SUFFIX,jd.com,DIRECT'
    - 'DOMAIN-SUFFIX,jianshu.com,DIRECT'
    - 'DOMAIN-SUFFIX,knewone.com,DIRECT'
    - 'DOMAIN-SUFFIX,le.com,DIRECT'
    - 'DOMAIN-SUFFIX,lecloud.com,DIRECT'
    - 'DOMAIN-SUFFIX,lemicp.com,DIRECT'
    - 'DOMAIN-SUFFIX,licdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,luoo.net,DIRECT'
    - 'DOMAIN-SUFFIX,meituan.com,DIRECT'
    - 'DOMAIN-SUFFIX,meituan.net,DIRECT'
    - 'DOMAIN-SUFFIX,mi.com,DIRECT'
    - 'DOMAIN-SUFFIX,miaopai.com,DIRECT'
    - 'DOMAIN-SUFFIX,microsoft.com,DIRECT'
    - 'DOMAIN-SUFFIX,microsoftonline.com,DIRECT'
    - 'DOMAIN-SUFFIX,miui.com,DIRECT'
    - 'DOMAIN-SUFFIX,miwifi.com,DIRECT'
    - 'DOMAIN-SUFFIX,mob.com,DIRECT'
    - 'DOMAIN-SUFFIX,netease.com,DIRECT'
    - 'DOMAIN-SUFFIX,office.com,DIRECT'
    - 'DOMAIN-SUFFIX,office365.com,DIRECT'
    - 'DOMAIN-KEYWORD,officecdn,DIRECT'
    - 'DOMAIN-SUFFIX,oschina.net,DIRECT'
    - 'DOMAIN-SUFFIX,ppsimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,pstatp.com,DIRECT'
    - 'DOMAIN-SUFFIX,qcloud.com,DIRECT'
    - 'DOMAIN-SUFFIX,qdaily.com,DIRECT'
    - 'DOMAIN-SUFFIX,qdmm.com,DIRECT'
    - 'DOMAIN-SUFFIX,qhimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,qhres.com,DIRECT'
    - 'DOMAIN-SUFFIX,qidian.com,DIRECT'
    - 'DOMAIN-SUFFIX,qihucdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,qiniu.com,DIRECT'
    - 'DOMAIN-SUFFIX,qiniucdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,qiyipic.com,DIRECT'
    - 'DOMAIN-SUFFIX,qq.com,DIRECT'
    - 'DOMAIN-SUFFIX,qqurl.com,DIRECT'
    - 'DOMAIN-SUFFIX,rarbg.to,DIRECT'
    - 'DOMAIN-SUFFIX,ruguoapp.com,DIRECT'
    - 'DOMAIN-SUFFIX,segmentfault.com,DIRECT'
    - 'DOMAIN-SUFFIX,sinaapp.com,DIRECT'
    - 'DOMAIN-SUFFIX,smzdm.com,DIRECT'
    - 'DOMAIN-SUFFIX,snapdrop.net,DIRECT'
    - 'DOMAIN-SUFFIX,sogou.com,DIRECT'
    - 'DOMAIN-SUFFIX,sogoucdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,sohu.com,DIRECT'
    - 'DOMAIN-SUFFIX,soku.com,DIRECT'
    - 'DOMAIN-SUFFIX,speedtest.net,DIRECT'
    - 'DOMAIN-SUFFIX,sspai.com,DIRECT'
    - 'DOMAIN-SUFFIX,suning.com,DIRECT'
    - 'DOMAIN-SUFFIX,taobao.com,DIRECT'
    - 'DOMAIN-SUFFIX,tencent.com,DIRECT'
    - 'DOMAIN-SUFFIX,tenpay.com,DIRECT'
    - 'DOMAIN-SUFFIX,tianyancha.com,DIRECT'
    - 'DOMAIN-SUFFIX,tmall.com,DIRECT'
    - 'DOMAIN-SUFFIX,tudou.com,DIRECT'
    - 'DOMAIN-SUFFIX,umetrip.com,DIRECT'
    - 'DOMAIN-SUFFIX,upaiyun.com,DIRECT'
    - 'DOMAIN-SUFFIX,upyun.com,DIRECT'
    - 'DOMAIN-SUFFIX,veryzhun.com,DIRECT'
    - 'DOMAIN-SUFFIX,weather.com,DIRECT'
    - 'DOMAIN-SUFFIX,weibo.com,DIRECT'
    - 'DOMAIN-SUFFIX,xiami.com,DIRECT'
    - 'DOMAIN-SUFFIX,xiami.net,DIRECT'
    - 'DOMAIN-SUFFIX,xiaomicp.com,DIRECT'
    - 'DOMAIN-SUFFIX,ximalaya.com,DIRECT'
    - 'DOMAIN-SUFFIX,xmcdn.com,DIRECT'
    - 'DOMAIN-SUFFIX,xunlei.com,DIRECT'
    - 'DOMAIN-SUFFIX,yhd.com,DIRECT'
    - 'DOMAIN-SUFFIX,yihaodianimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,yinxiang.com,DIRECT'
    - 'DOMAIN-SUFFIX,ykimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,youdao.com,DIRECT'
    - 'DOMAIN-SUFFIX,youku.com,DIRECT'
    - 'DOMAIN-SUFFIX,zealer.com,DIRECT'
    - 'DOMAIN-SUFFIX,zhihu.com,DIRECT'
    - 'DOMAIN-SUFFIX,zhimg.com,DIRECT'
    - 'DOMAIN-SUFFIX,zimuzu.tv,DIRECT'
    - 'DOMAIN-SUFFIX,zoho.com,DIRECT'
    - 'DOMAIN-KEYWORD,amazon,免费机场'
    - 'DOMAIN-KEYWORD,google,免费机场'
    - 'DOMAIN-KEYWORD,gmail,免费机场'
    - 'DOMAIN-KEYWORD,youtube,免费机场'
    - 'DOMAIN-KEYWORD,facebook,免费机场'
    - 'DOMAIN-SUFFIX,fb.me,免费机场'
    - 'DOMAIN-SUFFIX,fbcdn.net,免费机场'
    - 'DOMAIN-KEYWORD,twitter,免费机场'
    - 'DOMAIN-KEYWORD,instagram,免费机场'
    - 'DOMAIN-KEYWORD,dropbox,免费机场'
    - 'DOMAIN-SUFFIX,twimg.com,免费机场'
    - 'DOMAIN-KEYWORD,blogspot,免费机场'
    - 'DOMAIN-SUFFIX,youtu.be,免费机场'
    - 'DOMAIN-KEYWORD,whatsapp,免费机场'
    - 'DOMAIN-KEYWORD,admarvel,REJECT'
    - 'DOMAIN-KEYWORD,admaster,REJECT'
    - 'DOMAIN-KEYWORD,adsage,REJECT'
    - 'DOMAIN-KEYWORD,adsmogo,REJECT'
    - 'DOMAIN-KEYWORD,adsrvmedia,REJECT'
    - 'DOMAIN-KEYWORD,adwords,REJECT'
    - 'DOMAIN-KEYWORD,adservice,REJECT'
    - 'DOMAIN-SUFFIX,appsflyer.com,REJECT'
    - 'DOMAIN-KEYWORD,domob,REJECT'
    - 'DOMAIN-SUFFIX,doubleclick.net,REJECT'
    - 'DOMAIN-KEYWORD,duomeng,REJECT'
    - 'DOMAIN-KEYWORD,dwtrack,REJECT'
    - 'DOMAIN-KEYWORD,guanggao,REJECT'
    - 'DOMAIN-KEYWORD,lianmeng,REJECT'
    - 'DOMAIN-SUFFIX,mmstat.com,REJECT'
    - 'DOMAIN-KEYWORD,mopub,REJECT'
    - 'DOMAIN-KEYWORD,omgmta,REJECT'
    - 'DOMAIN-KEYWORD,openx,REJECT'
    - 'DOMAIN-KEYWORD,partnerad,REJECT'
    - 'DOMAIN-KEYWORD,pingfore,REJECT'
    - 'DOMAIN-KEYWORD,supersonicads,REJECT'
    - 'DOMAIN-KEYWORD,uedas,REJECT'
    - 'DOMAIN-KEYWORD,umeng,REJECT'
    - 'DOMAIN-KEYWORD,usage,REJECT'
    - 'DOMAIN-SUFFIX,vungle.com,REJECT'
    - 'DOMAIN-KEYWORD,wlmonitor,REJECT'
    - 'DOMAIN-KEYWORD,zjtoolbar,REJECT'
    - 'DOMAIN-SUFFIX,9to5mac.com,免费机场'
    - 'DOMAIN-SUFFIX,abpchina.org,免费机场'
    - 'DOMAIN-SUFFIX,adblockplus.org,免费机场'
    - 'DOMAIN-SUFFIX,adobe.com,免费机场'
    - 'DOMAIN-SUFFIX,akamaized.net,免费机场'
    - 'DOMAIN-SUFFIX,alfredapp.com,免费机场'
    - 'DOMAIN-SUFFIX,amplitude.com,免费机场'
    - 'DOMAIN-SUFFIX,ampproject.org,免费机场'
    - 'DOMAIN-SUFFIX,android.com,免费机场'
    - 'DOMAIN-SUFFIX,angularjs.org,免费机场'
    - 'DOMAIN-SUFFIX,aolcdn.com,免费机场'
    - 'DOMAIN-SUFFIX,apkpure.com,免费机场'
    - 'DOMAIN-SUFFIX,appledaily.com,免费机场'
    - 'DOMAIN-SUFFIX,appshopper.com,免费机场'
    - 'DOMAIN-SUFFIX,appspot.com,免费机场'
    - 'DOMAIN-SUFFIX,arcgis.com,免费机场'
    - 'DOMAIN-SUFFIX,archive.org,免费机场'
    - 'DOMAIN-SUFFIX,armorgames.com,免费机场'
    - 'DOMAIN-SUFFIX,aspnetcdn.com,免费机场'
    - 'DOMAIN-SUFFIX,att.com,免费机场'
    - 'DOMAIN-SUFFIX,awsstatic.com,免费机场'
    - 'DOMAIN-SUFFIX,azureedge.net,免费机场'
    - 'DOMAIN-SUFFIX,azurewebsites.net,免费机场'
    - 'DOMAIN-SUFFIX,bing.com,免费机场'
    - 'DOMAIN-SUFFIX,bintray.com,免费机场'
    - 'DOMAIN-SUFFIX,bit.com,免费机场'
    - 'DOMAIN-SUFFIX,bit.ly,免费机场'
    - 'DOMAIN-SUFFIX,bitbucket.org,免费机场'
    - 'DOMAIN-SUFFIX,bjango.com,免费机场'
    - 'DOMAIN-SUFFIX,bkrtx.com,免费机场'
    - 'DOMAIN-SUFFIX,blog.com,免费机场'
    - 'DOMAIN-SUFFIX,blogcdn.com,免费机场'
    - 'DOMAIN-SUFFIX,blogger.com,免费机场'
    - 'DOMAIN-SUFFIX,blogsmithmedia.com,免费机场'
    - 'DOMAIN-SUFFIX,blogspot.com,免费机场'
    - 'DOMAIN-SUFFIX,blogspot.hk,免费机场'
    - 'DOMAIN-SUFFIX,bloomberg.com,免费机场'
    - 'DOMAIN-SUFFIX,box.com,免费机场'
    - 'DOMAIN-SUFFIX,box.net,免费机场'
    - 'DOMAIN-SUFFIX,cachefly.net,免费机场'
    - 'DOMAIN-SUFFIX,chromium.org,免费机场'
    - 'DOMAIN-SUFFIX,cl.ly,免费机场'
    - 'DOMAIN-SUFFIX,cloudflare.com,免费机场'
    - 'DOMAIN-SUFFIX,cloudfront.net,免费机场'
    - 'DOMAIN-SUFFIX,cloudmagic.com,免费机场'
    - 'DOMAIN-SUFFIX,cmail19.com,免费机场'
    - 'DOMAIN-SUFFIX,cnet.com,免费机场'
    - 'DOMAIN-SUFFIX,cocoapods.org,免费机场'
    - 'DOMAIN-SUFFIX,comodoca.com,免费机场'
    - 'DOMAIN-SUFFIX,crashlytics.com,免费机场'
    - 'DOMAIN-SUFFIX,culturedcode.com,免费机场'
    - 'DOMAIN-SUFFIX,d.pr,免费机场'
    - 'DOMAIN-SUFFIX,danilo.to,免费机场'
    - 'DOMAIN-SUFFIX,dayone.me,免费机场'
    - 'DOMAIN-SUFFIX,db.tt,免费机场'
    - 'DOMAIN-SUFFIX,deskconnect.com,免费机场'
    - 'DOMAIN-SUFFIX,disq.us,免费机场'
    - 'DOMAIN-SUFFIX,disqus.com,免费机场'
    - 'DOMAIN-SUFFIX,disquscdn.com,免费机场'
    - 'DOMAIN-SUFFIX,dnsimple.com,免费机场'
    - 'DOMAIN-SUFFIX,docker.com,免费机场'
    - 'DOMAIN-SUFFIX,dribbble.com,免费机场'
    - 'DOMAIN-SUFFIX,droplr.com,免费机场'
    - 'DOMAIN-SUFFIX,duckduckgo.com,免费机场'
    - 'DOMAIN-SUFFIX,dueapp.com,免费机场'
    - 'DOMAIN-SUFFIX,dytt8.net,免费机场'
    - 'DOMAIN-SUFFIX,edgecastcdn.net,免费机场'
    - 'DOMAIN-SUFFIX,edgekey.net,免费机场'
    - 'DOMAIN-SUFFIX,edgesuite.net,免费机场'
    - 'DOMAIN-SUFFIX,engadget.com,免费机场'
    - 'DOMAIN-SUFFIX,entrust.net,免费机场'
    - 'DOMAIN-SUFFIX,eurekavpt.com,免费机场'
    - 'DOMAIN-SUFFIX,evernote.com,免费机场'
    - 'DOMAIN-SUFFIX,fabric.io,免费机场'
    - 'DOMAIN-SUFFIX,fast.com,免费机场'
    - 'DOMAIN-SUFFIX,fastly.net,免费机场'
    - 'DOMAIN-SUFFIX,fc2.com,免费机场'
    - 'DOMAIN-SUFFIX,feedburner.com,免费机场'
    - 'DOMAIN-SUFFIX,feedly.com,免费机场'
    - 'DOMAIN-SUFFIX,feedsportal.com,免费机场'
    - 'DOMAIN-SUFFIX,fiftythree.com,免费机场'
    - 'DOMAIN-SUFFIX,firebaseio.com,免费机场'
    - 'DOMAIN-SUFFIX,flexibits.com,免费机场'
    - 'DOMAIN-SUFFIX,flickr.com,免费机场'
    - 'DOMAIN-SUFFIX,flipboard.com,免费机场'
    - 'DOMAIN-SUFFIX,g.co,免费机场'
    - 'DOMAIN-SUFFIX,gabia.net,免费机场'
    - 'DOMAIN-SUFFIX,geni.us,免费机场'
    - 'DOMAIN-SUFFIX,gfx.ms,免费机场'
    - 'DOMAIN-SUFFIX,ggpht.com,免费机场'
    - 'DOMAIN-SUFFIX,ghostnoteapp.com,免费机场'
    - 'DOMAIN-SUFFIX,git.io,免费机场'
    - 'DOMAIN-KEYWORD,github,免费机场'
    - 'DOMAIN-SUFFIX,globalsign.com,免费机场'
    - 'DOMAIN-SUFFIX,gmodules.com,免费机场'
    - 'DOMAIN-SUFFIX,godaddy.com,免费机场'
    - 'DOMAIN-SUFFIX,golang.org,免费机场'
    - 'DOMAIN-SUFFIX,gongm.in,免费机场'
    - 'DOMAIN-SUFFIX,goo.gl,免费机场'
    - 'DOMAIN-SUFFIX,goodreaders.com,免费机场'
    - 'DOMAIN-SUFFIX,goodreads.com,免费机场'
    - 'DOMAIN-SUFFIX,gravatar.com,免费机场'
    - 'DOMAIN-SUFFIX,gstatic.com,免费机场'
    - 'DOMAIN-SUFFIX,gvt0.com,免费机场'
    - 'DOMAIN-SUFFIX,hockeyapp.net,免费机场'
    - 'DOMAIN-SUFFIX,hotmail.com,免费机场'
    - 'DOMAIN-SUFFIX,icons8.com,免费机场'
    - 'DOMAIN-SUFFIX,ifixit.com,免费机场'
    - 'DOMAIN-SUFFIX,ift.tt,免费机场'
    - 'DOMAIN-SUFFIX,ifttt.com,免费机场'
    - 'DOMAIN-SUFFIX,iherb.com,免费机场'
    - 'DOMAIN-SUFFIX,imageshack.us,免费机场'
    - 'DOMAIN-SUFFIX,img.ly,免费机场'
    - 'DOMAIN-SUFFIX,imgur.com,免费机场'
    - 'DOMAIN-SUFFIX,imore.com,免费机场'
    - 'DOMAIN-SUFFIX,instapaper.com,免费机场'
    - 'DOMAIN-SUFFIX,ipn.li,免费机场'
    - 'DOMAIN-SUFFIX,is.gd,免费机场'
    - 'DOMAIN-SUFFIX,issuu.com,免费机场'
    - 'DOMAIN-SUFFIX,itgonglun.com,免费机场'
    - 'DOMAIN-SUFFIX,itun.es,免费机场'
    - 'DOMAIN-SUFFIX,ixquick.com,免费机场'
    - 'DOMAIN-SUFFIX,j.mp,免费机场'
    - 'DOMAIN-SUFFIX,js.revsci.net,免费机场'
    - 'DOMAIN-SUFFIX,jshint.com,免费机场'
    - 'DOMAIN-SUFFIX,jtvnw.net,免费机场'
    - 'DOMAIN-SUFFIX,justgetflux.com,免费机场'
    - 'DOMAIN-SUFFIX,kat.cr,免费机场'
    - 'DOMAIN-SUFFIX,klip.me,免费机场'
    - 'DOMAIN-SUFFIX,libsyn.com,免费机场'
    - 'DOMAIN-SUFFIX,linkedin.com,免费机场'
    - 'DOMAIN-SUFFIX,line-apps.com,免费机场'
    - 'DOMAIN-SUFFIX,linode.com,免费机场'
    - 'DOMAIN-SUFFIX,lithium.com,免费机场'
    - 'DOMAIN-SUFFIX,littlehj.com,免费机场'
    - 'DOMAIN-SUFFIX,live.com,免费机场'
    - 'DOMAIN-SUFFIX,live.net,免费机场'
    - 'DOMAIN-SUFFIX,livefilestore.com,免费机场'
    - 'DOMAIN-SUFFIX,llnwd.net,免费机场'
    - 'DOMAIN-SUFFIX,macid.co,免费机场'
    - 'DOMAIN-SUFFIX,macromedia.com,免费机场'
    - 'DOMAIN-SUFFIX,macrumors.com,免费机场'
    - 'DOMAIN-SUFFIX,mashable.com,免费机场'
    - 'DOMAIN-SUFFIX,mathjax.org,免费机场'
    - 'DOMAIN-SUFFIX,medium.com,免费机场'
    - 'DOMAIN-SUFFIX,mega.co.nz,免费机场'
    - 'DOMAIN-SUFFIX,mega.nz,免费机场'
    - 'DOMAIN-SUFFIX,megaupload.com,免费机场'
    - 'DOMAIN-SUFFIX,microsofttranslator.com,免费机场'
    - 'DOMAIN-SUFFIX,mindnode.com,免费机场'
    - 'DOMAIN-SUFFIX,mobile01.com,免费机场'
    - 'DOMAIN-SUFFIX,modmyi.com,免费机场'
    - 'DOMAIN-SUFFIX,msedge.net,免费机场'
    - 'DOMAIN-SUFFIX,myfontastic.com,免费机场'
    - 'DOMAIN-SUFFIX,name.com,免费机场'
    - 'DOMAIN-SUFFIX,nextmedia.com,免费机场'
    - 'DOMAIN-SUFFIX,nsstatic.net,免费机场'
    - 'DOMAIN-SUFFIX,nssurge.com,免费机场'
    - 'DOMAIN-SUFFIX,nyt.com,免费机场'
    - 'DOMAIN-SUFFIX,nytimes.com,免费机场'
    - 'DOMAIN-SUFFIX,omnigroup.com,免费机场'
    - 'DOMAIN-SUFFIX,onedrive.com,免费机场'
    - 'DOMAIN-SUFFIX,onenote.com,免费机场'
    - 'DOMAIN-SUFFIX,ooyala.com,免费机场'
    - 'DOMAIN-SUFFIX,openvpn.net,免费机场'
    - 'DOMAIN-SUFFIX,openwrt.org,免费机场'
    - 'DOMAIN-SUFFIX,orkut.com,免费机场'
    - 'DOMAIN-SUFFIX,osxdaily.com,免费机场'
    - 'DOMAIN-SUFFIX,outlook.com,免费机场'
    - 'DOMAIN-SUFFIX,ow.ly,免费机场'
    - 'DOMAIN-SUFFIX,paddleapi.com,免费机场'
    - 'DOMAIN-SUFFIX,parallels.com,免费机场'
    - 'DOMAIN-SUFFIX,parse.com,免费机场'
    - 'DOMAIN-SUFFIX,pdfexpert.com,免费机场'
    - 'DOMAIN-SUFFIX,periscope.tv,免费机场'
    - 'DOMAIN-SUFFIX,pinboard.in,免费机场'
    - 'DOMAIN-SUFFIX,pinterest.com,免费机场'
    - 'DOMAIN-SUFFIX,pixelmator.com,免费机场'
    - 'DOMAIN-SUFFIX,pixiv.net,免费机场'
    - 'DOMAIN-SUFFIX,playpcesor.com,免费机场'
    - 'DOMAIN-SUFFIX,playstation.com,免费机场'
    - 'DOMAIN-SUFFIX,playstation.com.hk,免费机场'
    - 'DOMAIN-SUFFIX,playstation.net,免费机场'
    - 'DOMAIN-SUFFIX,playstationnetwork.com,免费机场'
    - 'DOMAIN-SUFFIX,pushwoosh.com,免费机场'
    - 'DOMAIN-SUFFIX,rime.im,免费机场'
    - 'DOMAIN-SUFFIX,servebom.com,免费机场'
    - 'DOMAIN-SUFFIX,sfx.ms,免费机场'
    - 'DOMAIN-SUFFIX,shadowsocks.org,免费机场'
    - 'DOMAIN-SUFFIX,sharethis.com,免费机场'
    - 'DOMAIN-SUFFIX,shazam.com,免费机场'
    - 'DOMAIN-SUFFIX,skype.com,免费机场'
    - 'DOMAIN-SUFFIX,smartdns免费机场.com,免费机场'
    - 'DOMAIN-SUFFIX,smartmailcloud.com,免费机场'
    - 'DOMAIN-SUFFIX,sndcdn.com,免费机场'
    - 'DOMAIN-SUFFIX,sony.com,免费机场'
    - 'DOMAIN-SUFFIX,soundcloud.com,免费机场'
    - 'DOMAIN-SUFFIX,sourceforge.net,免费机场'
    - 'DOMAIN-SUFFIX,spotify.com,免费机场'
    - 'DOMAIN-SUFFIX,squarespace.com,免费机场'
    - 'DOMAIN-SUFFIX,sstatic.net,免费机场'
    - 'DOMAIN-SUFFIX,st.luluku.pw,免费机场'
    - 'DOMAIN-SUFFIX,stackoverflow.com,免费机场'
    - 'DOMAIN-SUFFIX,startpage.com,免费机场'
    - 'DOMAIN-SUFFIX,staticflickr.com,免费机场'
    - 'DOMAIN-SUFFIX,steamcommunity.com,免费机场'
    - 'DOMAIN-SUFFIX,symauth.com,免费机场'
    - 'DOMAIN-SUFFIX,symcb.com,免费机场'
    - 'DOMAIN-SUFFIX,symcd.com,免费机场'
    - 'DOMAIN-SUFFIX,tapbots.com,免费机场'
    - 'DOMAIN-SUFFIX,tapbots.net,免费机场'
    - 'DOMAIN-SUFFIX,tdesktop.com,免费机场'
    - 'DOMAIN-SUFFIX,techcrunch.com,免费机场'
    - 'DOMAIN-SUFFIX,techsmith.com,免费机场'
    - 'DOMAIN-SUFFIX,thepiratebay.org,免费机场'
    - 'DOMAIN-SUFFIX,theverge.com,免费机场'
    - 'DOMAIN-SUFFIX,time.com,免费机场'
    - 'DOMAIN-SUFFIX,timeinc.net,免费机场'
    - 'DOMAIN-SUFFIX,tiny.cc,免费机场'
    - 'DOMAIN-SUFFIX,tinypic.com,免费机场'
    - 'DOMAIN-SUFFIX,tmblr.co,免费机场'
    - 'DOMAIN-SUFFIX,todoist.com,免费机场'
    - 'DOMAIN-SUFFIX,trello.com,免费机场'
    - 'DOMAIN-SUFFIX,trustasiassl.com,免费机场'
    - 'DOMAIN-SUFFIX,tumblr.co,免费机场'
    - 'DOMAIN-SUFFIX,tumblr.com,免费机场'
    - 'DOMAIN-SUFFIX,tweetdeck.com,免费机场'
    - 'DOMAIN-SUFFIX,tweetmarker.net,免费机场'
    - 'DOMAIN-SUFFIX,twitch.tv,免费机场'
    - 'DOMAIN-SUFFIX,txmblr.com,免费机场'
    - 'DOMAIN-SUFFIX,typekit.net,免费机场'
    - 'DOMAIN-SUFFIX,ubertags.com,免费机场'
    - 'DOMAIN-SUFFIX,ublock.org,免费机场'
    - 'DOMAIN-SUFFIX,ubnt.com,免费机场'
    - 'DOMAIN-SUFFIX,ulyssesapp.com,免费机场'
    - 'DOMAIN-SUFFIX,urchin.com,免费机场'
    - 'DOMAIN-SUFFIX,usertrust.com,免费机场'
    - 'DOMAIN-SUFFIX,v.gd,免费机场'
    - 'DOMAIN-SUFFIX,v2ex.com,免费机场'
    - 'DOMAIN-SUFFIX,vimeo.com,免费机场'
    - 'DOMAIN-SUFFIX,vimeocdn.com,免费机场'
    - 'DOMAIN-SUFFIX,vine.co,免费机场'
    - 'DOMAIN-SUFFIX,vivaldi.com,免费机场'
    - 'DOMAIN-SUFFIX,vox-cdn.com,免费机场'
    - 'DOMAIN-SUFFIX,vsco.co,免费机场'
    - 'DOMAIN-SUFFIX,vultr.com,免费机场'
    - 'DOMAIN-SUFFIX,w.org,免费机场'
    - 'DOMAIN-SUFFIX,w3schools.com,免费机场'
    - 'DOMAIN-SUFFIX,webtype.com,免费机场'
    - 'DOMAIN-SUFFIX,wikiwand.com,免费机场'
    - 'DOMAIN-SUFFIX,wikileaks.org,免费机场'
    - 'DOMAIN-SUFFIX,wikimedia.org,免费机场'
    - 'DOMAIN-SUFFIX,wikipedia.com,免费机场'
    - 'DOMAIN-SUFFIX,wikipedia.org,免费机场'
    - 'DOMAIN-SUFFIX,windows.com,免费机场'
    - 'DOMAIN-SUFFIX,windows.net,免费机场'
    - 'DOMAIN-SUFFIX,wire.com,免费机场'
    - 'DOMAIN-SUFFIX,wordpress.com,免费机场'
    - 'DOMAIN-SUFFIX,workflowy.com,免费机场'
    - 'DOMAIN-SUFFIX,wp.com,免费机场'
    - 'DOMAIN-SUFFIX,wsj.com,免费机场'
    - 'DOMAIN-SUFFIX,wsj.net,免费机场'
    - 'DOMAIN-SUFFIX,xda-developers.com,免费机场'
    - 'DOMAIN-SUFFIX,xeeno.com,免费机场'
    - 'DOMAIN-SUFFIX,xiti.com,免费机场'
    - 'DOMAIN-SUFFIX,yahoo.com,免费机场'
    - 'DOMAIN-SUFFIX,yimg.com,免费机场'
    - 'DOMAIN-SUFFIX,ying.com,免费机场'
    - 'DOMAIN-SUFFIX,yoyo.org,免费机场'
    - 'DOMAIN-SUFFIX,ytimg.com,免费机场'
    - 'DOMAIN-SUFFIX,telegra.ph,免费机场'
    - 'DOMAIN-SUFFIX,telegram.org,免费机场'
    - 'IP-CIDR,91.108.4.0/22,免费机场,no-resolve'
    - 'IP-CIDR,91.108.8.0/21,免费机场,no-resolve'
    - 'IP-CIDR,91.108.16.0/22,免费机场,no-resolve'
    - 'IP-CIDR,91.108.56.0/22,免费机场,no-resolve'
    - 'IP-CIDR,149.154.160.0/20,免费机场,no-resolve'
    - 'IP-CIDR6,2001:67c:4e8::/48,免费机场,no-resolve'
    - 'IP-CIDR6,2001:b28:f23d::/48,免费机场,no-resolve'
    - 'IP-CIDR6,2001:b28:f23f::/48,免费机场,no-resolve'
    - 'IP-CIDR,120.232.181.162/32,免费机场,no-resolve'
    - 'IP-CIDR,120.241.147.226/32,免费机场,no-resolve'
    - 'IP-CIDR,120.253.253.226/32,免费机场,no-resolve'
    - 'IP-CIDR,120.253.255.162/32,免费机场,no-resolve'
    - 'IP-CIDR,120.253.255.34/32,免费机场,no-resolve'
    - 'IP-CIDR,120.253.255.98/32,免费机场,no-resolve'
    - 'IP-CIDR,180.163.150.162/32,免费机场,no-resolve'
    - 'IP-CIDR,180.163.150.34/32,免费机场,no-resolve'
    - 'IP-CIDR,180.163.151.162/32,免费机场,no-resolve'
    - 'IP-CIDR,180.163.151.34/32,免费机场,no-resolve'
    - 'IP-CIDR,203.208.39.0/24,免费机场,no-resolve'
    - 'IP-CIDR,203.208.40.0/24,免费机场,no-resolve'
    - 'IP-CIDR,203.208.41.0/24,免费机场,no-resolve'
    - 'IP-CIDR,203.208.43.0/24,免费机场,no-resolve'
    - 'IP-CIDR,203.208.50.0/24,免费机场,no-resolve'
    - 'IP-CIDR,220.181.174.162/32,免费机场,no-resolve'
    - 'IP-CIDR,220.181.174.226/32,免费机场,no-resolve'
    - 'IP-CIDR,220.181.174.34/32,免费机场,no-resolve'
    - 'DOMAIN,injections.adguard.org,DIRECT'
    - 'DOMAIN,local.adguard.org,DIRECT'
    - 'DOMAIN-SUFFIX,local,DIRECT'
    - 'IP-CIDR,127.0.0.0/8,DIRECT'
    - 'IP-CIDR,172.16.0.0/12,DIRECT'
    - 'IP-CIDR,192.168.0.0/16,DIRECT'
    - 'IP-CIDR,10.0.0.0/8,DIRECT'
    - 'IP-CIDR,17.0.0.0/8,DIRECT'
    - 'IP-CIDR,100.64.0.0/10,DIRECT'
    - 'IP-CIDR,224.0.0.0/4,DIRECT'
    - 'IP-CIDR6,fe80::/10,DIRECT'
    - 'DOMAIN-SUFFIX,cn,DIRECT'
    - 'DOMAIN-KEYWORD,-cn,DIRECT'
    - 'GEOIP,CN,DIRECT'
    - 'MATCH,免费机场'
