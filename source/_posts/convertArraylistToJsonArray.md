---
title: "[JAVA] Convert ArrayList To JsonArray"
date: 2018-02-26 10:32:34
categories:
	- Develop
tags:
	- Java
	- ArrayList
	- Convert
	- JsonArray
---

將 ArrayList 轉變成 JsonArray

<!-- more -->

Code :
``` java
import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;
import java.util.ArrayList;
import java.util.Map;

public JSONArray arrayListToJson(ArrayList<Map<String, Object>> list){
    JSONArray jsonArr = new JSONArray();
    for(Map<String, Object> map : list){
        JSONObject jsonObj = new JSONObject();
        for(Map.Entry<String, Object> entry : map.entrySet()){
            String key = entry.getKey();
            Object val = entry.getValue();
            try {
                jsonObj.put(key, val);
            } catch (JSONException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        jsonArr.put(jsonObj);
    }
    return jsonArr;
}
```