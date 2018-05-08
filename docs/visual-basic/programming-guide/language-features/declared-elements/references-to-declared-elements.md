---
title: 宣言された要素の参照 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 18f9920891e35517efe7adcfd4c03e03ac771478
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="references-to-declared-elements-visual-basic"></a>宣言された要素の参照 (Visual Basic)
宣言された要素をコードが参照されているとき、Visual Basic コンパイラはその名前の適切な宣言に、参照内の名前と一致します。 複数の要素が同じ名前で宣言されている場合で参照するのにはそれらの要素を制御できます*正規*の名前。  
  
 コンパイラが、名前の参照名の宣言でを一致させようとしています。、*狭いスコープ*です。 これは、参照を実行するコードから開始して、下位レベルの要素を含むを通じてに向かってを意味します。  
  
 次の例では、同じ名前の 2 つの変数への参照を示します。 例では、2 つの変数を宣言して、各名前付き`totalCount`、モジュール内のスコープのさまざまなレベルで`container`です。 ときにプロシージャ`showCount`表示`totalCount`無条件では、Visual Basic コンパイラが、最も狭いスコープ、つまり内にローカル宣言で宣言への参照を解決`showCount`です。 適用されるときに`totalCount`を含むモジュールで`container`コンパイラより広いスコープを含む宣言への参照を解決します。  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>要素名の修飾  
 この検索処理をオーバーライドし、名前で宣言されているより広いスコープする必要がありますを指定する場合*修飾*より広いスコープを含む要素の名前。 場合によってでもありますコンテナー要素を修飾するためにします。  
  
 対象となる要素が定義されているを識別する情報、ソース ステートメント内の前名前手段を修飾します。 この情報と呼ばれる、*修飾文字列*です。 いずれかを含めること、または複数の名前空間とモジュールの場合、クラスまたは構造体します。  
  
 修飾文字列は、モジュール、クラス、または対象となる要素を含む構造体に明確を指定する必要があります。 コンテナーは、他のコンテナー要素、通常は名前空間に存在する可能性があります順番。 修飾文字列に含まれるいくつかの要素を含める必要がある可能性があります。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>その名前を修飾することによって宣言された要素にアクセスするには  
  
