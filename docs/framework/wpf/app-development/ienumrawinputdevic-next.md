---
title: "IEnumRAWINPUTDEVIC:Next | Microsoft Docs"
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
  - "次のメソッド"
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# IEnumRAWINPUTDEVIC:Next
列挙子の一覧で次の  `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) 構造を列挙し、実際に `pceltFetched` に列挙された要素の数とともに `rgelt` に返します。  
  
## 構文  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### パラメーター  
 `celt`  
  
 \[in\] `rgelt` に返される [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) 構造の数。  
  
 `rgelt`  
  
 \[out\] 列挙された RAWINPUTDEVICE 構造体を受け取る size celt \(またはそれ以上\) の配列。  
  
 `pceltFetched`  
  
 \[out\] `rgelt` に実際に指定された要素の数へのポインター。  `rgelt` が 1 の場合、呼び出し元は `NULL` に渡すことができます。  
  
## プロパティ値\/戻り値  
 指定された要素の数が `celt` の場合は HRESULT: S\_OK。それ以外の場合は S\_FALSE。