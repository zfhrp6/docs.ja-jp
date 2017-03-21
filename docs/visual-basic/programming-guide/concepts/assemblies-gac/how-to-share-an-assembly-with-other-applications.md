---
title: "方法: アセンブリを他のアプリケーション (Visual Basic) に共有 |Microsoft ドキュメント"
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
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
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
ms.openlocfilehash: 8065a66c8f7c7b9ccb9125b060b0c03cde273482
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>方法: アセンブリを他のアプリケーション (Visual Basic) と共有
アセンブリがプライベートまたは共有することができます。 既定では、ほとんどの単純なプログラムで構成されているプライベート アセンブリの他のアプリケーションで使用されるこれらの目的ではありませんので。  
  
 他のアプリケーションとアセンブリを共有するために配置する必要があります、[グローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)(GAC)。  
  
### <a name="sharing-an-assembly"></a>アセンブリの共有  
  
1.  アセンブリを作成します。 詳細については、次を参照してください。[アセンブリの作成](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)します。  
  
2.  アセンブリに厳密な名前を割り当てます。 詳細については、次を参照してください。[方法: 厳密な名前でアセンブリに署名](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)します。  
  
3.  アセンブリにバージョン情報を割り当てます。 詳細については、次を参照してください。[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)します。  
  
4.  アセンブリをグローバル アセンブリ キャッシュに追加します。 詳細については、次を参照してください。[方法: グローバル アセンブリ キャッシュにアセンブリをインストール](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)します。  
  
5.  他のアプリケーションからアセンブリに含まれる型にアクセスします。 詳細については、次を参照してください。[方法: 厳密な名前付きアセンブリを参照](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)します。  
  
## <a name="see-also"></a>関連項目  
 [プログラミングに関する概念](../../../../visual-basic/programming-guide/concepts/index.md)
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [アセンブリを使用したプログラミング](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
