<template>
  <div>
    <!-- Wrapper Section for spacing -->
    <div class="bg-white py-16">
      <div class="container mx-auto px-4 lg:flex lg:items-center lg:justify-center">
        <!-- Main Content Section -->
        <div class="lg:w-1/2">
          <section :class="['wrapper', isLoginActive ? 'active' : '']">
            <!-- Signup Form -->
            <div class="form signup">
              <header @click="toggleForm(false)">Signup</header>
              <form @submit.prevent="handleSignup">
                <input
                  type="text"
                  placeholder="Full name"
                  v-model="signupData.name"
                  required
                />
                <input
                  type="email"
                  placeholder="Email address"
                  v-model="signupData.email"
                  required
                />
                <input
                  type="password"
                  placeholder="Password"
                  v-model="signupData.password"
                  required
                />
                <div class="checkbox">
                  <input
                    type="checkbox"
                    id="signupCheck"
                    v-model="signupData.terms"
                  />
                  <label for="signupCheck">I accept all terms & conditions</label>
                </div>
                <input type="submit" value="Signup" />
              </form>
            </div>

            <!-- Login Form -->
            <div class="form login">
              <header @click="toggleForm(true)">Login</header>
              <form @submit.prevent="handleLogin">
                <input
                  type="email"
                  placeholder="Email address"
                  v-model="loginData.email"
                  required
                />
                <input
                  type="password"
                  placeholder="Password"
                  v-model="loginData.password"
                  required
                />
                <a href="#">Forgot password?</a>
                <input type="submit" value="Login" />
              </form>
            </div>
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoginActive: false,
      signupData: {
        name: "",
        email: "",
        password: "",
        terms: false,
      },
      loginData: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    toggleForm(isLogin) {
      this.isLoginActive = isLogin;
    },
    handleSignup() {
      if (this.signupData.terms) {
        alert(`Signup Successful!\nName: ${this.signupData.name}`);
      } else {
        alert("Please accept the terms & conditions!");
      }
    },
    handleLogin() {
      alert(`Login Successful!\nEmail: ${this.loginData.email}`);
    },
  },
};
</script>

<style scoped>
/* Import Google font - Poppins */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f0faff;
}

.bg-white {
  background-color: #ffffff;
}

.py-16 {
  padding-top: 4rem;
  padding-bottom: 4rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.wrapper {
  position: relative;
  max-width: 470px;
  width: 100%;
  border-radius: 12px;
  padding: 20px 30px 120px;
  background: #4070f4;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.form.login {
  position: absolute;
  left: 50%;
  bottom: -86%;
  transform: translateX(-50%);
  width: calc(100% + 220px);
  padding: 20px 140px;
  border-radius: 50%;
  height: 100%;
  background: #fff;
  transition: all 0.6s ease;
}

.wrapper.active .form.login {
  bottom: -15%;
  border-radius: 35%;
  box-shadow: 0 -5px 10px rgba(0, 0, 0, 0.1);
}

.form header {
  font-size: 30px;
  text-align: center;
  color: #fff;
  font-weight: 600;
  cursor: pointer;
}

.form.login header {
  color: #333;
  opacity: 0.6;
}

.wrapper.active .form.login header {
  opacity: 1;
}

.wrapper.active .signup header {
  opacity: 0.6;
}

.wrapper form {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 40px;
}

form input {
  height: 60px;
  outline: none;
  border: none;
  padding: 0 15px;
  font-size: 16px;
  font-weight: 400;
  color: #333;
  border-radius: 8px;
  background: #fff;
}

.form.login input {
  border: 1px solid #aaa;
}

.form.login input:focus {
  box-shadow: 0 1px 0 #ddd;
}

form .checkbox {
  display: flex;
  align-items: center;
  gap: 10px;
}

.checkbox input[type="checkbox"] {
  height: 16px;
  width: 16px;
  accent-color: #fff;
  cursor: pointer;
}

form .checkbox label {
  cursor: pointer;
  color: #fff;
}

form a {
  color: #333;
  text-decoration: none;
}

form a:hover {
  text-decoration: underline;
}

form input[type="submit"] {
  margin-top: 15px;
  padding: none;
  font-size: 18px;
  font-weight: 500;
  cursor: pointer;
}

.form.login input[type="submit"] {
  background: #4070f4;
  color: #fff;
  border: none;
}
</style>
