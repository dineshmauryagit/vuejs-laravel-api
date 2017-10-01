<template>
	<form>
		<div class="form-group">
			<label for="username">Username</label>
			<input type="text" id="username" name="username" v-model="username" class="form-control">
		</div>
		<div class="form-group">
			<label for="email">Email</label>
			<input type="email" id="email" name="email" v-model="email" class="form-control">
		</div>
		<div class="form-group">
			<label for="password">Password</label>
			<input type="password" id="password" name="password" v-model="password" class="form-control">
		</div>
		<button type="submit" class="btn btn-primary" @click.prevent="signup">Signup</button>
	</form>
</template>

<script>
	import axios from 'axios';

	export default {
		data(){
			return {
				username: '',
				email : '',
				password: ''
			}
		},
		methods: {
			signup() {
				axios.post('http://localhost/LAV/public/api/user', {name: this.username, email: this.email,password: this.password },
					{headers: {'X-Requested-With':'XMLHttpRequest'}
				})
				.then(
						(response) => console.log(response)
					)
				.catch(
						(error) => console.log(error)
					);
			}
		}
	}
</script>