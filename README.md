# LoRA_Dr.DeepChest (mini_22Analysis) 
LoRA를 이용한 흉부 X-ray 병명 진단 AI  Dr.DeepChest 개발 프로젝트
</br>


## Usage
- [ ] 세션
- [ ] 컨퍼런스
- [X] 미니프로젝트
- [ ] 스터디

<br/>

## Period
### 2024.05.02. ~ 2024.05.30.

<br/>

## Team

- 팀장: [김이정](https://github.com/shashamalone)
- 팀원: [이준석](https://github.com/jjunstone7), [전현지](https://github.com/HyunZ118), [유하린](https://github.com/HyunZ118)
<br/>

----
<br/>


## 프로젝트 소개 및 목적
 
#### Multimodal + LoRA fine-tuning을 이용하여, 흉부 X-ray 병명 진단 AI를 개발하는 프로젝트입니다.

<br/>

## 프로젝트 구현 개요
### 1. LoRA(Low-Rank Adaptation )
#### (1) RAG(Retrieval Augmented Generation, 검색 증강 생성)




#### (2) LangChain


### 2. 파인콘(Pynecone)을 이용하여 Vector DB 구축


<br/>

## Dataset
- [MIMIC-CXR](https://paperswithcode.com/dataset/mimic-cxr)
  - 대규모 흉부 X-ray Dataset 
  - CT이미지 + 판독문 (의사의 text : Tags, Findings, Impression)
  - 흉부 X-ray 이미지 수 : 약 377,110 장

<br/>

## Model

![11](https://github.com/user-attachments/assets/cdb9cfc0-3dc9-4c3a-9982-f5879503ba7d)

- **LoRA-Alpaca**
  - Alpaca 모델을 LoRA (Low-Rank Adaptation) 기법을 사용하여 경량화하고 튜닝한 모델
  - [Alpaca 모델](https://github.com/tatsu-lab/stanford_alpaca)은 Meta의 LLaMA (Large Language Model Meta AI)를 기반으로, 스탠포드 대학 연구팀이 ChatGPT의 성능을 따라잡기 위해 설계한 경량화된 언어 모델

<br/>

## System Architecture

![9](https://github.com/user-attachments/assets/c8c9f7dc-299f-45c9-bd89-c9cc5b392d5b)



<br/>

## 추가 개선 사항


