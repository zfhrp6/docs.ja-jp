---
title: "共通言語ランタイムの ETW イベント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLR ETW イベント"
  - "ETW, CLR イベント"
  - "ETW, 共通言語ランタイム"
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 共通言語ランタイムの ETW イベント
共通言語ランタイム \(CLR: Common Language Runtime\) は、さまざまなデバッグ イベントやプロファイリング イベントを通じて、有用な Windows イベント トレーシング \(ETW: Event Tracing for Windows\) 診断情報を提供します。  CLR ETW イベントは、Windows の ETW トレース システムを活用して、共通言語ランタイムの既存のプロファイリングとデバッグのサポートを補足します。  
  
 ETW の詳細については、MSDN の記事を参照してください。[ETW のデバッグおよびパフォーマンス調整を改善します。](http://go.microsoft.com/fwlink/?LinkID=161142) Xperf については NTDebugging ブログのエントリ [Windows Performance Toolkit \- Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) "を参照してください。  
  
 そのほかの CLR ETW ツールが使用可能に [CodePlex Web サイト](http://go.microsoft.com/fwlink/?LinkID=111138) なるように提供されます。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降のイベントに関するトピックで説明するすべてのイベントに必要です。  Windows Vista オペレーティング システムでは、最小限のサポートされているクライアントであり、Windows Server 2008 では、最小限のサポートされているサーバーです。  
  
## このセクションの内容  
 [.NET Framework のログ記録の制御](../../../docs/framework/performance/controlling-logging.md)  
 ETW イベントをキャプチャして表示するためのツールとコマンドについて説明します。  
  
 [CLR ETW プロバイダー](../../../docs/framework/performance/clr-etw-providers.md)  
 ランタイム プロバイダーとランダウン プロバイダーに関する情報を提供し、ETW データ コレクションでこれらのプロバイダーを使用する方法について説明します。  
  
 [CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 イベントのフィルター処理を可能にするランタイム プロバイダーとランダウン プロバイダーのキーワードを、カテゴリ別に説明します。  
  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)  
 CLR ETW イベント、キーワード、レベル、およびイベント データについて、詳しく説明します。  
  
## 参照  
 [.NET Framework の ETW イベント](../../../docs/framework/performance/etw-events.md)