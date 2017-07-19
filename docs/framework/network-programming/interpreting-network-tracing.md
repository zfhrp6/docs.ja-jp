---
title: "ネットワークのトレースの解釈 | Microsoft Docs"
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
  - "TraceMode 属性"
  - "16 進数データ、ネットワークのトレース出力"
  - "ネットワークのトレース、分析"
  - "protocolonly"
  - "テキスト、ネットワークのトレース出力"
  - "includehex"
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# ネットワークのトレースの解釈
ネットワーク追跡を有効にすると、アプリケーションはさまざまな <xref:System.Net> クラスのメンバにする通話の取り込みに追跡を使用できます。  これらの通話の出力は、次の例に類似する場合があります。  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 前の例では、\[588\]期限内のスレッドの固有 ID です。  \(4357\) および \(4387\) アプリケーションが開始されてから経過したミリ秒数を表示するタイムスタンプがあります。  タイムスタンプのデータが方法 **Socket.Send**を入力し、完了したアプリケーションを示します。  **\[送信\]** 方法を実行している対象に固有 ID として 33574638 があります。  方法の終了の追跡は、戻り値 \(前の例の 61\) が含まれます。  
  
 ネットワーク追跡は送信したり、自分のアプリケーションによってアプリケーション \(File Transfer Protocol\) などのアプリケーション レベルのセキュリティを使用して受信されているネットワーク トラフィックを取得できます。  このデータはテキストとして 16 桁数なデータとオプションで取得できます。  小数点以下 16 桁数なデータが **tracemode** の属性値として **\[includehex\]** の指定に使用できます。  \(この属性に関する詳細については、[方法へまたは: ネットワーク追跡をコンフィギュレーションします。](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)を参照してください。次の例の追跡は **\[includehex\]**を使用して生成します。  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 小数点以下に 16 のデータを省略するには、**tracemode** の属性の値として **\[protocolonly\]** を指定します。  次の例では、**\[protocolonly\]** が指定されている場合追跡を示します。  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## 参照  
 [ネットワークのトレースの有効化](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [方法へまたは: ネットワーク追跡をコンフィギュレーションします。](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [.NET Framework のネットワークのトレース](../../../docs/framework/network-programming/network-tracing.md)