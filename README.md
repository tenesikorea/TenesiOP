# TenesiOP

테네시 오픈 파일럿 도움말 - 브랜치의 포크는 NeoKii 교주사마님의 기본 포크를 기반으로 합니다..

21년 07월 06일 업데이트 내용 일부 설명..
[![](http://drive.google.com/uc?export=view&id=1hL0i6yiO2y5guzUY43wJ7vcj3V_1NFIk)](#)
- Prebuilt 파일생성 - 이건 모든 셋팅이 완료되고 빠른 부팅을 할때에 사용됩니다..주 기능은 빌드작업을 생략 개념이고 일부 강제 빌드는 무조건 빌드합니다..
  만약에 깃풀을 할때에 이부분이 켜져있고 깃풀을 하고 재부팅시에는 블랙스크린이 나올수 있으니 필수로 해제하세요!
  그리고 절차상 프리빌트해제및 깃리셋후에 깃풀을 추천합니다.. 재부팅이 정상일때에 다시 해제해서 적용이 가능하고
  만약에 블랙스크린등으로 부팅이 문제가 있으면 Ntune으로 프리빌트 삭제후에 부팅하면 됩니다..
  -(github.com/openpilotusers 에서 힌트를 얻어서 작성)
  
- GPS 오프  - 이건 GPS장치오류로 자동종료가 안되는 경우에 사용합니다.. 대표적으로 화이트 판다 사용자의 경우에 자동종료가 안됩니다..
   필수로 쓰셔야 합니다..
  -(github.com/openpilotusers 에서 힌트를 얻어서 작성)
  
- GitPull 관련 명령어를 내장...
  - 되도록 쓰지마시고.. 제 브랜치를 꾸준히 사용한다면 커밋(로컬/리모트)항목중 리모트가 파란색일때 또는 임의로 가능합니다..
    문제는 테스트중일때 꼬이면 EON폰도 꼬입니다.. 문의하고 하시길 추천합니다..주의 할점은 일부 반영이 안될수 있는데
    깃리셋후 깃풀을 추천합니다..특히나 종료시간을 임의 설정하면 반영이 안되기도 합니다..
  -(github.com/openpilotusers 에서 힌트를 얻어서 작성)
   
Git Pull 명령어 작업시에 SSL 에러 표시가 나오면서 업데이트가 안될때! 
  -> SSH 터미널에 접속해서 export GIT_SSL_NO_VERIFY=0 실행한다..

SSH터미널에서 VI,VIM명령어로 화일 내용을 수정하는 명령.. 
주요 명령 : 
  현재 편집 화일에서 나가기 => :q (키보드의 클론을 누르고 영어 q를 누른다 : 이걸 누른후에는 명령어 입력한다는 의미) 
  현재 편집 화일 저장하기 => :w (:wq 라면 저장하고 나가기가 된다)
  현재 편집 화일 저장안하고 나가기 => :qi 편집실수등을 보완..

  현재 커서위치에서 키보드의 i를 누르면 => 하단부에 insert가 나오면서 추가 모드가 된다.. ESC 누르면 취소 
  현재 커서위치에서 키보드의 r를 누르면 => 하단부에 아무것도 안나오고 입려되는 문자를 입력해서 바뀐다.. 
  현재 커서위치에서 키보드의 dd를 누르면 => 해당줄을 모두 삭제한다.

키보드 u를 누르면 입력해서 수정한것을 취소해서 원래되로 되돌린다...

운전 종료하고 이온폰이 자동으로 꺼지는 시간 설정하기.. 
  터미널 접속후
  
  vim /data/openpilot/selfdrive/shutdownd.py
  60초 * 1.00 은 60초로 1분후 종료.. 수정후 :wq

이온 화면을 강제로 어둡게 하거나 밝게 하기.. 
  터미널 접속후
  
  vim /data/openpilot/selfdrive/hardware/eon/hardware.h 
  
  //percent = 15;
  주석처리를 할경우에 (자동모드로 변경할경우) //를 넣어준다..  
  수정하고 :wq 
  
  percent = 15; // 배터리리스-다이오드방식에서 화면 밝기 적게 해보기

100퍼센트 밝기중에서 15프로 밝기로 어둡게 설정된 상태.. 수정하고 :wq

-------------------210705일자로 화이트 판다는 선택사항으로 적용-----------------------------------
화이트 판다의 경우 자동 종료가 안될때에..
vim /data/openpilot/selfdrive/boardd/boardd.cc 
화일을 열어서 제일 하단부에
	  //if(panda->is_pigeon)  // 화이트(비둘기 판다) 용
	      //threads.push_back(std::thread(pigeon_thread));  // 화이트(비둘기 판다) 용
주석처리를 하세요... 

상기 모든 적용사양을 재부팅을 해야 적용됩니다.. 음성 사운드 관련 설정등도 재부팅해야 적용됩니다..

--------------------------------------------------------------------------------------------
- TWRP 및 이온접속 - 공부 자료 동영상 - 초창기 eon.ppk를 활용해서 접속 가능한 동영상 
   https://drive.google.com/file/d/12uGwVXZkMyyDWaF0heV_ouDb8PyqBedU/view?usp=sharing
   https://drive.google.com/file/d/1Lp_Y5vGeG-R4KqMHeQrinaax4r-VBguS/view?usp=sharing
   https://drive.google.com/file/d/143vkDqCB99fjvmqJm3OjxE9PLiB1ksC-/view?usp=sharing
   https://drive.google.com/file/d/1TeVzSJra-ZySX7Ea70GMH6ER9NndQ_ca/view?usp=sharing
-------------------------------------------------------------------------------------------- 
- 안드로이드 폰에서 엔튠과 터보클라이언트 관련해서 등록 하는법등 동영상
https://drive.google.com/file/d/1UmV6d-_Uqim-lml2WIHSZReWLaPGk8mn/view?usp=sharing
------21년 6월 10일 초보와 고수도 봐야 하는 오픈파일럿 셋팅 관련된 내용 저장-------

다운로드 링크 
- 테네시 파일럿 전용 SSH접속시 필요한 ppk 화일 다운로드 경로 - 암호로 다운로드 가능함..
http://naver.me/xv0Ig0d5 
- Ntune 앱설치 다운로드.. 
https://drive.google.com/file/d/1-EPga-ukGl9p4SsTMCKfJs6zrZpZ6dqC/view?usp=sharing 
- 터보클라이언트로 SSH터미널이 아닌 상태에서 접속해서 수정이 가능한 앱으로 추천!  
https://play.google.com/store/apps/details?id=turbo.client 
- ssh 터미널앱으로 vim으로 편집가능한 앱이며 되도록 필수로 설치를 요하는 앱.. 특히나 ssl에러시에 필수다..
https://play.google.com/store/apps/details?id=com.sonelli.juicessh 
- 퍼티 64비트 PC용
https://drive.google.com/file/d/1slJ-aa5CLzwbFc3fPXk0nypgFKxUWUQr/view?usp=sharing
- 퍼티 32비트 PC용
https://drive.google.com/file/d/1yCZpOe12nrI2uHG9pY6S5pm87yv9RwpC/view?usp=sharing
- winscp PC용
https://drive.google.com/file/d/1rYHd_vI5KnaFQgQjweTHYYHRxqZXwbFK/view?usp=sharing


**This is based on xx979xx for Hyundai, Kia, Genesis.**

https://github.com/xx979xx/openpilot

It is open source and inherits MIT license. It is open source and inherits MIT license.  By installing this software you accept all responsibility for anything that might occur while you use it.  All contributors to this fork are not liable.  <b>Use at your own risk.</b>


------------------------------------------------------


[![](https://i.imgur.com/UelUjKAh.png)](#)

Table of Contents
=======================

* [What is openpilot?](#what-is-openpilot)
* [Integration with Stock Features](#integration-with-stock-features)
* [Supported Hardware](#supported-hardware)
* [Supported Cars](#supported-cars)
* [Community Maintained Cars and Features](#community-maintained-cars-and-features)
* [Installation Instructions](#installation-instructions)
* [Limitations of openpilot ALC and LDW](#limitations-of-openpilot-alc-and-ldw)
* [Limitations of openpilot ACC and FCW](#limitations-of-openpilot-acc-and-fcw)
* [Limitations of openpilot DM](#limitations-of-openpilot-dm)
* [User Data and comma Account](#user-data-and-comma-account)
* [Safety and Testing](#safety-and-testing)
* [Testing on PC](#testing-on-pc)
* [Community and Contributing](#community-and-contributing)
* [Directory Structure](#directory-structure)
* [Licensing](#licensing)

---

What is openpilot?
------

[openpilot](http://github.com/commaai/openpilot) is an open source driver assistance system. Currently, openpilot performs the functions of Adaptive Cruise Control (ACC), Automated Lane Centering (ALC), Forward Collision Warning (FCW) and Lane Departure Warning (LDW) for a growing variety of supported [car makes, models and model years](#supported-cars). In addition, while openpilot is engaged, a camera based Driver Monitoring (DM) feature alerts distracted and asleep drivers.

<table>
  <tr>
    <td><a href="https://www.youtube.com/watch?v=mgAbfr42oI8" title="YouTube" rel="noopener"><img src="https://i.imgur.com/kAtT6Ei.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=394rJKeh76k" title="YouTube" rel="noopener"><img src="https://i.imgur.com/lTt8cS2.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=1iNOc3cq8cs" title="YouTube" rel="noopener"><img src="https://i.imgur.com/ANnuSpe.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=Vr6NgrB-zHw" title="YouTube" rel="noopener"><img src="https://i.imgur.com/Qypanuq.png"></a></td>
  </tr>
  <tr>
    <td><a href="https://www.youtube.com/watch?v=Ug41KIKF0oo" title="YouTube" rel="noopener"><img src="https://i.imgur.com/3caZ7xM.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=NVR_CdG1FRg" title="YouTube" rel="noopener"><img src="https://i.imgur.com/bAZOwql.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=tkEvIdzdfUE" title="YouTube" rel="noopener"><img src="https://i.imgur.com/EFINEzG.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=_P-N1ewNne4" title="YouTube" rel="noopener"><img src="https://i.imgur.com/gAyAq22.png"></a></td>
  </tr>
</table>

Integration with Stock Features
------

In all supported cars:
* Stock Lane Keep Assist (LKA) and stock ALC are replaced by openpilot ALC, which only functions when openpilot is engaged by the user.
* Stock LDW is replaced by openpilot LDW.

Additionally, on specific supported cars (see ACC column in [supported cars](#supported-cars)):
* Stock ACC is replaced by openpilot ACC.
* openpilot FCW operates in addition to stock FCW.

openpilot should preserve all other vehicle's stock features, including, but are not limited to: FCW, Automatic Emergency Braking (AEB), auto high-beam, blind spot warning, and side collision warning.

Supported Hardware
------

At the moment, openpilot supports the EON Gold DevKit and the [comma two](https://comma.ai/shop/products/comma-two-devkit). A [car harness](https://comma.ai/shop/products/car-harness) is recommended to connect the EON or comma two to the car. For experimental purposes, openpilot can also run on an Ubuntu computer with external [webcams](https://github.com/commaai/openpilot/tree/master/tools/webcam).

Supported Cars
------

| Make      | Model (US Market Reference)   | Supported Package | ACC              | No ACC accel below | No ALC below      |
| ----------| ------------------------------| ------------------| -----------------| -------------------| ------------------|
| Acura     | ILX 2016-19                   | AcuraWatch Plus   | openpilot        | 25mph<sup>1</sup>  | 25mph             |
| Acura     | RDX 2016-18                   | AcuraWatch Plus   | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Acura     | RDX 2019-21                   | All               | Stock            | 0mph               | 3mph              |
| Honda     | Accord 2018-20                | All               | Stock            | 0mph               | 3mph              |
| Honda     | Accord Hybrid 2018-20         | All               | Stock            | 0mph               | 3mph              |
| Honda     | Civic Hatchback 2017-21       | Honda Sensing     | Stock            | 0mph               | 12mph             |
| Honda     | Civic Coupe 2016-18           | Honda Sensing     | openpilot        | 0mph               | 12mph             |
| Honda     | Civic Coupe 2019-20           | All               | Stock            | 0mph               | 2mph<sup>2</sup>  |
| Honda     | Civic Sedan 2016-18           | Honda Sensing     | openpilot        | 0mph               | 12mph             |
| Honda     | Civic Sedan 2019-20           | All               | Stock            | 0mph               | 2mph<sup>2</sup>  |
| Honda     | CR-V 2015-16                  | Touring           | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Honda     | CR-V 2017-21                  | Honda Sensing     | Stock            | 0mph               | 12mph             |
| Honda     | CR-V Hybrid 2017-2019         | Honda Sensing     | Stock            | 0mph               | 12mph             |
| Honda     | Fit 2018-19                   | Honda Sensing     | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Honda     | HR-V 2019-20                  | Honda Sensing     | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Honda     | Insight 2019-21               | All               | Stock            | 0mph               | 3mph              |
| Honda     | Inspire 2018                  | All               | Stock            | 0mph               | 3mph              |
| Honda     | Odyssey 2018-20               | Honda Sensing     | openpilot        | 25mph<sup>1</sup>  | 0mph              |
| Honda     | Passport 2019                 | All               | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Honda     | Pilot 2016-19                 | Honda Sensing     | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Honda     | Ridgeline 2017-21             | Honda Sensing     | openpilot        | 25mph<sup>1</sup>  | 12mph             |
| Hyundai   | Palisade 2020-21              | All               | Stock            | 0mph               | 0mph              |
| Hyundai   | Sonata 2020-21                | All               | Stock            | 0mph               | 0mph              |
| Lexus     | CT Hybrid 2017-18             | LSS               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | ES 2019-21                    | All               | openpilot        | 0mph               | 0mph              |
| Lexus     | ES Hybrid 2017-18             | LSS               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | ES Hybrid 2019-21             | All               | openpilot        | 0mph               | 0mph              |
| Lexus     | IS 2017-2019                  | All               | Stock            | 22mph              | 0mph              |
| Lexus     | NX 2018                       | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | NX 2020                       | All               | openpilot        | 0mph               | 0mph              |
| Lexus     | NX Hybrid 2018-19             | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | RX 2016-18                    | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | RX 2020-21                    | All               | openpilot        | 0mph               | 0mph              |
| Lexus     | RX Hybrid 2016-19             | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Lexus     | RX Hybrid 2020-21             | All               | openpilot        | 0mph               | 0mph              |
| Lexus     | UX Hybrid 2019-21             | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Alphard 2020                  | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Avalon 2016-21                | TSS-P             | Stock<sup>3</sup>| 20mph<sup>1</sup>  | 0mph              |
| Toyota    | Avalon Hybrid 2019-21         | TSS-P             | Stock<sup>3</sup>| 20mph<sup>1</sup>  | 0mph              |
| Toyota    | Camry 2018-20                 | All               | Stock            | 0mph<sup>4</sup>   | 0mph              |
| Toyota    | Camry 2021                    | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Camry Hybrid 2018-20          | All               | Stock            | 0mph<sup>4</sup>   | 0mph              |
| Toyota    | Camry Hybrid 2021             | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | C-HR 2017-20                  | All               | Stock            | 0mph               | 0mph              |
| Toyota    | C-HR Hybrid 2017-19           | All               | Stock            | 0mph               | 0mph              |
| Toyota    | Corolla 2017-19               | All               | Stock<sup>3</sup>| 20mph<sup>1</sup>  | 0mph              |
| Toyota    | Corolla 2020-21               | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Corolla Hatchback 2019-21     | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Corolla Hybrid 2020-21        | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Highlander 2017-19            | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Toyota    | Highlander 2020-21            | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Highlander Hybrid 2017-19     | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Toyota    | Highlander Hybrid 2020-21     | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Mirai 2021	                  | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Prius 2016-20                 | TSS-P             | Stock<sup>3</sup>| 0mph               | 0mph              |
| Toyota    | Prius 2021                    | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Prius Prime 2017-20           | All               | Stock<sup>3</sup>| 0mph               | 0mph              |
| Toyota    | Prius Prime 2021              | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Rav4 2016-18                  | TSS-P             | Stock<sup>3</sup>| 20mph<sup>1</sup>  | 0mph              |
| Toyota    | Rav4 2019-21                  | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Rav4 Hybrid 2016-18           | TSS-P             | Stock<sup>3</sup>| 0mph               | 0mph              |
| Toyota    | Rav4 Hybrid 2019-21           | All               | openpilot        | 0mph               | 0mph              |
| Toyota    | Sienna 2018-20                | All               | Stock<sup>3</sup>| 0mph               | 0mph              |

<sup>1</sup>[Comma Pedal](https://github.com/commaai/openpilot/wiki/comma-pedal) is used to provide stop-and-go capability to some of the openpilot-supported cars that don't currently support stop-and-go. ***NOTE: The Comma Pedal is not officially supported by [comma](https://comma.ai).*** <br />
<sup>2</sup>2019 Honda Civic 1.6L Diesel Sedan does not have ALC below 12mph. <br />
<sup>3</sup>When disconnecting the Driver Support Unit (DSU), openpilot ACC will replace stock ACC. ***NOTE: disconnecting the DSU disables Automatic Emergency Braking (AEB).*** <br />
<sup>4</sup>28mph for Camry 4CYL L, 4CYL LE and 4CYL SE which don't have Full-Speed Range Dynamic Radar Cruise Control. <br />

Community Maintained Cars and Features
------

| Make      | Model (US Market Reference)   | Supported Package | ACC              | No ACC accel below | No ALC below |
| ----------| ------------------------------| ------------------| -----------------| -------------------| -------------|
| Audi      | A3 2014-18                    | Prestige          | Stock            | 0mph               | 0mph         |
| Audi      | A3 Sportback e-tron 2017-18   | Prestige          | Stock            | 0mph               | 0mph         |
| Audi      | Q2 2018                       | Driver Assistance | Stock            | 0mph               | 0mph         |
| Buick     | Regal 2018<sup>1</sup>        | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Cadillac  | ATS 2018<sup>1</sup>          | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Chevrolet | Malibu 2017<sup>1</sup>       | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Chevrolet | Volt 2017-18<sup>1</sup>      | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Chrysler  | Pacifica 2017-18              | Adaptive Cruise   | Stock            | 0mph               | 9mph         |
| Chrysler  | Pacifica 2020                 | Adaptive Cruise   | Stock            | 0mph               | 39mph        |
| Chrysler  | Pacifica Hybrid 2017-18       | Adaptive Cruise   | Stock            | 0mph               | 9mph         |
| Chrysler  | Pacifica Hybrid 2019-21       | Adaptive Cruise   | Stock            | 0mph               | 39mph        |
| Genesis   | G70 2018                      | All               | Stock            | 0mph               | 0mph         |
| Genesis   | G80 2018                      | All               | Stock            | 0mph               | 0mph         |
| Genesis   | G90 2018                      | All               | Stock            | 0mph               | 0mph         |
| GMC       | Acadia 2018<sup>1</sup>       | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Holden    | Astra 2017<sup>1</sup>        | Adaptive Cruise   | openpilot        | 0mph               | 7mph         |
| Hyundai   | Elantra 2017-19               | SCC + LKAS        | Stock            | 19mph              | 34mph        |
| Hyundai   | Elantra 2021                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Elantra Hybrid 2021          | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Genesis 2015-16               | SCC + LKAS        | Stock            | 19mph              | 37mph        |
| Hyundai   | Ioniq Electric 2019           | SCC + LKAS        | Stock            | 0mph               | 32mph        |
| Hyundai   | Ioniq Electric 2020           | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Ioniq PHEV 2020               | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Kona 2020                     | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Kona EV 2019                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Santa Fe 2019-20              | All               | Stock            | 0mph               | 0mph         |
| Hyundai   | Sonata 2018-2019              | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Veloster 2019-20              | SCC + LKAS        | Stock            | 5mph               | 0mph         |
| Jeep      | Grand Cherokee 2016-18        | Adaptive Cruise   | Stock            | 0mph               | 9mph         |
| Jeep      | Grand Cherokee 2019-20        | Adaptive Cruise   | Stock            | 0mph               | 39mph        |
| Kia       | Forte 2018-2021               | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Niro EV 2020                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Optima 2017                   | SCC + LKAS        | Stock            | 0mph               | 32mph        |
| Kia       | Optima 2019                   | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Seltos 2021                   | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Sorento 2018-19               | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Stinger 2018                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Ceed 2019                     | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Nissan    | Altima 2019-20                | ProPILOT          | Stock            | 0mph               | 0mph         |
| Nissan    | Leaf 2018-20                  | ProPILOT          | Stock            | 0mph               | 0mph         |
| Nissan    | Rogue 2018-20                 | ProPILOT          | Stock            | 0mph               | 0mph         |
| Nissan    | X-Trail 2017                  | ProPILOT          | Stock            | 0mph               | 0mph         |
| SEAT      | Ateca 2018                    | Driver Assistance | Stock            | 0mph               | 0mph         |
| SEAT      | Leon 2014-2020                | Driver Assistance | Stock            | 0mph               | 0mph         |
| Škoda     | Kodiaq 2018                   | Driver Assistance | Stock            | 0mph               | 0mph         |
| Škoda     | Octavia 2015, 2019            | Driver Assistance | Stock            | 0mph               | 0mph         |
| Škoda     | Octavia RS 2016               | Driver Assistance | Stock            | 0mph               | 0mph         |
| Škoda     | Scala 2020                    | Driver Assistance | Stock            | 0mph               | 0mph         |
| Škoda     | Superb 2015-18                | Driver Assistance | Stock            | 0mph               | 0mph         |
| Subaru    | Ascent 2019                   | EyeSight          | Stock            | 0mph               | 0mph         |
| Subaru    | Crosstrek 2018-19             | EyeSight          | Stock            | 0mph               | 0mph         |
| Subaru    | Forester 2019-21              | EyeSight          | Stock            | 0mph               | 0mph         |
| Subaru    | Impreza 2017-19               | EyeSight          | Stock            | 0mph               | 0mph         |
| Volkswagen| Atlas 2018-19                 | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| e-Golf 2014, 2019-20          | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf 2015-19                  | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf Alltrack 2017-18         | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf GTE 2016                 | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf GTI 2018-19              | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf R 2016-19                | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf SportsVan 2016           | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Golf SportWagen 2015          | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Jetta 2018-20                 | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Jetta GLI 2021                | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Passat 2016-17<sup>2</sup>    | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Tiguan 2020                   | Driver Assistance | Stock            | 0mph               | 0mph         |
| Volkswagen| Touran 2017                   | Driver Assistance | Stock            | 0mph               | 0mph         |

<sup>1</sup>Requires an [OBD-II car harness](https://comma.ai/shop/products/comma-car-harness) and [community built ASCM harness](https://github.com/commaai/openpilot/wiki/GM#hardware). ***NOTE: disconnecting the ASCM disables Automatic Emergency Braking (AEB).*** <br />
<sup>2</sup>Only includes the MQB Passat sold outside of North America. The NMS Passat made in Chattanooga TN is not yet supported.

Community Maintained Cars and Features are not verified by comma to meet our [safety model](SAFETY.md). Be extra cautious using them. They are only available after enabling the toggle in `Settings->Developer->Enable Community Features`.

To promote a car from community maintained, it must meet a few requirements. We must own one from the brand, we must sell the harness for it, has full ISO26262 in both panda and openpilot, there must be a path forward for longitudinal control, it must have AEB still enabled, and it must support fingerprinting 2.0

Although they're not upstream, the community has openpilot running on other makes and models. See the 'Community Supported Models' section of each make [on our wiki](https://wiki.comma.ai/).

Installation Instructions
------

Install openpilot on an EON Gold or comma two by entering ``https://openpilot.comma.ai`` during the installer setup.

Follow these [video instructions](https://youtu.be/lcjqxCymins) to properly mount the device on the windshield. Note: openpilot features an automatic pose calibration routine and openpilot performance should not be affected by small pitch and yaw misalignments caused by imprecise device mounting.

Before placing the device on your windshield, check the state and local laws and ordinances where you drive. Some state laws prohibit or restrict the placement of objects on the windshield of a motor vehicle.

You will be able to engage openpilot after reviewing the onboarding screens and finishing the calibration procedure.

Limitations of openpilot ALC and LDW
------

openpilot ALC and openpilot LDW do not automatically drive the vehicle or reduce the amount of attention that must be paid to operate your vehicle. The driver must always keep control of the steering wheel and be ready to correct the openpilot ALC action at all times.

While changing lanes, openpilot is not capable of looking next to you or checking your blind spot. Only nudge the wheel to initiate a lane change after you have confirmed it's safe to do so.

Many factors can impact the performance of openpilot ALC and openpilot LDW, causing them to be unable to function as intended. These include, but are not limited to:

* Poor visibility (heavy rain, snow, fog, etc.) or weather conditions that may interfere with sensor operation.
* The road facing camera is obstructed, covered or damaged by mud, ice, snow, etc.
* Obstruction caused by applying excessive paint or adhesive products (such as wraps, stickers, rubber coating, etc.) onto the vehicle.
* The device is mounted incorrectly.
* When in sharp curves, like on-off ramps, intersections etc...; openpilot is designed to be limited in the amount of steering torque it can produce.
* In the presence of restricted lanes or construction zones.
* When driving on highly banked roads or in presence of strong cross-wind.
* Extremely hot or cold temperatures.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* Driving on hills, narrow, or winding roads.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. It is the driver's responsibility to be in control of the vehicle at all times.

Limitations of openpilot ACC and FCW
------

openpilot ACC and openpilot FCW are not systems that allow careless or inattentive driving. It is still necessary for the driver to pay close attention to the vehicle’s surroundings and to be ready to re-take control of the gas and the brake at all times.

Many factors can impact the performance of openpilot ACC and openpilot FCW, causing them to be unable to function as intended. These include, but are not limited to:

* Poor visibility (heavy rain, snow, fog, etc.) or weather conditions that may interfere with sensor operation.
* The road facing camera or radar are obstructed, covered, or damaged by mud, ice, snow, etc.
* Obstruction caused by applying excessive paint or adhesive products (such as wraps, stickers, rubber coating, etc.) onto the vehicle.
* The device is mounted incorrectly.
* Approaching a toll booth, a bridge or a large metal plate.
* When driving on roads with pedestrians, cyclists, etc...
* In presence of traffic signs or stop lights, which are not detected by openpilot at this time.
* When the posted speed limit is below the user selected set speed. openpilot does not detect speed limits at this time.
* In presence of vehicles in the same lane that are not moving.
* When abrupt braking maneuvers are required. openpilot is designed to be limited in the amount of deceleration and acceleration that it can produce.
* When surrounding vehicles perform close cut-ins from neighbor lanes.
* Driving on hills, narrow, or winding roads.
* Extremely hot or cold temperatures.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* Interference from other equipment that generates radar waves.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. It is the driver's responsibility to be in control of the vehicle at all times.

Limitations of openpilot DM
------

openpilot DM should not be considered an exact measurement of the alertness of the driver.

Many factors can impact the performance of openpilot DM, causing it to be unable to function as intended. These include, but are not limited to:

* Low light conditions, such as driving at night or in dark tunnels.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* The driver's face is partially or completely outside field of view of the driver facing camera.
* The driver facing camera is obstructed, covered, or damaged.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. A driver should not rely on openpilot DM to assess their level of attention.

User Data and comma Account
------

By default, openpilot uploads the driving data to our servers. You can also access your data by pairing with the comma connect app ([iOS](https://apps.apple.com/us/app/comma-connect/id1456551889), [Android](https://play.google.com/store/apps/details?id=ai.comma.connect&hl=en_US)). We use your data to train better models and improve openpilot for everyone.

openpilot is open source software: the user is free to disable data collection if they wish to do so.

openpilot logs the road facing camera, CAN, GPS, IMU, magnetometer, thermal sensors, crashes, and operating system logs.
The driver facing camera is only logged if you explicitly opt-in in settings. The microphone is not recorded.

By using openpilot, you agree to [our Privacy Policy](https://my.comma.ai/privacy). You understand that use of this software or its related services will generate certain types of user data, which may be logged and stored at the sole discretion of comma. By accepting this agreement, you grant an irrevocable, perpetual, worldwide right to comma for the use of this data.

Safety and Testing
----

* openpilot observes ISO26262 guidelines, see [SAFETY.md](SAFETY.md) for more details.
* openpilot has software in the loop [tests](.github/workflows/test.yaml) that run on every commit.
* The safety model code lives in panda and is written in C, see [code rigor](https://github.com/commaai/panda#code-rigor) for more details.
* panda has software in the loop [safety tests](https://github.com/commaai/panda/tree/master/tests/safety).
* Internally, we have a hardware in the loop Jenkins test suite that builds and unit tests the various processes.
* panda has additional hardware in the loop [tests](https://github.com/commaai/panda/blob/master/Jenkinsfile).
* We run the latest openpilot in a testing closet containing 10 comma devices continuously replaying routes.

Testing on PC
------
For simplified development and experimentation, openpilot can be run in the CARLA driving simulator, which allows you to develop openpilot without a car. The whole setup should only take a few minutes.

Steps:
1) Start the CARLA server on first terminal
```
bash -c "$(curl https://raw.githubusercontent.com/commaai/openpilot/master/tools/sim/start_carla.sh)"
```
2) Start openpilot on second terminal
```
bash -c "$(curl https://raw.githubusercontent.com/commaai/openpilot/master/tools/sim/start_openpilot_docker.sh)"
```
3) Press 1 to engage openpilot

See the full [README](tools/sim/README.md)

You should also take a look at the tools directory in master: lots of tools you can use to replay driving data, test, and develop openpilot from your PC.


Community and Contributing
------

openpilot is developed by [comma](https://comma.ai/) and by users like you. We welcome both pull requests and issues on [GitHub](http://github.com/commaai/openpilot). Bug fixes and new car ports are encouraged.

You can add support for your car by following guides we have written for [Brand](https://blog.comma.ai/how-to-write-a-car-port-for-openpilot/) and [Model](https://blog.comma.ai/openpilot-port-guide-for-toyota-models/) ports. Generally, a car with adaptive cruise control and lane keep assist is a good candidate. [Join our Discord](https://discord.comma.ai) to discuss car ports: most car makes have a dedicated channel.

Want to get paid to work on openpilot? [comma is hiring](https://comma.ai/jobs/).

And [follow us on Twitter](https://twitter.com/comma_ai).

Directory Structure
------
    .
    ├── cereal              # The messaging spec and libs used for all logs
    ├── common              # Library like functionality we've developed here
    ├── installer/updater   # Manages updates of NEOS
    ├── opendbc             # Files showing how to interpret data from cars
    ├── panda               # Code used to communicate on CAN
    ├── phonelibs           # External libraries
    ├── pyextra             # Extra python packages not shipped in NEOS
    └── selfdrive           # Code needed to drive the car
        ├── assets          # Fonts, images, and sounds for UI
        ├── athena          # Allows communication with the app
        ├── boardd          # Daemon to talk to the board
        ├── camerad         # Driver to capture images from the camera sensors
        ├── car             # Car specific code to read states and control actuators
        ├── common          # Shared C/C++ code for the daemons
        ├── controls        # Planning and controls
        ├── debug           # Tools to help you debug and do car ports
        ├── locationd       # Precise localization and vehicle parameter estimation
        ├── logcatd         # Android logcat as a service
        ├── loggerd         # Logger and uploader of car data
        ├── modeld          # Driving and monitoring model runners
        ├── proclogd        # Logs information from proc
        ├── sensord         # IMU interface code
        ├── test            # Unit tests, system tests, and a car simulator
        └── ui              # The UI

Licensing
------

openpilot is released under the MIT license. Some parts of the software are released under other licenses as specified.

Any user of this software shall indemnify and hold harmless comma.ai, Inc. and its directors, officers, employees, agents, stockholders, affiliates, subcontractors and customers from and against all allegations, claims, actions, suits, demands, damages, liabilities, obligations, losses, settlements, judgments, costs and expenses (including without limitation attorneys’ fees and costs) which arise out of, relate to or result from any use of this software by user.

**THIS IS ALPHA QUALITY SOFTWARE FOR RESEARCH PURPOSES ONLY. THIS IS NOT A PRODUCT.
YOU ARE RESPONSIBLE FOR COMPLYING WITH LOCAL LAWS AND REGULATIONS.
NO WARRANTY EXPRESSED OR IMPLIED.**

---

<img src="https://d1qb2nb5cznatu.cloudfront.net/startups/i/1061157-bc7e9bf3b246ece7322e6ffe653f6af8-medium_jpg.jpg?buster=1458363130" width="75"></img> <img src="https://cdn-images-1.medium.com/max/1600/1*C87EjxGeMPrkTuVRVWVg4w.png" width="225"></img>

[![openpilot tests](https://github.com/commaai/openpilot/workflows/openpilot%20tests/badge.svg?event=push)](https://github.com/commaai/openpilot/actions)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/alerts/)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/context:python)
[![Language grade: C/C++](https://img.shields.io/lgtm/grade/cpp/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/context:cpp)
[![codecov](https://codecov.io/gh/commaai/openpilot/branch/master/graph/badge.svg)](https://codecov.io/gh/commaai/openpilot)
