---
layout: post
title: The process of UDP hole punching
category: UDP
---
How the peers talk with each other behind the NAT.

![UDP hole punching](res/img/udp_hole_punching.png)

* **目的**
	在NAT设备后面的需要A与B需要通过UDP进行相互通信。  
	NAT设备处理收到的UDP报文有两个普遍规则：
	  * 如果报文是从内部（private network）发送到外部的，则生成一条临时的规则，允许使用该源于目的地址:端口的报文通行；规则有效期有限，在有报文交互的情况下，该有效期会被刷新；
	  * 如果报文是从外部（public network）发送到内部的，则检查相应的NAT规则，如果没有匹配的源地址:端口，则丢弃；  
	
	故由于NAT设备的存在，A与B即使知道对方的public IP:port，也无法相互通信，除非他们同时发送报文到对端，所以他们需要一个中间人做协调，告诉对方自己是否已经在NAT上打好洞，是否可以开始进行报文传输。  

* **过程**
    * A与B与中间人（Server）保持通话，A与B周期性地给server报告各自的private IP:port，通过NAT之后，转换成相应的public IP:port报告给server，server即拥有需要通信的A、B各自的public IP:port信息；
    * 当A需要和B进行通信时，A首先将需求报告给server；
    * server收到要求通信的请求后，将A的public IP:port信息发送给B，同样将B的public IP:port发送给A，A与B均知道了彼此的public IP:port；
    * B向A发送一个试探消息（主动打B侧的洞），消息的目的地址即是server告知的A的地址，报文可以从B侧的NAT出去，这样就在B侧的NAT上打了一个洞，如果A能够以此地址返回报文，则可以通过NAT；当然报文会在A侧的NAT上被丢弃，因为这个外来的报文的地址:端口不认识；
    * A也向B发送一个试探消息（主动打A侧的洞），消息的目的地址即是server告知的B的地址，因为B已经发送过一个试探报文（洞已通），B侧的NAT能够接收该源地址来的报文，所以报文可以通过NAT，到达B；
    * 同样，后续B发送给A的报文也因为同样的源地址:端口已经在A侧的NAT上记录，报文可以通过A侧的NAT设备，到达A；
    * Hole Punched!


###reference
https://www.usenix.org/legacy/event/usenix05/tech/general/full_papers/ford/ford_html/


