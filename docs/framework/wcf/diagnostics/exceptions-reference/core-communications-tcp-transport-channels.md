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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 92147e3887f9f82e37a4870ec6de767868c97c1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-tcp-transport-channels"></a>コア通信 : TCP トランスポート チャネル
ここでは、TCP トランスポート チャネル によって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|指定したソケットのリモート エンドポイントは、割り当てられたタイムアウト時間内に終了要求に応答しませんでした。 この原因としては、リモート エンドポイントが Receive 操作から EOF 信号 (NULL) を受信した後に Close を呼び出していない可能性があります。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|
