Android Intent
============

1. Overview
------

* Android Intent is aimed to provide developers with an intent to start a android phone in the method call via js.
  * Web Intent:
      Web Intent is a mechanism similar to the android intent, but its purpose is for web, namely simulated android intent on the web.
  * Android Intent:
      Android Intent is a startup intent on android phones in the way.
  * For pea pod treasure bag, the need for a comprehensive two features to achieve a passing js way to start an intent on the phone.

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

4. Return Value
--------

 Call startActivity () return value is as follows :
 
<pre>
   "PERMISSION_DENY" The intent is not entitled to use
   "SYSTEM_ERROR" System Error
   "NOT_CONNECTED" no phone connection
   "OK" intent sent successfully
</pre>


5. Android intent and meaning of each parameter :
--------

* Action
 - ACTION_CALL
 - ACTION_EDIT
 - ACTION_MAIN
 - ACTION_SYNC
 - ACTION_BATTERY_LOW
 - ACTION_HEADSET_PLUG
 - ACTION_SCREEN_ON
 - ACTION_TIMEZONE_CHANGED

* Type
 - Intent explicitly specify data types (MIME)

* Data
 - Perform an action to operate the data

* Category
 - Additional information is to perform an action , the format is json

* Constant
 - CATEGORY_BROWSABLE
 - CATEGORY_GADGET
 - CATEGORY_HOME
 - CATEGORY_LAUNCHER
 - CATEGORY_PREFERENCE

* Component
 - Specify the class name of the target component of Intent

* Extras
 - All other additional information collection , json format

<pre>
     extra data format as follows :
     {
       "key": "",
       "value": "",
       "type": ""
     }
</pre>

    Which type values ​​are as follows :
    
    * E extra in the value of string type
    * Esn extra ignore the value of values
    * Ez extra value to bool type in
    * Ei extra value of type int
    * El extra in the value of long type
    * Ef extra value to float in
    * Eu extra type of value for the uri
    * Ecn extra in the value of component name ( only usb mode, this value is valid )
    * Eia extra in value as int array types ( eg : 1 , 2, 3 )
    * Ela extra for the long array of value types ( eg : 1 , 2, 3 )
    * Efa extra in the value of float array types ( eg : 1.1 , 2.1, 3 )

* Flags
 - Control startup parameters

6. Sample
------

* Query location on the map

<pre>
    var i = new AndroidIntent("android.intent.action.VIEW", // action
                         "", // type
                         "geo:0,0?q=shanghai", // data
                         "", // category
                         "", //component,
                         "");
    i.startActivity();
</pre>

* Texting

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

* Add Calendar

<pre>
    var extras = [];
    var extra = {};
    
    // Name calendar of events
    extra.key = "title";
    extra.value = "title_test";
    extras.push(extra);

    // Description of the event
    extra = {};
    extra.key = "description";
    extra.value = "description_test111";
    extras.push(extra);

    // Start time of the event
    extra = {};
    extra.key = "beginTime";
    extra.value = "1351684995000";
    extra.type = "el";
    extras.push(extra);

    // End time of the event
    extra = {};
    extra.key = "endTime";
    extra.value = "1351740880000";
    extra.type = "el";
    extras.push(extra);

    // Mark is "all day"
    extra = {};
    extra.key = "allDay";
    extra.value = "false";
    extra.type = "ez";
    extras.push(extra);

    // Place of incident
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
