<script>
  import { Link } from "svelte-navigator";
</script>

<div>
  <header>
    <Link to="/">Home</Link>
    <Link to="/profile">Profile</Link>
    <Link to="/login">Login</Link>
  </header>
  <main>
    <aside>Sidebar</aside>

    <slot />
  </main>
</div>
