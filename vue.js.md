

### dynamic component

```is``` 프로퍼티 설정 값으로 랜더링될 컴포넌트를 동적으로 교체할 수 있다.

```html
<component v-bind:is="compName"></component>

<script>
    export default {
        components: { UserInfo, CompanyInfo },
        props: { isCompany: Boolean }
        computed: {
            compName() {
                return this.isCompany ? 'company-info', 'user-info'
            }
        }
    }
```

```is``` 프로퍼티가 변경될 때마다 매번 새로 생성한다. ```<keep-alive>``` 컴포넌트로 감싸주면 생성된 동적 컴포넌트를 캐쉬하여 매번 재생성되지 않게 할 수 있다.

```html
<keep-alive>
    <component v-bind:is="compName"></component>
</keep-alive>
```

### dynamic imports + &lt;component> 

`component` 의 `:is` 프로퍼티는 콤포넌트 명 또는 콤포넌트의 옵션 오브젝트를 사용할 수 있다. 

```html
<component v-bind:is="compObject"></component>

<script>
    export default {
        props: { isCompany: Boolean }
        computed: {
            compObject() {
                const compName = isCompany ? 'CompanyInfo' : 'UserInfo'
                return () => import(`./components/${compName}`)
            }
        }
    }
```
> 주의사항 : 동적 `import`를 사용할 경우, Webpack 은 `import` 함수내의 표현식과 일치하는 모든 파일에 대해서 청크 파일을 생성한다.

### Router

> NavigationDuplicated

* https://github.com/vuejs/vue-router/issues/2872

`$router.push` 로 동일한 `path` 를 전달할 경우 `NavigationDuplicated` 에러가 발생한다. 이 에러가 보기 싫으면 아래와 같이 처리한다.

```javascript
router.push('/location').catch(err => {})
```

또는 아래처럼 현재 `router` 의 `path` 와 다른 경우에만 `push`를 사용하는 방법도 있다.

```javascript
const path = `/products/${id}`
if (this.$route.path !== path) this.$router.push(path)
```
    
> 결정적으로 Vue-Router 는 path 가 변경되지 않으면 받아주질 않도록 되어 있다. 꼼수로는 router-view 에 :key 를 바인딩 시키고 :key 속성을 변경시켜서 DOM 에서 제거시키는 방법이 있는데... IE 에선 껌뻑이기도 하고 그다지 좋아보이지는 않는다.

