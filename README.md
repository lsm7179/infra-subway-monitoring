<p align="center">
    <img width="200px;" src="https://raw.githubusercontent.com/woowacourse/atdd-subway-admin-frontend/master/images/main_logo.png"/>
</p>
<p align="center">
  <img alt="npm" src="https://img.shields.io/badge/npm-%3E%3D%205.5.0-blue">
  <img alt="node" src="https://img.shields.io/badge/node-%3E%3D%209.3.0-blue">
  <a href="https://edu.nextstep.camp/c/R89PYi5H" alt="nextstep atdd">
    <img alt="Website" src="https://img.shields.io/website?url=https%3A%2F%2Fedu.nextstep.camp%2Fc%2FR89PYi5H">
  </a>
  <img alt="GitHub" src="https://img.shields.io/github/license/next-step/atdd-subway-service">
</p>

<br>

# 인프라공방 샘플 서비스 - 지하철 노선도

<br>

## 🚀 Getting Started

### Install
#### npm 설치
```
cd frontend
npm install
```
> `frontend` 디렉토리에서 수행해야 합니다.

### Usage
#### webpack server 구동
```
npm run dev
```
#### application 구동
```
./gradlew clean build
```
<br>

## 미션

* 미션 진행 후에 아래 질문의 답을 작성하여 PR을 보내주세요.

### 1단계 - 인프라 운영하기
1. 각 서버내 로깅 경로를 알려주세요

* [인프라정보는 여기 있습니다~](https://github.com/lsm7179/infra-subway-deploy/tree/lsm7179#%EB%AF%B8%EC%85%98)
* logPath  /home/ubuntu/infra-subway-monitoring/log/file.log
* nginx -> 요구사항 변경으로 alb로 수정되었습니다. 
2. Cloudwatch 대시보드 URL을 알려주세요
* https://ap-northeast-2.console.aws.amazon.com/cloudwatch/home?region=ap-northeast-2#dashboards:name=lsm7179-dashboard
---
* [x] 애플리케이션 진단하기 실습을 진행해보고 문제가 되는 코드를 수정
* [x] 로그 설정하기
  * 운영은 파일로 관리, 로컬은 콘솔로 관리, aop를 활용
* [ ] Cloudwatch로 모니터링
* [x] 로드밸런서 사용 : http://lsm7179-alb-1556721989.ap-northeast-2.elb.amazonaws.com/
* 참고자료 
  * aop: https://jeffrey-oh.tistory.com/332
  * aop: https://memostack.tistory.com/238
  * springActvie: https://blog.leocat.kr/notes/2018/09/18/spring-logback-config-with-spring-multi-active-profile
  * log: https://gaemi606.tistory.com/entry/Spring-Boot-AOP%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%B4-%EB%A1%9C%EA%B7%B8-%EC%B6%9C%EB%A0%A5%ED%95%98%EA%B8%B0-REST-API
---
#### 피드백 정리
1. https 접속은 안되고 http 접속만 가능한 상태로 보이네요!
~~~
    https 사용할수 있게 변경했습니다.~!
    다만 aws 도메인 연결(?)권한이 없어서 보안경고가 뜨네요. ㅎㅎ
~~~
2. 컨트롤러 이외에도 서비스 및 도메인 로직 등에서도 상황에 따라 적절한 로그를 심어주는게 좋지 않을까요?
~~~
    LogServiceAspect 클래스를 만들고 aop 설정을 하여 로그를 설정했습니다. ~
~~~
3. 로그를 파일은 주로 ELK 스택을 통해 관리하는데요, 이를 위해 json appender도 추가되면 좋지 않을까요?
~~~
json appender도 추가하였습니다~! 
~~~
4. 하나의 로그로 쌓는 것이 좋지 않을까요? 멀티스레드 환경이라면 로그가 뒤섞이면서 알아보기 힘들 것 같습니다.
~~~
넵 하나의 로그로 쌓도록 변경했습니다~ 감사합니다
~~~

### 2단계 - 성능 테스트
1. 웹 성능예산은 어느정도가 적당하다고 생각하시나요

2. 웹 성능예산을 바탕으로 현재 지하철 노선도 서비스는 어떤 부분을 개선하면 좋을까요

3. 부하테스트 전제조건은 어느정도로 설정하셨나요

4. Smoke, Load, Stress 테스트 스크립트와 결과를 공유해주세요
