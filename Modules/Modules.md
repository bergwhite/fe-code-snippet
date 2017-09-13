## Modules 手册

> 多种模块化方案

```

require/module.exports  // CommonJS规范（Node模块）
import/export  // ES6标准

require.js=>AMD
sea.js=>CMD

```

> NodeJS（CommonJS）

```

// a.js

module.exports = {
	a: function(){},
	b: 'xxx'
}

// b.js

var m = require('./a')
m.a();

```

> ES6

```

// a.js

const obj = {
	a: function(){},
	b: 'xxx'
}
exports default obj

// b.js

import {a} from './a'
a()

```

> RequireJS（ADM）

```

// a.js
define('moduleA', function()){
  return {
  	a: function(){},
	b: 'xxx'
  }
}

// b.js
require(['moduleA'], function(a)){
	a.a()
}

```

> SeaJS（CMD）

```

// a.js
define(function(require,exports,module)){
	module.exports = {
		a: function(){},
		b: 'xxx'
	}
}

// b.js
define(function(require,exports,module)){
	var m = require('./a');
	m.a()
}

```