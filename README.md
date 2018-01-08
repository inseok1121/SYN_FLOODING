# SYN FLOODING

### TCP 3-Way HandShake

> #### TCP/IP 프로토콜을 이용하는 통신을 하기 전에 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미함

```C
Sequence

Client->Server: TCP SYN
Server->Client: TCP SYN ACK
Client->Server: TCP ACK
```

> SYN : synchronize sequence numbers
> ACK : acknowledgment

**STEP 1** : **Client**는 Server에 **접속을 요청하는 SYN 패킷**을 보낸다.

**STEP 2** : **Server**는 SYN 요청을 받고 Client에게 요청을 수락한다는 **ACK와 SYN flag가 설정된 패킷을 발송**하고 
​			A가 다시 ACK으로 응답하기를 기다린다.

**STEP 3** : **Client**는 Server에게 **ACK**를 보내고 이후로 부터는 연결이 이루어지고 데이터가 오가게 된다.

------

SYN Flooding : Server에 **SYN 패킷을 지속적으로 보내 Server를 마비**시키는 공격 기법

![synflooding](https://github.com/inseok1121/images/blob/master/synflooding.png?raw=true)

- Server는 수신한 **각 SYN에 대해 자신의 연결 테이블에 입력**을 하고 **각 메시지에 SYN-ACK 메시지로 응답**을 한다. 
- 그러면 공격자는 ACK 메시지를 보내지 않거나 여러 차례 보내고 SYN 패킷에서 **Client IP 주소를 Spoofing**해서 대상 서버가 ACK **응답을 수신하지 못하게** 한다. 
- 그러면 Server는 SYN-ACK 대기 상태에서 벗어나질 못하며 **서비스 거부**라는 결과를 낳게 된다.