---
title: '&lt;メッセージ&gt;このエラーをファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります&#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 37a152da06a36756b86576bad9c6c5d6a392dc8d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;メッセージ&gt;このエラーをファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります&#39; &lt;assemblyname&gt;&#39;
\<メッセージ > このエラーをファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります '\<assemblyname >。 この場合、交換してみますファイル参照を '\<assemblyfilename >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。  
  
 プロジェクトのコードが別のプロジェクトのメンバーにアクセスは、ソリューションの構成は、参照を解決するのには、Visual Basic コンパイラを許可しません。  
  
 別のアセンブリで定義された型にアクセスするには、そのアセンブリへの参照が、Visual Basic コンパイラに必要です。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30971  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
