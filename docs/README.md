# 1.0 add User 第三方注册添加用户

> 请求地址:  http://example:8081/api/user/           请求方式:**POST** 

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",    //android_1q2w3e4r   ios_1q2w3e4r
    "type": "twitter",            //twitter   line   facebook
    "id": "asgfdhg134",           //三方注册的id
    "name":"dasdfgfgdf",
    "tel": null,
    "birthday": "2021-3-22",
    "email": "example@qq.com",
    "gender":"0",
    "address" : "address",
    "myid":"example_myid",           //传入myid参数自定义主表id字段名称,否则自动生成id字段名称
    "zone":"86",				 //传入zone代表手机区号,不传默认为81(日本)
    "avatar":"161873009247753952.png",  //头像字段, 传入上传头像接口返回的图片名称
    "password":"123456"
}
```

> 返回内容:

```javascript
//邮箱已存在
{
    "code": "LME0009",
    "message": "邮箱已存在",
    "success": false
}
//用户已存在
{
    "code": "LME0001",
    "message": "用户已存在",
    "success": false
}
//注册成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "twitter",
        "index": "153",
        "id": "87952633",
        "fid": null,
        "lid": null,
        "tid": "89464632135",
        "lev": null,
        "name": "dasdfgfgdf",
        "profile_photo": null,
        "birthday": "2021-3-22",
        "email": "895562647@qq.com",
        "gender": 0,
        "job": null,
        "address": null,
        "tel": null,
        "zone": "86",
        "password": "123456",
        "expires": null,
        "avatar": "161873009247753952.png",
        "token": ""
    }
}
```

# 1.1 Add profile photo 添加头像

> 请求地址:  http://example:8081/upload/avatar    请求方式:  **POST**  表单

------

> 请求体:

| key  | ios_1q2w3e4r |
| ---- | ------------ |
| type | twitter      |
| file | example.jpg  |

*file文件支持jpg  png  jpeg*

> 返回码:

```javascript
//正常返回
{
    "code": "200",
    "message": "161890049645681711110.jpeg",    //mseeage对应的是下载头像的名称参数
    "success": true
}
//file格式错误
{
    "code": "400",
    "message": "please upload image type",
    "success": false
}
```

# 1.2 Download profile photo 下载头像

> 请求地址: http://example:8081/download/avatar/{image_name}   请求方式: **GET**
>
> 请求示例: http://example:8081/download/avatar/161875210088866277807.jpg 



# 1.3 Get user info 获得用户信息

> 请求地址: http://example:8081/api/user/**{id}**?key=ios_1q2w3e4r&type=twitter   请求方式: **GET**
>
> 请求示例:  http://example:8081/api/user/324234234?key=ios_1q2w3e4r&type=twitter

**可用于获取三方登录信息**

------

> 返回内容:

```java
//成功返回:
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "twitter",
        "index": "140",
        "id": "324234234",
        "fid": null,
        "lid": null,
        "tid": null,
        "lev": 0,
        "name": "hahaha",
        "profile_photo": null,
        "birthday": "2010-01-01",
        "email": "857018877@qq.com",
        "gender": 1,
        "job": "工人",
        "address": "hahah",
        "tel": null,
        "zone": null,
        "password": null,
        "expires": null,
        "avatar": "161873009247753952.png",
        "token": null
    }
}

//未找到用户返回:
{
    "code": "400",
    "message": "not found user",
    "success": false
}
```

# 1.4 Change user info 修改部分用户信息

> 请求地址: http://example:8081/api/user/**{ID}**     请求方式: **POST**
>
> 请求示例: http://example:8081/api/user/85962

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "name":"doajdsif",
    "tel": "15820482954",
    "birthday": "2021-3-22",
    "email": "55889667@qq.com",
    "gender":"20",
    "password":"879632",
    "avatar":"111111111.png"
}
```

> 返回信息:

```javascript
//返回成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "normal",
        "index": null,
        "id": "85962",
        "fid": null,
        "lid": null,
        "tid": null,
        "lev": 0,
        "name": "doajdsif",
        "profile_photo": null,
        "birthday": "2021-3-22",
        "email": "55889667@qq.com",
        "gender": 20,
        "job": null,
        "address": null,
        "tel": "15820482954",
        "zone": null,
        "password": "879632",
        "expires": null,
        "avatar": "111111111.png",
        "token": null
    }
}

//未找到用户
{
    "code": "400",
    "message": "not found user !",
    "success": false
}
```

# 1.5 Normal user login 普通用户登陆

