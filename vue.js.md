

### dynamic component

```is``` 프로퍼티 설정 값으로 랜더링될 컴포넌트를 동적으로 교체할 수 있다.

```html
<component v-bind:is="compName"></component>
```

```is``` 프로퍼티가 변경될 때마다 매번 새로 생성한다. ```<keep-alive>``` 컴포넌트로 감싸주면 생성된 동적 컴포넌트를 캐쉬하여 매번 재생성되지 않게 할 수 있다.

```html
<keep-alive>
    <component v-bind:is="compName"></component>
</keep-alive>
```

