---
title: オブジェクト変数の宣言 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: f5f77b81380d997e078a9f52ac4aae6f6e975575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656283"
---
# <a name="object-variable-declaration-visual-basic"></a>オブジェクト変数の宣言 (Visual Basic)
オブジェクト変数を宣言するのにには、通常の宣言ステートメントを使用します。 どちらか、データ型を指定する`Object`(つまり、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)) または元のオブジェクトを作成する具体的なクラスです。  
  
 として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>です。  
  
 特定のオブジェクト クラスを持つ変数を宣言する場合は、すべてのメソッドとそのクラスと継承クラスによって公開されるプロパティにアクセスできます。 持つ変数を宣言する場合<xref:System.Object>のメンバーのみにアクセスできる、<xref:System.Object>クラスを有効にする場合を除き、`Option Strict Off`遅延バインドできるようにします。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 オブジェクト変数を宣言するのにには、次の構文を使用します。  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 指定することも[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、 `Protected Friend`、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、または[静的](../../../../visual-basic/language-reference/modifiers/static.md)宣言します。 次の例の宣言は有効です。  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>遅延バインディングと、事前バインディング  
 場合がありますの特定のクラスが、コードが実行されるまで不明です。 この例でオブジェクト変数を宣言する必要があります、`Object`データ型。 任意の型のオブジェクトへの参照を一般的なが作成され、実行時に特定のクラスが割り当てられます。 これと呼ばれる*遅延バインディング*です。 遅延バインディングには、その他の実行時間が必要です。 メソッドとそれに割り当てる最も最近クラスのプロパティに、コードも制限されます。 これにより、コードが別のクラスのメンバーにアクセスを試みると実行時エラーが発生することができます。  
  
 コンパイル時に特定のクラスをわかっている場合に、そのクラスを指定するオブジェクト変数を宣言する必要があります。 これは、*事前バインディング*と呼ばれます。 事前バインディングは、パフォーマンスが向上し、コードのすべてのメソッドと、特定のクラスのプロパティへのアクセスを保証します。 変数の場合は前の例宣言で`objA`クラスのオブジェクトのみを使用して<xref:System.Windows.Forms.Label?displayProperty=nameWithType>を指定する必要があります`As System.Windows.Forms.Label`その宣言でします。  
  
### <a name="advantages-of-early-binding"></a>事前バインディングの利点  
 特定のクラスとしてオブジェクト変数を宣言すると、いくつかの利点を示します。  
  
-   自動的な型チェック  
  
-   特定のクラスのすべてのメンバーに対するアクセスの保証  
  
-   コード エディターで Microsoft IntelliSense サポート  
  
-   コードの読みやすくします。  
  
-   コードの少ないエラー  
  
-   エラーが検出は、コンパイル時ではなく実行時  
  
-   コードの実行を高速化  
  
## <a name="access-to-object-variable-members"></a>オブジェクト変数のメンバーへのアクセス  
 ときに`Option Strict`なって`On`、オブジェクト変数が宣言するクラスのプロパティとメソッドのみにアクセスできます。 次に例を示します。  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 この例の場合、 `p` で使用できるのは <xref:System.Object> クラス自体のメンバーのみです。 `Left` プロパティは含まれません。 一方、 `q` は、 <xref:System.Windows.Forms.Label>型として宣言されているため、 <xref:System.Windows.Forms.Label> 名前空間の <xref:System.Windows.Forms> クラスのすべてのメソッドとプロパティを使用できます。  
  
## <a name="flexibility-of-object-variables"></a>オブジェクト変数の柔軟性  
 継承階層内のオブジェクトを使用する場合がある、オブジェクト変数を宣言するのに使用するどのクラスです。 クラスを選択するときに、クラスのメンバーへのアクセスに対してオブジェクトの代入の柔軟性のバランスを考慮する必要があります。 たとえば、継承階層につながる、<xref:System.Windows.Forms.Form?displayProperty=nameWithType>クラス。  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 アプリケーションと呼ばれるフォーム クラスを定義すると仮定`specialForm`、クラスから継承される<xref:System.Windows.Forms.Form>です。 具体的を参照するオブジェクト変数を宣言する`specialForm`次の例を示します。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 前の例で、宣言の制限、変数`nextForm`クラスのオブジェクトに`specialForm`、すべてのメソッドとプロパティのこともできますしかし、`specialForm`に利用可能な`nextForm`元となるすべてのクラスのすべてのメンバーと、。`specialForm`を継承します。  
  
 一般的なオブジェクト変数を設定するには、宣言する型にすることを<xref:System.Windows.Forms.Form>次の例を示します。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 前の例で、宣言には、任意のフォームをアプリケーションを割り当てることができます`anyForm`です。 ただしが`anyForm`クラスのすべてのメンバーにアクセスできる<xref:System.Windows.Forms.Form>、追加のメソッドやプロパティなどの特定のフォーム定義のいずれかを使用できません`specialForm`です。  
  
 基底クラスのすべてのメンバーが派生クラスで使用できますが、派生クラスで追加されたメンバーが、基底クラスにご利用いただけません。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てます](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [方法: オブジェクトのメンバーにアクセスする](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
