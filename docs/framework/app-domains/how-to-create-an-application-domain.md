---
title: "方法 : アプリケーション ドメインを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cdbab5e43d2af7608c4d8322eb071baf591e18d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-an-application-domain"></a>方法 : アプリケーション ドメインを作成する
共通言語ランタイム ホストにより、必要なときに、アプリケーション ドメインが自動的に作成されます。 ただし、独自のアプリケーション ドメインを作成し、個人的に管理するアセンブリにそれを読み込むことができます。 アプリケーション ドメインを作成し、そこからコードを実行することもできます。  
  
 <xref:System.AppDomain?displayProperty=nameWithType> クラスのオーバーロードされた **CreateDomain** メソッドの 1 つを利用し、新しいアプリケーション ドメインを作成します。 アプリケーション ドメインに名前を付け、その名前で参照できます。  
  
 次の例では、新しいアプリケーション ドメインを作成し、それに `MyDomain` という名前を割り当て、ホスト ドメインの名前と新しく作成された子アプリケーション ドメインがコンソールに出力されます。  
  
## <a name="example"></a>例  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>参照  
 [アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)
