---
title: "Nullable Value Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Nullable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nullable types [Visual Basic]"
  - "? [Visual Basic]"
  - "types [Visual Basic], nullable"
  - "nullable types"
  - "data types [Visual Basic], nullable"
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Nullable Value Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

特定の状況においては、定義された値を持たない値型を扱うことがあります。  たとえば、データベース内のフィールドには、意味のある値が代入されている場合と、値が代入されていない場合とがあり、これを区別する必要があります。  値型を拡張して、通常の値または null 値を受け入れるようにすることができます。  このような拡張は、*null 許容型*と呼ばれます。  
  
 各 null 許容型は、ジェネリックな <xref:System.Nullable%601> 構造体から作成されます。  データベースを使って、仕事に関連する活動を記録すると仮定します。  次のコード例は、null 許容 `Boolean` データ型を作成し、この型の変数を宣言する方法を示しています。  宣言を記述するには 3 種類の方法があります。  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 変数 `ridesBusToWork` には、`True` または `False` の値を格納できるほか、まったく値が格納されない状態も許されます。  初期の既定値は、まったく値のない状態です。今回の例では、これはその人物についてまだ情報が取得されていないことを意味します。  これとは対照的に、`False` は、その人物に関する情報が取得され、仕事のバスに乗務していないことを示します。  
  
 null 許容型で変数やプロパティを宣言したり、null 許容型の要素で配列を宣言したりすることができます。  null 許容型をパラメーターとしてプロシージャを宣言することや、null 許容型を戻り値として `Function` プロシージャから返すこともできます。  
  
 null 許容型を配列、`String`、クラスなどの参照型で作成することはできません。  基になる型は、値型である必要があります。  詳細については、「[Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
## null 許容型変数の使用  
 null 許容型の最も重要なメンバーは、<xref:System.Nullable%601.HasValue%2A> プロパティと <xref:System.Nullable%601.Value%2A> プロパティです。  null 許容型の変数に定義済みの値が格納されているかどうかは、<xref:System.Nullable%601.HasValue%2A> を使って確認できます。  <xref:System.Nullable%601.HasValue%2A> が `True` の場合、値を <xref:System.Nullable%601.Value%2A> から読み取ることができます。  <xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> は両方とも `ReadOnly` のプロパティであることに注意してください。  
  
### 既定値  
 null 許容型の変数を宣言すると、その変数の <xref:System.Nullable%601.HasValue%2A> プロパティは、既定で `False` 値に設定されます。  つまり、既定では、変数は、基になる値型の既定値が格納されるのではなく、定義済みの値が格納されていない状態になります。  次のコード例では、`Integer` 型の既定値は 0 ですが、変数 `numberOfChildren` に定義済みの初期値は格納されません。  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 null 値は、未定義または未知の値を示すには便利です。  `numberOfChildren` を `Integer` として宣言した場合、情報が現在使用できないことを示すために使用できる値はありません。  
  
### 値の格納  
 null 許容型の変数またはプロパティに値を格納する方法は、通常と変わりません。  次のコード例では、前の例で宣言した変数 `numberOfChildren` に値を代入しています。  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 null 許容型の変数またはプロパティに定義済みの値が格納されている場合でも、値が代入されていない初期状態に戻すことができます。  これを行うには、変数またはプロパティを `Nothing` に設定します。以下に例を示します。  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  null 許容型の変数に `Nothing` を代入することはできますが、変数の値が `Nothing` であるかどうかを等号を使用してテストすることはできません。  等号を使用した比較 `someVar = Nothing` は、常に `Nothing` と評価されます。  変数の <xref:System.Nullable%601.HasValue%2A> プロパティが `False` かどうかをテストしたり、`Is` 演算子または `IsNot` 演算子を使用してテストしたりすることはできます。  
  
### 値の取得  
 null 許容型の変数から値を取得するには、その変数の <xref:System.Nullable%601.HasValue%2A> プロパティを使って、変数に値が含まれているかどうかを最初にテストする必要があります。  <xref:System.Nullable%601.HasValue%2A> が `False` のときに値を読み取ろうとすると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は <xref:System.InvalidOperationException> 例外をスローします。  次のコード例は、前の例で使用した変数 `numberOfChildren` から値を読み取るための推奨される方法です。  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## Null 許容型の比較  
 null 許容の `Boolean` 変数をブール式で使用すると、結果は `True`、`False`、または `Nothing` になります。  次に示すのは、`And` および `Or` についての真理値表です。  `b1` と `b2` は 3 つの値を持つことができるので、9 つの組み合わせを評価します。  
  
|b1|b2|b1 And b2|b1 Or b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 ブール変数の値またはブール式の値が `Nothing` の場合は、`true` でも `false` でもありません。  例を次に示します。  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 この例では、`b1 And b2` は `Nothing` と評価されます。  したがって、各 `If` ステートメントでは `Else` 句が実行され、出力は次のようになります。  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` および `OrElse` はショートサーキット評価を使用し、最初の評価が `Nothing` のときは、2 番目のオペランドを評価する必要があります。  
  
## 反映  
 算術演算、比較演算、シフト演算、または型演算のオペランドの一方または両方が null 許容の場合は、演算の結果も null 許容になります。  両方のオペランドの値が `Nothing` ではない場合は、どちらも null 許容型ではないものとして、オペランドの基になる値に対して演算が実行されます。  次の例では、変数 `compare1` と `sum1` は暗黙的に型指定されています。  これらの変数の上にマウス ポインターを置くと、コンパイラが両方の変数を null 許容型と見なしていることがわかります。  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 一方または両方のオペランドの値が `Nothing` の場合は、結果は `Nothing` になります。  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## データのある null 許容型の使用  
 データベースは、null 許容型が使用される最も重要な場所です。  現在すべてのデータベース オブジェクトで null 許容型がサポートされているわけではありませんが、デザイナー生成テーブル アダプターではサポートされています。  詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」の「TableAdapter での Null 許容型のサポート」を参照してください。  
  
## 参照  
 <xref:System.InvalidOperationException>   
 <xref:System.Nullable%601.HasValue%2A>   
 [Null 許容型の使用](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)   
 [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)