> 请求地址:  http://example:8081/api/user/login   请求方式: **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "Pangpoe01",   //id名称
    "password": "123"	//密码
}
```

> 响应体:

```javascript
//登录成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "normal",
        "index": "65",
        "id": "jim13",
        "fid": null,
        "lid": null,
        "tid": null,
        "lev": null,
        "name": "lee",
        "profile_photo": null,
        "birthday": "1982-12-21",
        "email": "naver.com",
        "gender": 0,
        "job": "IT",
        "address": "japan",
        "tel": "010-9392-8888",
        "zone": null,
        "password": "123456",
        "expires": "2021-04-16 23:36:09",
        "avatar": null,
        "token": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIxMjM0NTYiLCJvcGVuSWQiOiJub3JtYWwiLCJ1c2VySWQiOiJqaW0xMyIsImp0aSI6InRva2VuSWQiLCJpYXQiOjE2MTg5MTc0MTMsImV4cCI6MTYxODkxNzg0NX0.7e7N1y1ZcbnIBjG0qAhn3iz-0y1-jiUBcGx1PwFdRuM"
    }
}
//密码错误
{
    "code": "LME0012",
    "message": "密码错误",
    "success": false
}
//用户ID不存在
{
    "code": "LME0011",
    "message": "登陆ID不存在",
    "success": false
}
```

# 1.6 email/tel exist check 邮件/电话检测是否存在

> 请求地址:  http://example:8081/api/user/exist   请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "ios_1q2w3e4r",
    "type": "normal",
    "email": "dasdasdasdasdf@qq.com",
    "tel": "133124565547"
}
```

> 响应体:

```javascript
{
    "code": "LME0003",
    "message": "电话已存在",
    "success": false
}
//邮箱已存在
{
    "code": "LME0009",
    "message": "邮箱已存在",
    "success": false
}

//email 和 tel 都不存在
{
    "code": "400",
    "message": "all doesn't exist",
    "success": false
}
```

# 1.7 check user id exist 检测id存在

> 请求地址:  http://example:8081/api/user/check/**{id}**?key=ios_1q2w3e4r&type=normal  请求方式:  **GET**
>
> 请求示例:  http://example:8081/api/user/check/904316822438068226?key=ios_1q2w3e4r&type=normal

------

> 响应体:

```javascript
//用户已存在
{
    "code": "LME0001",
    "message": "用户已存在",
    "success": false
}

//用户不存在
{
    "code": "LME0011",
    "message": "登陆ID不存在",
    "success": false
}
```

# 1.8 delete user 删除用户

> 请求地址:  http://example:8081/api/user/del/{id}   请求方式:  **POST**
>
> 请求示例:  http://example:8081/api/user/del/jim12

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal"
}
```

> 响应体:

```javascript
//删除成功
{
    "code": "200",
    "message": "删除成功",
    "success": true
}
//未找到用户
{
    "code": "400",
    "message": "未找到用户",
    "success": false
}
```

# 2.0 get basic test records 获取基础测试记录列表

> 请求地址:   http://example:8081/api/result/**{id}**?key=ios_1q2w3e4r&type=normal   请求方式:  **GET**
>
> 请求示例:  http://example:8081/api/result/1234567?key=ios_1q2w3e4r&type=normal

------

> 响应体:

```java
//响应成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": [
        {
            "type": null,
            "index": 55,
            "id": "1234567",
            "image_url": "prd-api3/20210216/b1f1b30d51e23e4409ea9ae0dbc3ff61-2251799813719383.jpg",
            "test_date_time": "1982-12-21 18:18:27",
            "total_score": 100,
            "blackhead": null,
            "dark_circle": null,
            "wrinkle": null,
            "pore": null,
            "pockmark": null,
            "spot": null,
            "roughness": null,
            "moisture": null,
            "texture": null,
            "chloasma": null,
            "skin_api_result": null
        },
        {
            "type": null,
            "index": 58,
            "id": "1234567",
            "image_url": "prd-api3/20210216/b1f1b30d51e23e4409ea9ae0dbc3ff61-2251799813719383.jpg",
            "test_date_time": "1982-12-21 18:18:27",
            "total_score": 100,
            "blackhead": null,
            "dark_circle": null,
            "wrinkle": null,
            "pore": null,
            "pockmark": null,
            "spot": null,
            "roughness": null,
            "moisture": null,
            "texture": null,
            "chloasma": null,
            "skin_api_result": null
        }
    ]
}

