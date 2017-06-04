---
title: "アセンブリの配置 | Microsoft Docs"
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
  - "<codeBase> 要素"
  - "アセンブリ [.NET Framework], 位置"
  - "アセンブリ [.NET Framework], 配置"
  - "検索 (アセンブリを)"
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# アセンブリの配置
多くの .NET Framework アプリケーションの場合、アプリケーションを構成するアセンブリは、そのアプリケーションのディレクトリ、アプリケーション ディレクトリのサブディレクトリ、またはグローバル アセンブリ キャッシュ \(アセンブリが共有されている場合\) に配置します。  構成ファイルの [\<codeBase\> 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) を使用すると、共通言語ランタイムがアセンブリを検索する場所をオーバーライドできます。  アセンブリが厳密な名前を持たない場合、[\<codeBase\> 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) を使用して指定できる場所は、そのアプリケーションのディレクトリまたはサブディレクトリに制限されます。  アセンブリが厳密な名前を持つ場合は、[\<codeBase\> 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) を使用してコンピューターまたはネットワーク上の任意の場所を指定できます。  
  
 また、アンマネージ コード アプリケーションや COM 相互運用アプリケーションで使用するアセンブリを検索する場所についても似たような規則が適用されます。アセンブリを複数のアプリケーションで共有する場合、そのアセンブリの検索場所はグローバル アセンブリ キャッシュになります。  アンマネージ コードで使用するアセンブリは、型ライブラリとしてエクスポートし、登録する必要があります。  COM 相互運用で使用するアセンブリは、カタログに登録する必要がありますが、場合によっては、この登録が自動的に行われることもあります。  
  
## 参照  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [アプリの構成](../../../docs/framework/configure-apps/index.md)   
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)