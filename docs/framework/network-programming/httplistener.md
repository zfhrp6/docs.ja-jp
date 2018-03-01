---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b4b8c1e916aa9382d156a197fa15c2e72e900a1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> クラスは、プログラムによって制御できる HTTP プロトコル リスナーを提供します。 リスナーは、<xref:System.Net.HttpListener> オブジェクトの有効期間にわたってアクティブで、アプリケーション内で実行されます。  
  
## <a name="httpsys"></a>HTTP.SYS  
 <xref:System.Net.HttpListener> クラスは、Windows のすべての HTTP トラフィックを処理するカーネル モード リスナーである HTTP.sys の上に構築されています。 HTTP.sys は、接続管理、帯域幅の調整、および Web サーバーのログ記録を提供します。 SSL 証明書の追加には `HttpCfg.exe` ツールを使用します。 詳細については、[サーバー](http://go.microsoft.com/fwlink/?LinkID=178285) ドキュメントで、[HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) ツールのドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [HTTP サーバー](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [インターネット インフォメーションにおけるセキュリティ強化](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [HttpListener ASPX ホスト アプリケーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [HttpListener テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)
