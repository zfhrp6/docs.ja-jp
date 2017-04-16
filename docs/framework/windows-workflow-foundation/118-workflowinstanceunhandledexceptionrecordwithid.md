---
title: "118 - WorkflowInstanceUnhandledExceptionRecordWithId | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 118 - WorkflowInstanceUnhandledExceptionRecordWithId
## プロパティ  
  
|||  
|-|-|  
|ID|118|  
|キーワード|HealthMonitoring、WFTracking|  
|レベル|Error|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー インスタンスが WorkflowInstanceUnhandledExceptionRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## メッセージ  
 TrackRecord \= WorkflowInstanceUnhandledExceptionRecord, InstanceID \= %1、RecordNumber \= %2、EventTime \= %3、ActivityDefinitionId \= %4、SourceName \= %5、SourceId \= %6、SourceInstanceId \= %7、SourceTypeName\=%8、Exception\=%9、Annotations\= %10、ProfileName \= %11、WorkflowDefinitionIdentity \= %12  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 \(UTC\)|  
|ActivityDefinitionId|xs:string|ワークフローのルート アクティビティの名前|  
|SourceName|xs:string|失敗して unhandledException が発生した原因のアクティビティ名|  
|SourceId|xs:string|エラーの原因であるアクティビティのアクティビティ ID|  
|SourceInstanceId|xs:string|エラーの原因であるアクティビティのアクティビティ インスタンス ID|  
|SourceTypeName|xs:string|失敗して unhandledException が発生した原因のアクティビティの型名|  
|例外|xs:string|ハンドルされない例外の詳細|  
|状態|xs:string|ワークフローの現在の状態。|  
|コメント|xs:string|このイベントに追加された注釈。  値は、\<items\>\< item name \= "annotationName" type\="System.String"\>annotationValue\<\/item\>\<\/items\> という形式で XML 要素に格納されます。  注釈が指定されていない場合は、文字列に \<items\/\> が含まれます。  ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。  イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|WorkflowDefinitionIdentity|xs:string|ワークフロー定義 ID|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|