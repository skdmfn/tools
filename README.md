import streamlit as st

# 웹앱 제목
st.title("📎 생활 속 도우미 웹앱")

# -----------------------------
# 1. 문장 / 단어 / 글자 수 분석기
# -----------------------------
st.header("1️⃣ 문장 / 단어 / 글자 수 분석기")

# 사용자로부터 텍스트 입력 받기
text = st.text_area("분석할 문장을 입력하세요:")

if text:
    # 문장 수: 마침표, 느낌표, 물음표 기준으로 간단 추정
    sentence_count = text.count('.') + text.count('!') + text.count('?')
    # 단어 수: 공백 기준으로 나눈 개수
    word_count = len(text.split())
    # 글자 수: 공백 제외
    char_count = len(text.replace(" ", ""))

    # 결과 출력
    st.success("📊 분석 결과")
    st.write(f"- 문장 수: {sentence_count}")
    st.write(f"- 단어 수: {word_count}")
    st.write(f"- 글자 수 (공백 제외): {char_count}")

# -----------------------------
# 2. 온도 변환기
# -----------------------------
st.header("2️⃣ 온도 변환기 (섭씨 ↔ 화씨)")

# 사용자 입력: 온도 값
temperature = st.number_input("온도를 입력하세요:", step=0.1)

# 사용자 선택: 변환 방향
conversion = st.radio("변환할 방향을 선택하세요:", ("섭씨 → 화씨", "화씨 → 섭씨"))

# 변환 결과 계산
if conversion == "섭씨 → 화씨":
    result = (temperature * 9/5) + 32
    st.write(f"🌡️ 변환 결과: {result:.2f} ℉")
else:
    result = (temperature - 32) * 5/9
    st.write(f"🌡️ 변환 결과: {result:.2f} ℃")
