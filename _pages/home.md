---
layout: splash
permalink: /
header:
  overlay_color: "#5e616c"
#  overlay_image: /assets/images/mm-home-page-feature.jpg
  cta_label: "<i class='fa fa-download'></i> Install Now"
  cta_url: "/quick-start-guide/"
  caption:
  excerpt: 'Sonnonet IoT Collection for AI <br /> <small><a href="https://github.com/sonnonet/sonnonet.github.io/releases/tag/4.4.1">Latest release v1.0.1</a></small><br /><br /> {::nomarkdown}<iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe> <iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=fork&count=true&size=large" frameborder="0" scrolling="0" width="158px" height="30px"></iframe>{:/nomarkdown}'
feature_row:
  - image_path: /assets/images/iothub.png
    alt: "sonnonet"
    title: "스마트 IoT 허브"
    excerpt: "무선센서 네트워크의 데이터를 안정적으로 수집/저장하여, 클라우드 서버시스템과 연동하는 스마트 IoT허브  시스템"
    url: "http://localhost:4000/iothub/"
#    url: "https://sonnonet.github.io/iothub"
    btn_label: "Learn More"
    
  - image_path: /assets/images/okplug_2.png
    alt: "sonnonet"
    title: "스마트 IoT 플러그"
    excerpt: "와이파이 스마트 플러그의 데이터를 수집/저장하여, 개별전력량을 웹 GUI로 보여주는 스마트 플러그 시스템"
#    url: "https://sonnonet.github.io/wplug"
    url: "http://localhost:4000/wplug/"
    btn_label: "Learn More"

  - image_path: /assets/images/rpc.png
    alt: "sonnonet"
    title: "스마트 IoT 카메라"
    excerpt: "라즈베리파이 카메라센서를 이용하여 타겟의 이미지를 서버로 전송하고 저장된 이미지로 부터 특정 정보를 추출하는 스마트 카메라 시스템 "
    url: "https://sonnonet.github.io/iothub"
    btn_label: "Learn More"

github:
  - excerpt: '{::nomarkdown}<iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe> <iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=fork&count=true&size=large" frameborder="0" scrolling="0" width="158px" height="30px"></iframe>{:/nomarkdown}'

intro:
  - excerpt: 'Get notified when I add new stuff &nbsp; [<i class="fa fa-twitter"></i> @sonnonet](https://twitter.com/mmistakes){: .btn .btn--twitter} [<i class="fa fa-paypal"></i> Tip Me](https://www.paypal.me/mmistakes){: .btn}'
---

{% include feature_row id="intro" type="center" %}

{% include feature_row %}
