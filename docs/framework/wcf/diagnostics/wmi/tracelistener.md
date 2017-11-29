---
title: TraceListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c0b595-a384-4eb3-b94d-1b3be7cc7a5c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c0bba558a7b0c727dd971960ab3f9120a6aaada
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tracelistener"></a>TraceListener
TraceListener  
  
## <a name="syntax"></a>構文  
  
```  
class TraceListener  
{  
  string Name;  
  TraceListenerArgument TraceListenerArguments[];  
};  
```  
  
## <a name="methods"></a>メソッド  
 TraceListener クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 TraceListener クラスには、次のプロパティがあります。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 トレース リスナーの名前。  
  
### <a name="tracelistenerarguments"></a>TraceListenerArguments  
 データ型 : TraceListenerArgument 配列  
  
 アクセスの種類 : 読み取り専用  
  
 トレース リスナーの引数。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
