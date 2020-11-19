## v-if 와 v-show의 차이
###
#### v-if는 조건에 따라 컴포넌트가 실제로 생성도고 제거된다.
#### 반면에 v-show는 단순히 cssd의 display 속성이 변경되는 것이다.

## v-show의 활용은 이와 같을 수 있다.
##### -template-
#####   -div- id="app"
#####     -h1-글을 입력해야만 버튼이 보입니다.-/h1-
#####     -textarea- v-model="message"-textarea-
#####     -button- v-show="message"제출-/button-
#####   -/div-
##### -/template

##### -script-
#####   export default {
#####     name: 'app',
#####     data() {
#####       return {
#####         message: '글을 입력했다!'
#####       }
#####     }
#####   }
##### -/script-
## 글을 입력하지 않으면 보이지 제출 버튼이 보이지 않는다.
## 그러나, 글을 입력하면 제출버 버튼이 보이게 된다.
