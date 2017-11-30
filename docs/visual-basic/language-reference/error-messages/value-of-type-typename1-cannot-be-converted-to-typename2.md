---
title: "型 &#39; の値&lt;typename1&gt;&#39; に変換できません (& m); #39&lt;typename2&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords: BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2154a56f9ff004f906cb2b571f8771e74cfca9c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>型 &#39; の値&lt;typename1&gt;&#39; に変換できません (& m); #39&lt;typename2&gt;&#39;です。
型の値 '\<typename1 >' に変換できません。'\<typename2 >' です。 型の不一致は、ファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります '\<assemblyname >' です。 ファイル参照を置き換えてください '\<filepath >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。  
  
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
  
 プロジェクト`P1`プロジェクト全体の間接的なプロジェクト参照は、`P2`プロジェクトに`P3`とへのファイルを直接参照も`P3`します。 宣言`commonObject`へのファイル参照を使用して`P3`への呼び出し中に`P2.getCommonClass`へのプロジェクト参照を使用して`P3`です。  
  
 このような状況に問題は、ファイルのパスと名前の出力ファイルのファイル参照が指定される`P3`(通常 p3.dll) プロジェクト参照には、ソース プロジェクトが識別するときに (`P3`) プロジェクトの名前。 このため、コンパイラは保証できませんを種類`P3.commonClass`は 2 つの異なる参照を使用して、同じソース コードから取得します。  
  
 通常このような状況が発生したときにプロジェクト参照とファイル参照が混在します。 前の図では、問題がない場合に発生する`P1`を直接プロジェクト参照した`P3`ファイル参照の代わりにします。  
  
 **エラー ID:** BC30955  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ファイル参照をプロジェクト参照を変更します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
