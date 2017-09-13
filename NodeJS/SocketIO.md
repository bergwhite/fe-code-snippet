> 安装

```

npm install socket.io

```

> Express 3/4(Server)

```


var app = require('express')();
var server = require('http').Server(app);
var io = require('socket.io')(server);

server.listen(80);

app.get('/', function (req, res) {
  res.sendFile(__dirname + '/index.html');
});

io.on('connection', function (socket) {
  socket.emit('news', { hello: 'world' });
  socket.on('my other event', function (data) {
    console.log(data);
  });
});

```

> Express 3/4(Client)

```


<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io.connect('http://localhost');
  socket.on('news', function (data) {
    console.log(data);
    socket.emit('my other event', { my: 'data' });
  });
</script>

```

> 连接监听

```

io.on('connection', function (socket) {
  socket.emit('user connected')
})

```

> 断开监听

```

socket.on('disconnect', function() {
  console.log('One is gone.')
})

```

> 加入房间

```

socket.join(rooms[, callback])

```

> 离开房间

```

socket.leave(room[, callback])

```

> 向指定房间发送消息

```

socket.to(room)
socket.to('others').emit('an event', { some: 'data' });
socket.to('room1').to('room2').emit('hello');

```

> 向除自己以外的所有人发送广播

```

io.on('connection', function (socket) {
  socket.broadcast.emit('user connected')
})

```

> query参数

```

socket.handshake.query.token;

```

> API

```

  // 发送给发起请求的用户
  socket.emit('hello', 'can you hear me?', 1, 2, 'abc');

  // 全局广播（除发送者）
  socket.broadcast.emit('broadcast', 'hello friends!');

  // 发送给所有在game房间的（除发送者）
  socket.to('game').emit('nice game', "let's play a game");

  // 发送给所有在game1/game2房间的（除发送者）
  socket.to('game1').to('game2').emit('nice game', "let's play a game (too)");

  // 发送给所有在game房间的（包括发送者）
  io.in('game').emit('big-announcement', 'the game will start soon');

  // 发送给所有在myNamespace命名空间的（包括发送者）
  io.of('myNamespace').emit('bigger-announcement', 'the tournament will start soon');

  // 发送给个人的socketid（私聊）
  socket.to(<socketid>).emit('hey', 'I just met you');

  // sending with acknowledgement
  socket.emit('question', 'do you think so?', function (answer) {});

  // 发送时不压缩
  socket.compress(false).emit('uncompressed', "that's rough");

  // sending a message that might be dropped if the client is not ready to receive messages
  socket.volatile.emit('maybe', 'do you really need it?');

  // sending to all clients on this node (when using multiple nodes)
  io.local.emit('hi', 'my lovely babies');

```