---
title: "Of 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="of-clause-visual-basic"></a>Of 句 (Visual Basic)
導入されています、`Of`句であることを識別、*パラメーター入力*上、*ジェネリック*クラス、構造体、インターフェイス、デリゲート、またはプロシージャ。 ジェネリック型については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。  
  
## <a name="using-the-of-keyword"></a>使用して、キーワードの  
 次のコード例では、`Of`キーワードを次の 2 つの型パラメーターを受け取るクラスの輪郭の定義します。 これは、*制約*、`keyType`によってパラメーター、<xref:System.IComparable>インターフェイスで、利用側のコードを実装する型引数を指定する必要がありますを意味<xref:System.IComparable>です。 これは、必要なできるように、`add`プロシージャを呼び出すことができます、<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>メソッドです。 制約の詳細については、次を参照してください。[型リスト](../../../visual-basic/language-reference/statements/type-list.md)です。  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 上記のクラス定義を完了する場合は、さまざまなを構築できます`dictionary`からクラスです。 指定する種類`entryType`と`keyType`エントリの種類、クラスを保持し、各エントリに関連付けるキーの種類を決定します。 制約のために指定する必要があります`keyType`を実装する型<xref:System.IComparable>です。  
  
 次のコード例を保持するオブジェクトを作成する`String`エントリと関連付け、 `Integer` 1 つずつキー。 `Integer`実装する<xref:System.IComparable>し、そのために、制約を満たす`keyType`です。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 キーワード `Of` は次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IComparable>  
 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
