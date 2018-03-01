---
title: IWpfHostSupport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a516d5917c2106bc83842befac9b506312fcce1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
ホストするアプリケーション[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]PresentationHost.exe 経由のコンテンツは、ホストと PresentationHost.exe 間の統合ポイントを提供するには、このインターフェイスを実装します。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]Web ブラウザーなどのアプリケーションをホストできます[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]コンテンツを含む[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]XAML が失われるとします。 ホストに[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]コンテンツ、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]アプリケーションのインスタンスを作成する、 [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)です。 ホストされる[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]PresentationHost.exe、提供、ホスト型のインスタンスを作成[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]で表示するホストへのコンテンツ、 [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)です。  
  
 有効になっている統合`IWpfHostSupport`に PresentationHost.exe を許可。  
  
-   検出し、ホスト アプリケーションが有用で生入力デバイス (ヒューマン インターフェイス デバイス) を登録します。  
  
-   ホスト アプリケーションに登録済みの生の入力デバイスと適切なメッセージを転送からの入力メッセージを受信します。  
  
-   進行状況とエラーのカスタム ユーザー インターフェイスのホスト アプリケーションのクエリを実行します。  
  
> [!NOTE]
>  この API は、ローカル クライアント コンピューターでの使用のみを目的とし、サポートされています。  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|E_NOTIMPL が返されない限り、メッセージを受信するたびに PresentationHost.exe によって呼び出されます。|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|既定では、PresentationHost.exe は、独自の展開の進行状況と配置エラー WPF コンテンツが展開されているときに表示されるユーザー インターフェイス。|
