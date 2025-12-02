# PR-HalluX: Perception–Reasoning Hallucination XAI for MLLMs

<p align="right">
<a href="./README.md">English</a> | <b>한국어</b>
</p>

## 개요

PR-HalluX는 멀티모달 / 비전–언어 모델(MLLM)의 환각을 분석하기 위한
실험용 코드베이스입니다.

핵심 초점은 다음과 같습니다.

- **Perception 관련 오류**와 **Reasoning 관련 오류**를 구분하는 것
- 내부 신호(attention / feature 등)를 추출하는 것
- 간단한 평가 및 완화(policy) 코드를 구성하는 것

## 디렉토리 구조

```text
src/
  models/        # MLLM wrapper (모델 로드, generate)
  attribution/   # attention hook, perception/reasoning 점수 계산
  policy/        # 단계별(stage-aware) 완화 정책
  utils/         # 입출력, 시각화, 로깅 유틸
notebooks/       # 실험용 Jupyter 노트북
configs/         # 실험 설정 파일
data/            # 데이터셋 (raw / processed, git ignore 대상)
````

## 설치

```bash
conda create -n mllm-hallu-pr-xai python=3.11
conda activate mllm-hallu-pr-xai

pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121
pip install transformers datasets accelerate pillow matplotlib
```

PyTorch 인덱스 URL은 사용하는 CUDA 버전에 맞게 수정하시면 됩니다.

## 최소 사용 예시

1. `src/models/mllm_wrapper.py`에 사용할 MLLM(LLaVA, Qwen-VL 등)을 구현합니다.
2. 테스트용 이미지와 프롬프트를 하나 준비합니다.
3. 간단한 스크립트나 `notebooks/01_baseline_inference.ipynb`로

   * 이미지 + 프롬프트 → 텍스트 생성이 동작하는지 확인합니다.
4. 필요에 따라

   * 환각 벤치마크 연동
   * attention 추출
   * perception/reasoning 점수 및 간단한 정책
     을 단계적으로 추가하면서 실험을 진행합니다.

