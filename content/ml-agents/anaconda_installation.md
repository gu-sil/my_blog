---
emoji: ๐ช
title: Anaconda ์ค์น์ ํ๊ฒฝ ์กฐ์ฑ
date: '2020-05-03 16:52:00'
author: jonghyun
tags: ml-agents
categories: ml-agents
---
์ค์น ํ์ ์๋์ฐ ๊ฐ์ ๊ฒฝ์ฐ Anaconda Prompt๊ฐ ๋ฐ๋ก ์์ฑ๋์ง๋ง
MacOS์์๋ Terminal์ ํตํฉ๋๋ค.

**์์ ๊ณต๊ฐ ์์ฑ**\
conda create -n [์์๊ณต๊ฐ์ด๋ฆ] python=[๋ฒ์ ]

**์์ ๊ณต๊ฐ ์ง์**\
conda activate [์์๊ณต๊ฐ์ด๋ฆ]

**Tensorflow ์ค์น**\
pip install tensorflow==[๋ฒ์ ]

**Jupyter Notebook ์ค์น** (์ฌ๊ธฐ์ ๊น์์ผ root ๊ณ์ ์ด ์๋๋ผ conda ํ๊ฒฝ์์ ์ฅฌํผํฐ ๋ธํธ๋ถ์ด ์คํ๋๋ค)\
conda install jupyter notebook

**Jupyter Notebook ์คํ**\
jupyter notebook

**ํ์๋ณด๋ ์คํ**\
tensorboard --logdir="./"
