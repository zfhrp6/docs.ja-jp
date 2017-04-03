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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15905b2c23320b57e5797d6084ce48cfc526ed7d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a>方法: アセンブリを読み込み、アンロードする (C#)
プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。 詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)」を参照してください。  
  
 個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。  
  
 一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。 詳細については、「[方法: アプリケーション ドメインをアンロードする](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)」を参照してください。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>アセンブリをアプリケーション ドメインに読み込むには  
  
1.  <xref:System.AppDomain> クラスと <xref:System.Reflection> クラスに含まれる load メソッドの 1 つを使用します。 詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)」を参照してください。  
  
### <a name="to-unload-an-application-domain"></a>アプリケーション ドメインをアンロードするには  
  
1.  個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 <xref:System.AppDomain> の `Unload` メソッドを使用して、アプリケーション ドメインをアンロードします。 詳細については、「[方法: アプリケーション ドメインをアンロードする](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [方法: アプリケーション ドメインにアセンブリを読み込む](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
