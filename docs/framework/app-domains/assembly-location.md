---
title: "アセンブリの場所"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e069c1636004896bfb193fd70a352195ba045865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-location"></a>アセンブリの場所
アセンブリの場所は、参照時に共通言語ランタイムがそれを見つけることができるかどうかを決定します。また、アセンブリをその他のアセンブリと共有できるかどうかも決定できます。 次の場所にアセンブリを展開することができます。  
  
-   アプリケーションのディレクトリまたはサブディレクトリ  
  
     これは、アセンブリを展開する最も一般的な場所です。 アプリケーションのルート ディレクトリのサブディレクトリは、言語またはカルチャを基にすることができます。 アセンブリにカルチャ属性の情報がある場合は、アプリケーション ディレクトリの下のサブディレクトリに、そのカルチャの名前で存在する必要があります。  
  
-   グローバル アセンブリ キャッシュ  
  
     これは、共通言語ランタイムをインストールしている場所にインストールされている、コンピューター全体で使用できるコード キャッシュです。 ほとんどの場合、あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内に展開する必要があります。  
  
-   HTTP サーバー上  
  
     HTTP サーバーに展開されているアセンブリは、厳密な名前を持つ必要があります。アプリケーションの構成ファイルのコードベース セクションにあるアセンブリをポイントします。  
  
## <a name="see-also"></a>関連項目  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)  
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
