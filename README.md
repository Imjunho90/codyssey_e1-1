내 컴퓨터에 개발자용 '작업실' 꾸미기



# 터미널 조작 로그 기록

## 현재 위치 확인, 목록 확인(숨김 파일 포함)
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % pwd
/Users/junhojeon/codyssey/codyssey-1-1
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -la
total 0
drwxr-xr-x  2 junhojeon  staff   64  8  1 16:50 .
drwxr-xr-x  6 junhojeon  staff  192  8  1 16:50 ..
~~~

## 이동, 생성, 복사
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % mkdir codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % touch test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % cp ~/codyssey/codyssey-1-1/test.txt ~/codyssey/codyssey-1-1/codyssey
~~~

## 이동/이름변경, 삭제
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % cd codyssey-1-1
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % mv test.txt codyssey/test_1.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % ls
test.txt	test_1.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % rm test.txt test_1.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % ls
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % 
~~~
