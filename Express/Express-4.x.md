## Express 4.x 手册

> cookie

```

// Cookie: name=tj
req.cookies.name
// => "tj"

```

> body、query和params

```

// POST user[name]=tobi&user[email]=tobi@learnboost.com
req.body.user.name
// => "tobi"

// GET /search?q=tobi+ferret
req.query.q
// => "tobi ferret"

// /user/tobi for /user/:name 
req.param('name')
// => "tobi"

```

> path、baseUrl和originalUrl

```

app.use('/admin', function(req, res, next) {  // GET 'http://www.example.com/admin/new'
  console.log(req.originalUrl); // '/admin/new'
  console.log(req.baseUrl); // '/admin'
  console.log(req.path); // '/new'
  next();
});

```