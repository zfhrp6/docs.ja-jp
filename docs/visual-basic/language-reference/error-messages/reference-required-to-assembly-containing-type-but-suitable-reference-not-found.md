---
title: "参照アセンブリ &#39; が必要です。&lt;assemblyidentity&gt;&#39;以外の場合は親の種類 &#39;&lt;typename&gt;&#39;以外の場合は、プロジェクト &#39; の間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;&#39; と &#39;&lt;projectname2&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>参照アセンブリ &#39; が必要です。&lt;assemblyidentity&gt;&#39;以外の場合は親の種類 &#39;&lt;typename&gt;&#39;以外の場合は、プロジェクト &#39; の間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;&#39; と &#39;&lt;projectname2&gt;&#39;です。
プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。 しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。  
  
 問題のプロジェクトは、同じ名前のアセンブリを複数作成します。 このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。  
  
 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30969  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
