---
title: "アセンブリの場所 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], 位置"
  - "検索 (アセンブリを)"
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# アセンブリの場所
アセンブリの場所は、共通言語ランタイムが参照されるアセンブリの位置を特定できるかどうかを決定します。また、アセンブリをほかのアセンブリと共有できるかどうかも決定します。  アセンブリは、次の場所に配置できます。  
  
-   アプリケーションのディレクトリまたはサブディレクトリ  
  
     これは、アセンブリの最も一般的な配置場所です。  アプリケーション ルート ディレクトリのサブディレクトリは、言語またはカルチャに基づいて作成できます。  アセンブリにカルチャ属性の情報がある場合、そのアセンブリは、そのカルチャ名を持つアプリケーション ディレクトリの下位のサブディレクトリに配置する必要があります。  
  
-   グローバル アセンブリ キャッシュ  
  
     これは、共通言語ランタイムがインストールされると常にインストールされる、コンピューター全体のコード キャッシュです。  通常、あるアセンブリを複数のアプリケーションで共有する場合、そのアセンブリをグローバル アセンブリ キャッシュ内にインストールする必要があります。  
  
-   HTTP サーバー上  
  
     アセンブリを HTTP サーバー上に配置する場合、厳密な名前が必要です。アセンブリへのポインターは、アプリケーション構成ファイルのコードベース セクションで指定します。  
  
## 参照  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)   
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)