docker build -f dockertraining_aorozco\Dockerfile --force-rm -t dockertraining_aorozco .

 

docker run --name Site1 -p 8085:80 dockertraining_aorozco

 

docker run --name Site2 -p 8086:80 -e "AppSettings:storename"="Container Dynamic Name" dockertraining_aorozco