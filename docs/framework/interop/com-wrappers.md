---
title: "COM ラッパー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 呼び出し可能ラッパー"
  - "COM 相互運用機能, COM ラッパー"
  - "COM ラッパー"
  - "COM, ラッパー"
  - "相互運用 (アンマネージ コードとの), COM ラッパー"
  - "ラッパー クラス"
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# COM ラッパー
COM は、次のいくつかの重要な点で、.NET Framework オブジェクト モデルとは異なります。  
  
-   COM オブジェクトのクライアントは、COM オブジェクトの有効期間を管理する必要があります。共通言語ランタイムはその環境でのオブジェクトの有効期間を管理します。  
  
-   COM オブジェクトのクライアントは、サービスを提供するインターフェイスを要求し、インターフェイス ポインターを取得して、そのサービスが利用可能かどうかを確認します。  .NET オブジェクトのクライアントは、リフレクションを使用してオブジェクトの機能の記述を取得できます。  
  
-   .NET オブジェクトは、.NET Framework の実行環境によって管理されるメモリに常駐します。  .NET Framework の実行環境では、パフォーマンス上の理由からオブジェクトをメモリ内で移動させることができ、移動するオブジェクトに合わせてすべての参照を更新できます。  オブジェクトへのポインターを取得するアンマネージ クライアントは、そのオブジェクトに依存するので同じ場所にとどまります。  アンマネージ クライアントには、場所が固定されていないオブジェクトを扱う機構が用意されていません。  
  
 このような相違を克服するために、ランタイムは、ラッパー クラスを用意して、マネージ クライアントとアンマネージ クライアントの両方がそれぞれの環境内でオブジェクトを呼び出していると認識するようにします。  マネージ クライアントが COM オブジェクトのメソッドを呼び出すと、ランタイムが[ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW: Runtime Callable Wrapper\) を作成します。  RCW の主な役割は、マネージ参照機構とアンマネージ参照機構の相違を克服することです。  また、ランタイムは、[COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md) \(CCW: COM Callable Wrapper\) を作成して、その逆のプロセスを使用し、COM クライアントがシームレスに .NET オブジェクトのメソッドを呼び出すことができるようにします。  呼び出し元のコードと、ランタイムが作成するラッパー クラスの関係を示す図を次に示します。  
  
 ![COM ラッパーの概要](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")  
COM ラッパーの概要  
  
 ほとんどの場合、ランタイムによって生成される標準の RCW または CCW は、COM と .NET Framework の境界をまたがる呼び出しに対して適切なマーシャリングを提供します。  カスタム属性を使用することにより、オプションで、ランタイムがマネージ コードおよびアンマネージ コードを表現する方法を調整できます。  
  
## 参照  
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)   
 [Customizing Standard Wrappers](http://msdn.microsoft.com/ja-jp/c40d089b-6a3c-41b5-a20d-d760c215e49d)   
 [How to: Customize Runtime Callable Wrappers](http://msdn.microsoft.com/ja-jp/4a4bb3da-4d60-4517-99f2-78d46a681732)