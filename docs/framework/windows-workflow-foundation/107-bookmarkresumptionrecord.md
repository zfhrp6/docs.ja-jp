---
title: "107 -- BookmarkResumptionRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 107 -- BookmarkResumptionRecord
## プロパティ  
  
|||  
|-|-|  
|Id|107|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|Information \(情報\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー インスタンスが BookmarkResumptionRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## メッセージ  
 TrackRecord \= BookmarkResumptionRecord、InstanceID\=%1、RecordNumber\=%2,EventTime\=%3、Name\=%4、SubInstanceID\=%5、OwnerActivityName\=%6、OwnerActivityId \=%7、OwnerActivityInstanceId\=%8、OwnerActivityTypeName\=%9、Annotations\=%10、ProfileName \= %11  
  
## 詳細  
  
|データ項目名|データ項目型|説明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 \(UTC\)|  
|Name|xs:string|再開したブックマークの名前|  
|SubInstanceID|xs:GUID|ブックマーク スコープの ID|  
|OwnerActivityName|xs:string|ブックマーク アクティビティの名前|  
|OwnerActivityId|xs:string|ブックマーク アクティビティの ID|  
|OwnerActivityInstanceId|xs:string|ブックマーク アクティビティのインスタンス ID|  
|OwnerActivityTypeName|xs:string|ブックマーク アクティビティの型|  
|Annotations|xs:string|このイベントに追加された注釈。値は、\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items という形式で XML 要素に格納されます。注釈が指定されていない場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、"Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名" と定義されます。たとえば、"Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService" と定義されます。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|