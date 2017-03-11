---
title: "ReadOnly (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ReadOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ReadOnly keyword"
  - "variables [Visual Basic], read-only"
  - "ReadOnly property"
  - "properties [Visual Basic], read-only"
  - "read-only variables"
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# ReadOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

読み取ることはできても書き込むことはできない変数またはプロパティを示します。  
  
## 解説  
  
## 規則  
  
-   **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。  つまり、`ReadOnly` 要素の宣言コンテキストは、ソース ファイル、名前空間、インターフェイス、プロシージャではなく、クラス、構造体、またはモジュールである必要があります。  
  
-   **結合された修飾子。**同じ変数宣言で `ReadOnly` と `Static` を同時に指定することはできません。  
  
-   **値の代入。** `ReadOnly` プロパティを使用するコードは値を設定できません。  しかし、基になるストレージにアクセスできるコードは、いつでもその値を代入および変更できます。  
  
     `ReadOnly` 変数に値を代入できるのは、変数の定義時、または、この変数が定義されたクラスまたは構造体のコンストラクターの中のみです。  
  
## ReadOnly 変数を使用する場合  
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) を使用して、定数の値を宣言および代入できない場合があります。  たとえば、`Const` ステートメントが代入するデータ型を受け入れない場合や、コンパイル時に定数式で値を計算できない場合などです。  コンパイル時には値がわからないことも考えられます。  このような場合、`ReadOnly` 変数を使用して定数値を格納します。  
  
> [!IMPORTANT]
>  この変数のデータ型が配列やクラス インスタンスなどの参照型の場合、変数自体が `ReadOnly` であっても、このメンバーは変更できます。  次に例を示します。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 初期化されたとき、`characterArray()` で参照される配列には "x"、"y"、"z" が格納されています。  変数 `characterArray` は `ReadOnly` なので、一度初期化するとこの値は変更できません。つまり、新しい配列をこれに代入することはできません。  しかし、配列のメンバー \(1 つまたは複数\) の値は変更できます。  プロシージャ `changeArrayElement` の呼び出し後、`characterArray()` が参照する配列には "x"、"M"、"z" が格納されています。  
  
 これは、プロシージャのパラメーターを [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) として宣言するのと同様です。プロシージャは呼び出し元の引数そのものは変更できませんが、そのメンバーは変更できます。  
  
## 使用例  
 次の例では、従業員が雇用された日付を表す `ReadOnly` プロパティを定義します。  このクラスは、プロパティの値を `Private` 変数として内部に格納し、クラス内のコードだけがこの値を変更できます。  ただし、このプロパティは `Public` であり、このクラスにアクセスできるすべてのコードがこのプロパティを読み取れます。  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/visualbasic/readonly_1.vb)]  
  
 `ReadOnly` 修飾子は、次の場合に使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 参照  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)