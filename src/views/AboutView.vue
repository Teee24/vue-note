<template>
  <div class="about">
    <h1>This is an about page</h1>
    <ul>
      <li>
        <RouterLink to="/">回首頁</RouterLink>
      </li>
      <li>
        <RouterLink to="/template">0_模板語法</RouterLink>
      </li>
      <li>
        <RouterLink to="/declarative">01DeclarativeView</RouterLink>
      </li>
      <li>
        <RouterLink to="/attribute">02AttributeBindingView</RouterLink>
      </li>
      <li>
        <RouterLink to="/eventlistener">03EventListenersView</RouterLink>
      </li>
      <li>
        <RouterLink to="/formbinding">04FormBindingsView</RouterLink>
      </li>
      <li>
        <RouterLink to="/conditionalrender">05ConditionalRenderingView</RouterLink>
      </li>
      <li>
        <RouterLink to="/listrendering">06ListRendering</RouterLink>
      </li>
      <li>
        <RouterLink to="/computedproperty">07計算屬性</RouterLink>
      </li>
      <li>
        <RouterLink to="/computed">07-1計算屬性緩存vs 方法</RouterLink>
      </li>
      <li>
        <RouterLink to="/lifecycletemplate">08生命週期和模板引用</RouterLink>
      </li>
    </ul>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