//响应失败
{
    "code": "400",
    "message": "search nothing",
    "success": false
}
```

# 2.1 Add test record添加测试记录

> 请求地址:  http://example:8081/api/result   请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "jim13",
    "image_url": "prd-api3/20210216/b1f1b30d51e23e4409ea9ae0dbc3ff61-2251799813719383.jpg",
    "test_date_time": "1982-12-21 18:18:27",
    "total_score": 100,
    "blackhead": 20,
    "dark_circle": 100,
    "wrinkle": 99,
    "pore": 99,
    "pockmark": 0,
    "spot": 99,
    "roughness": 99,
    "moisture": 99,
	"texture": 99,
    "chloasma": 99,
    "skin_api_result": "{\"color\":{\"result\":\"ziran\",\"score\":80,\"mapped_score\":61.560000000000002},\"forehead\":{\"type\":[\"fujiShape\"],\"result\":\"0.499176\"},\"wrinkle\":{\"category\":[{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"forehead\"},{\"score\":90,\"count\":2,\"level\":\"lightly\",\"cls\":\"eyecorner\"},{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"crowfeet\"},{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"glabella\"},{\"score\":75,\"count\":2,\"level\":\"lightly\",\"cls\":\"nasolabial\"}],\"score\":93,\"underlying_score\":[0.038374618217435555,0.007674923643487111,0.042327127978290358,5.3213504404895639e-05,1.330337610122391e-05,2.1961128802020423e-05,0.02],\"mapped_score\":78.640000000000001,\"count\":4,\"level\":\"lightly\",\"mapped_score_exp\":86.209999999999994,\"filename\":\"prd-apiout3\\/20210411\\/4f5ca71d9527119827896905a1a3dab7-2251799813739021.jpg\"},\"moisture\":{\"result\":\"0.223\",\"filename\":\"prd-apiout3\\/20210411\\/773b58cc5372dd634c60005b076717d5-2251799813739020.jpg\",\"score\":\"79\",\"class\":[{\"result\":0.123,\"class\":\"left_cheek\"},{\"result\":0.27100000000000002,\"class\":\"right_cheek\"},{\"result\":0.31900000000000001,\"class\":\"forehead\"},{\"result\":0,\"class\":\"chin\"}],\"level\":\"lightly\",\"mapped_score\":65.5},\"code\":0,\"image_detect\":[],\"face_detect\":{\"rects\":[{\"y0\":190,\"x1\":949,\"x0\":83,\"y1\":1400}]},\"texture\":{\"score\":57,\"filename\":\"prd-apiout3\\/20210411\\/4b6e1c1132bb69094990239a771b9bcb-2251799813739023.jpg\",\"mapped_score\":48.140000000000001},\"sensitive\":{\"filename\":\"prd-apiout3\\/20210411\\/58ca4323927d3913bf234d7ab2ed4068-2251799813739025.jpg\",\"score\":99,\"type\":\"tolerance\",\"underlying_score\":null,\"mapped_score\":100},\"skin_type\":{\"mapped_score\":57.119999999999997,\"score\":51,\"category\":[{\"cls\":\"forehead\",\"score\":49,\"level\":\"moderately\",\"prob\":3.9871997833251953,\"exp_type\":\"mid\",\"type\":\"mid\",\"oil_score\":68.689999999999998},{\"cls\":\"nose\",\"score\":70,\"level\":\"lightly\",\"prob\":4.926600456237793,\"exp_type\":\"oil\",\"type\":\"oil\",\"oil_score\":94.819999999999993},{\"cls\":\"left_cheek\",\"score\":53,\"level\":\"moderately\",\"prob\":4.1198000907897949,\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"oil_score\":77.430000000000007},{\"cls\":\"right_cheek\",\"score\":55,\"level\":\"moderately\",\"prob\":4.1796998977661133,\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"oil_score\":76.969999999999999},{\"cls\":\"chin\",\"score\":49,\"level\":\"moderately\",\"prob\":3.9965002536773682,\"exp_type\":\"mid\",\"type\":\"mid\",\"oil_score\":71.129999999999995}],\"exp_type_v0\":\"mid_oil\",\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"filename\":\"prd-apiout3\\/20210411\\/9f3253cce8b73e2d4a1a7a0db0e652d9-2251799813739029.jpg\",\"oil_score\":84.25,\"mix_extended\":\"mid\"},\"pockmark\":{\"category\":[{\"cls\":\"CC_DD\",\"count\":4,\"score\":89},{\"cls\":\"CC_DY\",\"count\":2,\"score\":80}],\"score\":82,\"underlying_score\":{\"CC_DY\":[0.0009545570983453828,0.000553827791489298,0.86178150773048401,0.001115794274902653,0.040000000000000001],\"CC_DD\":[0.003251138339801593,0.0008269049248155102,0.98292386531829834,0.0032882567087025197,0.080000000000000002]},\"mapped_score\":47.789999999999999,\"count\":6,\"level\":\"lightly\",\"filename\":\"prd-apiout3\\/20210411\\/55be7a6a8fdeea33c370d40bcd7e7e2c-2251799813739018.jpg\"},\"appearance\":{\"score\":75},\"roughness\":{\"score\":94,\"mapped_score\":79.939999999999998,\"level\":\"moderately\"},\"dark_circle\":{\"mapped_score\":68.840000000000003,\"score\":71,\"rightType\":\"XGX\",\"rightLevel\":\"lightly\",\"three_types\":{\"XGX\":{\"level\":\"lightly\",\"score\":68},\"SSX\":{\"level\":\"lightly\",\"score\":69},\"YYX\":{\"level\":\"none\",\"score\":100}},\"level\":\"lightly\",\"leftType\":\"HHX\",\"filename\":\"prd-apiout3\\/20210411\\/56871327f63e3ca5b898951217d6977c-2251799813739026.jpg\",\"type\":\"HHX\",\"leftLevel\":\"lightly\"},\"defeat_rank\":{\"pockmark\":0.11,\"blackhead\":0.56999999999999995,\"dark_circle\":0.95999999999999996,\"appearance\":0.5,\"pore\":0.84999999999999998,\"texture\":0.01,\"spot\":0.90000000000000002,\"chloasma\":0.76000000000000001,\"skin_type\":0.41999999999999998,\"moisture\":0.44,\"wrinkle\":0.42999999999999999},\"pore\":{\"category\":[{\"score\":100,\"cls\":\"forehead\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"left_cheek\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"right_cheek\",\"count\":0,\"level\":\"none\"}],\"score\":\"100\",\"area\":0,\"mapped_score\":100,\"count\":0,\"level\":\"none\",\"filename\":\"prd-apiout3\\/20210411\\/a1d8e2048e49d4cf286d0e006b903c43-2251799813739022.jpg\"},\"disease\":{\"niduses\":[{\"boxes\":[{\"coord\":[684,747,865,954],\"scores\":0.40903806686401367}],\"class\":\"CC\"},{\"boxes\":[],\"class\":\"MGJF\"},{\"boxes\":[{\"coord\":[507,837,574,899],\"scores\":0.44814836978912354},{\"coord\":[900,941,930,981],\"scores\":0.35853824019432068}],\"class\":\"PY\"}],\"filename\":\"prd-apiout3\\/20210411\\/6be8a5db74feed2d4aa4b140eb0308fe-2251799813739028.jpg\",\"result\":\"CC,PY\"},\"face_box\":{\"y0\":139,\"x1\":979,\"x0\":69,\"y1\":1440},\"filename\":\"prd-api3\\/20210411\\/4db27053fd015624c0b92ed498fd21e7-2251799813739015.jpg\",\"id\":\"26db5e1854606d680862cabbd7248e30\",\"error_detect_types\":34409021440,\"spot\":{\"category\":[{\"score\":100,\"cls\":\"Z_Z\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"B_HHB\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"B_QB\",\"count\":0,\"level\":\"none\"},{\"score\":98,\"cls\":\"B_QTB\",\"count\":1,\"level\":\"lightly\"}],\"score\":99,\"underlying_score\":{\"B_QB\":[0,0,0,0,0],\"B_QTB\":[0.001535022655028666,0.001634414778150366,0.93918794393539429,0.0016344147781503662,0.02],\"Z_Z\":[0,0,0,0,0],\"B_HHB\":[0,0,0,0,0]},\"mapped_score\":79.680000000000007,\"count\":1,\"level\":\"lightly\",\"filename\":\"prd-apiout3\\/20210411\\/5d4df15deb822c5070ba5edad98f3104-2251799813739017.jpg\"},\"blackhead\":{\"mapped_score\":77.629999999999995,\"score\":\"98\",\"count\":2,\"level\":\"lightly\",\"area\":0.0008891800534911454,\"filename\":\"prd-apiout3\\/20210411\\/3b7288653efdb42a7804d87eac68bab8-2251799813739024.jpg\"},\"detect_types\":\"192853555199\",\"age\":{\"result\":35},\"emotion\":{\"result\":\"neutral\"},\"features\":{\"wearing_hat\":\"0.00000\",\"pointy_nose\":\"0.00000\",\"heavy_makeup\":\"0.01340\",\"mustache\":\"0.00006\",\"straight_hair\":\"0.00000\",\"wearing_necktie\":\"0.00000\",\"brown_hair\":\"0.00034\",\"no_beard\":\"0.00000\",\"gray_hair\":\"0.00000\",\"arched_eyebrows\":\"0.00000\",\"receding_hairline\":\"0.00000\",\"eyeglasses\":\"0.00000\",\"bushy_eyebrows\":\"0.00000\",\"high_cheekbones\":\"0.03727\",\"double_chin\":\"0.00008\",\"oval_face\":\"0.00000\",\"wavy_hair\":\"0.00424\",\"pale_skin\":\"0.00000\",\"wearing_necklace\":\"0.00000\",\"bangs\":\"0.00000\",\"goatee\":\"0.00002\",\"sideburns\":\"0.00002\",\"blond_hair\":\"0.00000\",\"female\":0.98350614309310913,\"rosy_cheeks\":\"0.00000\",\"bags_under_eyes\":\"0.32717\",\"bald\":\"0.00000\",\"chubby\":\"0.40677\",\"wearing_earrings\":\"0.00000\",\"mouth_slightly_open\":\"0.00000\",\"big_nose\":\"0.00000\",\"attractive\":\"0.07421\",\"blurry\":\"0.00000\",\"male\":1,\"big_lips\":\"0.00000\",\"young\":\"0.00000\",\"5_o_clock_shadow\":\"0.50617\",\"smiling\":\"0.00000\",\"black_hair\":\"0.00000\",\"wearing_lipstick\":\"0.00000\",\"narrow_eyes\":\"0.00000\"},\"acne\":{\"mapped_score\":100,\"filename\":\"prd-apiout3\\/20210411\\/b249df865c7fbb301b251eba9cd1b1cc-2251799813739019.jpg\",\"level\":\"none\",\"count\":0,\"category\":[],\"underlying_score\":null},\"chloasma\":{\"filename\":\"prd-apiout3\\/20210411\\/57958da02820d92b7b1274d40934ab54-2251799813739027.jpg\",\"count\":3,\"score\":94,\"mapped_score\":80.209999999999994}}"

}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "normal",
        "index": null,
        "id": "jim13",
        "image_url": "prd-api3/20210216/b1f1b30d51e23e4409ea9ae0dbc3ff61-2251799813719383.jpg",
        "test_date_time": "1982-12-21 18:18:27",
        "total_score": 100,
        "blackhead": 20,
        "dark_circle": 100,
        "wrinkle": 99,
        "pore": 99,
        "pockmark": 0,
        "spot": 99,
        "roughness": 99,
        "moisture": 99,
        "texture": 99,
        "chloasma": 99,
        "skin_api_result": "{\"color\":{\"result\":\"ziran\",\"score\":80,\"mapped_score\":61.560000000000002},\"forehead\":{\"type\":[\"fujiShape\"],\"result\":\"0.499176\"},\"wrinkle\":{\"category\":[{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"forehead\"},{\"score\":90,\"count\":2,\"level\":\"lightly\",\"cls\":\"eyecorner\"},{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"crowfeet\"},{\"score\":100,\"count\":0,\"level\":\"none\",\"cls\":\"glabella\"},{\"score\":75,\"count\":2,\"level\":\"lightly\",\"cls\":\"nasolabial\"}],\"score\":93,\"underlying_score\":[0.038374618217435555,0.007674923643487111,0.042327127978290358,5.3213504404895639e-05,1.330337610122391e-05,2.1961128802020423e-05,0.02],\"mapped_score\":78.640000000000001,\"count\":4,\"level\":\"lightly\",\"mapped_score_exp\":86.209999999999994,\"filename\":\"prd-apiout3\/20210411\/4f5ca71d9527119827896905a1a3dab7-2251799813739021.jpg\"},\"moisture\":{\"result\":\"0.223\",\"filename\":\"prd-apiout3\/20210411\/773b58cc5372dd634c60005b076717d5-2251799813739020.jpg\",\"score\":\"79\",\"class\":[{\"result\":0.123,\"class\":\"left_cheek\"},{\"result\":0.27100000000000002,\"class\":\"right_cheek\"},{\"result\":0.31900000000000001,\"class\":\"forehead\"},{\"result\":0,\"class\":\"chin\"}],\"level\":\"lightly\",\"mapped_score\":65.5},\"code\":0,\"image_detect\":[],\"face_detect\":{\"rects\":[{\"y0\":190,\"x1\":949,\"x0\":83,\"y1\":1400}]},\"texture\":{\"score\":57,\"filename\":\"prd-apiout3\/20210411\/4b6e1c1132bb69094990239a771b9bcb-2251799813739023.jpg\",\"mapped_score\":48.140000000000001},\"sensitive\":{\"filename\":\"prd-apiout3\/20210411\/58ca4323927d3913bf234d7ab2ed4068-2251799813739025.jpg\",\"score\":99,\"type\":\"tolerance\",\"underlying_score\":null,\"mapped_score\":100},\"skin_type\":{\"mapped_score\":57.119999999999997,\"score\":51,\"category\":[{\"cls\":\"forehead\",\"score\":49,\"level\":\"moderately\",\"prob\":3.9871997833251953,\"exp_type\":\"mid\",\"type\":\"mid\",\"oil_score\":68.689999999999998},{\"cls\":\"nose\",\"score\":70,\"level\":\"lightly\",\"prob\":4.926600456237793,\"exp_type\":\"oil\",\"type\":\"oil\",\"oil_score\":94.819999999999993},{\"cls\":\"left_cheek\",\"score\":53,\"level\":\"moderately\",\"prob\":4.1198000907897949,\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"oil_score\":77.430000000000007},{\"cls\":\"right_cheek\",\"score\":55,\"level\":\"moderately\",\"prob\":4.1796998977661133,\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"oil_score\":76.969999999999999},{\"cls\":\"chin\",\"score\":49,\"level\":\"moderately\",\"prob\":3.9965002536773682,\"exp_type\":\"mid\",\"type\":\"mid\",\"oil_score\":71.129999999999995}],\"exp_type_v0\":\"mid_oil\",\"exp_type\":\"mid_oil\",\"type\":\"mid\",\"filename\":\"prd-apiout3\/20210411\/9f3253cce8b73e2d4a1a7a0db0e652d9-2251799813739029.jpg\",\"oil_score\":84.25,\"mix_extended\":\"mid\"},\"pockmark\":{\"category\":[{\"cls\":\"CC_DD\",\"count\":4,\"score\":89},{\"cls\":\"CC_DY\",\"count\":2,\"score\":80}],\"score\":82,\"underlying_score\":{\"CC_DY\":[0.0009545570983453828,0.000553827791489298,0.86178150773048401,0.001115794274902653,0.040000000000000001],\"CC_DD\":[0.003251138339801593,0.0008269049248155102,0.98292386531829834,0.0032882567087025197,0.080000000000000002]},\"mapped_score\":47.789999999999999,\"count\":6,\"level\":\"lightly\",\"filename\":\"prd-apiout3\/20210411\/55be7a6a8fdeea33c370d40bcd7e7e2c-2251799813739018.jpg\"},\"appearance\":{\"score\":75},\"roughness\":{\"score\":94,\"mapped_score\":79.939999999999998,\"level\":\"moderately\"},\"dark_circle\":{\"mapped_score\":68.840000000000003,\"score\":71,\"rightType\":\"XGX\",\"rightLevel\":\"lightly\",\"three_types\":{\"XGX\":{\"level\":\"lightly\",\"score\":68},\"SSX\":{\"level\":\"lightly\",\"score\":69},\"YYX\":{\"level\":\"none\",\"score\":100}},\"level\":\"lightly\",\"leftType\":\"HHX\",\"filename\":\"prd-apiout3\/20210411\/56871327f63e3ca5b898951217d6977c-2251799813739026.jpg\",\"type\":\"HHX\",\"leftLevel\":\"lightly\"},\"defeat_rank\":{\"pockmark\":0.11,\"blackhead\":0.56999999999999995,\"dark_circle\":0.95999999999999996,\"appearance\":0.5,\"pore\":0.84999999999999998,\"texture\":0.01,\"spot\":0.90000000000000002,\"chloasma\":0.76000000000000001,\"skin_type\":0.41999999999999998,\"moisture\":0.44,\"wrinkle\":0.42999999999999999},\"pore\":{\"category\":[{\"score\":100,\"cls\":\"forehead\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"left_cheek\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"right_cheek\",\"count\":0,\"level\":\"none\"}],\"score\":\"100\",\"area\":0,\"mapped_score\":100,\"count\":0,\"level\":\"none\",\"filename\":\"prd-apiout3\/20210411\/a1d8e2048e49d4cf286d0e006b903c43-2251799813739022.jpg\"},\"disease\":{\"niduses\":[{\"boxes\":[{\"coord\":[684,747,865,954],\"scores\":0.40903806686401367}],\"class\":\"CC\"},{\"boxes\":[],\"class\":\"MGJF\"},{\"boxes\":[{\"coord\":[507,837,574,899],\"scores\":0.44814836978912354},{\"coord\":[900,941,930,981],\"scores\":0.35853824019432068}],\"class\":\"PY\"}],\"filename\":\"prd-apiout3\/20210411\/6be8a5db74feed2d4aa4b140eb0308fe-2251799813739028.jpg\",\"result\":\"CC,PY\"},\"face_box\":{\"y0\":139,\"x1\":979,\"x0\":69,\"y1\":1440},\"filename\":\"prd-api3\/20210411\/4db27053fd015624c0b92ed498fd21e7-2251799813739015.jpg\",\"id\":\"26db5e1854606d680862cabbd7248e30\",\"error_detect_types\":34409021440,\"spot\":{\"category\":[{\"score\":100,\"cls\":\"Z_Z\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"B_HHB\",\"count\":0,\"level\":\"none\"},{\"score\":100,\"cls\":\"B_QB\",\"count\":0,\"level\":\"none\"},{\"score\":98,\"cls\":\"B_QTB\",\"count\":1,\"level\":\"lightly\"}],\"score\":99,\"underlying_score\":{\"B_QB\":[0,0,0,0,0],\"B_QTB\":[0.001535022655028666,0.001634414778150366,0.93918794393539429,0.0016344147781503662,0.02],\"Z_Z\":[0,0,0,0,0],\"B_HHB\":[0,0,0,0,0]},\"mapped_score\":79.680000000000007,\"count\":1,\"level\":\"lightly\",\"filename\":\"prd-apiout3\/20210411\/5d4df15deb822c5070ba5edad98f3104-2251799813739017.jpg\"},\"blackhead\":{\"mapped_score\":77.629999999999995,\"score\":\"98\",\"count\":2,\"level\":\"lightly\",\"area\":0.0008891800534911454,\"filename\":\"prd-apiout3\/20210411\/3b7288653efdb42a7804d87eac68bab8-2251799813739024.jpg\"},\"detect_types\":\"192853555199\",\"age\":{\"result\":35},\"emotion\":{\"result\":\"neutral\"},\"features\":{\"wearing_hat\":\"0.00000\",\"pointy_nose\":\"0.00000\",\"heavy_makeup\":\"0.01340\",\"mustache\":\"0.00006\",\"straight_hair\":\"0.00000\",\"wearing_necktie\":\"0.00000\",\"brown_hair\":\"0.00034\",\"no_beard\":\"0.00000\",\"gray_hair\":\"0.00000\",\"arched_eyebrows\":\"0.00000\",\"receding_hairline\":\"0.00000\",\"eyeglasses\":\"0.00000\",\"bushy_eyebrows\":\"0.00000\",\"high_cheekbones\":\"0.03727\",\"double_chin\":\"0.00008\",\"oval_face\":\"0.00000\",\"wavy_hair\":\"0.00424\",\"pale_skin\":\"0.00000\",\"wearing_necklace\":\"0.00000\",\"bangs\":\"0.00000\",\"goatee\":\"0.00002\",\"sideburns\":\"0.00002\",\"blond_hair\":\"0.00000\",\"female\":0.98350614309310913,\"rosy_cheeks\":\"0.00000\",\"bags_under_eyes\":\"0.32717\",\"bald\":\"0.00000\",\"chubby\":\"0.40677\",\"wearing_earrings\":\"0.00000\",\"mouth_slightly_open\":\"0.00000\",\"big_nose\":\"0.00000\",\"attractive\":\"0.07421\",\"blurry\":\"0.00000\",\"male\":1,\"big_lips\":\"0.00000\",\"young\":\"0.00000\",\"5_o_clock_shadow\":\"0.50617\",\"smiling\":\"0.00000\",\"black_hair\":\"0.00000\",\"wearing_lipstick\":\"0.00000\",\"narrow_eyes\":\"0.00000\"},\"acne\":{\"mapped_score\":100,\"filename\":\"prd-apiout3\/20210411\/b249df865c7fbb301b251eba9cd1b1cc-2251799813739019.jpg\",\"level\":\"none\",\"count\":0,\"category\":[],\"underlying_score\":null},\"chloasma\":{\"filename\":\"prd-apiout3\/20210411\/57958da02820d92b7b1274d40934ab54-2251799813739027.jpg\",\"count\":3,\"score\":94,\"mapped_score\":80.209999999999994}}"
    }
}

//id不存在失败
{
    "code": "400",
    "message": "id: jim13333 doesn't exist !",
    "success": false
}
```

