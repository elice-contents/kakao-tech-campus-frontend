## 1. 프론트엔드 배포 (S3)

### 1-1. index.html 준비

별도로 제공된 프론트엔드 레포지토리를 로컬에 클론합니다.

```bash
git clone https://github.com/<FRONTEND_REPO>.git
```

### 1-2. index.html 수정

클론한 레포의 `index.html` 내 `API_BASE_URL`을 EC2 퍼블릭 IP로 변경합니다.

```javascript
// 변경 전
const API_BASE_URL = "http://localhost:8000";
<img width="1205" height="640" alt="html-image" src="https://github.com/user-attachments/assets/09cf034d-3151-47cb-a335-6a310ebe6762" />

// 변경 후
const API_BASE_URL = "http://<EC2_PUBLIC_IP>:8000";
```

### 1-3. S3 버킷 생성

1. AWS 콘솔 → S3 → **버킷 만들기**
2. 버킷 이름 입력 
3. **퍼블릭 액세스 차단 → 4개 항목 모두 비활성화**

### 1-4. 정적 웹 호스팅 활성화

1. 버킷 → **속성** 탭 → 정적 웹 사이트 호스팅 → 편집
2. **활성화** 선택
3. 인덱스 문서: `index.html`


### 1-5. 파일 업로드

AWS 콘솔에서 `index.html`을 직접 업로드합니다.

### 1-6. 접속 URL 확인

```
http://YOUR_BUCKET_NAME.s3-website-<REGION>.amazonaws.com
```

---
