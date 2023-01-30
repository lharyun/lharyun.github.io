---
layout: single
title: "BootStrap정리(Bootcamp)"
categories: Javascript
tag: [Javascript]
toc: true
author_profile: false
---





부트스트랩:  무언가를 만들기 쉽게 도와주는 틀
ex)만약 까마귀모형을 제작할려면 까마귀 틀을 만들어주면 쉬워진다.



방법 bootStrap의 코드를 import하고 html의 원하는 요소의 클래스에 bootStrap에나와있는

코드를 적으면 된다.



뱃지,컬러,배경컬러,버튼,

스크립트가 포함되지않은 문서에서는
경고창을 만들수는 있어도 닫을 수 없다.
또한 경고창에서는 role="alert"추가해 줘야한다.
경고창은 페이지를 만들면서 실행되는것이아닌 어떠한 행위를
했을경우 실행되는 것이기 때문이다.

#Grid
grid시스템을 사용하려면 항상 container안에 있어야 사용 가능!
class는 row로 해야하고
col은 12유닛씩 가지고 있다.(=12유닛이 한줄!)
class="col-5" 로 지정하면 나머지를 지정하지 않았을때 나머지가 알아서
autosize로 지정됨 ex) col-6지정하고 div 3개하면 나머지 2사이즈로 만들어짐
col-m-* 중단 크기 이상부터의 형태
col-xl-*최대크기에서의 형태 설정
ex) div class="col-m-6 col-xl-3 bg-success" 중단크기까지는 사이즈가 6이고
최대크기에서의 사이즈는3이다. 

사이즈는 xs,s,m,l,xl순이다.
박스 움직이기(flexbox)
박스 위아래정렬하기=align-self-*(start,center,end)	
박스 좌우로 정렬하기 = justify-content-*(start,between,end,around,center)

윈도우크기에 맞춰 크기조정 -fluid