---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca0a22ff1d06485658da75a46bd408a12a3a964c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> クラスは、プログラムによって制御できる HTTP プロトコル リスナーを提供します。 リスナーは、<xref:System.Net.HttpListener> オブジェクトの有効期間にわたってアクティブで、アプリケーション内で実行されます。  
  
## <a name="httpsys"></a>HTTP.SYS  
 <xref:System.Net.HttpListener> クラスは、Windows のすべての HTTP トラフィックを処理するカーネル モード リスナーである HTTP.sys の上に構築されています。 HTTP.sys は、接続管理、帯域幅の調整、および Web サーバーのログ記録を提供します。 SSL 証明書の追加には `HttpCfg.exe` ツールを使用します。 詳細については、[サーバー](http://go.microsoft.com/fwlink/?LinkID=178285) ドキュメントで、[HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) ツールのドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [HTTP サーバー](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [インターネット インフォメーションにおけるセキュリティ強化](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [HttpListener ASPX ホスト アプリケーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [HttpListener テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)
