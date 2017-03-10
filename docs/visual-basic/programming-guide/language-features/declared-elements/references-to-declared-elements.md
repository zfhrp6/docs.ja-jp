---
title: "宣言された要素の参照 (Visual Basic) | Microsoft Docs"
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
  - "宣言された要素"
  - "宣言された要素の参照"
  - "修飾名"
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# 宣言された要素の参照 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コードが宣言された要素を参照している場合、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラでその名前の適切な宣言への参照を名前に一致します。 参照にはそれらの要素を制御するには複数の要素が同じ名前で宣言されている場合 *正規* の名前。  
  
 コンパイラが名の宣言でへの参照を名前に一致しようとした場合、 *だけ狭いスコープ*します。 これは、参照するコードから開始して、下位レベルの要素を含む外側はことを意味します。  
  
 次の例では、同じ名前の 2 つの変数への参照を示します。 例では、2 つの変数を宣言して、各名前付き `totalCount`, 、モジュール内でスコープのさまざまなレベルで `container`します。 ときにプロシージャ `showCount` 表示 `totalCount` 修飾なし、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラが最も狭いスコープ、つまり内でローカル宣言を使用して宣言への参照を解決 `showCount`します。 適用されるときに `totalCount` を含むモジュールを使用して `container`, 、コンパイラがより広いスコープを使用して宣言への参照を解決します。  
  
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
 この検索処理をオーバーライドし、名前で宣言されているより広いスコープする必要がありますを指定する場合 *修飾* より広いスコープのコンテナー要素の名前。 場合によっては、コンテナーの要素を修飾する必要がありますも。  
  
 ターゲット要素を定義する場所を識別する情報、ソース ステートメント内の前の名前を修飾します。 この情報と呼ばれる、 *修飾文字列*します。 1 つを含めることまたは複数の名前空間とモジュールの場合、クラスまたは構造体します。  
  
 修飾文字列は、モジュール、クラス、または対象の要素を含む構造体に明確を指定する必要があります。 コンテナーは、他のコンテナー要素、通常は名前空間に存在するさらに可能性があります。 修飾文字列に含まれるいくつかの要素を含める必要がある可能性があります。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>その名前を修飾することによって宣言された要素にアクセスするには  
  
1.  要素が定義されている場所を決定します。 これは、名前空間または名前空間の階層も含まれます。 最下位レベルの名前空間内では、モジュール、クラスまたは構造体の要素を含める必要があります。  
  
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
  
