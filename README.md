<h2>docker 배포</h2>

1. spring boot.jar를 gcp에 배포 완료
2. spring boot 프로젝트 docker 파일 이미지로 변경
3. docker hub에 repository push 완료
4. gcp 인스턴스에 docker image 다운로드후 배포
<img width="968" alt="스크린샷 2022-02-07 오후 10 28 44" src="https://user-images.githubusercontent.com/66988341/152798690-0cc70cf0-c700-417c-80c8-f6d975f37b22.png">

<h2> docker image 만들기 </h2>
1. 해당프로젝트에 docker.file 생성<br><br>
2. FROM openjdk:8-jdk-alpine<br>
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
복사해서 입력<br><br>

3.docker.filer을 build시켜 docker image 생성<br>
터미널에 명령어 입력<br>
Maven : docker build -t springio/gs-spring-boot-docker .
Gradle : docker build --build-arg DEPENDENCY=build/dependency -t springio/gs-spring-boot-docker . <br>
cf) springio/gs-spring-boot-docker =>> docker hub의 개인저장소 이름<br><br>
4.docker hub에 push<br>
docker push seung5457/spring-boot-cpu-bound<br>

5. gcp에서 docker-img pull<br>
docker pull seung5457/spring-boot-cpu-bound<br><br>
 
6. gcp에서 docker run<br>
docker run -p {HOST_port}:{containter_port} 사용자이름/저장소이름<br><br>




<a href="https://spring.io/guides/gs/spring-boot-docker/">스프링 공식문서</a>
