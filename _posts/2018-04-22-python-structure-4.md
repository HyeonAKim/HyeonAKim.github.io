---
layout: post
title:  "파이썬으로 파일 읽고 쓰기"
subtitle: 파이썬으로 글쓰기
categories: python
tags: structure
comments: true
---
- edwith 강좌를 바탕으로 정리한 내용입니다.


<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=2 orderedList=false} -->
<!-- code_chunk_output -->

* [1. 컴퓨터 파일이란](#1-컴퓨터-파일이란)
* [2. 파일열기](#2-파일열기)
* [3. 파일쓰기('w')](#3-파일쓰기w)
* [4. 파일읽기('r')](#4-파일읽기r)
* [5. 파일내용추가('a')](#5-파일내용추가a)
* [6. 파일닫기](#6-파일닫기)
* [7. 파일존재 확인](#7-파일존재-확인)

<!-- /code_chunk_output -->

## 1. 컴퓨터 파일이란

컴퓨터에서 파일이란 무엇일까요?
여러가지 문서를 우리는 파일철에 모아 놓습니다.
이와 마찬가지로 컴퓨터에서 하나의 파일철을 폴더라고 하고 폴더가 있는 곳을 디렉토리라고 합니다.

파일이 필요한 이유는 무엇일까요?
프로그래밍을 할때는 파일 없이 데이터를 그때 그때 입력이 가능합니다.
데이터가 너무 많거나 데이터를 저장하고 재사용할 경우에는 파일이 필요합니다.

## 2. 파일열기

파이썬을 이용해서 파일을 읽거나 쓰기위해 가장 먼저 해야하는 일이 무엇일까요?
바로 파일을 여는 일입니다.

```python
# 파일변수 = open(파일경로,모드)
```
`파일변수`에는 파일정보가 저장됩니다. 메모리상의 파일위치, 현재 읽는 곳과 다음에 읽어야하는 곳을 저장합니다.
`파일경로`는 파일을 저장되거나 저장할 경로를 의미합니다. 파일경로는 `역슬래시`로 표현합니다.  
`모드`는 파일을 열때 어떤 목적을 가지고 여는지를 정합니다. 3가지 모드가 있습니다.   
  * 'r' : 읽기
  * 'w' : 쓰기(덮어쓰기)
  * 'a' : 현재내용에 추가  

## 3. 파일쓰기('w')
 파일을 열었다면 쓰는 방법에 대해 알아보도록 하겠습니다.  

```python
# 파일열기
f = open('파일경로','w')
# 파일변수.write("문자열")
f.write("떡볶이\n")
```
파일을 쓰는 방법은 'w'모드로 열고 파일변수.write함수를 이용해서 간단하게 입력할 수 있습니다.

## 4. 파일읽기('r')
파일을 읽는 방법은 3가지 방법이 있습니다.
```python
# 파일열기
f = open('파일경로','r')

# 1.파일 전체 읽기
변수 = 파일변수.read()
```
첫 번째 방법은 전체 문서를 모두 읽는 방법입니다. 문서의 크기가 크지 않을 경우에는 유용하지만 문서가 클 경우에는 메모리에 모두 올라가 효율성이 떨어 질 수 있습니다.

```python
# 파일열기
f = open('파일경로','r')

# 2. 한줄씩 읽기
변수 = 파일변수.readline()
```
두 번째 방법은 한 줄씩 파일을 읽는 방법 입니다. 여러 줄을 읽기 위해서는 함수를 원하는 만큼 호출해야 하는 번거로움이 있습니다.

```python
# 파일열기
f = open('파일경로','r')

# 3. 여러줄 읽기
변수 = 파일변수.readlines()
```
세 번째 방법은 여러줄을 읽는 방법입니다. 여러줄을 리스트에 항목으로 생성합니다.

## 5. 파일내용추가('a')
'w' 모드로 파일을 작성할 때는 새로 작성할 때 사용됩니다. 기존의 내용에 추가할때는 반드시 'a' 모드를 사용해야 합니다.

내용을 작성하는 방법은 쓰기와 동일합니다.

```python
# 파일열기
f = open('파일경로','a')
# 파일변수.write("문자열")
f.write("떡볶이\n")
```

## 6. 파일닫기
파일을 모두 작성하거나 읽었다면 반드시 파일을 닫아줘야합니다. 파일을 닫지 않았을 경우에는 제대로 저장되지 않아 정보를 손실할 수 있습니다. 따라서 파일을 닫는 것은 읽거나 쓰는것 만큼 중요합니다.

```python
f.close()
```

## 7. 파일존재 확인
기본적으로 파일을 열때 파일이 없을 경우에는 파이썬에서 생성을 합니다. 하지만 파일이 없을 경우에 오류로 처리해야할 때가 있습니다. 그럴 때는 이전에 배운 **조건문과 파일확인 함수를** 활용할 수 있습니다.

```python
# os 모듈을 import합니다.
import os

# 파일 확인 조건문
if os.path.isfile("파일명") :
  # Ture일 경우  
  print "파일이 존재합니다"
else:
  # False일 경우
  print "파일이 존재하지 않습니다."
```

파일과 마찬가지로 디렉토리도 확인이 가능합니다.

```python
# os 모듈을 import합니다.
import os

# 파일 확인 조건문
if os.path.isdir("디렉토리") :
  # Ture일 경우  
  print "디렉토리가 존재합니다"
else:
  # False일 경우
  print "디렉토리가 존재하지 않습니다."
```
