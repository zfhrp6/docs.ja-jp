---
title: "方法: アセンブリを読み込み、アンロードする (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 8efd5a9ccfedbea401b0c95d443fe8cdb6ea6c32
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a>方法: アセンブリを読み込み、アンロードする (C#)
プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。 詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。  
  
 個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。  
  
 一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。 詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>アセンブリをアプリケーション ドメインに読み込むには  
  
1.  <xref:System.AppDomain> クラスと <xref:System.Reflection> クラスに含まれるいくつかの load メソッドの 1 つを使用します。 詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。  
  
### <a name="to-unload-an-application-domain"></a>アプリケーション ドメインをアンロードするには  
  
1.  個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 `Unload` の <xref:System.AppDomain> メソッドを使用してアプリケーション ドメインをアンロードします。 詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
