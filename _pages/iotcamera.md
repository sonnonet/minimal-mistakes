---
title: "스마트 IoT 카메라"
header:
   image: /assets/images/rpc.png
   cation: "Made by : [**Sonnonet**](http://www.sonnonet.com)"
permalink: /iotcamera/

layouts_gallery:
  - url: /assets/images/iotcamera_1.jpg
    image_path: /assets/images/iotcamera_1.jpg
    alt: "installtion of airconditioner"
  - url: /assets/images/iotcamera_2.png
    image_path: /assets/images/iotcamera_2.png
    alt: "installtion of washing machine"
#  - url: /assets/images/okplug_micro.png
#    image_path: /assets/images/okplug_micro.png
#    alt: "installtion of microwave"
last_modified_at: 2017-02-14T14:28:13-05:00
---

저가격 임베디드 하드웨어로 구성된 Pi 카메라와 라즈베리파이 게이트웨이를 통해 특정 타겟에 이미지를 촬영 후 서버로 전송하여 저장된 이미지로 부터 구글 Vision API를 이용하여 정보를 추출하는 어플리케이션

## 기능

```
    - 라즈베리파이 카메라 이미지 시간별 촬영 기능
    - 라즈베리파이 카메라 이미지 네트워크 전송 기능 
    - 년/일/시간별 이미지 저장기능 
    - 저장된 이미지 분류/히스토리 기능
    - 촬영된 이미지로 부터 특정 정보 문자 추출하는 기능
    - 이미지 서버 스케쥴링 기능
    - 라즈베리파이 외부접속 자동 DDNS 기능
```

{% include gallery id="layouts_gallery" caption="Examples of installtion `airconditioner`, `powermeter`, and `totalpowermeter`." %}

[Install]({{ "/quick-start-guide/" | absolute_url }}){: .btn .btn--success .btn--large}



