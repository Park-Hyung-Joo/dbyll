---
layout: post
title: jekyll install and serve
categories: [web]
tags: [jekyll, ruby, memo]
description: how to install jekyll and serve
---

**jekyll**을 설치해서 블로그 템플릿을 가져다 쓰기로 했다. **html**, **css**를 몰라서 템플릿과 마크다운 파일로 날먹하려고 했지만 안타깝게도 템플릿을 가져다 쓰는 데도 지식이 필요했다. 여기에 그동안 찍먹한 반쪽짜리 지식 중 **jekyll**을 설치하고 실행한 방법과 시행착오를 정리한다.


### ruby 설치

ruby를 설치한다. 이 글을 쓰는 시점 기준으로 3.x기준이 최신 버전이지만 2.7버전으로 설치하는 것이 좋다. 이쪽으로 문외안이라 왜인지는 모르지만 3.x버전으로 넘어오면서 지원을 중단한 **gem**이 있다고 한다. **msys2**를 설치하라는 메세지가 나오면 하라는 대로 한다.


### jekyll, bundler 설치

**jekyll**, **bundler**는 ruby의 **gem**파일이다. jekyll은 파이썬처럼 주어진 html텍스트로 사이트를 로컬에 생성해주는 생성기다. bundler는 gem파일 설치 및 버전관리 gem이다. 이게 왜 필요하냐면 jekyll만 가지고는 템플릿에 있는 소스코드를 모두 읽지 못하고 라이브러리 처럼 plug-in gem파일이 추가로 필요한데, 이 추가 gem파일을 한번에 설치하고 관리해주는 gem이 bundler다. bundler는 jekyll소스코드 폴더에 있는 Gemfile, Gemfile.lock에 나온 정보를 토대로 gem파일을 설치한다.

설치 명령어는 다음과 같다.
{% highlight ruby %}
gem install jekyll bundler
{% endhighlight %}
bundler를 이용해 추가 플러그인 gem은 다음 명령어로 설치한다.
{% highlight ruby %}
bundle install
{% endhighlight %}
이렇게만 치면 bundler가 알아서 설치해준다.


### jekyll 실행

configration 파일이 필요하다. _config.yml 파일이 있으면 된다. git clone 해온 템플릿을 쓴다면 조심해야 하는 게 _config.yml은 .gitignore에 포함되어 있어서 포함이 안됐을 수도 있다. 없다면 깃허브 레포지토리에서 수동으로 따로 가져와서 쓰자. config파일이 준비되면 터미널에 다음 명령어를 입력한다.
{% highlight ruby %}
bundle exec jekyll serve
{% endhighlight %}