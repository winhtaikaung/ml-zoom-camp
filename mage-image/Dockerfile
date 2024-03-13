FROM mageai/mageai:latest

RUN wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt-get update
RUN apt-get install -y google-chrome-stable
RUN pip uninstall PIL pillow -y
RUN apt-get install libjpeg-dev
RUN apt-get install libfreetype6-dev
RUN apt-get install zlib1g-dev
RUN apt-get install libpng-dev
RUN pip install pillow minio selenium selenium-stealth --upgrade

