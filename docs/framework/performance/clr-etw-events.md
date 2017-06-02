---
title: "CLR ETW イベント | Microsoft Docs"
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
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: 45
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 45
---
# CLR ETW イベント
このセクションのトピックでは、Windows イベント トレーシング \(ETW: Event Tracing for Windows\) イベントについて説明します。  各イベントには、キーワードとレベルが関連付けられています。キーワードとレベルについては、「[CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」で説明します。  CLR には、イベント用のプロバイダーとして次の 2 つがあります。  
  
-   ランタイム プロバイダー。これは、有効になっているキーワードに応じてイベントを発生させます \(キーワードとはイベントのカテゴリです\)。  CLR ランタイム プロバイダーの GUID は e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4 です。  
  
-   ランダウン プロバイダー。これには特殊な用途があります。  CLR ランダウン プロバイダーの GUID は a669021c\-c450\-4609\-a035\-5af59af4df18 です。  
  
 プロバイダーの詳細については、「[CLR ETW プロバイダー](../../../docs/framework/performance/clr-etw-providers.md)」を参照してください。  
  
## このセクションの内容  
 [ランタイム情報イベント](../../../docs/framework/performance/runtime-information-etw-events.md)  
 SKU、バージョン番号、アクティブ化の方法、起動時に使用されたコマンド ライン パラメーター、GUID \(該当する場合\) などのランタイムに関する情報をキャプチャします。  
  
 [Exception Thrown\_V1 イベント](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 スローされた例外に関する情報をキャプチャします。  
  
 [競合イベント](../../../docs/framework/performance/contention-etw-events.md)  
 ランタイムが使用するモニター ロックまたはネイティブ ロックの競合に関する情報をキャプチャします。  
  
 [スレッド プール イベント](../../../docs/framework/performance/thread-pool-etw-events.md)  
 ワーカー スレッド プールと I\/O スレッド プールに関する情報をキャプチャします。  
  
 [ローダー イベント](../../../docs/framework/performance/loader-etw-events.md)  
 アプリケーション ドメイン、アセンブリ、およびモジュールの読み込みとアンロードに関する情報をキャプチャします。  
  
 [メソッド イベント](../../../docs/framework/performance/method-etw-events.md)  
 シンボルを解決するための CLR メソッドに関する情報をキャプチャします。  
  
 [ガベージ コレクション イベント](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 ガベージ コレクションに関する情報をキャプチャして、診断とデバッグに役立つ情報を取得します。  
  
 [JIT トレース イベント](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Just\-In\-Time \(JIT\) のインライン展開と tail 呼び出しに関する情報をキャプチャします。  
  
 [相互運用イベント](../../../docs/framework/performance/interop-etw-events.md)  
 MSIL \(Microsoft Intermediate Language\) のスタブの生成とキャッシュに関する情報をキャプチャします。  
  
 [ARM のイベント](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 アプリケーション ドメインの状態に関する詳細な診断情報をキャプチャします。  
  
 [セキュリティ イベント](../../../docs/framework/performance/security-etw-events.md)  
 厳密な名前と Authenticode の検証に関する情報をキャプチャします。  
  
 [スタック イベント](../../../docs/framework/performance/stack-etw-event.md)  
 イベントの発生後にスタック トレースを生成するために他のイベントと共に使用される情報をキャプチャします。  
  
## 参照  
 [ETW のデバッグおよびパフォーマンス調整を改善します。](http://go.microsoft.com/fwlink/?LinkId=179696)   
 [Windows パフォーマンス ブログ](http://go.microsoft.com/fwlink/?LinkId=179509)   
 [.NET Framework のログ記録の制御](../../../docs/framework/performance/controlling-logging.md)   
 [CLR ETW プロバイダー](../../../docs/framework/performance/clr-etw-providers.md)   
 [CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)   
 [共通言語ランタイムの ETW イベント](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)