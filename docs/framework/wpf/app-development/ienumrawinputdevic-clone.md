---
title: "IEnumRAWINPUTDEVIC:Clone | Microsoft Docs"
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
  - "Clone メソッド"
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Clone
同じリストに対する反復処理を行うために、現在の列挙子と同じ状態の未加工の入力デバイス列挙子を別に作成します。  
  
## 構文  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### パラメーター  
 `ppenum`  
  
 \[out\] [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) インターフェイス ポインターを受け取る出力変数のアドレス。  メソッドが失敗した場合、この出力変数の値は未定義です。  
  
## プロパティ値\/戻り値  
 HRESULT : このメソッドは、標準の戻り値である E\_INVALIDARG、E\_OUTOFMEMORY、および E\_UNEXPECTED をサポートします。  
  
## 解説  
 このメソッドは、列挙体シーケンス内のポイントを記録して、後でそのポイントに戻ることができるようにしています。  呼び出し元は、この新しい列挙子を最初の列挙子とは別に解放する必要があります。