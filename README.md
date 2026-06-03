# Sandol Log Manager

산돌이 MSA 서비스들의 로그를 중앙에서 수집하고 모니터링하기 위한 Loki + Alloy + Grafana 구성입니다.

## 사용 방법

```bash
docker compose up -d
```

## 접속 정보

* Grafana: [http://localhost:3001](http://localhost:3001) (기본 ID/PW: admin / admin)
* Loki API: [http://localhost:3100](http://localhost:3100)

## 데이터 디렉터리 권한 주의

Loki가 `/var/lib/loki`에 쓸 수 있어야 정상 기동합니다.
bind mount를 사용할 때는 호스트 디렉터리 권한만 맞추는 것이 아니라,
Loki 컨테이너 실행 UID가 실제로 쓰기 가능한지도 확인해야 합니다.

예를 들어 Loki가 `UID 10001`로 실행되는 환경이라면:

```bash
mkdir -p /path/to/log-manager/loki
chown -R 10001:10001 /path/to/log-manager/loki
chmod -R 755 /path/to/log-manager
```

`mkdir /var/lib/loki/chunks: permission denied` 오류가 보이면,
대부분 bind mount된 Loki 데이터 디렉터리 권한 문제입니다.
