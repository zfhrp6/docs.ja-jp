---
title: アセンブリに必要な参照&#39; &lt;assemblyidentity&gt; &#39;型を含む&#39; &lt;typename&gt;&#39;との間のあいまいなので、適切な参照が見つかりませんでしたが、プロジェクト&#39; &lt;projectname1&gt; &#39;と&#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 670ac3ceb6a703a11b8f00a341dbcf868d4ceb7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597446"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>アセンブリに必要な参照&#39; &lt;assemblyidentity&gt; &#39;型を含む&#39; &lt;typename&gt;&#39;との間のあいまいなので、適切な参照が見つかりませんでしたが、プロジェクト&#39; &lt;projectname1&gt; &#39;と&#39; &lt;projectname2&gt;&#39;
プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。 しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。  
  
 問題のプロジェクトは、同じ名前のアセンブリを複数作成します。 このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。  
  
 別のアセンブリで定義された型にアクセスするには、そのアセンブリへの参照が、Visual Basic コンパイラに必要です。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30969  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
