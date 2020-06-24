
<!-- TOC -->

- [flask 框架笔记和项目](#flask-框架笔记和项目)
    - [flask 基础](#flask-基础)
        - [基础代码](#基础代码)
            - [app说明](#app说明)
            - [路由](#路由)
            - [app启动](#app启动)
    - [模式选择](#模式选择)
    - [flask前端页面传递数据，后端获取数据](#flask前端页面传递数据后端获取数据)
    - [flask数据库操作数据](#flask数据库操作数据)
    - [flask 整合示例](#flask-整合示例)
        - [注册与登录的步骤](#注册与登录的步骤)
        - [首页增删改查的步骤](#首页增删改查的步骤)
    - [扩展](#扩展)
        - [插件](#插件)
        - [前端知识](#前端知识)
        - [数据库相关知识](#数据库相关知识)
    - [事务](#事务)
    - [flask项目知识及项目步骤](#flask项目知识及项目步骤)
        - [最常使用的SQLAlchemy列选项](#最常使用的sqlalchemy列选项)
        - [用户实体类](#用户实体类)
        - [密码加密的方法](#密码加密的方法)
        - [密码解密的方法](#密码解密的方法)
        - [异常处理](#异常处理)
        - [保存用户头像](#保存用户头像)
        - [微博实体类](#微博实体类)
        - [实体首页分页](#实体首页分页)
        - [登陆验证装饰器](#登陆验证装饰器)
        - [评论表](#评论表)

<!-- /TOC -->


# flask 框架笔记和项目

## flask 基础
### 基础代码
```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
	return 'hello_world'

app.run()

```  
#### app说明 
`app = Flask(__name__)`  
flask运行，是通过app对象来完成操作    
源码： 
![app源码.png](/智能识别/pic/app源码.png)  

#### 路由
代码说明：  
![路由.png](/智能识别/pic/路由.png)   
路由的作用：  
1. 页面访问有很多链接/路径  
2. 后台有很多方法  
路由指定两者的关联性  

#### app启动
` app.run()`  
1. 启动项目  
命令：`python app.py`  
      `python 文件名.py`

2. 页面访问页面  
127.0.0.1:5000/  
实现效果：  
![app实现效果.png](/智能识别/pic/app实现效果.png)  

3. debug模式
步骤：  
1) `app.run(debug=True)`或者修改配置文件：`FLASK_DEBUG = 1`或者勾选选择框,如图：  
![pycharm勾选选框.png](/智能识别/pic/pycharm勾选选框.png)   
2)运行项目  
控制台显示如图：  
![控制台显示.png](/智能识别/pic/控制台显示.png)  
Debug已开启   
   
生成PIN码   
1) 当报错，可以在前端页面点击终端  
2) 输入PIN，控制台调错  
  
4. 其他设置  
可以设置：  
host地址  
port端口  
debug模式   
源码：  
![app其他设置.png](/智能识别/pic/app其他设置.png)  
示例：  
`app.run(host=0.0.0.0,port=8000,debug=Treu)`

## 模式选择
![模式选择1.png](/智能识别/pic/模式选择1.png)      
![模式选择2.png](/智能识别/pic/模式选择2.png)      
环境变量的配置      
![模式选择3.png](/智能识别/pic/模式选择3.png)       

## flask前端页面传递数据，后端获取数据    
get提交    
路由代码：`request.args.get('input标签name的值')`   
后端提交数据：`render_template('login.html',name=name)`   
前台显示：`{{name}}`
## flask数据库操作数据
1. 导入数据库操作包     
2. 声明需要使用的数据库     
3. 创建db对象     
4. 配置app对象     
5. 创建实体类（需要表名及字段属性）     
6. 创建表     
7. 通过db对象来操作数据库     
```
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://root:123456@127.0.0.1/cqlg' 
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
```
## flask 整合示例
### 注册与登录的步骤
1. 拆分项目    
2. 编写路由逻辑    
3. 编写对应的页面     
4. 启动项目    
### 首页增删改查的步骤
1. 拆分层级    
2. 编写首页    
3. 定义不同的路由方法    
4. 通过首页按钮执行不同的路由    

## 扩展
### 插件
1. flask_script&ensp;命令操作项目    
(可看官方文档)    
通过命令来操作flask框架，修改代码为   
![flask框架-修改代码.png](/智能识别/pic/flask框架-修改代码.png)   
启动命令为：    
`python 文件名.py runserver`   
查看-help     
2. Blueprint&ensp;蓝图管理路由    
蓝图/蓝本   
让蓝图管理路由   
![flask框架-blueprint.png](/智能识别/pic/flask框架-blueprint.png)
3. pymysql&ensp;声明数据库   
4. sha256&ensp;密码加密   
5. wraps&ensp;函数装饰器   
6. os&ensp;文件    
7. datetime&ensp;时间   
### 前端知识 
1. h1  ~  h6&emsp;标题标签    
2. p&emsp;段落标签    
3. a&emsp;网页链接     
4. ul&emsp;无序列表    
5. ol&emsp;有序列表     
6. dl&emsp;自定义列表     
7. table&emsp;表格    
8. form&emsp;表单    
9. style&emsp;样式     
### 数据库相关知识
数据库设计第三范式    
- 第一大范式：不可再分    
该字段不可再拆分    
```
user -- cat
用户    小花
```
- 第二大范式：消除多余    
```
name          sid            
admin   	   1
name          sid
root           1	

sex
1  男  
2  女 
3  保密 
```
- 第三大范式：消除依赖  
外键or主键
```
学生  admin  
  1   数学
分数   100  
```
## 事务
原子性&nbsp;隔离性&nbsp;持久性     
![flask框架-事务.png](/智能识别/pic/flask框架-事务.png)

## flask项目知识及项目步骤
`app.register_blueprint(weibo_bp, url_prefix='/weibo')
`
### 最常使用的SQLAlchemy列选项
| 选项名 | 说明 |
| :------:| ------: |
| primary_key | 如果设为 True ，这列就是表的主键 |
| unique | 如果设为 True ，这列不允许出现重复的值 |
| index | 如果设为 True ，为这列创建索引，提升查询效率 |
| nullable | 如果设为 True ，这列允许使用空值；如果设为 False ，这列不允许使用空值 |
| default |  为这列定义默认值 |

### 用户实体类
```
'''用户表'''
    __tablename__ = 'user'

    id 
    nickname              unique=True, nullable=False, index=True     # 昵称
    password  								# 密码
    gender 		 default='unknow' 					# 性别
    bio 										# 经历
    city 		 default='上海'  					# 所在城市
    avatar   									# 头像
    birthday  		db.Date default='1990-01-01' 			# 生日
    created 		 db.Column(db.DateTime)  			# 创建时间

id nickname password gender bio city avatar birthday created  
```
### 密码加密的方法
```
import random
from hashlib import sha256

def gen_password(user_password):
    '''产生一个安全的密码'''
    bin_password = user_password.encode('utf8')  # 将密码转成 bytes 类型
    hash_value = sha256(bin_password).hexdigest()  # 计算用户密码的哈希值
    # %x 自动转化16进制
    salt = '%x' % random.randint(0x10000000, 0xffffffff)  # 产生随机
    # 0x去ipython查看
    safe_password = salt + hash_value
    return safe_password
```
### 密码解密的方法
```
def check_password(user_password, safe_password):
    '''检查用户密码是否正确'''
    bin_password = user_password.encode('utf8')  # 将密码转成 bytes 类型
    hash_value = sha256(bin_password).hexdigest()  # 计算用户密码的哈希值
    # 只需要检测8位之后的
    return hash_value == safe_password[8:]
```
### 异常处理
```
    try:
        需要执行的逻辑
		（可能出错的逻辑）
    except IntegrityError:
        出错过后的逻辑
```
```
# 进行一个异常处理
    try:
        # 会设计事务的提交和回滚的处理
        db.session.commit()
    except IntegrityError:
        # 数据回滚
        db.session.rollback()
        return render_template('register.html', error='昵称已被占用，请换一个')
```
### 保存用户头像
```
import os

def save_avatar(nickname, avatar_file):
    base_dir = os.path.dirname(os.path.abspath(__name__))
    file_path = os.path.join(base_dir, 'static', 'upload', nickname)
    avatar_file.save(file_path)
```
### 微博实体类
```
__tablename__ = 'weibo'

    id = db.Column(db.Integer, primary_key=True)
    uid = db.Column(db.Integer, nullable=False)   #用户id
    content = db.Column(db.Text)  #创建时间
    created = db.Column(db.DateTime, default=datetime.now)  # 发布时间
    updated = db.Column(db.DateTime, default=datetime.now, onupdate=datetime.now)  # 最后修改的时间
    n_like = db.Column(db.Integer, default=0)  # 当前微博的点赞数量
```
### 实体首页分页
```
def index():
    '''显示最新的前 50 条微博'''
    # 获取微博数据
    # 传入页码  根据页码  给出默认值
    page = int(request.args.get('page', 1))
    n_per_page = 10
    offset = (page - 1) * n_per_page
    # 当前页要显示的微博
    # select * from weibo order by updated desc limit 10 offset 20;
    wb_list = Weibo.query.order_by(Weibo.updated.desc()).limit(10).offset(offset)
    n_weibo = Weibo.query.count()  # 微博总数
    n_page = 5 if n_weibo >= 50 else ceil(n_weibo / n_per_page)  # 总页数

    # 获取微博对应的作者
    uid_list = {wb.uid for wb in wb_list}  # 取出微博对应的用户 ID1
    # select id, nickname from user id in ...;
    # 取出之后是一个generator  里面是一个元组 转成字典
    users = dict(User.query.filter(User.id.in_(uid_list)).values('id', 'nickname'))
    return render_template('index.html', page=page, n_page=n_page, wb_list=wb_list,users=users)

```
### 登陆验证装饰器
```
def login_required(view_func):s
    @wraps(view_func)
    def check(*args, **kwargs):
        if 'uid' in session:
            return view_func(*args, **kwargs)
        else:
            return render_template('login.html', error='请您先登录')
    return check
```
### 评论表
```
  __tablename__ = 'comment'

    id = db.Column(db.Integer, primary_key=True)
    uid = db.Column(db.Integer, nullable=False)  # 评论的作者ID
    wid = db.Column(db.Integer, nullable=False)  # 被评论的微博的ID
    cid = db.Column(db.Integer, nullable=False, default=0)  # 回复的评论的ID
    rid = db.Column(db.Integer, nullable=False, default=0)  # 回复的回复的ID
    content = db.Column(db.Text)
    created = db.Column(db.DateTime, default=datetime.now)
    wid = request.args.get('wid')
    weibo = Weibo.query.get(wid)
    if weibo is None:
        abort(404)
    else:
        user = User.query.get(weibo.uid)
        comments = Comment.query.filter_by(wid=weibo.id).order_by(Comment.created.desc())
        all_uid = {c.uid for c in comments}  # 所有评论的作者的 ID
        cmt_users = dict(User.query.filter(User.id.in_(all_uid)).values('id', 'nickname'))
        comments = OrderedDict([[cmt.id, cmt] for cmt in comments])  # 将所有评论转成有序字典
        return render_template('show.html', weibo=weibo, user=user, cmt_users=cmt_users, comments=comments)

```
