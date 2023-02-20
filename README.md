---
coverY: 0
---

# Gaining operational insights with AIOps using Amazon DevOps Guru

AIOps(Artificial Intelligence for IT Operations)는 기계 학습 기술을 사용하여 운영 문제를 해결하는 프로세스입니다. AIOps의 목표는 IT 운영 프로세스에서 사람의 개입을 줄이는 것입니다.

고급 기계 학습 기술을 사용하면 운영 사고를 줄이고 서비스 품질을 높일 수 있습니다. AIOps는 다음과 같은 도움을 드릴 수 있습니다.

* 서비스 품질을 높입니다.
* 사고가 발생하기 전에 예측합니다.
* 새로운 사건과 통찰력을 분류합니다.

[Amazon DevOps Guru ](https://aws.amazon.com/devops-guru/)개발자와 운영자가 애플리케이션 가용성을 개선하고 운영 문제를 더 빠르게 해결할 수 있도록 하는 완전 관리형 AIOps 플랫폼 서비스를 제공합니다. 머신 러닝(ML) 기반 권장 사항을 활용하여 수동 작업을 최소화합니다. ML 모델은 20년 넘게 세계 최대 전자 상거래 비즈니스인 Amazon.com을 위해 고가용성 애플리케이션을 운영한 AWS의 전문성을 활용합니다. DevOps Guru는 운영 문제를 자동으로 감지하고 임박한 리소스 고갈을 예측하고 가능한 원인을 자세히 설명하고 수정 조치를 권장합니다.

이 워크숍에서는 일반적인 서버리스 환경에서 계정에 대해 DevOps Guru를 활성화하는 방법을 배우고 다양한 활동에 대해 생성된 통찰력과 권장 사항을 관찰합니다. 이러한 통찰력은 애플리케이션 가용성에 위험을 초래할 수 있는 운영 이벤트에 대해 생성됩니다. DevOps Guru는 AWS CloudFormation 스택을 애플리케이션 경계로 사용하여 리소스 관계를 감지하고 배포 이벤트와 상호 연관시킬 수 있습니다.

<figure><img src=".gitbook/assets/스크린샷 2023-02-20 오후 9.20.40.png" alt=""><figcaption><p>Amazon DevOps Guru 동작원리</p></figcaption></figure>

위 다이어그램에 표시된 대로 CloudFormation 스택을 사용하여 [Amazon API Gateway 로 구성된 서버리스 인프라를 생성합니다. ](https://aws.amazon.com/api-gateway)[AWS Lambda ](http://aws.amazon.com/lambda)및 [Amazon DynamoDB](https://aws.amazon.com/dynamodb/), 그리고 목록 레코드에 게시된 API에 HTTP 요청을 빠른 속도로 주입합니다.

{% hint style="info" %}
본 워크샵은 원본 AWS DevOps 블로그 [Amazon DevOps Guru를 사용하여 AIOps로 운영 통찰력 얻기를 기반으로 합니다. ](https://aws.amazon.com/blogs/devops/gaining-operational-insights-with-aiops-using-amazon-devops-guru/)
{% endhint %}
