---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30955"
  - "bc30955"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30955"
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型 '\<typename1\>' の値を '\<typename2\>' に変換できません。型の不一致は、ファイル参照とアセンブリ '\<assemblyname\>' へのプロジェクト参照との混合によって生じた可能性があります。プロジェクト '\<projectname1\>' の '\<filepath\>' へのファイル参照を '\<projectname2\>' へのプロジェクト参照に置き換えてください。  
  
 プロジェクトでプロジェクト参照とファイル参照の両方が作成される場合、コンパイラは型が別の型に正しく変換されることを保証できません。  
  
 次の擬似コードは、このエラーが発生する可能性がある状況を示しています。  
  
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
  
 プロジェクト `P1` は、プロジェクト `P2` を経由するプロジェクト `P3` への間接プロジェクト参照を作成し、一方でプロジェクト `P3` への直接ファイル参照も作成します。  `commonObject` の宣言では、`P3` へのファイル参照を使用しますが、`P2.getCommonClass` の呼び出しでは `P3` へのプロジェクト参照を使用します。  
  
 この状況で問題となるのは、ファイル参照では `P3` の出力ファイル \(通常は p3.dll\) のファイル パスとファイル名を指定するのに対して、プロジェクト参照ではソース プロジェクト \(`P3`\) をプロジェクト名で識別することです。  これが原因で、コンパイラは、2 つの参照のどちらもからも同じソース コードの `P3.commonClass` 型に到達することを保証できません。  
  
 通常、この状況は、プロジェクト参照とファイル参照が混在する場合に起こります。  前記の例では、`P1` が `P3` を参照するためにファイル参照ではなく直接プロジェクト参照を作成すると、この問題は起こりません。  
  
 **Error ID:** BC30955  
  
### このエラーを解決するには  
  
-   ファイル参照をプロジェクト参照に変更します。  
  
## 参照  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)   
 [方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)