<!DOCTYPE html>
<html>
<head>
	<title>JavaScript Chat Application</title>
	<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script src="https://cdn.socket.io/4.3.2/socket.io.min.js"></script>
</head>
<body>
	<h1>JavaScript Chat Application</h1>
	<div id="messages"></div>
	<input type="text" id="message" placeholder="Type your message">
	<button id="send">Send</button>

	<script>
		// connect to the server
		const socket = io('http://localhost:3000');

		// handle incoming messages
		socket.on('message', (data) => {
			$('#messages').append($('<p>').text(data));
		});

		// handle sending messages
		$('#send').click(() => {
			const message = $('#message').val();
			socket.emit('message', message);
			$('#message').val('');
		});
	</script>
</body>
</html>
