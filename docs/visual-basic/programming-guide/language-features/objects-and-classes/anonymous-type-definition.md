---
title: 匿名型の定義 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 179fb9773fde2631666498d54894037b2bbfd087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649621"
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名型の定義 (Visual Basic)
匿名型のインスタンスの宣言に応答してでは、コンパイラは、型の指定したプロパティを格納する新しいクラス定義を作成します。  
  
## <a name="compiler-generated-code"></a>コンパイラによって生成されたコード  
 定義については、次の`product`、コンパイラがプロパティを格納する新しいクラス定義を作成`Name`、 `Price`、および`OnHand`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 クラス定義には、次のようなプロパティ定義が含まれています。 あることに注意してくださいありません`Set`キーのプロパティのメソッドです。 キー プロパティの値とは、読み取り専用です。  
  
```vb  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 さらに、匿名型の定義には、既定のコンス トラクターが含まれます。 パラメーターが必要なコンス トラクターが許可されていません。  
  
 型定義がから継承した 3 つのメンバーをオーバーライドして匿名型の宣言には、少なくとも 1 つのキー プロパティが含まれている場合、 <xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。 キー プロパティが宣言されていない場合、のみ<xref:System.Object.ToString%2A>はオーバーライドします。 上書きは、次の機能を提供します。  
  
-   `Equals` 返します`True`匿名型の 2 つのインスタンスが、同じインスタンスである場合、または、次の条件を満たしている場合。  
  
    -   同じ数のプロパティがあります。  
  
    -   プロパティが同じ名前を持つ、同じ順序で宣言されているし、推論された型が同じです。 名前の比較は区別されません。  
  
    -   キー プロパティでは、少なくとも 1 つのプロパティと`Key`キーワードは、同じプロパティに適用します。  
  
    -   キー プロパティの対応する各ペアの比較を返します`True`です。  
  
     たとえば、次の例についてで`Equals`を返します`True`のみ`employee01`と`employee08`です。 各行は、なぜ新しいインスタンスと一致しません理由を指定する前に、コメント`employee01`です。  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` 適切に一意の GetHashCode アルゴリズムを提供します。 アルゴリズムでは、キー プロパティだけを使って、ハッシュ コードを計算します。  
  
-   `ToString` 次の例のように連結されたプロパティの値の文字列を返します。 キーとキー以外のプロパティの両方が含まれます。  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 匿名型のプロパティを明示的に指定されたこれらの生成されたメソッドと競合することはできません。 つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`プロパティの名前を付ける。  
  
 匿名型の定義には、少なくとも 1 つを含むキー プロパティも実装して、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の型です。  
  
> [!NOTE]
>  匿名型の宣言は、同じアセンブリで発生した、それらのプロパティは、同じ名前を持つと推論された型が同じで、プロパティが同じ順序で宣言されているおよび同じプロパティがキー プロパティとしてマークされている場合にのみ、同じ匿名型を作成します。  
  
## <a name="see-also"></a>関連項目  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
