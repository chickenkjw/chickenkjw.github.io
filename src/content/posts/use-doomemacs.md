---
title: Emacs에도 봄은 오는가 
published: 2024-09-15
description: '새 유니티 스크립트 에디터로 emacs를 도입해보려고 한 이야기입니다'
image: ''
tags: [emacs]
category: '이맥스'
draft: false
language: 'ko'
---

## 그래! Emacs를 써보자!
6월 말, 홀린듯이 튜링의 사과에서 여는 커뮤니티 강의를 신청했다. 강의에 관한 내용은 아래 링크에서 확인할 수 있다.

[『튜링의 사과』 커뮤니티 강의 - '모든 길은 Emacs로 통한다' (velog)](https://velog.io/@turingapple/%E3%80%8E%ED%8A%9C%EB%A7%81%EC%9D%98-%EC%82%AC%EA%B3%BC%E3%80%8F-%EC%BB%A4%EB%AE%A4%EB%8B%88%ED%8B%B0-%EA%B0%95%EC%9D%98-%EB%AA%A8%EB%93%A0-%EA%B8%B8%EC%9D%80-Emacs%EB%A1%9C-%ED%86%B5%ED%95%9C%EB%8B%A4)

당시 에디터로 Visual Studio를 사용하고 있었지만, 노트북에서 유니티와 함께 사용하기엔 조금 무거웠던 점, 그리고 VSC는 당시 유니티와의 연결이 잘 안 되었던지라 (지금은 통합이 되어서 잘 되는 것 같다) 새 에디터를 써보고 싶었다.

*본심은, 사실 힙해보였다* (그냥 홍대병 걸린 힙찔이)

## 시작은 바닐라로

처음으로 내 노트북에 이맥스(바닐라)를 설치했다. 내 마음대로 환경을 구축할 수 있다는 게 너무나도 매력적으로 다가왔다. 

:::note
사용 운영체제: Windows 11  
설치 Emacs 버전: 29.3
유니티 에디터 버전: 2022.3
:::

마우스를 쓰지 않는다는 개념이 가장 어려웠던 것 같다. 이맥스는 마우스를 쓸 수 있지만, 마우스에 손을 대지 않는 것이 옳은 길인 것 같아 evil 모드를 설치하고 hjkl 이동에 익숙해지기를 기다렸다.  
여담으로, 지금은 어느정도 hjkl 이동에 익숙한 듯하다.

하지만 이맥스를 사용하기에는 내게 문제가 있었다. 

1. 키를 잘못 눌렀을 때 내가 뭔 잘못을 했는지도 모르겠고 그냥 `:q`(종료)를 누르게 된다. 그러면 리셋돼서 돌아온다 (...) 이는 지금도 해당하는 것 같다. 단축키가 머릿속에 들어오지를 않는다. 

2. 비주얼 스튜디오보다 느렸다. 실행 자체는 빠릿빠릿하고 메모리도 비약적으로 적게 먹는다. 그렇지만 magit, projectile, evil 등등 패키지를 15개 정도만 설치해도 시작 시 비주얼 스튜디오의 홈? 화면보다 늦게 뜬다. (이맥스가 윈도우에서는 느리다고..)  
이는 데몬으로 해결할 수 있었는데, cmd창이 계속 켜져 있어야만 하는 게 눈에 너무 거슬렸다. 

이 외에도 자잘한 문제들이 여럿 있다보니 사용을 거의 포기하다시피 했던 것 같다. 계속 써야 익숙해지지만 말이다. 아직도 이맥스에는 손이 잘 안 간다. 개발할 때면 그냥 비주얼 스튜디오나 비주얼 스튜디오 코드가 더 편해다..

WSL도 고려했으나, 이맥스 하나 쓰자고 설치하기에는 굳이 싶어서 제외했다. 나중에 이맥스 외에도 더 쓸 거 같으면 WSL은 그때나 사용해볼 것 같다.

## 둠으로 옮기기

lsp 세팅에 너무 많은 애로를 겪었다. [eglot](https://github.com/joaotavora/eglot)이니 [treemacs](https://github.com/Alexander-Miller/treemacs)니 뭐니 이것저것 시도해봐도 잘 안 돌아간다..?

그리고 처음부터 '내 마음대로' 만든다는 것이 벅차기도 했던 것 같다. 황무지에서 땅을 개간하는 개척자가 되어버려..

결국 바닐라로 처음부터 박치기하기 보다는 편의성이 제공되는 커뮤니티판인 '[DoomEmacs](https://github.com/doomemacs/doomemacs)'로 시작해보기로 결정했다. 

:::note
사용 운영체제: Windows 11  
설치 Emacs 버전: 29.4
:::  

설치가 조금 복잡하긴 했지만,  
둠이맥스의 첫 경험은 너무나도 편리했다는 것이다. 사용하는 데 있어 필요한 상당수의 패키지는 설정 파일에서 주석을 해제하는 것만으로도 사용할 수 있다. 솔직히 여기서 제공해주는 것 외의 패키지를 내가 쓸 일이 있을까 싶다. 게다가 emacs-lisp를 작성할 일도 거의 없다. 

Doom emacs는 바닐라-윈도우보다 훨씬 빨랐다. 설치 과정이 조금 복잡하긴 해도 윈도우에서 이맥스는 좀 심각하게 느렸다. 패키지를 10개 가량 추가하고 나니까 VS Code가 더 빨리 실행된다. 에..

바닐라에 10개 가량 패키지를 설치하니 5~6초 뒤에 켜진다.  
Doom은 이보다 더 패키지를 추가해도 1.4초 가량 걸린다. 그냥 쓰는 것 보다야는 좋은 것 같다. 

## 그럼, 유니티에 적용해봅시다

이맥스 사용의 최종 목표? 인 유니티와 함께 사용할 수 있는가였다. 

문제는...

![유니티 지원 IDE](https://blogimage001.blob.core.windows.net/pictures/unity-support-ide.webp)

유니티가 이맥스를 인식하지 못 한다. 

하지만 이에 굴하지 않고 이맥스를 유니티와 써보고 싶었던 사람들도 있었다.
아래는 어떤 분께서 그 노력을 공유해주신 글이다.  
-> [Using Unity Editor with Emacs (eliza.sh)](https://eliza.sh/2021-06-01-using-unity-editor-with-emacs.html)

따라하기 위해 Cargo에 올라가 있는 rider2emacs 패키지랑 이맥스 내 설정(언어 설정에서 unity 추가)을 변경한다. 아래 사진과 같이 유니티 에디터에서 `Browse...`로  위치를 찍으면 `Rider (custom location)`이라 뜨면서 이맥스를 인식한다. (이제 누르면 Rider가 아니라 이맥스가 실행된다!)  
이맥스를 Rider라고 유니티를 속이는 원리라고. windows에서는 이맥스의 daemon을 먼저 활성화 한 후에 유니티 에디터에서 스크립트를 열어야 한다. 그렇지 않으면 이맥스에서 경고를 띄운다. 
 
![Rider Custom Location](https://blogimage001.blob.core.windows.net/pictures/unity-rider-custom-location.webp)
(이거 써보려고 러스트도 안 하는데 cargo 설치하기)

cargo 말고도 랭귀지 서버로 omnisharp를 설치했다.

(추신) **Unity의 비주얼 스튜디오와 VS Code의 통합** 이후 유니티랑 VS Code 사용하려고 고통받던 일이 없어졌다. 아무래도 이맥스를 쓸 일이 없어질 것 같다.

## 목표는 달성! 그러나..

유니티에서 이맥스를 실행시키는 것까지 해봤지만,  
아마 안 쓸 듯?? 하다.

에디터가 가벼운 것은 매우 좋다.  
내 노트북에서의 실행 기준으로 각 스크립트 에디터의 메모리 사용량은 아래와 같다.
- Visual Studio (1.7 ~ 2.8GB)
- Visual Studio Code (600 ~ 900MB)
- **Emacs (300MB)**

유니티 사용할 때의 팬 돌아가는 소리가 작아지긴 했다. 확실히 팬이 덜 돈다. 노트북이 빠릿빠릿해지니 매우 좋은 현상이다.

그렇지만 여기까지 오니까 그냥 비주얼 스튜디오가 편하게 느껴진다. 배우면서까지 사용해야 할 필요를 별로 느끼지를 못하겠다. 이미 VS Code랑 Visual Studio를 잘만 사용하고 있고,, 사용에 문제가 크지 않다. 굳이 이맥스를? 

유니티와 사용하려면 결국 데몬을 써야한다. (다른 방법이 있을지도 모르지만 아직은 이 방법밖에 모르겠다) 위에서 언급했듯이 꽤 거슬린다. 실수로 cmd 창을 닫아버리면 그대로 꺼진다.    
심지어 아직 내게는 이맥스의 창 분리/이동도 익숙치 않고, 킬러 어플리케이션이라는 magit은 써보지도 못했고.. project도 어떻게 쓰는지 아직도 잘 모르겠다...

그냥 내게 쓰기에는 너무 많은 기능을 담고 있는 게 아닐지도 모르겠다. 

잘 쓰면 강력한 도구가 될 것 같지만, 아직까지 필요성이라던지를 잘 모르겠다. '개발 공부하기도 바쁜데, 에디터 공부를?' 같은 느낌이다. 계속 써보면 익숙해지지 않을까 싶지만서도, 어쩌면 마우스에 너무 익숙하다보니 보내지를 못하는 게 아닐까? 

아직 삭제는 안 했으니, 언젠가 생각나면 다시 사용을 시도하지 않을까.. 싶다.

마지막으로 현재 둠이맥스의 대시보드 화면
![DoomDashBoard](https://blogimage001.blob.core.windows.net/pictures/doomemacs-dashboard.webp)

&nbsp;
## 이맥스 공부에 도움이 되었던 자료들

영어가 보기 싫어서.. 한글로 된 자료를 많이 찾아다녔다. 물론 영어로 된 자료가 양이나 질적으로도 우수하다고 생각하지만, 내가 영어를 못한다.  
그치만 공부해야죠,, 영어..

아래에 링크를 몇 남겨놓는다. 

- 강연자 분의 발표자료  
https://talks.rangho.me/emacs-road/
- GNU Emacs Configuration for Korean  
https://github.com/clockoon/my-emacs-setting/blob/master/config.org
-  이맥스와 함께하는 개발환경  
https://meetup.nhncloud.com/posts/133
- (emacsian ohyecloudy)  
http://ohyecloudy.com/emacsian/