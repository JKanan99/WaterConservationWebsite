<script>
  import { Auth } from "@supabase/auth-ui-svelte";
  import { ThemeSupa } from "@supabase/auth-ui-shared";

  import { browser } from '$app/environment';
	import { goto } from '$app/navigation';
	import { page } from '$app/stores';

	export let data
	$: {
		const redirectTo = $page.url.searchParams.get('redirect');

		// check if user has been set in session store then redirect
		if (browser && data.session) {
			goto(redirectTo ?? '/dashboard');
		}
	}
</script>

<svelte:head>
  <title>Login</title>
  <meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="form">
  <header>Log in</header>

  <Auth
    supabaseClient={data.supabase}
    view="sign_in"
    redirectTo={`${data.url}/logging-in?redirect=/`}
    showLinks={false}
    appearance={{
      theme: ThemeSupa,
      style: {
        input: `height: 50px;
          width: 100%;
          border: none;
          display: block;
          box-sizing: border-box;
          font-size: 16px;
          font-weight: 400;
          border-radius: 6px;
          background: #eeeeee;
        `,
        button: `height: 50px;
          width: 100%;
          border: none;
          display: block;
          box-sizing: border-box;
          font-size: 16px;
          font-weight: 400;
          border-radius: 6px;
          background-color: #00ace5;
        `,
      },
    }}
  />

  <div class="form-link">
    <span>
      Don't have an account?{" "}
      <a class="link signup-link" href="/signup">Sign up!</a>
    </span>
  </div>

  <div class="form-link">
    <a href="/forgot_password" class="forgot-pass">Forgot your password?</a>
  </div>
</section>

<style>
  .forms {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
  .form {
    max-width: 430px;
    width: 100%;
    padding: 30px;
    border-radius: 3px;
    background: #f9f8f6;
    opacity: 0.95;
  }

  header {
    font-size: 28px;
    font-weight: 600;
    color: #232836;
    text-align: center;
    margin-bottom: 2rem;
  }
  form {
    margin-top: 30px;
  }
  .form .field {
    position: relative;
    height: 50px;
    width: 100%;
    margin-top: 20px;
    border-radius: 6px;
  }

  .field input,
  .field button {
    height: 50px;
    width: 100%;
    border: none;
    display: block;
    box-sizing: border-box;
    font-size: 16px;
    font-weight: 400;
    border-radius: 6px;
    background: #eeeeee;
    transition: background 0.2s, border-color 0.5s;
  }
  .field input {
    padding: 0 15px;
    border: 1px solid #dddddd;
  }
  .field input:focus {
    border-bottom-width: 2px;
  }
  .field button {
    color: #fff;
    background-color: #006d8f;
    transition: all 0.4s ease;
    cursor: pointer;
    width: 99%;
    font-weight: bold;
    outline: none;
  }
  .field button:hover {
    background-color: #00ace5;
  }
  .form-link span .link {
    background-color: none;
  }
  .form-link {
    text-align: center;
    margin-top: 10px;
  }
  .form-link span,
  .form-link a {
    font-size: 14px;
    font-weight: 400;
    color: #232836;
  }
  .form a {
    color: #0061ff;
    text-decoration: none;
  }
  /*.form-content a:hover {
    text-decoration: underline;
    text-decoration-style: wavy;
    text-decoration-color: #0061ff;
  }*/
</style>
