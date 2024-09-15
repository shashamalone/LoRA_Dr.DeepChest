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
#### (1) Multi Modal의 언어모델 fine-tuning의 어려움
LoRA는 MultModal이 아닌 LLM에 특화된 Fine-Tuning방식
따라서, MultModal을 LoRA방식으로 Fine-Tuning하기 위해서는
1) Image모델과 Text 모델(LLM)이 구분되어 있는 형태에서
2) LLM만 LoRA로 Fine-Tuning해야하는 문제
3) 학습시킬 Image를 LLM에 맞는 형태로 전처리해 임베딩해야하는 문제 존재

[해결 방법]
pretrained 된 vision model로 이미지를 임베딩하여 prompt에 같이 전달 (문제1 & 문제 3 해결)
→ 학습에 필요한 파라미터 수를 크게 줄이고,  LLM부분은 LLama 모델을 사용하여 구현 (문제2 해결)
LLM tuning 하는 과정에서 lora를 적용하여 기존의 모두 파라미터를 학습 시키는 것이 아닌 전체 파라미터의 4%정도의 데이터만 학습시킴 



#### (2) 전처리
 - torchxrayvision 의 사전학습된 DenseNet 모델 import
 - DenseNet 사용해서 Feature Map 추출
 - extract_findings 함수 설정
 - 최종 전처리 데이터 json 파일로 저장

#### (3) 이미지 임베딩 & 선형 변환
 - torchXrayvision의 사전학습된 DenseNet(CNN)을 가져옴
 - Feature Map을 뽑음
 - 행렬 → average pooling → 하나의 값으로 변환⇒ Feature Map각각에서 값이 1024개가 뽑힘
 - nn.Linear(선형 변환)을 거침 ⇒ 값이 1024개에서 64개로 줄어듦

#### (4) Vsion Model이미지 임베딩(DenseNet) + LLM 파인튜닝  (Llama)
 - LoRA 모델을 사용하여 사전 학습된 언어 모델 Llama를 파인튜닝
 - 이미지 임베딩 결과를 입력으로 받아 병명과 진단사항을 도출
 - LLM(대형 언어 모델)을 활용하여 자연어 형태로 결과를 출력



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


