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
