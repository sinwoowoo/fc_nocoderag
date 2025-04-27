# 자체 호스팅 AI 스타터 킷

**자체 호스팅 AI 스타터 킷**은 포괄적인 로컬 AI 및 로우코드(low-code) 개발 환경을 신속하게 초기화하도록 설계된 오픈 소스 Docker Compose 템플릿입니다.

![n8n.io - 스크린샷](https://raw.githubusercontent.com/n8n-io/self-hosted-ai-starter-kit/main/assets/n8n-demo.gif)

<https://github.com/n8n-io>에서 선별했으며, 자체 호스팅 n8n 플랫폼과 호환되는 AI 제품 및 구성 요소 목록을 결합하여 자체 호스팅 AI 워크플로우 구축을 빠르게 시작할 수 있도록 지원합니다.

> [!팁]
> [발표 내용 읽기](https://blog.n8n.io/self-hosted-ai/)

### 포함된 내용

✅ [**자체 호스팅 n8n**](https://n8n.io/) - 400개 이상의 통합 및 고급 AI 구성 요소를 갖춘 로우코드 플랫폼

✅ [**Ollama**](https://ollama.com/) - 최신 로컬 LLM을 설치하고 실행하는 크로스 플랫폼 LLM 플랫폼

✅ [**Qdrant**](https://qdrant.tech/) - 포괄적인 API를 갖춘 오픈 소스 고성능 벡터 스토어

✅ [**PostgreSQL**](https://www.postgresql.org/) - 데이터 엔지니어링 세계의 핵심 도구로, 대량의 데이터를 안전하게 처리

✅ [**flowise**](https://flowiseai.com/) - 개발자가 맞춤형 LLM 오케스트레이션 플로우 및 AI 에이전트를 구축할 수 있는 오픈 소스 로우코드 도구

### 구축 가능한 것들

⭐️ 약속 예약을 위한 **AI 에이전트**

⭐️ 데이터 유출 없이 안전하게 **회사 PDF 요약**

⭐️ 향상된 회사 커뮤니케이션 및 IT 운영을 위한 **더 스마트한 Slack 봇**

⭐️ 최소 비용으로 **비공개 금융 문서 분석**

## 설치

### 리포지토리 복제

```bash
git clone https://github.com/aieeiee/fc_nocoderag.git
cd fc_nocoderag/self-hosted-ai-starter-kit
```

### Docker Compose를 사용하여 n8n 실행

> [!IMPORTANT]
> Docker Compose 명령을 실행하기 전에 먼저 환경 설정을 구성해야 합니다.
> `.env.example` 파일을 `.env` 파일로 복사하십시오. PowerShell에서는 다음 명령을 사용할 수 있습니다:
> ```powershell
> copy .env.example .env
> ```
> 그런 다음 필요에 따라 `.env` 파일 내의 설정을 검토하고 수정하십시오.

#### Nvidia GPU 사용자용

```bash
docker compose --profile gpu-nvidia up
```

> [!참고]
> 이전에 Docker와 함께 Nvidia GPU를 사용한 적이 없다면,
> [Ollama Docker 지침](https://github.com/ollama/ollama/blob/main/docs/docker.md)을 따르십시오.

### Linux의 AMD GPU 사용자용

```bash
docker compose --profile gpu-amd up
```

#### Mac / Apple Silicon 사용자용

M1 또는 최신 프로세서가 장착된 Mac을 사용하는 경우 안타깝게도 GPU를 Docker 인스턴스에 노출할 수 없습니다. 이 경우 두 가지 옵션이 있습니다.

1.  아래 "기타 사용자" 섹션처럼 CPU에서만 스타터 킷 실행
2.  더 빠른 추론을 위해 Mac에서 Ollama를 실행하고 n8n 인스턴스에서 연결

Mac에서 Ollama를 실행하려면 [Ollama 홈페이지](https://ollama.com/)에서 설치 지침을 확인하고 다음과 같이 스타터 킷을 실행하십시오.

```bash
docker compose up
```

##### Mac에서 로컬로 OLLAMA를 실행하는 사용자용

Mac에서 로컬로 OLLAMA를 실행하는 경우(Docker 내부가 아님), n8n 서비스 구성에서 `OLLAMA_HOST` 환경 변수를 수정해야 합니다. Docker Compose 파일의 `x-n8n` 섹션을 다음과 같이 업데이트하십시오.

```yaml
x-n8n: &service-n8n
  # ... 기타 설정 ...
  environment:
    # ... 기타 환경 변수 ...
    - OLLAMA_HOST=host.docker.internal:11434
```

또한 "Editor is now accessible via: <http://localhost:5678/>" 메시지가 표시된 후:

1.  <http://localhost:5678/home/credentials> 로 이동합니다.
2.  "Local Ollama service"를 클릭합니다.
3.  기본 URL을 "http://host.docker.internal:11434/"로 변경합니다.

#### 기타 사용자

```bash
git clone https://github.com/aieeiee/fc_nocoderag.git
cd self-hosted-ai-starter-kit
docker compose --profile cpu up
```

## ⚡️ 빠른 시작 및 사용법

자체 호스팅 AI 스타터 킷의 핵심은 네트워크 및 스토리지 설정이 사전 구성된 Docker Compose 파일로, 추가 설치 필요성을 최소화합니다.
위의 설치 단계를 완료한 후 아래 단계에 따라 시작하십시오.

1.  브라우저에서 <http://localhost:5678/> 을 열어 n8n을 설정합니다. 이 작업은 한 번만 수행하면 됩니다.
2.  포함된 워크플로우 열기:
    <http://localhost:5678/workflow/srOnR8PAY3u4RSwb>
3.  캔버스 하단의 **Chat** 버튼을 클릭하여 워크플로우 실행을 시작합니다.
4.  워크플로우를 처음 실행하는 경우 Ollama가 Llama3.2 다운로드를 마칠 때까지 기다려야 할 수 있습니다. Docker 콘솔 로그를 확인하여 진행 상황을 확인할 수 있습니다.

언제든지 n8n을 열려면 브라우저에서 <http://localhost:5678/> 을 방문하십시오.

n8n 인스턴스를 사용하면 400개 이상의 통합과
[AI 에이전트](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/),
[텍스트 분류기](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.text-classifier/),
[정보 추출기](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.information-extractor/)와 같은
기본 및 고급 AI 노드 모음에 액세스할 수 있습니다. 모든 것을 로컬로 유지하려면 언어 모델에는 Ollama 노드를 사용하고 벡터 저장소에는 Qdrant를 사용하는 것을 잊지 마십시오.

> [!참고]
> 이 스타터 킷은 자체 호스팅 AI 워크플로우를 시작하는 데 도움이 되도록 설계되었습니다. 프로덕션 환경에 완전히 최적화되지는 않았지만, 개념 증명(PoC) 프로젝트에 적합한 강력한 구성 요소들을 결합합니다. 특정 요구 사항에 맞게 사용자 정의할 수 있습니다.

## 업그레이드

*   ### Nvidia GPU 설정용:

```bash
docker compose --profile gpu-nvidia pull
docker compose create && docker compose --profile gpu-nvidia up
```

*   ### Mac / Apple Silicon 사용자용

```bash
docker compose pull
docker compose create && docker compose up
```

*   ### 비 GPU 설정용:

```bash
docker compose --profile cpu pull
docker compose create && docker compose --profile cpu up
```

## 👓 추천 자료

n8n은 AI 개념 및 노드를 빠르게 시작하는 데 유용한 콘텐츠로 가득합니다. 문제가 발생하면 [지원](#지원) 섹션으로 이동하십시오.

-   [개발자를 위한 AI 에이전트: 이론에서 n8n 실습까지](https://blog.n8n.io/ai-agents/)
-   [튜토리얼: n8n에서 AI 워크플로우 구축하기](https://docs.n8n.io/advanced-ai/intro-tutorial/)
-   [n8n의 Langchain 개념](https://docs.n8n.io/advanced-ai/langchain/langchain-n8n/)
-   [에이전트와 체인의 주요 차이점 시연](https://docs.n8n.io/advanced-ai/examples/agent-chain-comparison/)
-   [벡터 데이터베이스란 무엇인가?](https://docs.n8n.io/advanced-ai/examples/understand-vector-databases/)

## 🎥 비디오 둘러보기

-   [n8n용 로컬 AI 설치 및 사용](https://www.youtube.com/watch?v=xz_X2N-hPg0)

## 🛍️ 더 많은 AI 템플릿

더 많은 AI 워크플로우 아이디어를 보려면 [**공식 n8n AI 템플릿 갤러리**](https://n8n.io/workflows/?categories=AI)를 방문하십시오. 각 워크플로우에서 **워크플로우 사용** 버튼을 선택하여 로컬 n8n 인스턴스로 워크플로우를 자동으로 가져옵니다.

### 주요 AI 개념 학습

-   [AI 에이전트 채팅](https://n8n.io/workflows/1954-ai-agent-chat/)
-   [모든 데이터 소스와 AI 채팅 (n8n 워크플로우 도구 사용)](https://n8n.io/workflows/2026-ai-chat-with-any-data-source-using-the-n8n-workflow-tool/)
-   [OpenAI 어시스턴트와 채팅 (메모리 추가)](https://n8n.io/workflows/2098-chat-with-openai-assistant-by-adding-a-memory/)
-   [오픈 소스 LLM 사용 (Hugging Face 경유)](https://n8n.io/workflows/1980-use-an-open-source-llm-via-huggingface/)
-   [AI를 사용하여 PDF 문서와 채팅 (출처 인용)](https://n8n.io/workflows/2165-chat-with-pdf-docs-using-ai-quoting-sources/)
-   [웹페이지 스크랩 가능한 AI 에이전트](https://n8n.io/workflows/2006-ai-agent-that-can-scrape-webpages/)

### 로컬 AI 템플릿

-   [세법 도우미](https://n8n.io/workflows/2341-build-a-tax-code-assistant-with-qdrant-mistralai-and-openai/)
-   [MistralAI 및 Qdrant를 사용하여 문서를 학습 노트로 분해](https://n8n.io/workflows/2339-breakdown-documents-into-study-notes-using-templating-mistralai-and-qdrant/)
-   [Qdrant 및 Mistral.ai를 사용한 금융 문서 도우미](https://n8n.io/workflows/2335-build-a-financial-documents-assistant-using-qdrant-and-mistralai/)
-   [Qdrant 및 Mistral을 사용한 레시피 추천](https://n8n.io/workflows/2333-recipe-recommendations-with-qdrant-and-mistral/)

## 팁 & 트릭

### 로컬 파일 액세스

자체 호스팅 AI 스타터 킷은 공유 폴더(기본적으로 동일한 디렉토리에 위치)를 생성하며, 이 폴더는 n8n 컨테이너에 마운트되어 n8n이 디스크의 파일에 액세스할 수 있도록 합니다. n8n 컨테이너 내 이 폴더의 위치는 `/data/shared` 이며, 로컬 파일 시스템과 상호 작용하는 노드에서 사용해야 하는 경로입니다.

**로컬 파일 시스템과 상호 작용하는 노드**

-   [디스크에서 파일 읽기/쓰기](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.filesreadwrite/)
-   [로컬 파일 트리거](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.localfiletrigger/)
-   [명령 실행](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.executecommand/)

## 📜 라이선스

이 프로젝트는 Apache License 2.0에 따라 라이선스가 부여됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하십시오.

## 💬 지원

[n8n 포럼](https://community.n8n.io/)에서 대화에 참여하여 다음을 수행할 수 있습니다.

-   **작업 공유**: n8n으로 구축한 것을 자랑하고 커뮤니티의 다른 사람들에게 영감을 줍니다.
-   **질문하기**: 이제 막 시작했든 숙련된 전문가든, 커뮤니티와 우리 팀은 모든 어려움을 지원할 준비가 되어 있습니다.
-   **아이디어 제안**: 기능이나 개선에 대한 아이디어가 있습니까? 알려주세요! 다음에 보고 싶은 내용을 항상 듣고 싶어합니다.
