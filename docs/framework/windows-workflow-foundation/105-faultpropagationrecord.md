---
title: "105 - FaultPropagationRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 105 - FaultPropagationRecord
## プロパティ  
  
|||  
|-|-|  
|ID|105|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|Warning \(警告\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー インスタンスを持つアクティビティが FaultPropagationRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## メッセージ  
 TrackRecord \= FaultPropagationRecord、InstanceID\=%1、RecordNumber\=%2、EventTime\=%3、FaultSourceActivityName\=%4、FaultSourceActivityId\=%5、FaultSourceActivityInstanceId\=%6、FaultSourceActivityTypeName\=%7、FaultHandlerActivityName\=%8、 FaultHandlerActivityId \= %9、FaultHandlerActivityInstanceId \=%10、FaultHandlerActivityTypeName\=%11、Fault\=%12、IsFaultSource\=%13、Annotations\=%14、ProfileName \= %15  
  
## 詳細  
  
|データ項目名|データ項目型|説明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベンの生成時刻 \(UTC\)。|  
|FaultSourceActivityName|xs:string|エラーを生成したアクティビティの名前。|  
|FaultSourceActivityId|xs:string|エラーを生成したアクティビティの ID。|  
|FaultSourceActivityInstanceId|xs:string|エラーを生成したアクティビティのインスタンス ID。|  
|FaultSourceActivityTypeName|xs:string|エラーを生成したアクティビティのタイプ。|  
|FaultHandlerActivityName|xs:string|エラー ハンドラー アクティビティの表示名。|  
|FaultHandlerActivityId|xs:string|エラー ハンドラー アクティビティの ID。|  
|FaultHandlerActivityInstanceId|xs:string|エラー ハンドラー アクティビティのインスタンス ID。|  
|FaultHandlerActivityTypeName|xs:string|エラー ハンドラー アクティビティのタイプ。|  
|Fault|xs:string|エラーの詳細。|  
|IsFaultSource|xs:unsignedByte|イベントがエラー ソースから生成されたかどうかを示します。|  
|Annotations|xs:string|このイベントに追加された注釈。値は、\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items という形式で XML 要素に格納されます。注釈が指定されていない場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、"Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名" と定義されます。たとえば、"Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService" と定義されます。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|