# 2.2 Delete one record 删除一条记录

> 请求地址:  http://example:8081/api/result/del       请求方式: **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "1234567",
    "test_date_time": "2021-03-16 18:18:27"   //测试时间
}
```

> 响应体:

```javascript
//删除成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": "delete ok"
}
//未找到记录
{
    "code": "400",
    "message": "Record doesn't exist !",
    "success": false
}
```

# 2.3 Delete all record by id 删除对应id所有记录

> 请求地址:  http://example:8081/api/result/del/all    请求方式:  **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "22"
}
```

> 响应体:

```javascript
//删除成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": "delete 1 records"
}

//未找到删除记录
{
    "code": "400",
    "message": "nothing delete",
    "success": false
}
```

# 2.4 Get record by id and time 根据id和时间获取单条记录

> 请求地址:  http://example:8081/api/result/data   请求方式:  **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "1",
    "test_date_time": "2021-04-01 09:29:42"
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": null,
        "index": 52,
        "id": "1",
        "image_url": "444",
        "test_date_time": "2021-04-01 09:29:42",
        "total_score": 8,
        "blackhead": 8,
        "dark_circle": 8,
        "wrinkle": 8,
        "pore": 8,
        "pockmark": 8,
        "spot": 8,
        "roughness": 8,
        "moisture": 8,
        "texture": 8,
        "chloasma": 8,
        "skin_api_result": null
    }
}

