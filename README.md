/**
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
 */
var yzm = 'yzma';//验证码，5分钟过期，建议刷票前一两分钟填入
var sj = 500;//刷新时间：500为1秒2次，1000为1秒1次
var i,cc,refreshImg2 = refreshImg;
refreshImg = function(a,b,c){ return true }//验证码过滤
var timer = setInterval(function(){
    $('#query_ticket').removeClass('btn-disabled').click();
    setTimeout(function(){
        if($('a.btn72').length > 0){
            clearInterval(timer);
            refreshImg = refreshImg2;//恢复原始获取验证码功能
            $('#randCode, #randCode2').val(yzm).keyup();//填入验证码
        }
    }, sj);
}, sj);

//循环刷新
window.setTimeout2 = window.setTimeout;
window.setTimeout = function(f, t){
    if(t == sj) window.setTimeout2(f, sj);
    else window.setTimeout2(f, t);
}
