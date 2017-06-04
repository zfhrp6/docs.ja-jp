---
title: "GetRawInputDevices | Microsoft Docs"
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
  - "GetRawInputDevices メソッド"
  - "未加工の入力 [WPF]"
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetRawInputDevices
PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス \(ヒューマン インターフェイス デバイス\) を検出できるようにします。  
  
## 構文  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### パラメーター  
 `ppEnum`  
  
 \[out\] 未加工入力デバイスを列挙するための [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) へのポインター。  
  
## プロパティ値\/戻り値  
 HRESULT:  
  
 S\_OK \- [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) は、S\_OK が返された場合に、PresentationHost.exe によってのみ使用されます。  
  
 E\_NOTIMPL  
  
## 解説  
 未加工入力デバイスは、キーボード、マウス、およびリモート コントロールのような比較的新しいデバイスを含む入力デバイスのセットです。  
  
 未加工の入力デバイスの一覧を取得すると、PresentationHost.exe は WM\_INPUT 通知メッセージを受信するデバイスを登録します。  
  
## 参照  
 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/winui\/winui\/windowsuserinterface\/userinput\/rawinput\/rawinputreference\/rawinputfunctions\/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)   
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)