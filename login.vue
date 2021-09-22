<template>
	<div class="container">
		<h1>Please Login</h1>
		<form>
			<div class='form-control'>
				<input type="text" required />
				<label>
					<span style="transition-delay: 0ms">E</span>
					<span style="transition-delay: 50ms">m</span>
					<span style="transition-delay: 100ms">a</span>
					<span style="transition-delay: 150ms">i</span>
					<span style="transition-delay: 200ms">l</span>
				</label>
			</div>
			<div class='form-control'>
				<input type="password" required />
				<label>
					<span style="transition-delay: 0ms">P</span>
					<span style="transition-delay: 50ms">a</span>
					<span style="transition-delay: 100ms">s</span>
					<span style="transition-delay: 150ms">s</span>
					<span style="transition-delay: 200ms">w</span>
					<span style="transition-delay: 250ms">o</span>
					<span style="transition-delay: 300ms">r</span>
					<span style="transition-delay: 350ms">d</span>
				</label>
			</div>
			<button class='btn'>btn</button>
			<p class='text'>Don't have an account?
				<a href="#">Register</a>
			</p>
		</form>
	</div>
</template>

<script>
	export default {
		name: 'Login',
	}
</script>

<style scoped lang='scss'>
	.container {
		padding: 20px 40px;
		border-radius: 0 0 5px 5px;
		background: steelblue;
		color: white;
		font-family: sans-sserif;

		h1 {
			text-align: center;
			margin-bottom: 30px;
		}

		.btn {
			cursor: pointer;
			width: 100%;
			background-color: lightblue;
			padding: 15px;
			border: 0;
			font-size: 16px;
			font-family: inherit;
			border-radius: 10px;

			&:focus {
				outline: 0;
			}

			&:active {
				transform: scale(0.98);
			}
		}

		.text {
			margin-top: 30px;

			a {
				text-decoration: none;
				color: lightblue
			}
		}

		.form-control {
			width: 300px;
			margin: 20px 0 40px;
			position: relative;

			input {
				background-color: transparent;
				border: 0;
				border-bottom: 2px solid white;
				display: block;
				width: 100%;
				padding: 15px 0;
				font-size: 18px;
				color: white;

				&:focus {
					outline: 0;
					border-bottom-color: lightblue;
				}

				&:valid {
					outline: 0;
					border-bottom-color: lightgreen;
				}
			}

			label {
				position: absolute;
				left: 0;
				top: 15px;

				span {
					display: inline-block;
					font-size: 18px;
					margin: 0;
					transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
				}
			}

			input:focus+label span,input:valid+label span {
				transform: translateY(-30px);
				color: lightblue
			}
		}
	}
</style>
