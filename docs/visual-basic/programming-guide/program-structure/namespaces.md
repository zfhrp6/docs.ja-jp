---
title: "Visual Basic における名前空間 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.global"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "アセンブリ [Visual Basic], 名前空間"
  - "名前の競合"
  - "Global キーワード [Visual Basic]"
  - "名前空間の汚染"
  - "名前、競合の回避"
  - "名前付けの競合、名前空間"
  - "名前空間、アセンブリ"
  - "Visual Basic コード、名前空間"
  - "完全修飾名"
  - "名前付け規則、名前付けの競合"
  - "名前空間"
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Visual Basic における名前空間
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アセンブリ内で定義されているオブジェクトは、名前空間によって編成されています。 アセンブリには複数の名前空間を含めることができます。さらに、名前空間の中に他の名前空間を含めることもできます。 名前空間を使用するとあいまいさがなくなるため、クラス ライブラリを使用する場合など、多数のオブジェクトを使用する場合に参照が簡単になります。  
  
 たとえば、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] では <xref:System.Windows.Forms?displayProperty=fullName> 名前空間に <xref:System.Windows.Forms.ListBox> クラスが定義されています。 次のコードは、このクラスの完全修飾名を使用して変数を宣言する方法を示しています。  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## 名前の競合の回避  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の名前空間は、他のライブラリで似た名前が使用されている場合にクラス ライブラリの開発者が遭遇する、*名前空間の汚染*と呼ばれる問題に対処しています。 このような既存コンポーネントとの競合は、*名前の競合*とも呼ばれます。  
  
 たとえば、`ListBox` という名前の新しいクラスを作成した場合、プロジェクト内ではこのクラスを修飾子を付けずに使用できます。 ただし、同じプロジェクトで [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の <xref:System.Windows.Forms.ListBox> クラスを使用する場合は、参照を一意にするために完全修飾参照を使用する必要があります。 参照が一意でない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、名前があいまいであることを示すエラーを生成します。 次のコード例では、これらのオブジェクトを宣言する方法を示しています。  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 次の図は、いずれも `ListBox` という名前のオブジェクトを持つ、2 つの名前空間の階層を表しています。  
  
 ![名前空間階層](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.png "vaNamespaceHierarchy")  
  
 既定では、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で作成するすべての実行可能ファイルには、プロジェクトと同名の名前空間が含まれます。 たとえば、`ListBoxProject` という名前のプロジェクト内でオブジェクトを定義した場合、実行可能ファイル ListBoxProject.exe には `ListBoxProject` という名前空間が含まれます。  
  
 複数のアセンブリで同じ名前空間を使用することができます。[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はこれらを 1 つの名前セットとして扱います。 たとえば、`Assemb1` というアセンブリの `SomeNameSpace` という名前空間のクラスを定義した後に、`Assemb2` というアセンブリの同じ名前空間のクラスを定義できます。  
  
## 完全修飾名  
 完全修飾名は、オブジェクトが定義されている名前空間の名前で始まるオブジェクト参照です。 他のプロジェクトで定義されているオブジェクトを使用するには、**\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックしてそのクラスへの参照を作成し、コード内でそのオブジェクトの完全修飾名を使用します。 次のコードは、別のプロジェクトの名前空間のオブジェクトを使用して完全修飾名を使用する方法を示しています。  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 完全修飾名を使用すると、どのオブジェクトを使用するかをコンパイラが認識できるため、名前の競合を防止できます。 ただし、名前自体が長くなるため、使いにくくなります。 この問題を回避するには、`Imports` ステートメントを使って*エイリアス*を定義します。エイリアスとは、完全修飾名の代わりに使用できる短い名前です。 たとえば、次のコード例では、2 つの完全修飾名に対してエイリアスを作成し、作成したエイリアスを使って 2 つのオブジェクトを定義しています。  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 エイリアスを指定せずに `Imports` ステートメントを使用すると、インポートした名前空間のすべての名前を修飾子を付けずに使用できます。ただし、それらの名前がプロジェクト内で一意であることが必要です。 プロジェクトに、同じ名前の複数の項目を持つ名前空間をインポートする `Imports` ステートメントがある場合は、それらの名前を使用するときに完全修飾名を使用する必要があります。 たとえば、プロジェクトに次の 2 つの `Imports` ステートメントがあるとします。  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 この場合、完全修飾名を使わずに `Class1` を使おうとすると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] から、`Class1` という名前があいまいであることを指摘するエラーが生成されます。  
  
## 名前空間レベルのステートメント  
 名前空間内では、モジュール、インターフェイス、クラス、デリゲート、列挙体、構造体、他の名前空間などの項目を定義できます。 プロパティ、プロシージャ、変数、イベントなどの項目を名前空間のレベルで定義することはできません。 これらの項目は、モジュール、構造体、クラスなどのコンテナー内で宣言する必要があります。  
  
## 完全修飾名の Global キーワード  
 入れ子になった階層構造の名前空間を定義すると、その階層構造の内部にあるコードが .NET Framework の <xref:System?displayProperty=fullName> 名前空間にアクセスできない場合があります。 次の例は、`SpecialSpace.System` 名前空間から <xref:System?displayProperty=fullName> にアクセスできない階層構造を示しています。  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 この場合、`SpecialSpace.System` に `Int32` が定義されていないため、Visual Basic コンパイラは <xref:System.Int32?displayProperty=fullName> への参照を正しく解決できません。`Global` キーワードを使用すると、修飾チェーンを .NET Framework クラス ライブラリの最も外側のレベルで開始できます。 これにより、クラス ライブラリの <xref:System?displayProperty=fullName> 名前空間や、その他のあらゆる名前空間を指定できるようになります。 次に例を示します。  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 `Global` を使用して、<xref:Microsoft.VisualBasic?displayProperty=fullName> などの他のルート レベルの名前空間、およびプロジェクトに関連する任意の名前空間にアクセスできます。  
  
## 名前空間のステートメントでの Global キーワード  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)で `Global` キーワードを使用できます。 これにより、プロジェクトのルート名前空間から名前空間を定義できます。  
  
 プロジェクト内のすべての名前空間は、プロジェクトのルート名前空間に基づいています。  Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。 たとえば、プロジェクト名が `ConsoleApplication1` である場合、そのプログラミング要素は `ConsoleApplication1` 名前空間に属します。`Namespace Magnetosphere` を宣言すると、プロジェクトの `Magnetosphere` への参照は `ConsoleApplication1.Magnetosphere` にアクセスします。  
  
 次の例では、プロジェクトのルート名前空間から名前空間を宣言するために `Global` キーワードを使用しています。  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 名前空間宣言では、`Global` を別の名前空間に入れ子にすることはできません。  
  
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic) を使用して、プロジェクトの**ルート名前空間**を表示および変更できます。  新しいプロジェクトの場合、**ルート名前空間**の既定値は、プロジェクト名です。`Global` を最上位レベルの名前空間にするには、**ルート名前空間**のエントリを消去して、ボックスを空にします。**ルート名前空間**を消去すると、名前空間の宣言で `Global` キーワードの必要がなくなります。  
  
 `Namespace` ステートメントで .NET framework の名前空間にもなっている名前を宣言する場合、`Global` キーワードが完全修飾名で使用されていない場合、.NET Framework 名前空間は使用できなくなります。`Global` キーワードを使用せずに、.NET Framework 名前空間へのアクセスを有効にするには、`Global` キーワードを `Namespace` ステートメントに含めます。  
  
 次の例では、`System.Text` 名前空間の宣言で、`Global` キーワードを使用しています。  
  
 名前空間の宣言に `Global` キーワードが含まれていない場合、<xref:System.Text.StringBuilder> にアクセスするには、`Global.System.Text.StringBuilder` を指定する必要があります。`ConsoleApplication1` という名前のプロジェクトで、`Global` キーワードが使用されていない場合、`System.Text` を参照すると、`ConsoleApplication1.System.Text` にアクセスすることになります。  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## 参照  
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName>   
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法: コマンド ラインを使用してアセンブリを作成および使用する](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Office ソリューションのコードの記述](/office-dev/office-dev/writing-code-in-office-solutions)