<script>
  import { Router, Route } from "svelte-navigator";
  import Layout from "./components/Layout.svelte";
  import Home from "./pages/Home.svelte";
  import Login from "./pages/Login.svelte";
  import Profile from "./pages/Profile.svelte";
</script>

<Router>
  <div>
    <Route path="/">
      <Layout>
        <Home />
      </Layout>
    </Route>
    <Route path="profile">
      <Layout>
        <Profile />
      </Layout>
    </Route>
    <Route path="login">
      <Login />
    </Route>
  </div>
</Router>
