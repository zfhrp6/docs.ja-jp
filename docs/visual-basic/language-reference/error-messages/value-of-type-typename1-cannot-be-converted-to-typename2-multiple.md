---
title: "型の値 &quot;&lt;&quot; typename1 &quot;&gt;&quot;に変換できない&quot;&lt;typename2&gt;&quot; (複数のファイル参照) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
dev_langs:
- VB
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 732291ce9c4b83bb9fc7e83fbbc2a8da9748db59
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>型の値 '&lt;' typename1 '&gt;'に変換できない'&lt;typename2&gt;' (複数のファイル参照)
型の値 '\<' typename1 '>' に変換できません。'\<typename2 >' です。 型の不一致に対するファイル参照の混在が考えられます '\<filepath1 >' プロジェクトで'\<projectname1 >' への参照をファイルに '\<filepath2 >' プロジェクトで'\<projectname2 >' です。 両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。  
  
 プロジェクトはアセンブリへの&1; つ以上のファイル参照を状況の場合、コンパイラは、別に、1 つの型を変換できることを保証できません。  
  
 それぞれのファイル参照は、ファイルのパスとプロジェクト (通常は DLL ファイル) の出力ファイルの名前を指定します。 コンパイラは、出力ファイルが同じソースから取得するか、同じアセンブリの同じバージョンを表すことを保証できません。 したがって、種類別の参照では、同じ型か、その他にも、あるを変換できることを保証することはできません。  
  
 参照先アセンブリのアセンブリ id が同じであることがわかっている場合は、1 つのファイルの参照を使用できます。 *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。 この情報はアセンブリを一意に識別します。  
  
 **エラー ID:** BC30961  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照先アセンブリのアセンブリ id が同じ場合は、削除や、置き換えるファイルの参照のいずれか&1; つのファイル参照のみがあります。  
  
-   参照されたアセンブリは同じアセンブリの id を持っていない場合は、1 つのもう一方の型に型変換を行いませんようにコードを変更します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
