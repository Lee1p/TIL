### 1.Git 폴더 생성
```
git init
```
폴더에 .git 폴더 생성 확인 (숨김파일일)


### 2. Git 이름과 이메일 주소 설정
```
git config --global user.name "본인닉네임"

git config --global user.email "본인이메일"
```

### 3. Git 설정 확인
```
git config --global user.name
git config --global user.email
```

### 4. Git 상태 확인

-- 조건: GitHub와 연결 추가하거나 또는 새로운 파일 생성 후

```
git status
```

### 5. 첫 번째 커밋
```
5-1 파일을 추가
git add .

5-2 커밋밋
git commit -m "Initial commit"

5-3 커밋 후 원격 저장소에 푸시시
git push -u origin master
```

