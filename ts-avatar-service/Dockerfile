FROM python:3.8-slim

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

RUN apt update -y && apt install -y \
    cmake \
    build-essential \
    libgl1-mesa-glx \
    libgtk-3-dev

ENV PYTHONUNBUFFERED=TRUE

RUN mkdir -p /app
ADD . /app/
WORKDIR /app

RUN pip install --upgrade pip setuptools==65.5.0 wheel

RUN pip install -r requirements.txt

CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:17001", "app:app"]

EXPOSE 17001