//未找到记录
{
    "code": "400",
    "message": "search no data",
    "success": false
}
```

# 2.5 Get latest record 获取最新的测服记录

> 请求地址:  http://example:8081/api/result/data/latest     请求方式:  **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "1"
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": null,
        "index": 52,
        "id": "1",
        "image_url": "444",
        "test_date_time": "2021-04-01 09:29:42",
        "total_score": 8,
        "blackhead": 8,
        "dark_circle": 8,
        "wrinkle": 8,
        "pore": 8,
        "pockmark": 8,
        "spot": 8,
        "roughness": 8,
        "moisture": 8,
        "texture": 8,
        "chloasma": 8,
        "skin_api_result": null
    }
}

//未找到数据
{
    "code": "400",
    "message": "search no data",
    "success": false
}
```

# 2.6 Get same age scores  获取同年龄段平均数

> 请求地址:  http://example:8081/api/result/score   请求方式:  **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "birthday": "2021-03-22"
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": null,
        "index": null,
        "id": null,
        "image_url": null,
        "test_date_time": null,
        "total_score": null,
        "blackhead": 20,
        "dark_circle": 100,
        "wrinkle": 99,
        "pore": 99,
        "pockmark": 0,
        "spot": 99,
        "roughness": 99,
        "moisture": 99,
        "texture": 99,
        "chloasma": 99,
        "skin_api_result": null
    }
}

