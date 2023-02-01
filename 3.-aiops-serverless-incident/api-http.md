# API에 HTTP 트래픽 전송

이제`ListRestApiEndpointMonitorOper API에` HTTP Request를 전송합니다. Cloud9 터미널을 사용하여 아래 단계에 따라 API 엔드포인트로 트래픽 전송을 시작합니다.

1. CloudFormation 스택 `myServerless-Stack`의 **출력(Output)** 탭에서  `ListRestApiEndpointMonitorOper`API 엔드포인트를 찾거나 혹은 또는 다음 명령을 실행합니다.

```properties
cd ~/environment/amazon-devopsguru-samples/generate-devopsguru-insights
aws cloudformation describe-stacks --stack-name myServerless-Stack --query 'Stacks[0].Outputs[?OutputKey==`ListRestApiEndpointMonitorOper`].OutputValue' --output text
```

&#x20; 2\. 백엔드에서 DynamoDB를 호출하는 Lambda 함수를 호출하는 API 게이트웨이 구성을 포함하여 지원한 인프라의 API 엔드포인트입니다.

&#x20;`ListRestApiEndpointMonitorOper`API 엔드포인트를 찾아 sendAPIRequest.py url를 업데이트 해줍니다.&#x20;

```
vi sendAPIRequest.py
```

![](<../.gitbook/assets/스크린샷 2022-07-02 오후 1.43.10 1.png>)

&#x20; 3\. 이 RestAPI를 자동으로 호출하는 설정은 python 파일 형식으로 generate-devopsguru-insights 디렉토리에 설정됩니다. sendAPIRequest.py가 호출되면 HTTP 요청이 API로 반복적으로 루프되고 Lambda 함수와 DynamoDB가 호출됩니다. 데이터를 읽는 테이블. 트래픽 패턴의 급증을 시뮬레이트하려면 다음 명령을 실행하여 python 스크립트의 네 개의 인스턴스를 실행합니다. 이는 이 애플리케이션 스택에서 비정상적인 메트릭을 생성하기 위한 적절한 트래픽을 생성하는 데 필요합니다.

```properties
cd ~/environment/amazon-devopsguru-samples/generate-devopsguru-insights
python sendAPIRequest.py & python sendAPIRequest.py & python sendAPIRequest.py & python sendAPIRequest.py
```

높은 트래픽 속도로 주입하기 위해 스크립트를 실행하려면 터미널 여러 탭(가급적 4개) 실행해야 할 수 있습니다.

![](<../.gitbook/assets/스크린샷 2022-07-02 오후 1.46.11 (1).png>)

Loop에서 실행되는 스크립트의 **약 10분 후 DevOps Guru에서 운영 통찰력이 생성됩니다.**
