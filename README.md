# InvestPulse (빅테크 투자 추적기) 📈

InvestPulse는 미국 주요 빅테크 기업(Nvidia, Google, Meta, Microsoft, Apple 등)의 최신 투자 및 M&A 소식을 실시간으로 추적하고, 관련 기업의 주가 차트와 기술적 지표를 분석하여 제공하는 대시보드 애플리케이션입니다.

## 🚀 주요 기능

### 1. 빅테크 투자 뉴스 분석
- **Gemini AI 통합**: Google의 최신 Gemini AI 모델을 활용하여 방대한 뉴스 데이터에서 빅테크 기업의 상장사 투자 및 인수 소식을 정밀하게 추출합니다.
- **실시간 동기화**: 'Sync' 버튼을 통해 최신 딜(Deal) 정보를 즉시 업데이트할 수 있습니다.

### 2. 고성능 주가 차트
- **기술적 지표 제공**:
  - **이동평균선(MA)**: 20일(단기), 60일(중기), 120일(장기) 라인을 제공하여 추세 파악을 돕습니다.
  - **RSI(상대강도지수)**: 과매수/과매도 구간을 파악하기 위한 RSI(14) 지표를 하단 보조 차트에 표시합니다.
- **커스텀 툴팁**: 차트 위 마우스 오버 시 120선, 60일선, 20일선, 현재 주가 순으로 정렬된 상세 데이터를 한눈에 확인할 수 있습니다.

### 3. 스마트 매수 신호 (1차 매수 추천)
- **역배열 과매도 탐색**: 하락 추세 중 기술적으로 반등 가능성이 높은 구간을 자동으로 포착합니다.
- **추천 로직**:
  1. **역배열 상태**: 120일선 > 60일선 > 20일선 순으로 위치 (하락 추세)
  2. **가격 위치**: 현재가가 20일 이동평균선보다 아래에 위치 (단기 과매도)
- **시각적 알림**: 조건 충족 시 차트 우측 상단에 애니메이션 배지가 표시되어 직관적인 의사결정을 지원합니다.

## 🌐 GitHub Pages 배포 방법

이 프로젝트는 GitHub Actions를 통해 자동으로 GitHub Pages에 배포되도록 설정되어 있습니다.

1. **GitHub Secrets 설정**:
   - GitHub 저장소의 **Settings > Secrets and variables > Actions**로 이동합니다.
   - `New repository secret`을 클릭하고 이름은 `GEMINI_API_KEY`, 값은 사용자님의 Gemini API 키를 입력합니다.
2. **GitHub Pages 활성화**:
   - 첫 배포(Push)가 완료된 후, **Settings > Pages**로 이동합니다.
   - `Build and deployment > Branch`에서 `gh-pages` 브랜치를 선택하고 저장합니다.
3. **확인**:
   - 잠시 후 `https://사용자계정.github.io/investpulse/` 주소에서 앱을 확인할 수 있습니다.

## 🛠 Tech Stack

- **Frontend**: React 19, TypeScript, Vite
- **Styling**: Tailwind CSS 4, Framer Motion (motion/react)
- **Charts**: Recharts
- **AI**: @google/genai (Gemini 3 Flash)
- **Icons**: Lucide React

## 📦 설치 및 실행 방법

### 1. 저장소 클론
```bash
git clone https://github.com/사용자계정/investpulse.git
cd investpulse
```

### 2. 의존성 설치
```bash
npm install
```

### 3. 환경 변수 설정
`.env` 파일을 생성하고 Gemini API 키를 설정합니다.
```env
GEMINI_API_KEY=your_api_key_here
```

### 4. 개발 서버 실행
```bash
npm run dev
```

## 📊 기술적 세부 사항

### 이동평균선 계산 (MA)
```typescript
function calculateMA(prices: number[], period: number) {
  // 지정된 기간 동안의 종가 평균을 계산하여 추세선을 생성합니다.
}
```

### 매수 신호 로직
```typescript
const isBuySignal = last.ma120 > last.ma60 && 
                   last.ma60 > last.ma20 && 
                   last.price < last.ma20;
```

## 📄 라이선스
이 프로젝트는 Apache-2.0 라이선스를 따릅니다.

---
**InvestPulse** - 빅테크의 움직임을 가장 먼저 포착하세요.
