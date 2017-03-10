---
title: "Determining Object Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], discovering which an object belongs to"
  - "types [Visual Basic], determining Visual Basic object types"
  - "object variables, testing values"
  - "TypeOf...Is expression, object type at run time"
  - "TypeName function"
  - "objects [Visual Basic], type determining"
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Determining Object Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

汎用オブジェクト変数 \(`Object` として宣言する変数\) は、あらゆるクラスのオブジェクトを保持できます。  `Object` 型の変数を使用するときは、オブジェクトのクラスに基づいて異なるアクションを行うことが必要な場合があります。たとえば、特定のプロパティまたはメソッドが、一部のオブジェクトではサポートされないことがあります。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、オブジェクト変数に格納されているオブジェクトの型を判断するための 2 つの方法が用意されています。`TypeName` 関数と `TypeOf...Is` 演算子です。  
  
## TypeName および TypeOf…Is  
 `TypeName` 関数は文字列を返します。このため、たとえば次のコードのように、オブジェクトのクラス名を格納したり表示したりする場合に適しています。  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#92)]  
  
 `TypeOf...Is` 演算子は、`TypeName` を使った同等の文字列比較に比べ、処理が大幅に速くなります。このため、オブジェクトの型をテストする場合に適しています。  次のコード片では、`If...Then...Else` ステートメントの中で `TypeOf...Is` が使用されています。  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#93)]  
  
 TypeOf...Is 演算子を使用する場合には注意が必要です。  `TypeOf...Is` 演算子は、オブジェクトが特定の型である場合、または特定の型から派生してる場合に `True` を返します。  オブジェクトは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のほとんどの作業で使用されます。中には、文字列や整数のように、通常はオブジェクトと見なされない要素もあります。  これらのオブジェクトは、<xref:System.Object> から派生し、メソッドを継承しています。  `Integer` が渡されて `Object` で評価されると、`TypeOf...Is` 演算子は `True` を返します。  次の例では、パラメーター `InParam` は `Object` と `Integer` の両方であると報告されます。  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#94)]  
  
 次の例は、`TypeOf...Is` と `TypeName` の両方を使って、引数 `Ctrl` で渡されるオブジェクトの型を調べます。  `TestObject` プロシージャは、3 種類のコントロールで `ShowType` を呼び出します。  
  
#### 例を実行するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成し、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、および <xref:System.Windows.Forms.RadioButton> の各コントロールをフォームに追加します。  
  
2.  フォームのボタンから `TestObject` プロシージャを呼び出します。  
  
3.  フォームに次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#95)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)