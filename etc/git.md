# git



#### - Linux의 Alias(별칭) 을 이용하여 편리하게 명령어 사용하기

`git log --oneline --graph` 처럼 명령어를 입력하면 Log를 보기 좋게 출력할 수 있는데, 매번 이 명령어를 치기도 곤혹이다. 

Linux의 alias를 이용하여 특정 명령어를 별도의 키워드로 지정하여 간단하게 사용할 수 있는다.

- $ git config --global alias.**키워드** **'명령어'**



아래 예는 `git log --oneline --graph`를 `git logs`로 간단히 사용하게 하는 방법의 예이다.

```
junhobaik@Junho-Windows:/mnt/d/Development/scrum-board$ git config --global alias.logs 'log --oneline --graph'
junhobaik@Junho-Windows:/mnt/d/Development/scrum-board$ git logs
*   73a81d6 Merge branch 'dev'
|\
| * 6f75a02 Add memo features
| * b4de8c5 Modify bookmark localstorage name
| * 7fa5424 Modify styles
| * 86a5634 Add memo.js, add mvc layout
| * 3688670 Add memo script
| * 76e1478 Modify namespace name
| * bd6dbdd Add bookmark title
| * 4fbe5fb Add memo layout
* | 78addaa Update README.md
|/
* 328f641 Fix bookmark add bug
*   eb32dbc Merge branch 'dev'
|\
| * 84b0d77 Modify bookmark modal style
| * 4fc5a5c Modify bookmark bug fix
| * 5ac2c33 Modify bookmark modal message
| * 0a08125 Modify bookmark modal style
| * 9d88539 Modify bookmark.js, Remove Unused property
| * 34a6dd1 Refactoring bookmark.js
| * 57cdfc5 Add .gitignore
| * 1d1145b Modify bookmark, add drag sorting feature
| * 2b13a6a Add jQuery-ui
| * ebc5f98 Modify bookmark.js
| * a58d2ff Modift bookmark, add modify function
| * f0c1224 Modify Styles
| * 4cf5a2a Modify index.html, cdn -> local
| * c7d3110 Add Bootstrap local file
junhobaik@Junho-Windows:/mnt/d/Development/scrum-board$
```

