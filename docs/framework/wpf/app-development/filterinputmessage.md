---
title: "FilterInputMessage | Microsoft Docs"
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
  - "FilterInputMessage メソッド"
  - "未加工の入力 [WPF]"
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# FilterInputMessage
E\_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。  
  
## 構文  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### パラメーター  
 `pMsg`  
  
 \[in\] 未加工入力を取得するウィンドウに送信される WM\_INPUT メッセージ。  
  
## プロパティ値\/戻り値  
 HRESULT:  
  
 S\_OK \- フィルターはメッセージを処理せず、それ以降の処理は実行されることがあります。  
  
 S\_FALSE \- フィルターはこのメッセージを処理しました。それ以降の処理は実行されません。  
  
 E\_NOTIMPL – この値が返される場合、[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) は再度呼び出されません。  この値は、カスタムの進行状況の提供のみを対象とするホスト アプリケーションから返されることがあります。PresentationHost.exe へのエラー ユーザー インターフェイスは、PresentationHost.exe からの未加工の入力メッセージの転送を対象としていません。  
  
## 解説  
 PresentationHost.exe は、キーボード、マウス、およびリモート コントロールなどのさまざまな未加工入力デバイスのターゲットになります。  場合によって、ホスト アプリケーションでの動作は PresentationHost.exe で使用される入力に依存します。  たとえば、ホスト アプリケーションは、特定のユーザー インターフェイス要素を表示するかどうかを判断するために、特定の入力メッセージの受信に依存することがあります。  
  
 これらの動作を提供するためにホスト アプリケーションが必要な入力メッセージを受信できるようにするため、PresentationHost.exe は、[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) を呼び出して、適切な未加工の入力メッセージをホストされるアプリケーションに転送します。  
  
 ホストされるアプリケーションは、[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md) によって返される未加工の入力デバイス \(ヒューマン インターフェイス デバイス\) のセットを登録することで、未加工の入力メッセージを受信します。  
  
## 参照  
 [Microsoft API とリファレンスのカタログ](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)