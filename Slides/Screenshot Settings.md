---
marp: true
size: 4:3
theme: default
class: invert
author: mk
---

# 스크린샷 옵션
---

# 스크린샷 저장 경로 변경
> ```~/ $ defaults write com.apple.screencapture location /Users/mk/Library/Mobile\ Documents/com\~apple\~CloudDocs/Screenshots```
---

# 스크린샷 저장 포맷 변경
> ```defaults write com.apple.screencapture type png```
- bmp, gif, jpg, jp2, tiff, pdf, pict, png, tga
---

# 스크린샷 파일 이름 접두어 변경
> ```$ defaults write com.apple.screencapture name "zs"```
---

# 스크린샷 파일 이름에서 날짜/시간 제거
> ```$ defaults write com.apple.screencapture "include-date" 0```

.ref 스크린샷 파일 이름 날짜 포맷 변경
> ```Mac OS X / System Preferences / Language & Region / 24-Hour Time```
---

# 그림자 사용 안 함
> ```$ defaults write com.apple.screencapture disable-shadow -bool true```
---

# 시스템 UI 서버 재실행
> ```$ killall SystemUIServer```
---
