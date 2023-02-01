# DevOps Guru 활성화

이 섹션에서는 다음과 같은 고급 단계를 완료합니다.&#x20;

1\. CloudFormation 스택에 대해 DevOps Guru를 사용하도록 설정합니다.&#x20;

2.서버리스 스택이 완료될 때까지 기다린다.&#x20;

3\. 스택을 업데이트한다.&#x20;

4\. HTTP 요청을 API에 삽입합니다.

### 1. DevOps Guru 활성화

CloudFormation 템플릿을 실행하여 이 CloudFormation 스택에 대해 DevOps Guru를 활성화합니다.

```bash
aws cloudformation create-stack \
--stack-name EnableDevOpsGuruForServerlessCfnStack \
--template-body file:///$PWD/EnableDevOpsGuruForServerlessCfnStack.yaml \
--parameters ParameterKey=CfnStackNames,ParameterValue=myServerless-Stack \
--region ${AWS_REGION}
```

스택이 만들어진것을 확인한후, Amazon DevOps Guru 콘솔로 이동합니다.&#x20;

```
aws cloudformation describe-stacks --stack-name EnableDevOpsGuruForServerlessCfnStack --query Stacks[0].StackStatus
```

{% hint style="info" %}
선택적으로 Amazon Simple Notification Service(Amazon SNS) 항목을 구성하거나 AWS Systems Manager 통합을 활성화하여 DevOps Guru가 만든 모든 분석(Insights)에 대한 OpsItem 항목을 만들 수 있습니다. 여러 계정 및 리전에 걸쳐 스택 세트로 배포해야 하는 경우 AWS CloudFormation StackSets를 사용하여 여러 계정 및 리전에 걸쳐 Amazon DevOps Guru 쉽게 구성을 참조하십시오.
{% endhint %}

대시보드를 클릭하면 영향을 받는 애플리케이션을 보실 수 있습니다.&#x20;

* 애플리케이션이 영향을 받을 수 있는 문제에 대한 사전 예방 분석을 생성합니다.
* 진행중인 사후(Reactive) 예방분석을 알려주고 있습니다.&#x20;
* 진행중인 사전(Proactive) 예방분석을 알려주고 있습니다.&#x20;

![](<../.gitbook/assets/스크린샷 2022-07-03 오전 9.51.38.png>)

분석(Insights)을 클릭하면 사후(Reactive) 예방분석과 사전(Proactive) 예방분석을 보실수 있습니다.&#x20;

* 사후대응(Reactive) : 이제 사후 대응 인사이트를 통해 애플리케이션 성능을 개선하기 위한 권장 사항을 알 수 있습니다.
* 사전예방(Proactive) : 사전 예방 인사이트를 통해 향후 애플리케이션에 영향을 미칠 것으로 예측되는 문제를 알 수 있습니다.

### 2. Waiting for baselining of resources

DevOps Guru가 리소스의 베이스라인을 완료하고 일반적인 동작을 벤치마킹할 수 있도록 하기 위한 필수 단계입니다. 3 개의 리소스가있는 서버리스 스택의 경우 다음 단계를 수행하기 전에 2시간을 기다리는 것이 좋습니다. 프로덕션 환경에서 활성화되면 모니터링하기 위해 선택한 리소스 수에 따라 기준선을 완성하는데 최대 24 시간이 걸릴 수 있습니다.

{% hint style="warning" %}
참고: 대부분의 모니터링 툴과 달리 DevOps Guru는 대시보드가 지속적으로 모니터링될 것으로 예상하지 않으므로 정상적인 시스템 상태에서는 대시보드에 진행 중인 통찰력에 대해 제로(zero) 카운터가 표시될 뿐입니다. 이상 징후가 감지될 때만 경고가 발생하고 대시보드에 통찰력이 표시됩니다.
{% endhint %}

![](<../.gitbook/assets/스크린샷 2022-08-08 오전 1.02.09.png>)

따라서, 프로비저닝 처리량을 ReadCapacityUnits 5에서 1로 설정해보겠습니다.
