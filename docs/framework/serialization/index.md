---
title: "シリアル化 | Microsoft Docs"
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
  - "オブジェクト, シリアル化"
  - "シリアル化"
  - "オブジェクトのシリアル化"
  - "XML シリアル化, が定義されている場合"
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# シリアル化
シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。シリアル化を補完するプロセスとして、ストリームをオブジェクトに変換する逆シリアル化があります。これらのプロセスを組み合わせて使用することで、データを簡単に格納および転送できます。  
  
 .NET Framework には、次の 2 つのシリアル化技術が用意されています。  
  
-   バイナリ シリアル化は、型そのものを正確に維持するため、アプリケーションを次回起動するまでの間、オブジェクトの状態を維持するのに役立ちます。たとえば、クリップボードを出力先としてオブジェクトをシリアル化することによって、そのオブジェクトを異なるアプリケーション間で共有できます。オブジェクトをシリアル化して、ストリーム、ディスク、メモリ、ネットワーク上などに出力できます。リモート処理では、シリアル化を使用して、コンピューター間やアプリケーション ドメイン間でオブジェクトを "値渡し" します。  
  
-   XML シリアル化では、パブリック プロパティとパブリック フィールドのみがシリアル化され、型そのものは維持されません。これは、データを使用するアプリケーションに制限を加えずに、データを提供または処理する場合に有効です。XML はオープン標準であるため、Web 経由でデータを共有する場合には有用な選択肢となります。SOAP も同様のオープン標準であるため、有用な選択肢です。  
  
## このセクションの内容  
 [シリアル化に関する「方法」トピック](../../../docs/framework/serialization/serialization-how-to-topics.md)  
 このセクションに含まれる、方法を説明したトピックへのリンクを示します。  
  
 [バイナリ シリアル化](../../../docs/framework/serialization/binary-serialization.md)  
 共通言語ランタイムに付属しているバイナリ シリアル化機構について説明します。  
  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 共通言語ランタイムに付属している XML シリアル化および SOAP シリアル化機構について説明します。  
  
 [シリアル化ツール](../../../docs/framework/serialization/serialization-tools.md)  
 これらのツールは、シリアル化コードの開発に役立ちます。  
  
 [シリアル化のサンプル](../../../docs/framework/serialization/serialization-samples.md)  
 サンプルでは、シリアル化の方法を示します。  
  
## 関連項目  
 <xref:System.Runtime.Serialization>  
 オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。  
  
 <xref:System.Xml.Serialization>  
 オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用できるクラスが含まれています。  
  
## 関連項目  
 [Remote Objects](http://msdn.microsoft.com/ja-jp/515686e6-0a8d-42f7-8188-73abede57c58)  
 .NET Framework でリモート通信に利用できるさまざまな通信方法について説明します。  
  
 [Advanced Development Technologies](http://msdn.microsoft.com/ja-jp/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 .NET Framework での高度な開発タスクと技法に関する詳細情報へのリンクを示します。  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/ja-jp/1e64af78-d705-4384-b08d-591a45f4379c)  
 ASP.NET を使用して作成した XML Web サービスのプログラミング方法について説明するトピックを示します。