 * 12306抢票神器
 * 功能：可绕过验证码和自动刷新
 * By yaosine.github.io @ 2013春运
 * 执行步骤：
	 * 1.登录12306网站，填写购票信息，选好乘车人、车次和席别，并勾选自动提交
	 * 2.获取验证码，在新页面打开URL: 
	 	*       https://kyfw.12306.cn/otn/passcodeNew/getPassCodeNew?module=login&rand=sjrand
	 * 3.核对验证码，将验证码替换第一行代码中的yzma，
	 	*       核对验证码是否正确：https://kyfw.12306.cn/otn/passcodeNew/checkRandCodeAnsyn?rand=sjrand&randCode=yzma
	 	*       正确："data":"Y"，错误："data":"N"
	 * 4.控制台执行代码，在12306服务不瘫痪情况下一出票即可秒下订单
 * 控制台：360浏览器、搜狗浏览器在极速模式下右键->审查元素->console，谷歌、火狐等按F12即可打开控制台
 * 温馨提示：抢票有风险，请勿过于依赖，祝你抢票顺利！
