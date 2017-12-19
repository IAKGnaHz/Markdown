# Account类
> 声明一个账户的信息拥有以下五个变量
+ cardid    'String'
+ cardname  'String'
+ cardpwd   "String"
+ phone     'String'
+ balance   'double'


# Bank类
>  用于登陆银行系统，如果登陆失败，提示用户重新登录。登录成功，提供存款，取款，查询余额，退出
+ login() 用户登录方法
+ menu()  登录成功显示主菜单方法
+ deposit() 存款方法
+ withdraw() 取款方法
+ display() 显示余额方法

# DBUtil类
>初始化银行账户，当用户输入账户信息时，验证账户是否存在
+ BDUtil ()构造方法：用于初始化两个账户信息
+ getCardid() 获得账户id方法，用于比较数据库中是否存在该账户

# Test类
>包含主方法的类，项目的起点
+ main() main方法
