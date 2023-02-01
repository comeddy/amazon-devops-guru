# Status recovery

이상 현상을 원복해보고 대시보드의 변화를 살펴보도록 하겠습니다.

충분한 시간이 경과되면 구성을 변경하여 일반적인 작동 이벤트를 시뮬레이션합니다. 아래 그림과 같이 CloudFormation 템플릿을 업데이트하여 DynamoDB 테이블의 읽기 용량을 1에서 5로 원복합니다.

1. 동작중인 sendAPIRequest.py 4개의 프로세스를 찾아 종료합니다. (i.e, ps -ef | grep python3)&#x20;
2. Cloud9 IDE의 왼쪽 상단에서 amazon-devopsguru-samples 디렉토리를 확장하여 디렉토리 구조를 볼 수 있으며, 다른 중첩 디렉토리(`generate-devopsguru-insights)`를 찾을 수 있습니다. 여기에서 CloudFormation 템플릿 파일 `cfn-shops-monitoroper-code.yaml`을 더블 클릭하여 엽니다.
3. `cfn-shops-monitoroper-code.yaml`Cloud9 IDE에서 연 후 15행으로 이동합니다 . `ReadCapacityUnits`아래와 같이 값을 1에서 5로 원복합니다 . 이렇게 하면 DynamoDB 테이블에서 [읽기 용량이 늘어납니다. ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ProvisionedThroughput.html#ProvisionedThroughput.CapacityUnits.Read)

![ ](<../.gitbook/assets/스크린샷 2022-08-08 오후 6.03.54.png>)

&#x20; 4\. DynamoDB Table의 백업 메뉴에서 point-in-time recovery(PITR), 즉 특정 시점으로 복구기능을 enable 해둡니다.&#x20;

![](<../.gitbook/assets/스크린샷 2022-08-08 오후 6.12.35.png>)

&#x20; 5\.  10분정도 이후 DevOps Guru 대시보드에서 사전대응과 사후대응의 변화를 확인해봅니다.&#x20;

![](<../.gitbook/assets/스크린샷 2022-08-08 오후 6.12.22.png>)

{% hint style="info" %}
사후 대응의 진행상태를 Amazon DevOps Guru가 반영하고 있는지 확인해보았습니다.&#x20;
{% endhint %}