2.  ターゲット要素の場所に基づいて修飾パスを決定します。 最上位レベルの名前空間を持つ起動、最下位レベルの名前空間に進み、モジュール、クラス、または対象の要素を含む構造体で終了します。 パス内の各要素には、それに続く要素を含める必要があります。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  ターゲット要素の修飾文字列を準備します。 ピリオドを挿入 (`.`) のパスのすべての要素の後です。 アプリケーションによっては、修飾文字列内のすべての要素へのアクセスが必要です。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  式または通常の方法で対象となる要素を参照する代入ステートメントを記述します。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  修飾文字列とターゲットの要素名の前に記述します。 名前は、ピリオドの直後 (`.`) モジュール、クラス、または、要素を格納する構造体を参照します。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  コンパイラでは、修飾文字列を使用して、ターゲット要素の参照と一致させて、明確に明確な宣言を見つけます。  
  
 アプリケーションに同じ名前を持つ 2 つ以上のプログラミング要素へのアクセスがある場合は、名前の参照を修飾することもあります。 たとえば、 <xref:System.Windows.Forms> と <xref:System.Web.UI.WebControls> 両方名前空間が含まれて、 `Label` クラス (<xref:System.Windows.Forms.Label?displayProperty=fullName> と <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>)。 アプリケーションは、両方を使用している場合、またはそれ自体を定義する `Label` クラス、さまざまなを区別する必要があります `Label` オブジェクトです。 変数の宣言には、名前空間またはインポート エイリアスを含めます。 次の例では、インポート エイリアスを使用します。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>別のコンテナー要素のメンバー  
 別のクラスまたは構造体の非共有メンバーを使用する場合は、最初に変数またはクラスまたは構造体のインスタンスを指す式でメンバー名を修飾する必要があります。 次の例で `demoClass` という名前のクラスのインスタンスは、 `class1`です。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 クラス名自体を使用していないメンバーを修飾することはできません [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)します。 まず、オブジェクト変数のインスタンスを作成する必要があります (ここで `demoClass`) それを変数名で参照します。  
  
 クラスまたは構造体がある場合、 `Shared` メンバー、またはいずれかでクラスまたは構造体の名前の変数またはインスタンスを指す式には、そのメンバーを修飾することができます。  
  
 モジュールには、個別のインスタンスはありませんし、そのすべてのメンバーが `Shared` 既定です。 そのため、モジュール名を持つモジュール メンバーを修飾します。  
  
 次の例では、モジュール メンバー プロシージャへの修飾参照を示します。 2 つの例 `Sub` という名前の手順、 `perform`, 、プロジェクト内の異なるモジュールでします。 1 つずつでは、独自のモジュール内の修飾なしで指定できますが、それ以外の任意の場所から参照されている場合に限定する必要があります。 最後を参照するため `module3` 修飾していない `perform`, 、コンパイラは、その参照を解決できません。  
  
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
 使用する [パブリック](../../../../visual-basic/language-reference/modifiers/public.md) 、別のプロジェクトで定義されている要素は、まず設定、 *参照* そのプロジェクトのアセンブリやタイプ ライブラリにします。 参照を設定する] をクリックして **参照の追加** 上、 **プロジェクト** ] メニュー、 [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) コマンド ライン コンパイラ オプション。  
  
 XML オブジェクト モデルを使用するなど、 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)]です。 参照を設定した場合、 <xref:System.Xml> 名前空間宣言し、をなど、そのクラスのいずれかを使用して <xref:System.Xml.XmlDocument>します。 次の例では使用 <xref:System.Xml.XmlDocument>します。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>コンテナー要素のインポート  
 使用することができます、 [Imports ステートメント (.NET 名前空間よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) に *インポート* モジュールまたはを使用するクラスを含む名前空間。 これにより、その名前を完全に修飾せずにインポートされた名前空間で定義された要素を参照してください。 次の例は、インポートする前の例を書き換える、 <xref:System.Xml> 名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 さらに、 `Imports` ステートメントで定義できる、 *インポート エイリアス* インポートされた名前空間ごとにします。 これにより、ソース コード短く、読みやすくします。 次の例を使用する前の例を書き換える `xD` のエイリアスとして、 <xref:System.Xml> 名前空間。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
  `Imports` ステートメントは行いません要素が他のプロジェクトからアプリケーションに使用します。 つまり、参照を設定場所は考慮しません。 だけに、名前空間をインポートするには、その名前空間で定義されている名前を修飾するための要件を削除します。  
  
 使用することも、 `Imports` モジュール、クラス、構造体、および列挙型をインポートするステートメントです。 このようなインポートされた要素の修飾なしのメンバーを使用して送信することができます。 ただし、クラスと構造体は、変数またはクラスまたは構造体のインスタンスに評価される式の非共有メンバーを常に修飾する必要があります。  
  
## <a name="naming-guidelines"></a>名前付けのガイドライン  
 同じ名前を持つ 2 つ以上のプログラミング要素を定義するとき、 *あいまいさという名前を* 、コンパイラがその名前への参照を解決しようとすると発生することができます。 1 つの定義がスコープ内にある数より多い場合、または、参照が解決されない定義がスコープでない場合は、です。 例については、このページで「修飾参照の使用例」を参照してください。  
  
 すべての要素に一意の名前を提供することにより、名前のあいまいさを回避できます。 その名の名前空間、モジュール、またはクラスを修飾しなくても任意の要素への参照をすることができます。 正しくない要素を誤って参照する可能性を低くします。  
  
## <a name="shadowing"></a>シャドウ  
 2 つのプログラミング要素は、同じ名前を共有する場合の 1 つ非表示にできます、または *シャドウ*, 、もう 1 つです。 影付きの要素は参照できません。代わりに、コードが影付きの要素名を使用する場合、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラでは、それを解決する要素。 例と詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)します。  
  
## <a name="see-also"></a>「  
 [宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Imports ステートメント (.NET 名前空間よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [パブリック](../../../../visual-basic/language-reference/modifiers/public.md)