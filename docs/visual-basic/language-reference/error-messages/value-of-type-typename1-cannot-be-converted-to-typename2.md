---
title: "型の値 &quot;&lt;&quot; typename1 &quot;&gt;&quot;に変換できない&quot;&lt;typename2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c973d5e2aa03d423e1dea8053946172655f08490
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>型の値 '&lt;' typename1 '&gt;'に変換できない'&lt;typename2&gt;'
型の値 '\<' typename1 '>' に変換できません。'\<typename2 >' です。 型の不一致ファイル参照アセンブリへのプロジェクト参照とを混在させるが考えられます '\<assemblyname >' です。 ファイルの参照を置き換えてください '\<filepath >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。  
  
 プロジェクトがプロジェクト参照とファイル参照の両方を使用する場合、コンパイラは、別に、1 つの型を変換できることを保証できません。  
  
 次の擬似コードは、このエラーを生成できる状況を示しています。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 プロジェクト`P1`プロジェクトを通じて間接的なプロジェクトで参照した`P2`プロジェクトに`P3`とへのファイルを直接参照も`P3`です。 宣言`commonObject`へのファイル参照を使用して`P3`への呼び出し中に`P2.getCommonClass`へのプロジェクト参照を使用して`P3`します。  
  
 この状況で問題は、ファイルのパスと名前の出力ファイルのファイル参照が指定される`P3`(通常 p3.dll) プロジェクト参照には、ソース プロジェクトが識別するときに (`P3`) プロジェクトの名前。 このため、コンパイラは保証できませんが、型`P3.commonClass`は&2; つの異なる参照を使用して、同じソース コードから取得します。  
  
 通常このような状況が発生したプロジェクト参照とファイル参照が混在します。 上の図で問題がない場合に発生する`P1`を直接プロジェクト参照した`P3`ファイル参照の代わりにします。  
  
 **エラー ID:** BC30955  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ファイルの参照をプロジェクト参照を変更します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
