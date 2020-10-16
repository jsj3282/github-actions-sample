---
Title: 1-2. AWS_Product_FAQ_Computing_Auto_Scaling
Publish Date: 2020-10-16 11:20:27
---

### 2) Amazon EC2 Auto Scaling

- 일반
  - Amazon EC2 Auto Scaling이란?
    - Amazon EC2 Auto Scaling은 **Amazon EC2 인스턴스를 자동으로 시작하거나 종료**하여 애플리케이션 로드를 처리하기에 적절한 수의 Amazon EC2 인스턴스를 유지할 수 있도록 설계된 완전관리형 서비스. Amazon C2 Auto Scaling을 사용하면 비정상 인스턴스를 탐지하여 교체하는 EC2 인스턴스 플릿 관리를 통해 그리고 사용자가 정의하는 조건에 따라 Amazon EC2 용량을 자동으로 확장 또는 축소함으로써 애플리케이션 가용성을 유지할 수 있음. Amazon EC2 Auto Scaling을 사용하면 수요가 급증할 경우 Amazon EC2 인스턴스의 수를 자동으로 늘려 성능을 그대로 유지하고, 수요가 적을 경우 자동으로 용량을 줄여 비용을 절감할 수 있음.
  - Amazon EC2 Auto Scaling과 AWS Auto Scaling은 각각 언제 사용?
    - **여러 서비스에 걸쳐 여러 리소스의 규모를 조정하려면 AWS Auto Scaling**을 사용해야 함. AWS Auto Scaling을 사용하면 사전 정의된 규모 조정 정책을 사용하여 여러 EC2 Auto Scaling 그룹 또는 다른 리소스에 대한 동적 규모 조정 정책을 정의할 수 있음. **Amazon EC2 Auto Scaling 그룹의 규모만 조정하면 되거나 EC2 플릿의 상태만 유지 관리하려는 경우 Amazon EC2 Auto Scaling**을 사용해야 합니다. 또한, Amazon EC2 Auto Scaling 그룹을 생성 또는 구성해야 하거나 예약된 또는 단계별 규모 조정 정책을 설정해야 하는 경우에도(AWS Auto Scaling에서는 목표 추적 규모 조정 정책만 지원하므로) EC2 Auto Scaling을 사용해야 함.
  - Amazon EC2 Auto Scaling을 사용할 때의 이점?
    - Amazon EC2 Auto Scaling은 Amazon EC2 인스턴스 가용성을 유지하는 데 도움이 됨. 하나의 Amazon EC2 인스턴스를 실행하든 수천 개를 실행하든 Amazon EC2 Auto Scaling을 사용하면 **손상된 Amazon EC2 인스턴스를 탐지하고 개입 없이 이를 교체**할 수 있음. 따라서 애플리케이션이 사용자가 기대하는 수준의 컴퓨팅 파워를 확보할 수 있음. Amazon EC2 Auto Scaling을 사용하면 애플리케이션의 수요 곡선을 따라 Amazon EC2 플릿을 자동으로 확장할 수 있으므로 미리 수동으로 Amazon EC2 용량을 프로비저닝해야 할 필요가 줄어듬. **Amazon CloudWatch**를 통해 용량 조정 활동을 트리거하는 경보를 전송하고 **Elastic Load Balancing(ELB)**을 사용하여 ASG 내 인스턴스로 트래픽을 분산할 수 있음. 로드 변화가 예측 가능한 경우에는 Amazon EC2 Auto Scaling을 통해 **일정을 예약**하여 용량 조정 활동을 계획할 수 있음.
  - 플릿 관리란 무엇이며 동적 규모 조정과 어떻게 다른가?
    - 애플리케이션이 Amazon EC2 인스턴스에서 실행되는 경우 **'플릿'**이라고 부르는 것을 보유하게 됨. ***플릿 관리*는 비정상 인스턴스를 자동으로 교체하고 플릿을 원하는 용량으로 유지하는 기능**을 말함. Amazon EC2 Auto Scaling의 ***동적 조정* **기능은 **로드 또는 다른 지표를 기반으로 용량을 자동으로 확장 또는 축소하는 기능**을 말함. 
  - EC2 ASG(Auto Scaling 그룹)이란?
    - Amazon EC2 Auto Scaling 그룹(ASG)에는 비슷한 특성을 공유하고 플릿 관리 및 동적 조정을 위해 논리적 그룹으로 취급되는 EC2 인스턴스 모음이 포함. Amazon EC2 Auto Scaling은 인스턴스가 비정상이 되더라도 고정된 인스턴스 수를 유지하도록 또는 지정한 기준에 따라 그룹의 인스턴스 수를 자동으로 조정.
  - 시작 구성이란?
    - **시작 구성**은 EC2 Auto Scaling 그룹에서 EC2 인스턴스를 시작하는 데 사용하는 템플릿이다. 시작 구성 생성 시 **Amazon 머신 이미지(AMI)의 ID, 인스턴스 유형, 키 페어, 하나 이상의 보안 그룹, 블록 디바이스 매핑 등 인스턴스에 대한 정보를 지정**. 
  - Amazon EC2 Auto Scaling은 용량을 어떻게 밸런싱하는가?
    - EC2 Auto Scaling 그룹 설정에 [여러 개의 영역을 구성](http://docs.aws.amazon.com/autoscaling/latest/userguide/as-add-availability-zone.html)하면 Amazon EC2 Auto Scaling이 영역 전체에서 EC2 인스턴스를 자동으로 밸런싱.
  - 수명 주기 후크란?
    - 수명 주기 후크를 사용하면 인스턴스가 서비스에 사용되기 전에 또는 종료되기 전에 조치를 취할 수 있음.
  - '비정상' 인스턴스의 특징은 무엇인가?
    - 비정상 인스턴스란 하드웨어가 어떤 이유에서 손상되거나(불량 디스크 등) 사용자가 구성한 ELB 상태 확인을 통과하지 못한 인스턴스를 말함.
  - '상태 저장 인스턴스'란 무엇을 말하는가?
    - 상태 저장 인스턴스란 인스턴스에만 존재하는 데이터가 있는 인스턴스를 말함. 일반적으로 상태 저장 인스턴스를 종료한다는 것은 인스턴스에 있는 데이터(또는 상태 정보)가 손실된다는 의미임. 수명 주기 후크를 사용하여 상태 저장 인스턴스가 종료하기 전에 인스턴스의 데이터를 복사하거나, 인스턴스 보호를 사용하여 Amazon EC2 Auto Scaling이 인스턴스를 종료하지 않도록 할 수 있음.
- 손상된 인스턴스 교체
  - Amazon EC2 Auto Scaling은 손상된 인스턴스를 어떻게 교체하는가?
    - 손상된 인스턴스가 상태 확인에 실패하면, Amazon EC2 Auto Scaling이 자동으로 이를 종료하고 새로운 인스턴스로 교체함. Elastic Load Balancing 로드 밸런서를 사용하고 있는 경우, Amazon EC2 Auto Scaling이 새로운 인스턴스를 프로비저닝하여 로드 밸런서에 연결하기 전에 손상된 인스턴스를 로드 밸런서에서 단계적으로 분리함. 
  - 축소 시 Amazon EC2 Auto Scaling이 종료하는 인스턴스를 제어하려면 어떻게 해야 하며 인스턴스의 데이터를 보호하려면 어떻게 해야 하는가?
    - 사용자는 각 Amazon EC2 Auto Scaling 그룹에서 Amazon EC2 Auto Scaling이 그룹에 인스턴스를 추가하거나(확장이라고 함) 그룹에서 인스턴스를 제거하는(축소라고 함) **시점을 제어**함. 인스턴스를 연결하거나 분리하여 **수동으로 그룹 크기를 조정하거나, 조정 정책을 사용하여 이러한 프로세스를 자동화**할 수 있음. 자동으로 축소하도록 Amazon EC2 Auto Scaling을 설정한 경우, Amazon EC2 Auto Scaling에서 먼저 종료해야 하는 인스턴스가 무엇인지 결정해야 함. 이 작업은 종료 정책을 사용하여 구성할 수 있음. 또한, **인스턴스 보호 기능**을 사용하여 Amazon EC2 Auto Scaling이 축소를 위해 인스턴스를 종료할 때 특정 인스턴스를 선택에서 배제하도록 할 수도 있음. 인스턴스에 데이터가 있으며 인스턴스를 축소하더라도 해당 데이터를 유지해야 하는 경우, **S3, RDS 또는 DynamoDB와 같은 서비스를 사용하여 인스턴스 외부로 데이터를 저장**할 수 있음.
- 보안
  - Amazon EC2 Auto Scaling 리소스에 대한 액세스를 제어하려면 어떻게 해야 하는가?
    -  [AWS Identity and Access Management](https://aws.amazon.com/iam/)(IAM)와 통합
- 비용 최적화
- 요금