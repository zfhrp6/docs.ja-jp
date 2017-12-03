---
title: 101 - WorkflowInstanceUnhandledExceptionRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 811b8d451625e03b47b13644a5d7330789eda7a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 - WorkflowInstanceUnhandledExceptionRecord
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|101|  
|キーワード|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|レベル|Error|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ワークフロー インスタンスが WorkflowInstanceUnhandledExceptionRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>メッセージ  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、SourceName = %5、SourceId = %6、SourceInstanceId = %7、SourceTypeName=%8、Exception=%9、Annotations= %10、ProfileName = %11  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|ActivityDefinitionId|xs:string|ワークフローのルート アクティビティの名前|  
|SourceName|xs:string|失敗して unhandledException が発生した原因のアクティビティ名|  
|SourceId|xs:string|エラーの原因であるアクティビティのアクティビティ ID|  
|SourceInstanceId|xs:string|エラーの原因であるアクティビティのアクティビティ インスタンス ID|  
|SourceTypeName|xs:string|失敗して unhandledException が発生した原因のアクティビティの型名|  
|例外|xs:string|ハンドルされない例外の詳細|  
|コメント|xs:string|このイベントに追加された注釈。  形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。  注釈が指定されていない場合、文字列が含まれる\<項目/>。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  これは、形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
