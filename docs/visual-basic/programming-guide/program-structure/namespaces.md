---
title: "Visual Basic における名前空間 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe94e65ddbb4ebd2f7d26e8750a0a7ef5d3153af
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-in-visual-basic"></a>Visual Basic における名前空間
アセンブリ内で定義されているオブジェクトは、名前空間によって編成されています。 アセンブリには複数の名前空間を含めることができます。さらに、名前空間の中に他の名前空間を含めることもできます。 名前空間を使用するとあいまいさがなくなるため、クラス ライブラリを使用する場合など、多数のオブジェクトを使用する場合に参照が簡単になります。  
  
 たとえば、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]を定義、<xref:System.Windows.Forms.ListBox>クラス、<xref:System.Windows.Forms?displayProperty=fullName>名前空間</xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms.ListBox>。 次のコードは、このクラスの完全修飾名を使用して変数を宣言する方法を示しています。  
  
 [!code-vb[VbVbalrApplication&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>名前の競合の回避  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]名前空間とも呼ばれる問題に対処*名前空間の汚染*で別のライブラリでの類似した名前を使用してクラス ライブラリの開発者が妨げられます。 このような既存コンポーネントとの競合は、 *名前の競合*とも呼ばれます。  
  
 たとえば、 `ListBox`という名前の新しいクラスを作成した場合、プロジェクト内ではこのクラスを修飾子を付けずに使用できます。 ただし、使用する場合、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox>クラス同じプロジェクト内の参照を一意にするための完全修飾参照を使用する必要があります</xref:System.Windows.Forms.ListBox>。 参照が一意でない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、名前があいまいであることを示すエラーを生成します。 次のコード例では、これらのオブジェクトを宣言する方法を示しています。  
  
 [!code-vb[VbVbalrApplication&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 次の図は、いずれも `ListBox`という名前のオブジェクトを持つ、2 つの名前空間の階層を表しています。  
  
 ![Namespace 階層](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 既定では、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で作成するすべての実行可能ファイルには、プロジェクトと同名の名前空間が含まれます。 たとえば、 `ListBoxProject`という名前のプロジェクト内でオブジェクトを定義した場合、実行可能ファイル ListBoxProject.exe には `ListBoxProject`という名前空間が含まれます。  
  
 複数のアセンブリで同じ名前空間を使用することができます。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はこれらを&1; つの名前セットとして扱います。 たとえば、`Assemb1` というアセンブリの `SomeNameSpace` という名前空間のクラスを定義した後に、`Assemb2` というアセンブリの同じ名前空間のクラスを定義できます。  
  
## <a name="fully-qualified-names"></a>完全修飾名  
 完全修飾名は、オブジェクトが定義されている名前空間の名前で始まるオブジェクト参照です。 他のプロジェクトで定義されているオブジェクトを使用するには、 **[プロジェクト]** メニューの **[参照の追加]** をクリックしてそのクラスへの参照を作成し、コード内でそのオブジェクトの完全修飾名を使用します。 次のコードは、別のプロジェクトの名前空間のオブジェクトを使用して完全修飾名を使用する方法を示しています。  
  
 [!code-vb[VbVbalrApplication&#8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 完全修飾名を使用すると、どのオブジェクトを使用するかをコンパイラが認識できるため、名前の競合を防止できます。 ただし、名前自体が長くなるため、使いにくくなります。 この問題を回避するには、 `Imports` ステートメントを使って *エイリアス*を定義します。エイリアスとは、完全修飾名の代わりに使用できる短い名前です。 たとえば、次のコード例では、2 つの完全修飾名に対してエイリアスを作成し、作成したエイリアスを使って&2; つのオブジェクトを定義しています。  
  
 [!code-vb[VbVbalrApplication&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 エイリアスを指定せずに `Imports` ステートメントを使用すると、インポートした名前空間のすべての名前を修飾子を付けずに使用できます。ただし、それらの名前がプロジェクト内で一意であることが必要です。 プロジェクトに、同じ名前の複数の項目を持つ名前空間をインポートする `Imports` ステートメントがある場合は、それらの名前を使用するときに完全修飾名を使用する必要があります。 たとえば、プロジェクトに次の&2; つの `Imports` ステートメントがあるとします。  
  
 [!code-vb[VbVbalrApplication&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 この場合、完全修飾名を使わずに `Class1` を使おうとすると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] から、`Class1` という名前があいまいであることを指摘するエラーが生成されます。  
  
## <a name="namespace-level-statements"></a>名前空間レベルのステートメント  
 名前空間内では、モジュール、インターフェイス、クラス、デリゲート、列挙体、構造体、他の名前空間などの項目を定義できます。 プロパティ、プロシージャ、変数、イベントなどの項目を名前空間のレベルで定義することはできません。 これらの項目は、モジュール、構造体、クラスなどのコンテナー内で宣言する必要があります。  
  
## <a name="global-keyword-in-fully-qualified-names"></a>完全修飾名の Global キーワード  
 その階層内のコードがへのアクセスをブロックされている名前空間の入れ子になった階層を定義している場合、 <xref:System?displayProperty=fullName>.NET Framework の名前空間</xref:System?displayProperty=fullName>。 次の例では、階層を`SpecialSpace.System` <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName>へのアクセスをブロックの名前空間  
  
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
  
 その結果、Visual Basic コンパイラにはへの参照が解決できない正常に<xref:System.Int32?displayProperty=fullName>ので、`SpecialSpace.System`が定義されていません`Int32`</xref:System.Int32?displayProperty=fullName>。 `Global` キーワードを使用すると、修飾チェーンを .NET Framework クラス ライブラリの最も外側のレベルで開始できます。 これによりを指定する、<xref:System?displayProperty=fullName>名前空間またはクラス ライブラリの他の名前空間</xref:System?displayProperty=fullName>。 次に例を示します。  
  
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
  
 使用することができます`Global`などにアクセスする他のルート レベルの名前空間<xref:Microsoft.VisualBasic?displayProperty=fullName>、およびプロジェクトに関連付けられている任意の名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName>。  
  
## <a name="global-keyword-in-namespace-statements"></a>名前空間のステートメントでの Global キーワード  
 使用することも、`Global`のキーワード、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)します。 これにより、プロジェクトのルート名前空間から名前空間を定義できます。  
  
 プロジェクト内のすべての名前空間は、プロジェクトのルート名前空間に基づいています。  Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。 たとえば、プロジェクト名が `ConsoleApplication1`である場合、そのプログラミング要素は `ConsoleApplication1`名前空間に属します。 `Namespace Magnetosphere`を宣言すると、プロジェクトの `Magnetosphere` への参照は `ConsoleApplication1.Magnetosphere`にアクセスします。  
  
 次の例では、プロジェクトのルート名前空間から名前空間を宣言するために `Global` キーワードを使用しています。  
  
 [!code-vb[VbVbalrApplication #&22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 名前空間宣言では、 `Global` を別の名前空間に入れ子にすることはできません。  
  
 使用することができます、[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)を表示および変更、**ルート Namespace**プロジェクトのです。  新しいプロジェクトの場合、 **ルート名前空間** の既定値は、プロジェクト名です。 `Global` を最上位レベルの名前空間にするには、 **ルート名前空間** のエントリを消去して、ボックスを空にします。 **ルート名前空間** を消去すると、名前空間の宣言で `Global` キーワードの必要がなくなります。  
  
 `Namespace` ステートメントで .NET framework の名前空間にもなっている名前を宣言する場合、 `Global` キーワードが完全修飾名で使用されていない場合、.NET Framework 名前空間は使用できなくなります。 `Global` キーワードを使用せずに、.NET Framework 名前空間へのアクセスを有効にするには、 `Global` キーワードを `Namespace` ステートメントに含めます。  
  
 次の例では、 `Global` 名前空間の宣言で、 `System.Text` キーワードを使用しています。  
  
 場合、`Global`キーワードが名前空間宣言に存在しなかった<xref:System.Text.StringBuilder>を指定せずにアクセスできませんでした`Global.System.Text.StringBuilder`</xref:System.Text.StringBuilder>。 `ConsoleApplication1`という名前のプロジェクトで、 `System.Text` キーワードが使用されていない場合、 `ConsoleApplication1.System.Text` を参照すると、 `Global` にアクセスすることになります。  
  
 [!code-vb[VbVbalrApplication #&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName>   
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [方法: を作成し、コマンドラインを使用してアセンブリを使用します。](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Office ソリューションのコードの記述](https://msdn.microsoft.com/library/bb608596)
