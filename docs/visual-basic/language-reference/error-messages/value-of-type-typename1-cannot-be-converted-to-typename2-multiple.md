---
title: "型 &#39; の値&lt;typename1&gt;&#39; に変換できません (& m); #39&lt;typename2&gt;&#39;です。(複数のファイル参照)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc6138c7a7ca7d50a56fdd1f536e8d2dc3462a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>型 &#39; の値&lt;typename1&gt;&#39; に変換できません (& m); #39&lt;typename2&gt;&#39;です。(複数のファイル参照)
型の値 '\<typename1 >' に変換できません。'\<typename2 >' です。 型の不一致へのファイル参照を混在させる可能性があります '\<filepath1 >' プロジェクトで'\<projectname1 >' へのファイル参照を '\<filepath2 >' プロジェクトで'\<projectname2 >' です。 両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。  
  
 状況では、プロジェクトは、1 つ以上のファイル参照アセンブリをコンパイラは、1 つの型を別に変換できることを保証できません。  
  
 それぞれのファイル参照は、ファイルのパスと (通常は DLL ファイル) のプロジェクトの出力ファイルの名前を指定します。 コンパイラは、出力ファイルが、同じソースから取得することや、同じアセンブリの同じバージョンを表すことを保証できません。 そのため、その種類別の参照では、同じの型またはも、あるは、その他に変換できることは保証できません。  
  
 参照アセンブリが同じアセンブリ id を持つことがわかっている場合は、1 つのファイルの参照を使用できます。 *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。 この情報はアセンブリを一意に識別します。  
  
 **エラー ID:** BC30961  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照されるアセンブリのアセンブリ id が同じ場合は、削除するか、1 つのファイル参照のみがあるように、ファイル参照のいずれかを置き換えます。  
  
-   参照アセンブリが同じアセンブリ id を持たない場合は、1 つのもう一方の型に型変換を行いませんようにコードを変更します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
