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
