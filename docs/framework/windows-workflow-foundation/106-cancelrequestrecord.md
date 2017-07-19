---
title: "106 - CancelRequestRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 106 - CancelRequestRecord
## プロパティ  
  
|||  
|-|-|  
|Id|106|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|Information \(情報\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー インスタンス内のアクティビティが cancelrequestedrecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## メッセージ  
 TrackRecord \= CancelRequestedRecord、InstanceID\=%1、RecordNumber\=%2、EventTime\=%3、Name\=%4、ActivityId\=%5、ActivityInstanceId\=%6、ActivityTypeName \= %7、ChildActivityName \= %8、ChildActivityId \= %9、ChildActivityInstanceId \= %10、ChildActivityTypeName \=%11、Annotations\=%12、ProfileName \= %13  
  
## 詳細  
  
|データ項目名|データ項目型|説明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 \(UTC\)|  
|Name|xs:string|操作のキャンセルを要求したアクティビティの名前|  
|ActivityId|xs:string|操作のキャンセルを要求したアクティビティの ID|  
|ActivityInstanceId|xs:string|操作のキャンセルを要求したアクティビティのインスタンス ID|  
|ActivityTypeName|xs:string|操作のキャンセルを要求したアクティビティの型|  
|ChildActivityName|xs:string|キャンセルされるアクティビティの名前|  
|ChildActivityId|xs:string|キャンセルされるアクティビティの ID|  
|ChildActivityInstanceId|xs:string|キャンセルされるアクティビティのインスタンス ID|  
|ChildActivityTypeName|xs:string|キャンセルされるアクティビティの型|  
|Annotations|xs:string|このイベントに追加された注釈。値は、\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items という形式で XML 要素に格納されます。注釈が指定されていない場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、"Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名" と定義されます。たとえば、"Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService" と定義されます。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|