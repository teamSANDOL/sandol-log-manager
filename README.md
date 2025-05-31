# Sandol Log Manager

산돌이 MSA 서비스들의 로그를 중앙에서 수집하고 모니터링하기 위한 Loki + Promtail + Grafana 구성입니다.

## 사용 방법

```bash
docker compose up -d
````

## 접속 정보

* Grafana: [http://localhost:3001](http://localhost:3001) (기본 ID/PW: admin / admin)
* Loki API: [http://localhost:3100](http://localhost:3100)
