---
title: "方法: ロード テストとアンロード アセンブリ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 460d3a18fdee74c9b9c49ee465247b5b12d554d8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>方法: ロード テストとアンロード アセンブリ (Visual Basic)
プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。 詳細については、次を参照してください。[方法: アプリケーション ドメインにアセンブリをロード](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)します。  
  
 個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。  
  
 一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。 詳細については、次を参照してください。[方法: アプリケーション ドメインをアンロード](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)します。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>アセンブリをアプリケーション ドメインに読み込むには  
  
1.  クラス<xref:System.AppDomain>と<xref:System.Reflection></xref:System.Reflection></xref:System.AppDomain>に含まれているいくつかの load メソッドのいずれかを使用します。 詳細については、次を参照してください。[方法: アプリケーション ドメインにアセンブリをロード](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)します。  
  
### <a name="to-unload-an-application-domain"></a>アプリケーション ドメインをアンロードするには  
  
1.  個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 使用して、`Unload`メソッドから<xref:System.AppDomain>アプリケーション ドメインをアンロードします</xref:System.AppDomain>。 詳細については、次を参照してください。[方法: アプリケーション ドメインをアンロード](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)します。  
  
## <a name="see-also"></a>関連項目  
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [方法: アプリケーション ドメインにアセンブリを読み込む](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
