---
title: "アプリケーション ドメインとアセンブリを使用したプログラミング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション ドメイン, プログラミング"
  - "アセンブリ [.NET Framework], プログラミング"
  - "プログラミング (アプリケーション ドメインの)"
  - "プログラミング (アセンブリの)"
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# アプリケーション ドメインとアセンブリを使用したプログラミング
Microsoft Internet Explorer、ASP.NET、Windows シェルなどのホストは、共通言語ランタイムをプロセスに読み込み、そのプロセス内で[アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)を作成します。その後 .NET Framework アプリケーションを実行するときに、そのアプリケーション ドメインにユーザー コードを読み込んでコードを実行します。  通常は、アプリケーション ドメインの作成およびアセンブリへの読み込みはランタイム ホストで実行するため、考慮する必要はありません。  
  
 しかし、共通言語ランタイムをホストするアプリケーションを作成する場合、プログラムによってアンロードされるツールまたはコードを作成する場合、または実行時にアンロードおよび再読み込みできるプラグ可能なコンポーネントを作成する場合は、独自のアプリケーション ドメインを作成します。  ランタイム ホストを作成しない場合でも、このセクションにある、アプリケーション ドメインとアプリケーション ドメインに読み込まれたアセンブリをどのように使用するかという説明は重要です。  
  
## このセクションの内容  
 [アプリケーション ドメインとアセンブリに関する方法のトピック](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 概念を説明したドキュメントに用意されている、アプリケーション ドメインとアセンブリを利用したプログラミングに関するトピックへのリンクを示します。  
  
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)  
 アプリケーション ドメインを作成、構成、および使用する例を示します。  
  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 アセンブリを作成し、署名し、その属性を設定する方法を説明します。  
  
## 関連項目  
 [動的メソッドおよびアセンブリの出力](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 動的アセンブリの作成方法を説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 アセンブリの概念的な概要を説明します。  
  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインの概念的な概要を説明します。  
  
 [リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使って、アセンブリに関する情報を取得する方法を説明します。