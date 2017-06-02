---
title: "バイナリ シリアル化 | Microsoft Docs"
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
  - "バイナリ シリアル化"
  - "バイナリ シリアル化, シリアル化について"
  - "逆シリアル化"
  - "シリアル化, シリアル化について"
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# バイナリ シリアル化
シリアル化は、オブジェクトの状態をストレージ メディアに格納するプロセスとして定義することができます。このプロセスの実行中に、オブジェクトのパブリックおよびプライベートなフィールドとクラス \(クラスを格納しているアセンブリを含む\) の名前がバイト ストリームに変換され、データ ストリームに書き込まれます。続いてオブジェクトが逆シリアル化され、元のオブジェクトの完全な複製が作成されます。  
  
 オブジェクト指向環境でシリアル化機構を実装する場合は、使いやすさと柔軟性の間での数多くのトレードオフについて考慮する必要があります。プロセスを十分に制御できる場合は、プロセスの大部分を自動化できます。たとえば、単純なバイナリ シリアル化では不十分な状況が発生する場合や、シリアル化が必要なクラス内のフィールドを決定するだけの明確な理由がある場合があります。以下のセクションでは、.NET Framework に用意されている堅牢なシリアル化機構について検討し、必要に応じてプロセスをカスタマイズするためのいくつかの重要な機能について説明します。  
  
> [!NOTE]
>  オブジェクトのシリアル化と逆シリアル化を行う際に使用した .NET Framework のバージョンが異なる場合、UTF\-8 または UTF\-7 でエンコードされたオブジェクトの状態は保持されません。  
  
## このセクションの内容  
 [シリアル化の概念](../../../docs/framework/serialization/serialization-concepts.md)  
 データをストレージに永続化するシナリオと、アプリケーション ドメインを越えてオブジェクトを受け渡しするシナリオの 2 つを例として、シリアル化の有効な利用方法について説明します。  
  
 [基本的なシリアル化](../../../docs/framework/serialization/basic-serialization.md)  
 バイナリ フォーマッタと SOAP フォーマッタを使用してオブジェクトをシリアル化する方法について説明します。  
  
 [選択的シリアル化](../../../docs/framework/serialization/selective-serialization.md)  
 クラスの一部のメンバーがシリアル化されないようにする方法について説明します。  
  
 [カスタムのシリアル化](../../../docs/framework/serialization/custom-serialization.md)  
 <xref:System.Runtime.Serialization.ISerializable> インターフェイスを使用してクラスのシリアル化をカスタマイズする方法について説明します。  
  
 [シリアル化プロセスの手順](../../../docs/framework/serialization/steps-in-the-serialization-process.md)  
 フォーマッタで <xref:System.Runtime.Serialization.Formatter.Serialize%2A> メソッドを呼び出した場合のシリアル化方法について説明します。  
  
 [バージョン トレラントなシリアル化](../../../docs/framework/serialization/version-tolerant-serialization.md)  
 アプリケーションに例外をスローさせることなく後から変更できる、シリアル化可能な型の作成方法について説明します。  
  
 [シリアル化のガイドライン](../../../docs/framework/serialization/serialization-guidelines.md)  
 オブジェクトをシリアル化するタイミングを決定するのに役立つ、いくつかの一般的なガイドラインを示します。  
  
## 関連項目  
 <xref:System.Runtime.Serialization>  
 オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。  
  
## 関連項目  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 共通言語ランタイムに付属している XML シリアル化機構について説明します。  
  
 [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)  
 シリアル化を実行するコードを記述する際に従う必要がある、安全なコーディングのガイドラインについて説明します。  
  
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)  
 .NET Framework でリモート通信に利用できるさまざまな通信方法について説明します。  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/ja-jp/1e64af78-d705-4384-b08d-591a45f4379c)  
 ASP.NET を使用して作成した XML Web サービスのプログラミング方法について説明するトピックを示します。