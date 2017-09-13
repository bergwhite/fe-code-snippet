> require

```

var db = mongoose.connect('mongodb://localhost/nodejsChat');
var mongoose = require('mongoose');
var Schema = mongoose.Schema;

var userScheme = new Schema({
  name: String,
  pass: String
});

var userModel = db.model('users', dbScheme.userScheme)

var userSave = new userModel({
	name: 'a',
	pass: 'b'
})

userSave.save()

```

> update

```

PersonModel.findById(id,function(err,person){
      person.name = 'MDragon';
      var _id = person._id; //需要取出主键_id
      delete person._id;    //再将其删除
      PersonModel.update({_id:_id},person,function(err){});
      //此时才能用Model操作，否则报错
    });

PersonModel.update({_id:_id},{$set:{name:'MDragon'}},function(err){});

```

> save

```

var userSave = new userModel({
	name: 'a',
	pass: 'b'
})

userSave.save()

```

> find

```

var user = require('./userModel')

user.find({name: 'a'}, function(err, val){
	if(!err && val !== null){
        console.log(val)
    }
})

user.findOne({name: 'a'}, function(err, val){
	if(!err && val !== null){
        console.log(val)
    }
})

```

> condition

```

Person
      .find({ occupation: /host/ })
      .where('name.last').equals('Ghost')
      .where('age').gt(17).lt(66)
      .where('likes').in(['vaporizing', 'talking'])
      .limit(10)
      .sort('-occupation')
      .select('name occupation')
      .exec(callback);

```

> scheme

```

var PersonSchema = new Schema({
      name:{
        type:'String',
        required:true //姓名非空
      },
      age:{
        type:'Nunmer',
        min:18,       //年龄最小18
        max:120     //年龄最大120
      },
      city:{
        type:'String',
        enum:['北京','上海']  //只能是北京、上海人
      },
      other:{
        type:'String',
        validate:[validator,err]  //validator是一个验证函数，err是验证失败的错误信息
      }
    });

```

> example

```

/*

Person.findByIdAndUpdate(_id,{$set:{name:'MDragon'}},function(err,person){
  console.log(person.name); //MDragon
});

findByIdAndRemove

如果是Entity，使用save方法，如果是Model，使用create方法

//使用Entity来增加一条数据
var krouky = new PersonModel({name:'krouky'});
krouky.save(callback);
//使用Model来增加一条数据
var MDragon = {name:'MDragon'};
PersonModel.create(MDragon,callback);

remove



var schema = new Schema(...);
    schema.pre('save',function(next){
      //做点什么
      next();
    });

 var schema = new Schema(...);
    schema.pre('save',function(next,done){
      //下一个要执行的中间件并行执行
      next();
      doAsync(done);
    });

*/

```