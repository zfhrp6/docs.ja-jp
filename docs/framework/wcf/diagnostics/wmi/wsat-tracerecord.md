---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>構文  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>メソッド  
 WSAT_TraceRecord クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 WSAT_TraceRecord クラスには、次のプロパティがあります。  
  
### <a name="activityid"></a>ActivityID  
 データ型: object  
アクセスの種類 : 読み取り専用  
  
 トレース レコードのアクティビティ ID です。  
  
### <a name="eventid"></a>EventID  
 データ型 : sint32  
アクセスの種類 : 読み取り専用  
  
 トレース レコードのイベント ID です。  
  
### <a name="tracerecord"></a>TraceRecord  
 データ型: string  
アクセスの種類 : 読み取り専用  
  
 トレース レコード  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
