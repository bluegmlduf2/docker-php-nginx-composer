# 도커허브로부터 이미지 취득
FROM php:8.1.18-fpm
# 로컬의 php.ini파일을 컨테이너 내부의 /usr/local/etc/php/에 저장
COPY php.ini /usr/local/etc/php/

# 패키지와 php확장프로그램을 설치
RUN apt-get update && apt-get install -y \
	git \
	curl \
	zip \
	unzip
    # && docker-php-ext-install pdo_mysql 
    # docker-php-ext-install는 도커에서 php확장을 설치하기위한 커맨드이다. pdo_mysql이라는 확장을 설치할건데 이번엔 php와 mysql을 연동하지 않을것이기때문에 사용하지 않는다 

# php컴포저 설치
COPY --from=composer /usr/bin/composer /usr/bin/composer

# 작업디렉토리를 /var/www로 설정
WORKDIR /var/www

# php컴포저로 필요 라이브러리 설치
RUN composer require google/apiclient:~2.0
