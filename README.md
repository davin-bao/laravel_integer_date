# laravel_integer_date
this is support set integer date field in datebase laravel 5 model trait

### How to Install

in model, you need add:

```
class Role extends Model
{
  use TimezoneTrait;

  protected $dates = ['repaid_at'];
}
```

### How to Use

```
  //find
  var_dump(Role::all()->toArray());
  var_dump(Role::find(2)->repaid_at);
  var_dump(Role::find(2)->repaid_at->timezone('Asia/Shanghai'));
  var_dump(Role::find(2)->repaid_at->timezone('Asia/Shanghai')->timestamp);
  
  //create
  $role = Role::create([
    'name'=> str_random(20),
    'repaid_at' => '1470123960',
  ]);
  
  $role = Role::create([
    'name'=> str_random(20),
    'display_name'=> 'test',
    'repaid_at' =>  Carbon::createFromFormat('Y-m-d H:i', '2016-08-02 11:44', 'Asia/Shanghai')
  ]);
  
  //update
  $role = Role::find(2);
  $role->repaid_at = Carbon::createFromFormat('Y-m-d H:i', '2016-08-02 03:44', 'UTC');
  $role->save();
  
  $role->update([
    'repaid_at' =>  Carbon::createFromFormat('Y-m-d H:i', '2016-08-03 11:44', 'Asia/Shanghai')
  ]);

```



