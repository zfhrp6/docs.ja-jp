---
title: "IEnumRAWINPUTDEVIC:Skip | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Skip メソッド"
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Skip
列挙体の次の `celt` 個の要素をスキップするように列挙子に指示し、それらの要素が次の [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) の呼び出しで返されないようにします。  
  
## 構文  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### パラメーター  
 `celt`  
  
 \[in\] スキップする要素の数。  
  
## プロパティ値\/戻り値  
 HRESULT : スキップされた要素の数が `celt` の場合は S\_OK。それ以外の場合は S\_FALSE。