//响应失败
{
    "code": "400",
    "message": "search error",
    "success": false
}
```

# 2.7 Delete multi records 根据id和主键删除多条记录

> 请求地址:  http://example:8081/api/result/del/multi    请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "ios_1q2w3e4r",
    "type": "line",
    "index_list": "60,61",   //data_info 表中的主键index索引
    "id": "1234567"          //id用户名
}
```

> 响应体:

```javascript
//删除成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": "delete ok"
}
//未找到数据
{
    "code": "400",
    "message": "nothing delete",
    "success": false
}
```

# 3.0 Add my today info 添加今日数据

> 请求地址:  http://example:8081/api/today     请求方式:  **POST**

------

> 请求体:

```javascript
{ 
    "key": "android_1q2w3e4r",
    "type": "normal",
    "id": "lzq2006123",
    "record_date": "2021-03-04",
    "feeling": "good",
    "sleep": "5h",
    "exercise": "10m",
    "appetite": "normal",
    "water": "1L",
    "defecation": "1 time",
    "memo": "hello"
}
```

> 响应体:

```javascript
//成功响应
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "normal",
        "id": "lzq2006123",
        "record_date": "2021-03-04",
        "feeling": "good",
        "sleep": "5h",
        "exercise": "10m",
        "appetite": "normal",
        "water": "1L",
        "defecation": "1 time",
        "memo": "hello"
    }
}

//id用户不存在
{
    "code": "400",
    "message": "id: lzq20061239 doesn't exist !",
    "success": false
}
```

