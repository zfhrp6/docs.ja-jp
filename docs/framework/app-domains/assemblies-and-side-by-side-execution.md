---
title: "アセンブリと side-by-side 実行 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], side-by-side 実行"
  - "side-by-side 実行 [.NET Framework]"
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# アセンブリと side-by-side 実行
side\-by\-side 実行は、アプリケーションやコンポーネントの複数のバージョンを同じコンピューターに格納して実行する機能です。  つまり、ランタイムの複数のバージョンと、特定のバージョンのランタイムを使用するアプリケーションおよびコンポーネントの複数のバージョンを、同一コンピューター上に共存させることができます。  side\-by\-side 実行によって、アプリケーションをバインドするコンポーネントのバージョンや、アプリケーションが使用するランタイムのバージョンを細かく制御できます。  
  
 同じアセンブリの異なるバージョンの side\-by\-side ストレージにおける side\-by\-side 実行のサポートは、厳密な名前には不可欠の要素であり、ランタイムのインフラストラクチャに組み込まれています。  厳密な名前を持つアセンブリのバージョン番号がその識別子の一部に含まれているため、ランタイムは同じアセンブリの複数のバージョンをグローバル アセンブリ キャッシュに格納し、実行時にこれらのアセンブリを読み込むことができます。  
  
 ランタイムは、side\-by\-side 実行できるアプリケーションの作成機能を提供しますが、side\-by\-side 実行は自動的にサポートされるわけではありません。  side\-by\-side 実行用のアプリケーション作成の詳細については、「[side\-by\-side 実行用のコンポーネントを作成するためのガイドライン](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)」を参照してください。  
  
## 参照  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)