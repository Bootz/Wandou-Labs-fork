Android Intent
============

1. Overview
------

 * Android Intent的目的是为了给开发者提供一个通过js调用在android手机上启动一个intent的方法。
 * Web Intent：
     Web Intent是类似与android intent的一个机制，但是它的目的还是用于web，即在web上模拟android intent。
 * Android Intent：
     Android Intent是一个在android手机上启动intent的方式。
 * 对于豌豆荚百宝袋而言，需要综合两种的特点，实现一种通过js的方式来在手机上启动一个intent。

2. Design
------


    interface AndroidIntent { 
        attribute DOMString action; 
        attribute DOMString type; 
        attribute DOMString data; 
        attribute DOMString category; 
        attribute DOMString component; 
        attribute DOMString extras; 
        attribute long flags;

        void startActivity();
    };

3. Implementation
--------

    var component = "com.wandoujia.phoenix2/com.wandoujia.phoenix2.ui.WelcomeActivity";
    var extras = [];
 
    var item = {};
    item.key = "phoenix.intent.extra.USER_AGENT";
    item.value = "wandoujia";
    extras.push(item);

    var i = new AndroidIntent("","","",
                             JSON.stringify(category),
                             component,
                             JSON.stringify(extras));
    // i.setFlags(0);

    i.startActivity();

4. 返回值
--------
 调用 startActivity() 返回值如下：
 <pre>
   "PERMISSION_DENY"  无权使用该 intent
   "NOT_USB"          该 intent 需要 usb 模式
   "NOT_CONNECTED"    无手机连接
   "OK"               intent 发送成功
 </pre>

5. 各个参数的含义与android intent的含义一致：
----
* action
 - ACTION_CALL
 - ACTION_EDIT
 - ACTION_MAIN
 - ACTION_SYNC
 - ACTION_BATTERY_LOW
 - ACTION_HEADSET_PLUG
 - ACTION_SCREEN_ON
 - ACTION_TIMEZONE_CHANGED

* type
 - 显式指定Intent的数据类型（MIME）
* data
 - 执行动作要操作的数据
* category
 - 被执行动作的附加信息，格式为json

* Constant
 - CATEGORY_BROWSABLE
 - CATEGORY_GADGET
 - CATEGORY_HOME
 - CATEGORY_LAUNCHER
 - CATEGORY_PREFERENCE

 

* component
 - 指定Intent的的目标组件的类名称
* extras
 - 其它所有附加信息的集合，格式为json

    extra 数据格式定义如下：
     {
       "key":"",
       "value":"",
       "type":""
     }

    其中 type 取值如下：
    
    * e    extra 中的 value 为 string 类型
    * esn  extra 中的忽略 value 的取值
    * ez   extra 中的 value 为 bool 类型
    * ei   extra 中的 value 为 int 类型
    * el   extra 中的 value 为 long 类型
    * ef   extra 中的 value 为 float 类型
    * eu   extra 中的 value 为 uri 类型
    * ecn  extra 中的 value 为 component name(只有 usb 模式，该值有效)
    * eia  extra 中的 value 为 int array 类型(如：1, 2, 3)
    * ela  extra 中的 value 为 long array 类型(如：1, 2, 3)
    * efa  extra 中的 value 为 float array 类型(如：1.1, 2.1, 3)

* flags
 - 控制启动参数


6. Sample
------
* 在地图上查询地点
<pre>
    var i = new AndroidIntent("android.intent.action.VIEW", // action
                         "", // type
                         "geo:0,0?q=shanghai", // data
                         "", // category
                         "", //component,
                         "");
    i.startActivity();
</pre>

* 发短信
<pre>
    var extras = [];
    var extra = {};
    extra.key = "sms_body";
    extra.value = "sms_body_test";
    extras.push(extra);

    var i = new AndroidIntent("android.intent.action.SENDTO", // action
                         "", // type
                         "sms:10086", // data
                         "", // category
                         "", //component,
                         JSON.stringify(extras));
    i.startActivity();
</pre>

* 添加日历
<pre>
    var extras = [];
    var extra = {};
    
    // 日历事件的名称
    extra.key = "title";
    extra.value = "title_test";
    extras.push(extra);

    // 事件的描述
    extra = {};
    extra.key = "description";
    extra.value = "description_test111";
    extras.push(extra);

    // 事件的开始时间
    extra = {};
    extra.key = "beginTime";
    extra.value = "1351684995000";
    extra.type = "el";
    extras.push(extra);

    // 事件的结束时间
    extra = {};
    extra.key = "endTime";
    extra.value = "1351740880000";
    extra.type = "el";
    extras.push(extra);

    // 标记是否为 "全天"
    extra = {};
    extra.key = "allDay";
    extra.value = "false";
    extra.type = "ez";
    extras.push(extra);

    // 事件的地点
    extra = {};
    extra.key = "eventLocation";
    extra.value = "The gym";
    extras.push(extra);

    var i = new AndroidIntent("android.intent.action.EDIT",
                         "vnd.android.cursor.item/event",
                         "", // data
                         "", // category
                         "", //component,
                         JSON.stringify(extras));
    i.startActivity();
</pre>