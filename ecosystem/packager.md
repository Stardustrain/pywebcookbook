패키지 관리자
-------------

개발을 하다 보면 외부 라이브러리를 이것저것 설치하게 됩니다. 그럴 때 직접 사이트를 찾아서 압축 파일을 풀고 설치 스크립트를 실행하려면 많이 번거롭습니다. 또, 내가 어떤 라이브러리를 설치했고 지금 프로젝트에서 어떤 버전을 사용하고 있는지 기억하기도 힘듭니다. 패키지 관리자를 사용하면 개발 환경을 쉽게 관리할 수 있습니다.

현재 몇가지 파이썬 패키징 도구가 공존하고 있어 혼란스러운 상황입니다. 그렇지만 이 문서에서는 비교적 사용하기 간단한 pip를 위주로 설명합니다.

### pip

pip는 PyPI(Python Package Index)에서 패키지를 내려받아 설치해주고 관리해주는 툴입니다. PyPI에 등록된 패키지 이름만 알면, 패키지 관리자가 알아서 정보를 가져와서 패키지를 설치해줍니다. [PyPI 사이트](http://pypi.python.org/)에서 패키지를 검색할 수 있습니다.

pip 를 설치하려면 다음과 같은 방법을 사용하면 됩니다. 

#### pip 설치 방법

소스로 설치하는법은 다음과 같습니다. 대부분의 환경에서 지원이 됩니다.

	wget http://pypi.python.org/packages/source/p/pip/pip-1.2.tar.gz 
	tar xzf pip-1.2.tar.gz 
	cd pip-1.2
	python setup.py install

easy_install 로 설치하는 방법은 다음과 같습니다.

	easy_install pip
	
각 배포판의 패키지로 설치하는 방법

	ubuntu $ apt-get install python-pip	
	centos $ yum install python-setuptools ; easy_install pip

TODO: pip 설치방법 ( 윈도우즈용 : http://stackoverflow.com/a/4921215/1712380 )

### 패키지 설치, 업그레이드, 삭제

패키지를 설치하려면 명령 프롬프트(또는 터미널)에서 다음 명령을 실행합니다. 여기서는 simplejson 패키지를 설치해봅시다. (유닉스 계열 운영체제에서는 루트 권한이 필요합니다.)

	pip install simplejson
	
그러면 PyPI에서 패키지를 찾아서 설치해줍니다. 만약 설치하려는 패키지가 다른 패키지를 필요로 한다면 그 패키지도 함께 설치됩니다.

이미 설치된 패키지를 최신 버전으로 업그레이드하려면 `-U` 옵션을 줘서 실행합니다.

	pip install -U simplejson
	
더이상 필요 없어진 패키지를 지우려면 `pip uninstall` 명령을 사용합니다.

	pip uninstall simplejson
	
### Requirements 파일

파일에서 패키지 목록을 읽어서 한번에 설치하는 것이 가능합니다. 프로젝트마다 패키지 목록 파일을 하나씩 관리하면 개발 환경을 편하게 구축할 수 있습니다.

패키지 목록 파일의 형식은 아주 간단합니다. 패키지 이름을 한줄에 하나씩 적으면 됩니다.

	simplejson

또는 특정 버전을 지정할 수도 있습니다.

	simplejson==2.6.2

`pip install -r` 명령으로 패키지 목록에서 바로 설치할 수 있습니다.

	pip install -r /path/to/requirements.txt

`pip freeze` 명령을 사용하면 현재 설치된 패키지 목록이 출력됩니다. 이 목록을 파일에 바로 저장하여 사용할 수도 있습니다.

	pip freeze > requirements.txt
	
### 다른 설치 방법

#### easy_install

pip와 달리 easy_install은 바이너리 패키지 설치를 지원합니다. 따라서 컴파일러를 설치하기 힘든 환경(윈도 등)에서 C 확장이 포함된 패키지를 설치할 때 유용합니다.

예를 들어 simplejson 패키지를 설치하려면 다음처럼 합니다.

	easy_install simplejson

#### OS에서 제공하는 패키지 관리자

리눅스 배포판들은 직접 파이썬 패키지를 제공하고 있습니다. `apt-get`이나 `yum` 같은 명령을 사용하여 설치합니다. 안정적이지만 버전이 너무 낮아서 쓰기 곤란한 경우가 많습니다.

### 조언

* 프로젝트마다 패키지 목록을 파일로 만들어두세요. 버전은 명시하는 것이 좋습니다.
* 한가지 패키지 관리자를 정해서 그것만 사용하세요. 여러가지를 사용하다보면 꼬일 수 있습니다.
* 패키지 설치가 실패하는 경우, 파이썬 밖의 라이브러리가 필요한 경우가 많습니다. 그럴 때는 먼저 라이브러리를 설치해야 합니다.
