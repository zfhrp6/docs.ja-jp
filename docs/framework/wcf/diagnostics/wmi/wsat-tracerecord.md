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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
