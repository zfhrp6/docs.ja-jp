---
title: "Shared (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Shared"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared keyword"
  - "members, shared"
  - "shared members"
  - "nonshared"
  - "shared elements"
  - "elements, shared"
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Shared (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言された 1 つ以上のプログラミング要素が、クラス全体または構造体全体に関連付けられ、クラスまたは構造体の特定のインスタンスに関連付けられないことを指定します。  
  
## 解説  
  
## Shared を使用する状況  
 *非共有*であるクラスまたは構造体のメンバーを共有すると、各インスタンスがメンバーのコピーを別々に保持するのではなく、すべてのインスタンスがそのメンバーを使用できます。  このことは、たとえば、変数の値をアプリケーション全体で参照する場合に便利です。  そのような変数を `Shared` で宣言した場合、すべてのインスタンスがストレージ内の同じ場所にアクセスするため、あるインスタンスが変数の値を変更すると、すべてのインスタンスが変更後の値にアクセスするようになります。  
  
 共有メンバーとして宣言したからといって、アクセス レベルが変更されるわけではありません。  たとえば、クラスのメンバーを、共有プライベート メンバーとして宣言することも \(クラス内でのアクセスのみ可能\)、非共有のパブリック メンバーとして宣言することも可能です。  詳細については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## 規則  
  
-   **宣言コンテキスト。** `Shared` は、モジュール レベルでのみ使用できます。  つまり、`Shared` 要素の宣言コンテキストは、ソース ファイル、名前空間、プロシージャではなく、クラスまたは構造体である必要があります。  
  
-   **結合された修飾子。**同じ宣言内で `Shared` を [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)、[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)、または [Static](../../../visual-basic/language-reference/modifiers/static.md) と共に指定することはできません。  
  
-   **アクセス。**共有要素にアクセスするには、そのクラスや構造体の特定のインスタンスの変数名ではなく、クラスや構造体の名前を使用して共有要素を修飾します。  共有メンバーにアクセスするために、そのクラスや構造体のインスタンスを作成する必要もありません。  
  
     次の例は、<xref:System.Double> 構造体で公開されている共有プロシージャ <xref:System.Double.IsNaN%2A> を呼び出します。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **暗黙の共有。** [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) で `Shared` 修飾子を使うことはできませんが、定数は暗黙的に共有されます。  同様に、モジュールやインターフェイスのメンバーは `Shared` では宣言できませんが、暗黙的に共有されます。  
  
## \[動作\]  
  
-   **ストレージ。**共有変数や共有イベントは、そのクラスや構造体のインスタンスが何回作成されたとしても、メモリに一度だけ格納されます。  同様に、共有プロシージャや共有プロパティは、ローカル変数を 1 セットだけ保持します。  
  
-   **インスタンス変数を使用したアクセス。**クラスや構造体の特定のインスタンスを格納する変数の名前で修飾して、共有要素にアクセスすることが可能です。  この方法で予期しない動作が起きることは通常ありませんが、コンパイラは警告メッセージを表示し、変数名ではなくクラス名や構造体名を使ってアクセスします。  
  
-   **インスタンス式を使用したアクセス。**クラスや構造体のインスタンスを返す式を使用して共有要素にアクセスした場合、コンパイラは式を評価せず、クラス名や構造体名を使ってアクセスします。  この式を使ってインスタンスを返す他に何か別の処理も実行しようとしていた場合は、予期しない結果になります。  次に例を示します。  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     このコード例では、インスタンスを使って共有変数 `total` に 2 度アクセスしていますが、コンパイラは 2 度とも警告メッセージを生成します。  どちらの場合も、コンパイラは直接 `shareTotal` クラスを使ってアクセスし、インスタンスを使用しません。  プロシージャ `returnClass` を呼び出そうとしていた部分では、`returnClass` の呼び出しが行われないため、ここに追加されている "Function returnClass\(\) called" というメッセージの表示は実行されません。  
  
 修飾子 `Shared` は、次の構文で使用します。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)