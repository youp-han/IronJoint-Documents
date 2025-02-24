jenkins 서비스 설치 - FBOW
서버: 10.253.98.127
젠킨스 구성 이동을 위한 새로운 jenkins 서비스 설치


1. DEV_EOMS_APP
2. DEV_EOMS_CORE
3. DEV_EOMS_WEB
4. QAS_EOMS_APP_NEW
5. QAS_EOMS_CORE
6. QAS_EOMS_WEB_NEW
7. PRD_EOMS_AP
8. PRD_EOMS_APP_NEW
9. PRD_EOMS_CORE
10. PRD_EOMS_WEB
11. PRD_EOMS_WEB_NEW
12. PRD_EOMS_WEB_TEST

Core build -> web -> DEV_EOMS_APP

CORE 구성 
- PRD 에서 패키징이 끝나면, 버전을 업그레이드 하여 pom.xml 에 넣고, 해당 pom.xml 을 svn 으로 업데이트 한다.
- QAS 와 dev 는 prd 에서 업데이트가 된 버전의 번호로 빌드/패키징을 한다. 업데이트는 안됨.



1. DEV_EOMS_CORE
mvn clean package -Dmaven.test.skip=true -Dspring.profiles.active=dev -Pdev


1. QAS_EOMS_CORE
mvn clean package -Dmaven.test.skip=true -Dspring.profiles.active=qas -Pqas


1. PRD_EOMS_CORE

inject => SVN_PWD

- mvn clean build-helper:parse-version versions:set -DnewVersion=${parsedVersion.majorVersion}.${parsedVersion.minorVersion}.${parsedVersion.incrementalVersion} 

oms-core 1.2.194-SNAPSHOT
build-helper:parse-version 
- build-helper-maven-plugin의 parse-version 목표를 사용하여 pom.xml에 
    정의된 현재 프로젝트 버전을 majorVersion 1, minorVersion 2, incrementalVersion 194 분리


versions:set -DnewVersion=${parsedVersion.majorVersion}.${parsedVersion.minorVersion}.${parsedVersion.incrementalVersion} 
-version:set
 - Maven 프로젝트의 버전을 변경합니다 이 작업은 pom.xml 파일의 <version> 태그를 업데이트합니다.
-DnewVersion 옵션:새 버전을 동적으로 설정합니다.
- ${parsedVersion.majorVersion}.${parsedVersion.minorVersion}.${parsedVersion.incrementalVersion}로 설정하면, 
   현재 버전의 majorVersion, minorVersion, incrementalVersion 조합으로 새 버전을 구성합니다.



- mvn clean package -Dmaven.test.skip=true
위에 가지고 온 버전으로 패키징 한다. 1.2.194-SNAPSHOT

#sh script
# get current datetime
DATE=`TZ=":Asia/Seoul" date +%Y%m%d%H%M`
POM_VERSION=`/usr/local/apache-maven-3.6.3/bin/mvn -o org.apache.maven.plugins:maven-help-plugin:2.1.1:evaluate -Dexpression=project.version | grep -v '\['`

# release build artifact to nexus
curl -v -F r=releases -F hasPom=true -F e=jar -F file=@pom.xml -F file=@target/oms-core-${POM_VERSION}.jar -u admin:'itWise1!a' http://10.123.184.235/nexus/service/local/artifact/maven/content

# svn upgrade cause SVN server version is too old
svn upgrade

# svn commit for release version
#svn commit pom.xml --username formularadmin --password gksksladml01234ehdntla98 -m "commit before ${POM_VERSION} release"
svn commit pom.xml --username formularadmin --password $SVN_PWD -m "commit before ${POM_VERSION} release"

# release tagging
svn copy --username formularadmin --password $SVN_PWD \
		http://svn.elandsystems.com/EOMS_Project/trunk/oms-core@$REV \
        http://svn.elandsystems.com/EOMS_Project/tags/oms-core-$DATE -m "${POM_VERSION} release"



#mvn cmd
mvn clean build-helper:parse-version versions:set -DnewVersion=${parsedVersion.majorVersion}.${parsedVersion.minorVersion}.${parsedVersion.nextIncrementalVersion}-SNAPSHOT
   - 1.2.195-SNAPSHOT


# svn commit for release version
svn commit pom.xml --username formularadmin --password $SVN_PWD -m "commit after release"

if [ -f "$WORKSPACE/pom.xml.versionsBackup" ]; then
	rm "$WORKSPACE/pom.xml.versionsBackup"
fi





