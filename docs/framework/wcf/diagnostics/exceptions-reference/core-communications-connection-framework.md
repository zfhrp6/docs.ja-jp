---
title: "コア通信 : 接続フレームワーク"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 878d2b01ee22d339115925e101f7349ecd5207bd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-connection-framework"></a>コア通信 : 接続フレームワーク
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 接続フレームワークによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|CloseTimedOut|Close メソッドは、指定された時間の経過後にタイムアウトしました。 Close の呼び出しに渡されるタイムアウト値を増やすか、バインディングの CloseTimeout 値を増やします。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|  
|ContentTypeMismatch|指定されたものを予期していたサービスに対して、指定されたコンテンツ タイプが送信されました。 クライアントとサービスのバインディングは一致しない場合もあります。|  
|DuplexChannelAbortedDuringOpen|指定対象への二重チャネルは、開始処理中に中止されました。|  
|FramingValueNotAvailable|完全にデコードされていないため、値にアクセスできません。|  
|OperationAbortedDuringConnectionEstablishment|指定対象への接続の確立中に操作が中止されました。|  
|ReceiveTimedOut2|受信操作は指定された時間の経過後にタイムアウトになります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|  
|SendCannotBeCalledAfterCloseOutputSession|CloseOutputSession の呼び出し後にチャネルでメッセージを送信することはできません。|
