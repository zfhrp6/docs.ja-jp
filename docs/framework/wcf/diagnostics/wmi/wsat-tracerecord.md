---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487777"
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
