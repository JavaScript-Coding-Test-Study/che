# 백준에서 javascript 사용하기

백준 사이트는 자바스크립트 언어를 사용하기위해서는 node.js 를 통해서 입출력을 받아야한다.

입출력을 받기위해서 두가지 방법이있는데  

**1. readline 모듈**  
**2. fs 모듈** 

시간 효율성을 따지자면 fs 모듈이 더빠르다고 한다.

## fs모듈 불러오기
fs 모듈은 Node.js에 내장되어 있어 있기 때문에 별도의 라이브러리 설치없이 바로 불러와서 사용할 수 있다.  
CommonJS 모듈 시스템을 사용하는 프로젝트에서는 require 키워드로 불러오고,  
ES 모듈 시스템을 사용하는 프로젝트에서는 import 키워드를 사용할 수 있다.

```
// CommonJS Modules
const fs = require("fs");

// ES Modules
import fs from "fs";
```
## 백준 도움말(fs모듈)

백준도움말에 보면  위 코드를 기본으로 제공한다.  
간단하게 설명하자면 /dev/stdin 경로에 있는 값을 문자열로 만들고 split 메서드로 배열로 쪼갠뒤 입력값을 저장하고   
저장된 입력값을 알맞게 가공하는 코드이다.  
```
var fs = require('fs');
var input = fs.readFileSync('/dev/stdin').toString().split(' ');
var a = parseInt(input[0]);
var b = parseInt(input[1]);
console.log(a + b);
```

## fs모듈로 문제풀기
```
// 1. 하나의 값을 입력받을 때
const input = require('fs').readFileSync('/dev/stdin').toString().trim();

// 2. 공백으로 구분된 한 줄의 값들을 입력받을 때
const input = require('fs').readFileSync('/dev/stdin').toString().trim().split(' ');

// 3. 여러 줄의 값들을 입력받을 때
const input = require('fs').readFileSync('/dev/stdin').toString().trim().split('\n');

// 4. 첫 번째 줄에 자연수 n을 입력받고, 그 다음줄에 공백으로 구분된 n개의 값들을 입력받을 때
const [n, ...arr] = require('fs').readFileSync('/dev/stdin').toString().trim().split(/\s/);

// 5. 첫 번째 줄에 자연수 n을 입력받고, 그 다음줄부터 n개의 줄에 걸쳐 한 줄에 하나의 값을 입력받을 때
const [n, ...arr] = require('fs').readFileSync('/dev/stdin').toString().trim().split('\n');

// 6. 하나의 값 또는 공백으로 구분된 여러 값들을 여러 줄에 걸쳐 뒤죽박죽 섞여서 입력받을 때
// ex) n 입력 - 공백으로 구분된 n개의 값 입력 - m 입력 - 여러 줄에 걸쳐 m개의 값 입력
const input = require('fs').readFileSync('/dev/stdin').toString().trim().split(/\s/);
const n = input[0];
const n_arr = input.slice(1, n+1);
const [m, ...m_arr] = input.slice(n+1);

// 2~6에서 입력받는 값들을 모두 String에서 Number로 바꾸려면 split()뒤에 .map(v => +v)를 추가
```

## 참고
https://jaehyun2yo.tistory.com/17  
https://www.daleseo.com/js-node-fs/
