---
description: 이번 워크샵의 목적은 DevOps 운영에서 DevOps Guru가 탐지한 이상징후에 대해 생성된 통찰력을 입증하는 것입니다.
---

# Overview

테스트 환경이 없고 통찰력 생성을 테스트하기 위한 인프라를 구축하려는 경우 아래 워크샵을 순서대로 진행합니다. 그러나 테스트 또는 프로덕션 환경(가급적이면 CloudFormation 스택에서 생성)이 있는 경우 첫 번째 섹션을 건너뛰고 DevOps Guru 활성화 및 트래픽 주입 섹션으로 바로 이동할 수 있습니다.

솔루션에는 다음 단계가 포함됩니다.&#x20;

A. 서버리스 인프라를 배포합니다.&#x20;

B. DevOps Guru를 활성화하고 트래픽을 주입합니다.&#x20;

C. 생성된 DevOps Guru 통찰력을 검토합니다.&#x20;

D. 새로운 통찰력을 생성하기 위해 또 다른 실패를 주입하십시오.&#x20;

다음 다이어그램에 표시된 대로 CloudFormation 스택을 사용하여 [Amazon API Gateway](https://aws.amazon.com/api-gateway), [AWS Lambda](http://aws.amazon.com/lambda),  및 [Amazon DynamoDB](https://aws.amazon.com/dynamodb/)로 구성된 서버리스 인프라를 생성하고 목록 레코드에 게시된 API에 HTTP 요청을 고속으로 주입합니다.

<figure><img src="../.gitbook/assets/스크린샷 2023-02-20 오후 9.46.49.png" alt=""><figcaption></figcaption></figure>

DevOps Guru가 계정 내에서 리소스를 모니터링할 수 있도록 설정하면 벤딩된 Amazon CloudWatch 메트릭과 ML 모델의 특정 패턴을 결합하여 이상을 탐지합니다. 이상 징후가 감지되면 권장 사항에 대한 통찰력을 생성합니다. 통찰력의 생성은 몇 가지 요인에 의해 좌우된다.&#x20;

이 게시물은 통찰력을 재현할 수 있는 캔 환경을 제공하지만 트래픽 패턴, 트래픽 주입 시기 등에 따라 결과가 달라질 수 있습니다.
