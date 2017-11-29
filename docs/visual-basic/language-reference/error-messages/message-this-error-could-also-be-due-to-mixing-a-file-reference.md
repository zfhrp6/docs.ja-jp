---
title: "&lt;メッセージ&gt;このエラーをファイル参照アセンブリ &#39; への参照をプロジェクトとの混合によって生じた可能性があります&lt;assemblyname&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;メッセージ&gt;このエラーをファイル参照アセンブリ &#39; への参照をプロジェクトとの混合によって生じた可能性があります&lt;assemblyname&gt;&#39;です。
\<メッセージ > このエラーをファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります '\<assemblyname >。 この場合、交換してみますファイル参照を '\<assemblyfilename >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。  
  
 プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、このプロジェクトのソリューションは [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラに参照の解決を許可するよう構成されていません。  
  
 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30971  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
