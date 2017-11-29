---
title: FilterInputMessage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b3a0e58c7485d46f004db7ea52215be60340b68
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="filterinputmessage"></a>FilterInputMessage
E_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pMsg`  
  
 [in] 未加工入力を取得するウィンドウに送信される WM_INPUT メッセージ。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:  
  
 S_OK - フィルターはメッセージを処理せず、それ以降の処理は実行されることがあります。  
  
 S_FALSE - フィルターはこのメッセージを処理しました。それ以降の処理は実行されません。  
  
 E_NOTIMPL – この値が返される場合は[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)は再度呼び出されません。 この値は、カスタムの進行状況の提供のみを対象とするホスト アプリケーションから返されることがあります。PresentationHost.exe へのエラー ユーザー インターフェイスは、PresentationHost.exe からの未加工の入力メッセージの転送を対象としていません。  
  
## <a name="remarks"></a>コメント  
 PresentationHost.exe は、キーボード、マウス、およびリモート コントロールなどのさまざまな未加工入力デバイスのターゲットになります。 場合によって、ホスト アプリケーションでの動作は PresentationHost.exe で使用される入力に依存します。 たとえば、ホスト アプリケーションは、特定のユーザー インターフェイス要素を表示するかどうかを判断するために、特定の入力メッセージの受信に依存することがあります。  
  
 ホスト アプリケーションがこれらの動作を提供するために必要な入力メッセージを受信するには、PresentationHost.exe では、呼び出すことによって、ホストされるアプリケーションに適切な未加工の入力メッセージを転送[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)です。  
  
 ホストされるアプリケーションでは、生の入力メッセージを受信によって返された生の入力デバイス (ヒューマン インターフェイス デバイス) のセットを登録して[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WM_INPUT 通知](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
