# IAM

Identity and Access Management

- ID 및 액세스 관리, 글로벌 서비스
- 사용자를 생성하고 그룹을 할당한다.
- 디폴트로 Root 계정이 있지만, 사용되거나 공유되지는 못한다.
    - 대신 조직에서 User 계정을 만들어서 사용하면 된다.
    - 하나의 User = 조직 내에 한 사람
    - 경우에 따라 그룹화해서 사용할 수 있다.
    
    ![image](https://user-images.githubusercontent.com/76610641/218316075-00759a57-323c-4077-b5e3-d209a1f13833.png)
    
    - 그룹은 오직 그룹내 사용자만 포함하고 있다.
    - 일부 사용자는 어느 그룹에도 포함하지 않을 수 있다.
    
    ![image](https://user-images.githubusercontent.com/76610641/218316119-97e63fa4-01c5-4221-b5f1-4c5dcd1f53f5.png)
    
    - 사용자는 여러 그룹에 속할 수 있다.

---

### IAM을 사용하는 이유?

AWS 계정을 사용하도록 허용하고 싶기 때문이다.

그들이 그렇게 할 수 있도록 권한을 주어야 한다.

따라서 JSON 문서(정책)를 통해 사용자 또는 그룹을 할당할 수 있다.

---

### IAM 정책

![image](https://user-images.githubusercontent.com/76610641/218316056-a2e706af-e1f1-42a0-b299-807f81f4dd13.png)

- 사용자가 수행할 수 있는 작업 또는 그룹이 수행할 수 있는 작업을 명시해놓으면, 해당 그룹 내의 모든 사용자가 수행할 수 있다.
- 사용자가 AWS에서 일부 서비스를 사용할 수 있도록 허용할 수 있다.
- 정책을 통해 권한을 정의하는데 도움이 된다.
- AWS는 모든 사람이 모든 작업을 수행하도록 허용하지 않는다.
- AWS는 다음과 같은 원칙을 따르도록 한다.

### 최소 권한 원칙

사용자에게 필요한것보다 더 많은 권한을 부여하지 않는다.

---

### IAM 설정하기

- IAM은 글로벌 서비스이다.
- IAM은 글로벌 영역에서 사용자나 그룹이 생성된다.
- 루트 사용자는 모든 권한을 가진다.
    - 따라서 사용하기에 위험한 계정이다.
    - 관리자 계정을 만들어 사용하는 것이 좋다.
    - 루트 계정은 정말 필요할 때만 사용한다. (보안관점에서)

---

![image](https://user-images.githubusercontent.com/76610641/218316140-04e562c6-705e-4892-a4ad-3d8b3cc1e8f5.png)

- 이름을 설정한다.
- 자격 증명 유형을 선택한다.
    - 암호 유형의 자격 증명을 활성화한다.
- 콘솔 패스워드를 설정한다.
    - 자동 혹은 커스텀 버전이 있는데 기호에 맞게 선택하고
    - 비밀번호를 설정한다.
- 완료한다.
- 사용자를 그룹에 추가한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad77ac5b-cb00-445b-9be1-0bca8792c8f8/Untitled.png)

- 그룹을 만든다. (admin 그룹)
    - 권한은 정책을 통해 정의된다.
    - AdministratorAccess 권한을 설정한다.

![image](https://user-images.githubusercontent.com/76610641/218316150-6fe5e246-7a8d-462d-a436-3aeb62ae9fc7.png)

- admin 그룹에 속한 모든 사용자는 해당 그룹과 연결된 권한을 상속한다.

![image](https://user-images.githubusercontent.com/76610641/218316162-7034f5b3-2c99-4d15-a862-b36d4f2d6ef8.png)

- 태그를 설정한다.
- AWS에서는 거의 모든 곳에서 태그를 찾을 수 있다.
    - 추적하는데 도움이 되는 정보이다.
    - 예를 들어 부서와 같은 것이다.

![image](https://user-images.githubusercontent.com/76610641/218316174-76c80e15-3f1a-4356-9146-a7cbbdbc2256.png)

- 사용자가 생성되었다.

![image](https://user-images.githubusercontent.com/76610641/218316182-19c01b56-56ab-4cec-b9d4-52e824db5e5a.png)

- 암호를 자동 생성한 경우 이동하기 전에 .csv를 다운로드해야 한다.
- .csv를 다운받으면 사용자의 자격 증명을 가질 수 있다.

---

### IAM 계정 살펴보기

사용자 stephane은 우리가 정책으로 설정한 AdministratorAccess 권한은 admin 그룹으로부터 물려받은 관리형 정책이다.

![image](https://user-images.githubusercontent.com/76610641/218316199-b5ae29e7-d2ec-48a4-aa53-65f96965f5f0.png)

Account alias를 설정하여 긴 숫자 ID를 좀 더 간결하게 설정할 수 있다.

---

### IAM 정책

![image](https://user-images.githubusercontent.com/76610641/218316225-0c67cbde-198e-4e68-b457-25748f9b322d.png)

Alice, Bob, Charles는 같은 그룹에 속해 있기 때문에 액세스 권한을 얻고 해당 정책을 사용한다.

David, Edward 또한 그룹에 해당되는 정책을 사용한다. 

Fred는 그룹에 속해있지 않고, 사용자에게만 연결되는 인라인 정책을 가지고 있다. 

Charles와 David는 감사팀의 정책도 가지고 있다. Charles는 개발자의 정책과 감사팀의 정책을, David는 운영자의 정책과 감사팀의 정책 두 개를 가지게 된다. 

따라서 정책 구조 측면에서 높은 수준으로 알면 된다. 

---

### IAM 정책 구조

![image](https://user-images.githubusercontent.com/76610641/218316240-f27f12da-af98-48c0-8be0-a2fb17e70c4a.png)

- Version: 일반적인 버전은 2012-10-17이다. (정책 언어 버전)
- Id : 해당 정책을 식별하는 ID가 있다. (선택사항)
- Statement : 하나 또는 여러개 일 수 있다.
    - Sid : 식별자인 명령문 ID (선택사항)
    - **Effect : 특정 권한 (API에 대한 액세스 허용하거나 거부)**
    - **Principle : 원칙 (이 정책이 적용될 대상인 계정, 사용자, 또는 역할로 구성)**
    - **Action : 호출 목록 (수행될 API 호출 목록, Effect에 따라 거부 혹은 허용)**
    - **Resource : 리소스 목록 (작업이 적용될 대상)**
- (옵션) 조건 : 해당 문장을 적용할지 말지, 선택적으로 적용

---

### IAM 정책 설정

![image](https://user-images.githubusercontent.com/76610641/218316256-99092394-fe8a-4561-be62-f1aaaf9ba987.png)

- 권한 추가하기
- Attach existing policies directly
- IAMReadOnlyAccess 선택
- 따라서 해당 User로 로그인한 상태로 들어가면 IAM 계정에서 정책을 수정(추가, 변경)하는 일은 할 수 없다.

![image](https://user-images.githubusercontent.com/76610641/218316271-b6e7eeb1-e5cb-4288-8a24-0e87472b928f.png)

- 만약 그림처럼 User가 하나의 인라인 그룹, 두 개의 그룹에 속해있을 때, 세개의 정책이 적용된다.
- Admin 그룹에 속해있는 Stephan은 Admin에서 적용된 정책인 모든 권한을 허용하는 정책이 적용된다.
- 그리고 인라인 정책으로는 iam 계정에 대한 리소스를 Read만 할 수 있다.

---

### IAM 보호

1. **암호 정책 정의**
    1. 최소 비밀번호 길이 설정
    2. 특정 문자 유형 요구 (대문자, 숫자, 소문자 등)
    3. IAM 사용자가 비밀번호를 변경하는 것을 허용
    4. 비밀번호를 만료시키기 위해 사용자에게 비밀번호를 변경하도록 요구할 수 있다. (ex. 90일마다 변경)
    5. 비밀번호 재사용 방지
    
    → 해당 정책을 따르면 무차별 대입 공격에서 안전해질 수 있다.
    
2. **다단계 인증 또는 MFA**
    1. MFA 장치를 사용한다.
    2. root 계정과 IAM users를 보호하기 위해 사용한다.

---

### MFA

- 사용자가 알고있는 password + 사용자 소유의 보안 장치
- **예시**
    - Alice는 자신의 비밀번호와 MFA 생성 토큰을 가지고 있다.
    - 따라서 로그인 동안 위의 것을 함께 사용해서 성공적으로 로그인할 수 있다.
    - 해커 입장에서는 비밀번호만 탈취해서는 로그인을 할 수 없다. ( 즉, 물리적 장치도 확보해야 한다. )
    - 물리적 장치란, Alice가 사용하는 휴대폰이 될 수 있다.

---

### MFA 디바이스 옵션

- **가상 MFA 디바이스**
    - Google Authenticator 사용
        - 한 번에 하나의 휴대전화에서만 작동
    - Authy 사용
        - 다중 장치 가능
    - 각 장치에는 multiple 토큰을 지원한다.
    - 따라서, 가상 MFA 디바이스를 사용하면 루트 계정, IAM 사용자, 다른 계정 등 많은 사용자를 가질 수 있다.
- **Universal 2nd Factor(U2F)**
    - YubiKey
        - AWS가 제공하는 제 3자가 제공함
        - 여러 투트 및 사용자에게 단일 보안 키를 사용하여 지원한다.
- **Hardware Key Fob MFA**
    - 제 3자가 제공하는 Gemalto
- **AWS GovCloud**
    - 정부의 클라우드를 사용하는 경우
    - Key Fob (제 3자 제공)

---

### 암호 정책 설정

![image](https://user-images.githubusercontent.com/76610641/218316512-f555226f-bc16-47fc-ab4c-240d13f90615.png)

- 암호 정책 설정

### MFA 설정

- 루트 계정에 대한 MFA 설정

![image](https://user-images.githubusercontent.com/76610641/218316500-a30d5f30-dbdb-42e0-8ad7-d4ce6d70f110.png)

- 가상 MFA 머신
- UF2 security key
- 하드웨어 MFA 머신

---

### 사용자는 AWS에서 어떻게 접근할 수 있는가?

- 3가지 옵션
    - AWS Mangement Console (protected password + MFA)
    - AWS CLI (Command Line Interface) : protected by access key
        - 컴퓨터에서 설정 → 액세스 키로 보호된다.
        - 액세스 키는 우리가 다운로드할 자격증명이다.
        - 그리고 터미널에서 AWS에 액세스 한다.
    - AWS SDK (Software Development Kit) : AWS에서 애플리케이션 코드 내에서 API 호출할 때 사용, 액세스 키로 보호된다.
- 사용자는 자신의 액세스 키를 관리한다.
- 액세스 키는 비밀번호와 같이 비밀이기 때문에, 공유하면 안된다.
    - Access Key ID = username
    - Secret Access Key = password

![image](https://user-images.githubusercontent.com/76610641/218316491-3356fd36-b11f-4c1d-b836-9232003e4155.png)

- CLI에서 로드되면, AWS API에 액세스할 수 있다.
- CLI : 상호작용할 수 있는 도구, 명령을 사용하여 AWS 서비스 사용

![image](https://user-images.githubusercontent.com/76610641/218316475-36c0dd6d-7622-4770-85de-3517b51c011c.png)
---

### AWS SDK

- 다양한 프로그래밍 언어에 대한 액세스 관리
- 프로그래밍 방식으로 AWS 서비스 및 API를 코딩하는 애플리케이션 내에서 임베디드 된다.
- 따라서 애플리케이션은 AWS SDK가 있다.
    - 자바스크립트, 파이썬, PHP, 자바 등 많은 프로그래밍 언어가 지원한다.

---

![image](https://user-images.githubusercontent.com/76610641/218316459-d59f02e1-c8a8-41b3-82d8-2d5b3b295b6f.png)

- access key를 생성한다.
- CLI에서 aws configure를 입력하고, ID와 비밀번호를 입력한다.
- aws iam list-users

![image](https://user-images.githubusercontent.com/76610641/218316451-c59351b3-27eb-41a1-a85f-f17a47e75b18.png)
---

### AWS Cloud Shell

- 일부 영역에서 사용할 수 있다. (안되면 터미널 방식 사용하면 됨!)
- 무료로 사용할 수 있는 AWS 내의 터미널

---

### IAM Role

- 몇 개의 AWS 서비스는 사용자 대신 수행하는 것이 필요할 것이다.
- 이것을 수행하기 위해서는, IAM Role을 사용한 AWS 서비스에 대한 권한이 있어야 한다.
- 물리적인 사용자가 사용하는 것이 아니라, AWS 서비스에서 사용한다.
- **예시**
    
    ![image](https://user-images.githubusercontent.com/76610641/218316431-3a0541fe-90db-4239-89d5-cf842715f8b6.png)
    
    - EC2 인스턴스가 있다고 하자.
    - AWS에서 몇 가지 과정을 수행하기 위해 인스턴스에 권한을 부여해야 한다.
    - 따라서 IAM Role을 만들고, 하나의 실체를 만든다.
    - AWS 일부 정보에 액세스 하기 위해 IAM Role을 사용한다.
    - 만약, IAM Role에 할당된 권한이 맞다면 액세스가 가능해지게 된다.
- 예시 이외에도, Lambda 함수 역할, CloudFormation 등에서 사용될 수 있다.

---

### IAM Role 실습

![image](https://user-images.githubusercontent.com/76610641/218316418-a36dc6da-11b5-4710-b10d-e970878864b9.png)

- 신뢰할 수 있는 엔터티 유형을 선택한다.

![image](https://user-images.githubusercontent.com/76610641/218316406-c60b3cff-4625-4c9e-92d3-6dd6ed0cceba.png)

- AWS Service에 대한 것만 알면 된다.

![image](https://user-images.githubusercontent.com/76610641/218316366-3a8ade53-014f-42f7-b0a2-58661bb46d26.png)

- 대표적으로 EC2 또는 Lambda가 있고, 다른 서비스도 많다.
- EC2에 대한 Role을 만든다.

![image](https://user-images.githubusercontent.com/76610641/218316335-d89f7446-7454-42f9-844e-0a89299c4d36.png)

- 역할에 대한 정책을 할당한다.
- 이후 IAM Role을 생성한다.
- 따라서 EC2 인스턴스가 역할에 맞게 해당 작업을 수행하도록 허용해줄 수 있다.

---

### IAM Security Tools

- **IAM 자격증명 보고서** (계정 레벨)
    - 계정의 사용자와 다양한 증명 상태에 대한 보고서이다.
- **IAM Access Advisor** (사용자 레벨)
    - 사용자에게 부여된 서비스 권한을 볼 수 있고,
    - 해당 서비스에 마지막으로 액세스된 시간
    
    - 이것들은 최소 권한 원칙에서 매우 유용하다.
    - 이 도구를 이용하여 어떤 권한이 있는지 확인할 수 있다.
    - 만약 사용되지 않으면 권한을 줄일 수 있다.

---

### IAM 자격증명 보고서 작성

![image](https://user-images.githubusercontent.com/76610641/218316323-89fc5101-3ebd-4fe4-ac3a-03c9395ed582.png)

- 보고서 다운로드 클릭

![image](https://user-images.githubusercontent.com/76610641/218316313-9b336030-53fd-424c-9b27-c86d67855eb2.png)

---

### Access Advisor

![image](https://user-images.githubusercontent.com/76610641/218316300-f89d4712-5011-4f37-9169-95f42313f689.png)

- 위의 권한은 사용하지 않는 것을 확인할 수 있다.
- 따라서 사용자로부터 이러한 권한을 제거할 수 있다.

---

### IAM 가이드라인 및 모범 사례

- AWS 설정 이외는 루트 계정으로 AWS를 사용하지 않는다.
    - 루트 계정과 자신의 개인 계정이 필요하다.
- 한 명의 AWS 사용자는 한 명의 물리적 사용자와 동일하다는 점을 기억해야 한다.
    - 다른 사람이 사용하고자 한다면 User 계정을 주지말고, 다른 User를 하나 생성해준다.
- 그룹에 권한을 할당하여 사용자를 그룹에 할당할 수 있다.
- 강력한 암호 정책을 만든다.
- 다단계 인증(MFA - Multi Factor Authentication)을 이용하여 보안을 강화한다.
- 역할을 통해 AWS 서비스에 대한 권한을 부여한다.
- 프로그래밍적으로 액세스하기 위해 액세스 키를 사용한다. (AWS CLI/SDK)
- 권한을 감사하기 위해서는 계정 내에서 IAM 자격 증명 보고서를 사용하거나 사용자 수준에서 Access Advisor를 통해 최소 권한 원칙을 지킬 수 있다.
- IAM 사용자와 액세스 키를 절대 공유하면 안된다.

---

### 요약

Users : 물리적인 사용자와 연결되고, AWS 콘솔에 대한 password를 가지고 있다.

Groups : 오직 users만 포함할 수 있다.

Policies : JSON 문서를 통해 그룹 또는 사용자에게 권한을 부여할 수 있다.

Role : EC2 인스턴스 또는 AWS 서비스를 위한 것이다.

Security : MFA + Password Policy

Access Keys : AWS CLI 또는 SDK에 접근

Audit : IAM Credential Reports & IAM Access Advisor

---

### Quiz

- IAM 역할
    - AWS 서비스에 요청하기 위한 일련의 권한을 정의하고, AWS 서비스에서 사용할 IAM 엔터티
- 다음 중 IAM 보안 도구는 무엇입니까?
    - IAM 자격 증명 보고서
- IAM 사용자와 관련하여 **올바르지 않은** 답변은 무엇입니까?
    - IAM 사용자는 루트 계정 자격 증명을 사용하여 AWS 서비스에 액세스한다.
        - IAM 사용자는 자신의 자격 증명을 사용하여 AWS 서비스에 액세스한다.
- 다음 중 IAM 모범 사례는 무엇입니까?
    - 루트 사용자 계정을 사용하지 마십시오.
        - 루트 계정은 첫 번째 IAM 사용자와 몇 가지 계정 및 서비스 관리 작업 생성할 때만 사용!
        - 일상적인 경우, IAM 사용자를 사용하는게 좋다.
- IAM 정책이란?
    - AWS 서비스에 요청하기 위한 권한 집합을 정의하고 IAM 사용자, 사용자 그룹 및 IAM 역할에서 사용할 수 있는 JSON 문서
- IAM 권한과 관련하여 어떤 원칙을 적용해야 합니까?
    - 최소 권한 부여
- 루트 계정 보안을 강화하려면 어떻게 해야 할까?
    - MFA 활성화
- IAM 사용자 그룹은 IAM 사용자 및 기타 사용자 그룹을 포함할 수 있다.
    - IAM 사용자 그룹은 IAM 사용자만 포함할 수 있다.
- IAM 정책은 하나 이상의 Statement로 구성된다. IAM 정책의 Statement에서 제외되는 것은
    - Version
        - IAM 정책에서 Statement 문은 Sid, Effect, Principle, Action, Resource 및 Condition으로 구성된다.
        - Version은 Statement에 포함되는 것이 아니라 정책 자체의 일부이다.
