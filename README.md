#ADD setting.xml ( add mirror VTS)
- cp file setting.xml trong serives app vào usr/m2
cài dặt thêm proxy nếu có


 
 

#Build command:
-Module App: mvn -pl VcrmGeneral,VcrmApp install
-Module Sys: mvn -pl VcrmGeneral,VcrmSys install

#Build image command: 
docker-compose build

#Run image command:
docker stop ${image_name} || true
docker run --name ${image_name} -d --volume ${directory-host}:/app/CRMDocument --network host --env spring_profiles_active=product ${image_name}:latest

#add lib local
mvn install:install-file -Dfile=./lib/FTUDynamicReport-1.9.jar -DgroupId=com.fis.ftu  -DartifactId=ftu-dynamic-report   -Dversion=1.0  -Dpackaging=jar  -DgeneratePom=true
mvn install:install-file -Dfile=./lib/betall_sdk-1.2.0.2.jar -DgroupId=com.betall  -DartifactId=betall_sdk   -Dversion=1.2.0.2  -Dpackaging=jar  -DgeneratePom=true
mvn install:install-file -Dfile=./lib/BulkWS.jar -DgroupId=bulk-ws  -DartifactId=bulk-ws   -Dversion=1.9  -Dpackaging=jar  -DgeneratePom=true
mvn install:install-file -Dfile=./lib/GNOC.jar -DgroupId=GNOC  -DartifactId=GNOC   -Dversion=1.0  -Dpackaging=jar  -DgeneratePom=true