# 3.1 Get my today info 根据日期获得今日数据

> 请求地址:  http://localhost:8081/api/today/**{id}**        请求方式:  **GET**
>
> 请求示例:  http://localhost:8081/api/today/lzq2006123?key=ios_1q2w3e4r&type=normal&record_date=2021-03-04

------

> 请求参数:

| key         | ios_1q2w3e4r                   |
| ----------- | ------------------------------ |
| type        | normal                         |
| record_date | 2021-03-04     //today数据日期 |

> 返回体:

```javascript
//获取成功
{
    "code": "200",
    "message": "Success",
    "success": true,
    "body": {
        "type": "normal",
        "id": "lzq2006123",
        "record_date": "2021-03-04",
        "feeling": "good",
        "sleep": "5h",
        "exercise": "10m",
        "appetite": "normal",
        "water": "1L",
        "defecation": "1 time",
        "memo": "hello"
    }
}
//没有获取到数据
{
    "code": "400",
    "message": "今日のデータがありません",
    "success": false
}
```

# 4.0 Send sms for register 新用户验证注册

> 请求地址:   http://example:8081/api/user/sns/verify    请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "email": "857018877@qq.com",             //email和tel只能传一个,不能同时传递
    "tel":null,                              //email和tel只能传一个,不能同时传递
    "gender":1,
    "name":"hahaha",
    "job":"工人",
    "address":"hahah",
     "birthday":"2010-1-1",
    "password":"12345678",
    "idname":"cgx41999",                    //idname 对应用户表id字段, 如果没传该参数,会自动生成id
    "zone":"81",                            //国家区号, 如果注册成功,传入的zone会写入主表
    "avatar": "161873009247753952.png"      //上传头像是获取的图片名
}
```

> 响应体:

```javascript


