<script>
  import { user } from "$lib/sessionStore";
  import { supabase } from "$lib/supabaseClient";

  import login from "../routes/login/+page.svelte";
  import profile from "../routes/profile/+page.svelte";

  user.set(supabase.auth.user());

  supabase.auth.onAuthStateChange((_, session) => {
    user.set(session.user);
  });
</script>
