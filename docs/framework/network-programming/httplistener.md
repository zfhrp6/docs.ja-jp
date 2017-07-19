---
title: "HttpListener | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "HTTP"
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# HttpListener
<xref:System.Net.HttpListener> クラスは、プログラムによって制御できる HTTP プロトコル リスナーを提供します。  リスナーは、<xref:System.Net.HttpListener> オブジェクトの有効期間にわたってアクティブで、アプリケーション内で実行されます。  
  
## HTTP.SYS  
 <xref:System.Net.HttpListener> クラスは、Windows のすべての HTTP トラフィックを処理するカーネル モード リスナーである HTTP.sys の上に構築されています。  HTTP.sys は、接続管理、帯域幅の調整、および Web サーバーのログ記録を提供します。  SSL 証明書の追加には `HttpCfg.exe` ツールを使用します。  詳細については、[サーバー](http://go.microsoft.com/fwlink/?LinkID=178285)に関するドキュメント内の [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) ツールに関するドキュメントを参照してください。  
  
## 参照  
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.HttpWebResponse>   
 [HTTP サーバー](http://go.microsoft.com/fwlink/?LinkID=178285)   
 [インターネット インフォメーションにおけるセキュリティの強化](http://go.microsoft.com/fwlink/?LinkID=178286)   
 [HttpListener ASPX ホスト アプリケーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=179560)   
 [HttpListener テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179558)   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)