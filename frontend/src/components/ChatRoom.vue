<template>
	<div class="chat-window">
		<div class="messages">
			<div class="message" v-for="message in messages" v-bind:key="message._id">
				<div class="username">{{ message.username }}</div>
				<div class="message-text">{{ message.msg }}</div>
			</div>
		</div>
		<form class="input-container" v-on:submit="sendMessage">
			<input type="text" v-model="msg">
			<button v-on:click="sendMessage" v-bind:disabled="!msg">Send</button>
		</form>
	</div>
</template>

<script>
export default {
	name: 'chatroom',
	props: ['messages'],
	data: function () {
		return {
			msg: ""
		}
	},
	methods: {
		sendMessage: function () {
			if (!this.msg) {
				alert("Please enter a message");
				return;
			}
			this.$emit('sendMessage', this.msg);
			this.msg = "";
		}
	}
}
</script>

<style lang="scss" scoped>
.chat-window {
	flex: 1;
	display: flex;
	flex-direction: column;
	background-color: #F9F9F9;

	.messages {
		flex: 1;
		overflow: scroll;
		font-size: 24px;

		.message {
			display: flex;
			border-bottom: 1px solid #EFEFEF;
			padding: 10px;

			&:last-of-type {
				border-bottom: none;
				border-color: #166BC8;
			}

			.username {
				color: #96B8FF;
				width: 100px;
				margin-right: 20px;
			}

			.message-text {
				font-family: 'Poppins';
				font-weight: normal;
				color: black;
				flex: 1;
				margin-left: 20px;
			}
		}
	}

	.input-container {
		display: flex;

		input {
			flex: 1;
			height: 35px;
			font-size: 24px;
			box-sizing: border-box;
		}

		button {
			font-family: 'Poppins';
			font-size: 16px;
			background-color: #A690E0;
			color: white;
			width: 75px;
			height: 35px;
			box-sizing: border-box;
		}
	}
}
</style>