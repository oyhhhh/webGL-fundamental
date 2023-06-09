# webGL-fundamental
封装了几个基础类，纯WebGL实现网页版简易跳一跳

{DirectionLight, PointLight, SpotLight, Mesh, Group, Camera, init, render}

DirectionLight类
-------------------------------------------------
构造器：DirectionLight(object: Object)
object可选属性：
color: Integer 默认值0xffffff
direction: Float[3] 默认值[0, -1, 0]

属性：
color:颜色
direction:方向

方法：
setColor(color: Integer)
setDirection(direction: Float[3])


PointLight类
-------------------------------------------------
构造器：PointLight(object: Object)
object可选属性：
color: Integer 默认值0xffffff
position: Float[3] 默认值[0, 100, 0]
constant: Float 默认值1.0
linear: Float 默认值0.09
quadratic: Float 默认值0.032

属性：
color:颜色
position:位置
constant, linear, quadratic:衰减参数

方法：
setColor(color: Integer)
setPosition(position: Float[3])
setParameter(constant: Float, linear: Float, quadratic: Float)


SpotLight类
-------------------------------------------------
构造器：SpotLight(object: Object)
object可选属性：
color: Integer 默认值0xffffff
position: Float[3] 默认值[0, 100, 0]
direction: Float[3] 默认值[0, -1, 0]
constant: Float 默认值1.0
linear: Float 默认值0.09
quadratic: Float 默认值0.032
cutOff: Float 默认值0.218
outerCutOff: Float 默认值0.305

属性：
color:颜色
direction:方向
position:位置
constant, linear, quadratic:衰减参数
cutOff, outerCutOff:切光角

方法：
setColor(color: Integer)
setDirection(direction: Float[3])
setPosition(position: Float[3])
setParameter(constant: Float, linear: Float, quadratic: Float)
setRad(cutOff: Float, outerCutOff: Float)


Mesh类
-------------------------------------------------
构造器：Mesh(object: Object, material: Object)
object必选属性：
type: String 目前type有box,sphere和cylinder，即立方体、球体和圆柱体
object可选属性：
position: Float[3] 默认值[0, 0, 0]
size: Float[3] 默认值[1, 1, 1]

material必选属性：
type: String 目前type有normal和light_sensitive两种，即不受光照影响和受光照影响
material可选属性：（color和src需有其一）
color: Integer
src: String/String[]

属性（这里只写建议直接查询的）：
material:材质
position:位置
type:形状
size:大小

方法：
setPosition(x: Float, y: Float, z: Float)
scale(x: Float, y: Float, z: Float)
setColor(color: Integer)
setTexture(material: Object) material属性：type:String, src: String/String[]
rotateX(rad: Float) 旋转是局部坐标下的且顺序为X-Y-Z 与设置先后无关
rotateY(rad: Float)
rotateZ(rad: Float)
clone()


Group类
-------------------------------------------------
构造器：Group(mesh1: Mesh, mesh2: Mesh, ...)

方法：
setPosition(x: Float, y: Float, z: Float)
scale(x: Float, y: Float, z: Float)
rotateX(rad: Float) 旋转是局部坐标下的且顺序为X-Y-Z 与设置先后无关
rotateY(rad: Float)
rotateZ(rad: Float)


Camera类（透视投影相机）
-------------------------------------------------
构造器：Camera(fovy: Float, aspect: Float, near: Float, far: Float)

属性（这里只写建议直接查询的）：
position:位置
target:目标

方法：
setPosition(x: Float, y: Float, z: Float)
setTarget(x: Float, y: Float, z: Float)
setPerspective(fovy: Float, aspect: Float, near: Float, far: Float)


init函数：初始化设置，在构造各种类之前调用
-------------------------------------------------
调用方法：init(gl)

render函数：对物体进行渲染
-------------------------------------------------
调用方法：render(backgroundColor: Integer, meshs: Mesh[], camera: Camera, lights: Light[])
