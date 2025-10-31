#  BackEnd

## 환경 설정

1️⃣ 가상환경 생성 및 활성화

~~~python
# 프로젝트 폴더로 이동
cd BACKEND
# 가상환경 생성
python3 -m venv .venv
# 가상환경 활성화 (Mac / Linux)
source .venv/bin/activate
# 비활성화
deactivate
~~~


2️⃣ 필수 패키지 설치

~~~python
pip install upgrade pip
pip install django python-dotenv
pip freeze > requirements.txt
~~~


3️⃣ Django 초기 세팅

~~~python
# 마이그레이션
python manage.py migrate
# 개발 서버 실행
python manage.py runserver
# 서버가 정상 실행되면 http://127.0.0.1:8000 에서 확인할 수 있습니다.
~~~

4️⃣ 환경 변수 설정 (.env)

프로젝트 루트(BACKEND/)에 .env 파일 생성:
~~~bash
DJANGO_SECRET_KEY=your_secret_key_here
DJANGO_DEBUG=True
config/settings.py 상단에 다음 코드 추가:

from dotenv import load_dotenv
import os, pathlib
load_dotenv(dotenv_path=pathlib.Path(__file__).resolve().parent.parent / '.env')

SECRET_KEY = os.getenv('DJANGO_SECRET_KEY', 'fallback-secret')
DEBUG = os.getenv('DJANGO_DEBUG', 'False') == 'True'
~~~

