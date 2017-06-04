---
title: "103 - ActivityStateRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 103 - ActivityStateRecord
## プロパティ  
  
|||  
|-|-|  
|Id|103|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|Information \(情報\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー インスタンス内のアクティビティが ActivityStateRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## メッセージ  
 TrackRecord \= ActivityStateRecord、InstanceID \= %1、RecordNumber\=%2、EventTime\=%3、State \= %4、Name\=%5、ActivityId\=%6、ActivityInstanceId\=%7、ActivityTypeName\=%8、Arguments\=%9、Variables\=%10、Annotations\=%11、ProfileName \= %12  
  
## 詳細  
  
|データ項目名|データ項目型|説明|  
|------------|------------|--------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 \(UTC\)|  
|State|xs:string|アクティビティの状態|  
|Name|xs:string|イベントを生成したアクティビティの表示名|  
|ActivityId|xs:string|生成したアクティビティのアクティビティ ID|  
|ActivityInstanceId|xs:string|生成したアクティビティのアクティビティ インスタンス ID|  
|ActivityTypeName|xs:string|生成したアクティビティの型名|  
|Arguments|xs:string|このイベントで追跡された引数。値は、\<items\>\<\> item  name \= "argumentName" type\="System.String"\<argumentValue\>\<\/item\>\/items という形式で XML 要素に格納されます。引数が追跡されなかった場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。string、char、bool、int、short、long、uint、ushort、ulong、System.Single、float、double、System.Guid、System.DateTimeOffset、および System.DateTime の各型は、ToString\(\) から返される値として格納されます。その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|Variables|xs:string|このイベントで追跡された変数。値は、\<items\>\<\> item  name \= "variableName" type\="System.String"\<variableValue\>\<\/item\>\/items という形式で XML 要素に格納されます。変数が追跡されなかった場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、変数の値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。string、char、bool、int、short、long、uint、ushort、ulong、System.Single、float、double、System.Guid、System.DateTimeOffset、および System.DateTime の各型は、ToString\(\) から返される値として格納されます。その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|Annotations|xs:string|このイベントに追加された注釈。値は、\<items\>\<\> item  name \= "annotationName" type\="System.String"\<annotationValue\>\<\/item\>\/items という形式で XML 要素に格納されます。注釈が指定されていない場合は、文字列に \<items\/\> が含まれます。ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。イベントのサイズが ETW の制限を超えると、注釈が破棄され、注釈値が \<items\>...\<\/items\> に置き換えられて、イベントが切り捨てられます。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、"Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名" と定義されます。たとえば、"Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService" と定義されます。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|