---
title: "方法: アセンブリを他のアプリケーションと共有する (C#) | Microsoft Docs"
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
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
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
ms.openlocfilehash: 79397b18b67becf91d04358ea62cb2351be7d252
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>方法 : アセンブリを他のアプリケーションと共有する (C#)
アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。  
  
 他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC) にアセンブリを置く必要があります。  
  
### <a name="sharing-an-assembly"></a>アセンブリの共有  
  
1.  アセンブリを作成します。 詳しくは、「[アセンブリの作成](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)」をご覧ください。  
  
2.  アセンブリに厳密な名前を割り当てます。 詳しくは、「[方法 : 厳密な名前でアセンブリに署名する](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)」をご覧ください。  
  
3.  アセンブリにバージョン情報を割り当てます。 詳細については、「[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)」を参照してください。  
  
4.  グローバル アセンブリ キャッシュにアセンブリを追加します。 詳しくは、「[方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)」をご覧ください。  
  
5.  他のアプリケーションからアセンブリに含まれる型にアクセスします。 詳しくは、「[方法 : 厳密な名前のアセンブリを参照する](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [アセンブリを使用したプログラミング](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
