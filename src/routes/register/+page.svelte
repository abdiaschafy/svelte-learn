<script>
  import { supabase } from "../../lib/supabaseClient";

  let loading = false;
  let email;
  let password;

  async function register() {
    const { user, error } = await supabase.auth.signUp({
      email: email,
      password: password,
    });
  }
</script>

<form class="row flex-center flex" on:submit|preventDefault={register}>
  <div class="col-6 form-widget">
    <h1 class="header">REGISTER</h1>
    <div>
      <input
        class="inputField"
        type="email"
        placeholder="Your email"
        bind:value={email}
      />
      <input
        class="inputField"
        type="password"
        placeholder="Your password"
        bind:value={password}
      />
    </div>
    <div>
      <input
        type="submit"
        class="button block"
        value={loading ? "Loading" : "Register"}
        disabled={loading}
      />
    </div>
  </div>
</form>
