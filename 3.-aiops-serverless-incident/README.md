---
description: 다음은 DevOps Guru가 활성화된 계정에 설정된 간단한 서버리스 애플리케이션의 아키텍처 다이어그램입니다.
---

# 3. AIOps serverless incident

![](<../.gitbook/assets/architecture-diagram (1).png>)

Amazon DevOps Guru는 활성화된 모든 리소스에 대한 지표를 자동으로 수집하고 분석합니다. 이를 통해 Amazon DevOps Guru는 기준선 또는 정상 작동 패턴을 설정하여 사전 교육 ML 모델이 편차를 감지할 수 있습니다.

DevOps Guru의 기본 기능을 다루는 첫 번째 인시던트를 시뮬레이션하기 위해 API Gateway를 대상으로 하는 매우 많은 양의 HTTP 트래픽을 전달하여 의도적으로 애플리케이션을 중단하고 오류를 주입할 것입니다. 해당 오류를 삽입한 후 DevOps Guru를 사용하여 애플리케이션 문제를 해결하고 문제를 해결하는 데 필요한 단계를 안내합니다. 다음 섹션에서 필요한 모든 단계를 자세히 설명합니다.

\
