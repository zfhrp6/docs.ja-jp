---
title: "コア通信 : TCP トランスポート チャネル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c00c32ff93fd06250127f88ff5317c6daed18c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="core-communications-tcp-transport-channels"></a>コア通信 : TCP トランスポート チャネル
ここでは、TCP トランスポート チャネル によって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|指定したソケットのリモート エンドポイントは、割り当てられたタイムアウト時間内に終了要求に応答しませんでした。 この原因としては、リモート エンドポイントが Receive 操作から EOF 信号 (NULL) を受信した後に Close を呼び出していない可能性があります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|
