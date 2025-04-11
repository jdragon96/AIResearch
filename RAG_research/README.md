# RAG

0. 소스코드 
1. 개요
2. RAG 구성요소
3. Ollama

## 0. 소스코드
- `ollama_deepseek.ipynb`
    - Ollama를 통해 DeepSeek을 RAG화 함께 실행시키는 예제

## 1. 개요

## 2. RAG 구성요소

### 2.1. Indexing

- 외부 지식을 벡터 형태로 전처리하여 빠르게 검색할 수 있게 준비하는 단계
- 주요 작업
    1. 문서 분할
        - 텍스트를 문단/문장/의미 단위로 쪼갬
        - `RecursiveCharacterTextSplitter`
    2. 임베딩 생성
        - 각 chunk를 벡터화
    3. 벡터DB 저장
        - FAISS, Pinecone, Weaviate 등등

### 2.2. Retrieval(검색)
- 사용자의 질문을 임베딩으로 변환
- 벡터DB에서 의미적으로 유사한 chunk를 탐색
- 주요 작업
    1. 질문 임베딩
        - 유저 질문을 동일한 임베딩 모델로 벡터화
    2. 벡터 검색
        - 벡터DB에서 코사인 유사도 등을 기준으로 유사한 문서 N개 검색
    3. 필터링
        - 메탇데이터 필터링 적용

### 2.3. Generation(생성)
- 검색된 문서와 질문을 함께 LLM에게 제공하여 자연어 응답을 생성


## 3. Ollama
- 로컬 PC에서 LLM을 쉽고 빠르게 실행할 수 있게 해주는 오픈소스 툴킷
```bash
ollama list       // 모델 목록 보는법
ollama rm <모델명> // 모델 지우는 방법
```