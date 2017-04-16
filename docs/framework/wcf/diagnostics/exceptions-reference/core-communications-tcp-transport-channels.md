---
title: "コア通信 : TCP トランスポート チャネル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# コア通信 : TCP トランスポート チャネル
ここでは、TCP トランスポート チャネル によって生成されるすべての例外を示します。  
  
## 例外の一覧  
  
|リソース コード|リソースの文字列|  
|--------------|--------------|  
|SocketCloseReadTimeout|指定したソケットのリモート エンドポイントは、割り当てられたタイムアウト時間内に終了要求に応答しませんでした。  この原因としては、リモート エンドポイントが Receive 操作から EOF 信号 \(NULL\) を受信した後に Close を呼び出していない可能性があります。  この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|