---
title: "方法 : アプリケーション ドメインを作成する | Microsoft Docs"
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
  - "アプリケーション ドメイン、作成"
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : アプリケーション ドメインを作成する
共通言語ランタイム ホストは、必要に応じてアプリケーション ドメインを自動的に作成します。  一方、独自のアプリケーション ドメインを作成して、個人的に管理するアセンブリを読み込ませることもできます。  アプリケーション ドメインを作成してコードを実行することもできます。  
  
 新しいアプリケーション ドメインを作成するには、<xref:System.AppDomain?displayProperty=fullName> クラスのオーバーロードされた **CreateDomain** メソッドの 1 つを使用します。  アプリケーション ドメインに名前を付けると、その名前を使用してアプリケーション ドメインを参照できます。  
  
 `MyDomain` という名前の新しいアプリケーション ドメインを作成し、ホスト ドメイン名と新しく作成された子アプリケーション ドメイン名をコンソールに出力する例を次に示します。  
  
## 使用例  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## 参照  
 [Hosting Overview](http://msdn.microsoft.com/ja-jp/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)