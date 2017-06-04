---
title: "ネットワークのトレースの有効化 | Microsoft Docs"
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
  - "トレースのターゲット"
  - "ログ ファイルへのトレースの送信"
  - "トレース リスナー、ネットワークのトレース"
  - "ネットワークのトレース、有効化"
  - "CLR デバッガー"
  - "既定のリスナー"
  - "ログ、トレース"
  - "トレース出力のターゲット"
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# ネットワークのトレースの有効化
ネットワーク追跡はメソッド呼び出しに関する情報へのアクセスおよび管理アプリケーションによって生成されたネットワーク トラフィックを提供します。  自分のアプリケーションのネットワーク追跡を有効にするために、次の作業を行う必要があります:  
  
-   有効になる追跡とのコードをコンパイル。  追跡を有効にするために必要な作成者の Switch に関する詳細については [How to: Compile Conditionally with Trace and Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) を参照してください。  
  
-   トレース出力の相手方を指定します。  
  
-   ネットワーク追跡の動作をコンフィギュレーションします。  詳細については [方法: ネットワーク追跡をコンフィギュレーションします。](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) を参照してください。  
  
 また、追跡リスナーに対して共通の追跡のコピー先は、既定のリスナーとログ ファイルです。  
  
 追跡は追跡リスナーを指定する既定のリスナーを使用します。  Windows SDK と出荷される .NET Framework SDK と出荷される CLR のデバッガーなどの管理によってコードを有効にするデバッガーのコードで既定のリスナーに送信されるメッセージまたは DBwin32.exe を表示できます。  CLR のデバッガーを使用して、Tracing メッセージが **出力** のウィンドウに表示されます。  
  
 追跡を受け取る場合にファイルを使用するには、次の例で示すように、コンフィギュレーションの設定を使用してログ ファイルを指定できます。  \(コンフィギュレーション ファイルの概論については、[&#91;構成ファイル&#93;](../../../docs/framework/configure-apps/index.md)を参照してください。  
  
 ログ ファイルに追跡を送信するには、適切なコンフィギュレーション ファイルの `<system.diagnostics>` ノードに、次のノードの追加 \(アプリケーションまたは設備\)。  ニーズに合うようにファイル \(trace.log\) を変更できます。  
  
```  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## 参照  
 [ネットワークのトレースの解釈](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [.NET Framework のネットワークのトレース](../../../docs/framework/network-programming/network-tracing.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/ja-jp/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)