<script>
  import { Router, Link, Route } from 'svelte-routing';
  import { getContext } from 'svelte';
  import { ROUTER } from 'svelte-routing/src/contexts';

  const { activeRoute } = getContext(ROUTER);

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === '/' ? isCurrent : isPartiallyCurrent || isCurrent;

    // The object returned here is spread on the anchor element's attributes
    if (isActive) {
      return { class: 'router-link-active' };
    }
    return {};
  }
</script>

<nav class="column is-2 menu">
  <p class="menu-label">Menu</p>
  <ul class="menu-list">
    <Link to="/heroes" {getProps}>Heroes</Link>
    <Link to="/villains" {getProps}>Villains</Link>
    <Link to="/about" {getProps}>About</Link>
  </ul>
</nav>