//如果只填写了邮箱,则是邮箱送信中,如果值填写电话则是电话送信中
{
    "code": "200",
    "message": "邮箱送信中",
    "success": true
}

//id已存在  (对应idname参数)
{
    "code": "400",
    "message": "id exist",
    "success": false
}

//邮箱已存在
{
    "code": "LME0009",
    "message": "邮箱已存在",
    "success": false
}
//电话已存在
{
    "code": "LME0003",
    "message": "电话已存在",
    "success": false
}
```

# 4.1 Check id active 查询id是否激活

> 请求地址:   http://example:8081/api/user/check/active/**{id}**          请求方式:  **GET**
>
> 请求示例:   http://example:8081/api/user/check/active/babalala?key=android_1q2w3e4r&type=normal

------

> 响应体:

```javascript
//已激活
{
    "code": "200",
    "message": "已激活",
    "success": true
}
//未激活
{
    "code": "400",
    "message": "未激活",
    "success": false
}
```

# 4.2 Change tel by SNS 短信改手机号

> - **需要**原手机号存在的情况下, 请求地址:http://example:8081/api/user/sns/ctel    请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "num":"12554512253",         //原号码,如果不存在会提示400状态码
    "newnum":"12554512253",     //新号码,  对新号码发送短信
    "index":"69",               //用户索引主键 index字段,电话所对应的用户主键
    "zone":"86"                 //新号码zone区域  发短信必须
}
```

> 响应体:

```javascript
//成功返回
{
    "code": "200",
    "message": "电话送信中",
    "success": true
}

//原电话不存在
{
    "code": "400",
    "message": "电话不存在",
    "success": false
}

//新号码已存在
{
    "code": "LME0003",
    "message": "新号码已存在",
    "success": false
}
```

> - **不需要**原手机号存在  请求地址:http://example:8081/api/user/update/tel   请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "ios_1q2w3e4r",
    "type": "normal",
    "id": "85962",          
    "tel": "12345678941",    //修改的新号码, 发送验证短信到此手机号上
    "zone": "81"             //新号码zone
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "电话送信中",
    "success": true
}
//送信失败
{
    "code": "400",
    "message": "电话送信失败",
    "success": false
}
```

# 4.3 Change email by SES 邮件修改邮箱

> - **需要**原邮箱存在的情况,  请求地址:  http://example:8081/api/user/sns/cemail   请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "email":"8888888777@qq.com",     //原来的邮箱,会验证原来的邮箱是否存在
    "newemail":"857018877@qq.com",   //新邮箱, 对新邮箱发送验证邮件
    "index":"107",                   //用户索引主键index,  邮箱所对应的用户主键
    "zone":"86"                      //用户国家区域
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "邮件送信中",
    "success": true
}
//原邮箱不存在
{
    "code": "400",
    "message": "邮箱不存在",
    "success": false
}
//新邮箱已经存在
{
    "code": "LME0009",
    "message": "新邮箱已存在",
    "success": false
}
```

> - **不需要**原邮箱的存在  请求地址:  http://example:8081/api/user/update/email    请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "ios_1q2w3e4r",
    "type": "normal",
    "id": "85962",
    "email": "857018877@qq.com"
}
```

> 响应体:

```javascript
//送信成功
{
    "code": "200",
    "message": "邮箱送信中",
    "success": true
}
//送信失败 id不存在
{
    "code": "400",
    "message": "邮箱送信失败",
    "success": false
}
//新邮箱已存在
{
    "code": "400",
    "message": "新邮箱已存在",
    "success": false
}
```

# 4.4 Change password sns 短信/邮件修改密码

> 请求地址:  http://example:8081/api/user/sns/cpass    请求方式:  **POST**

------

> 请求体:

```javascript
{
    "key": "android_1q2w3e4r",
    "type": "normal",
    "email": null,				 //主表中存在的 的邮箱     (邮箱和电话只能二选一,不能同时存在)
    "tel": "985900370599999",    //主表中存在的 的电话号码  (邮箱和电话只能二选一,不能同时存在)
    "zone":"1",                  //对应发送短信所需的区域, 如果是邮箱改密码zone值填"81"即可
    "password":"8888888"
}
```

> 响应体:

```javascript
//响应成功
{
    "code": "200",
    "message": "电话送信中",
    "success": true
}
//根据电话或邮箱未找到用户
{
    "code": "400",
    "message": "not found user",
    "success": false
}
```
