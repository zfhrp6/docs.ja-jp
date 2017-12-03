---
title: 104 - ActivityScheduledRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36196f6814081a059e4a04de0ee9f0dd42d79bbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="104---activityscheduledrecord"></a>104 - ActivityScheduledRecord
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|104|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ワークフロー インスタンス内のアクティビティが ActivityScheduledRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>メッセージ  
 TrackRecord = ActivityScheduledRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、Name = %4、ActivityId = %5、ActivityInstanceId = %6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|子アクティビティをスケジュールしたアクティビティの名前|  
|ActivityId|xs:string|子アクティビティをスケジュールしたアクティビティの ID|  
|ActivityInstanceId|xs:string|子アクティビティをスケジュールしたアクティビティのインスタンス ID|  
|ActivityTypeName|xs:string|操作のキャンセルを要求したアクティビティの型|  
|ChildActivityName|xs:string|スケジュール済みアクティビティの名前|  
|ChildActivityId|xs:string|スケジュール済みアクティビティの ID|  
|ChildActivityInstanceId|xs:string|スケジュール済みアクティビティのインスタンス ID|  
|ChildActivityTypeName|xs:string|スケジュール済みアクティビティの型|  
|コメント|xs:string|このイベントに追加された注釈。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。  注釈が指定されていない場合、文字列が含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