1.  要素が定義されている場所を決定します。 名前空間、または名前空間の階層も可能性があります。 最下位レベルの名前空間内には、モジュール、クラスまたは構造体の要素を含まれなければなりません。  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  ターゲット要素の場所に基づく修飾パスを決定します。 最上位レベルの名前空間を持つ開始、最下位レベルの名前空間に進んで、モジュール、クラス、または対象となる要素を含む構造体で終わる。 パス内の各要素には、それに続く要素を含める必要があります。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  ターゲット要素の修飾文字列を準備します。 ピリオドを配置 (`.`) のパスのすべての要素の後にします。 アプリケーション、修飾文字列内のすべての要素へのアクセスが必要です。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  式または通常の方法で対象となる要素を参照する代入ステートメントを記述します。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  修飾文字列にターゲット要素名の前にします。 名前は、期間の直後に続く (`.`) モジュール、クラス、または要素を含む構造に依存しています。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  コンパイラでは、修飾文字列を使用して、ターゲット要素の参照に一致する明確であいまいさのない宣言を見つけます。  
  
 また、アプリケーションが同じ名前を持つ 2 つ以上のプログラミング要素にアクセスしている場合は、名前の参照を修飾する必要があります。 たとえば、<xref:System.Windows.Forms>と<xref:System.Web.UI.WebControls>両方名前空間を含む、`Label`クラス (<xref:System.Windows.Forms.Label?displayProperty=nameWithType>と<xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>)。 アプリケーションは、両方を使用している場合、またはそれ自体を定義する`Label`クラス、する必要がありますと区別する、さまざまな`Label`オブジェクト。 変数の宣言で名前空間やインポート エイリアスが含まれます。 次の例では、インポート エイリアスを使用します。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>その他のコンテナー要素のメンバー  
 別のクラスまたは構造体の非共有メンバーを使用する場合は、最初変数やクラスまたは構造体のインスタンスを指す式でメンバー名を修飾する必要があります。 次の例では、`demoClass`という名前のクラスのインスタンスは、`class1`です。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 メンバーがないことを修飾するためにクラス名自体を使用することはできません[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)です。 最初、object 変数にインスタンスを作成する必要があります (ここでは`demoClass`) して変数の名前で参照します。  
  
 クラスまたは構造体がある場合、`Shared`メンバー クラスまたは構造体の名前を持つか、変数またはインスタンスを指す式では、そのメンバーを修飾することができます。  
  
 モジュールが、個別のインスタンスとそのすべてのメンバーは`Shared`既定です。 そのため、モジュール名を持つモジュール メンバーを修飾します。  
  
 次の例では、モジュール メンバー プロシージャへの修飾参照を示します。 2 つの例では、宣言`Sub`という両方の手順、`perform`プロジェクト内の異なるモジュールでします。 1 つずつでは、独自のモジュール内で修飾なしで指定できますが、それ以外の任意の場所から参照されている場合に修飾する必要があります。 参照されて最終的なので`module3`が満たしていない`perform`コンパイラは、その参照を解決できません。  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>プロジェクトへの参照  
 使用する[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)別のプロジェクトで定義された要素を設定する必要あります最初、*参照*そのプロジェクトのアセンブリまたは型のライブラリにします。 参照を設定するには、をクリックして**参照の追加**上、**プロジェクト**メニューのまたはを使用して、 [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)コマンド ライン コンパイラ オプション。  
  
 たとえばの XML オブジェクト モデルを使用することができます、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 参照を設定した場合、<xref:System.Xml>名前空間を宣言して使用できますそのクラスのいずれかのように<xref:System.Xml.XmlDocument>です。 次の例で<xref:System.Xml.XmlDocument>です。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>コンテナー要素のインポート  
 使用することができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)に*インポート*モジュールまたはを使用するクラスが含まれている名前空間。 これにより、名前を完全に修飾せずに、インポートされた名前空間で定義された要素を参照してください。 次の例は、インポートする前の例を書き換える、<xref:System.Xml>名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 さらに、`Imports`ステートメントを定義できます、*インポート エイリアス*インポートされた名前空間ごとにします。 これにより、ソース コードできるだけ短く、また読みやすくします。 次の例を使用する前の例を書き換える`xD`のエイリアスとして、<xref:System.Xml>名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports`ステートメントは行いません他のプロジェクトからの要素をアプリケーションに使用できます。 これは行われず、参照を設定します。 名前空間だけをインポートするには、その名前空間で定義されている名前を修飾するための要件を削除します。  
  
 使用することも、`Imports`モジュール、クラス、構造体、および列挙型をインポートするステートメント。 このようなインポートされた要素修飾なしのメンバーを使用できます。 ただし、クラスと構造体変数またはクラスまたは構造体のインスタンスに評価される式での非共有メンバーを常に修飾する必要があります。  
  
## <a name="naming-guidelines"></a>名前付けのガイドライン  
 同じ名前を持つ 2 つまたは複数のプログラミング要素を定義するとき、*あいまいさを名前*名前への参照を解決するのには、コンパイラがしようとしたときにします。 1 つの定義がスコープ内にある複数のまたは定義がスコープでない場合は、参照を解決できません。 例については、このヘルプ ページの修飾参照例」を参照してください。  
  
 すべての要素の一意の名前を指定すると、名前のあいまいさを回避できます。 名前空間、モジュール、またはクラス名を修飾することがなく任意の要素への参照をことができます。 正しくない要素を誤って参照する可能性を低くします。  
  
## <a name="shadowing"></a>シャドウ  
 2 つのプログラミング要素は、同じ名前を共有する場合それらのいずれかの非表示に、または*シャドウ*、もう 1 つです。 シャドウされた要素は参照できません。代わりに、コードでは、シャドウされた要素名を使用する場合、Visual Basic コンパイラに解決されます、シャドウする要素。 例と詳細な説明については、次を参照してください。 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)
