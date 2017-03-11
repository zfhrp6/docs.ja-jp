---
title: "Anonymous Type Definition (Visual Basic) | Microsoft Docs"
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
  - "anonymous types [Visual Basic], type definition"
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Anonymous Type Definition (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラは、匿名型のインスタンスの宣言に応答して、指定された型のプロパティを含む新しいクラス定義を作成します。  
  
## コンパイラが生成するコード  
 次の `product` の定義の場合、コンパイラは、`Name`、`Price`、および `OnHand` を含む新しいクラス定義を作成します。  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_1.vb)]  
  
 このクラス定義には、次のようなプロパティの定義が含まれます。  主要なプロパティには `Set` メソッドがないことに注意してください。  主要なプロパティの値は読み取り専用です。  
  
```vb#  
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
  
 さらに、匿名型の定義には、既定のコンストラクターが含まれます。  パラメーターを必要とするコンストラクターは使用できません。  
  
 匿名型の宣言に、少なくとも 1 つの主要なプロパティが含まれている場合、型定義は、<xref:System.Object> から継承された 3 つのメンバー \(<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、および <xref:System.Object.ToString%2A>\) をオーバーライドします。  主要なプロパティの宣言がない場合は、<xref:System.Object.ToString%2A> だけがオーバーライドされます。  このオーバーライドには、次の機能があります。  
  
-   `Equals` は、2 つの匿名型のインスタンスが同一のインスタンスである、またはそれらが以下の条件に適合する場合は `True` を返します。  
  
    -   プロパティの数が同じである。  
  
    -   名前と推論された型が一致するプロパティが、同じ順序で宣言されている。  名前の比較では、大文字と小文字が区別されません。  
  
    -   少なくとも 1 つのプロパティが主要なプロパティであり、`Key` キーワードが同一のプロパティに適用されている。  
  
    -   対応する主要なプロパティのペアごとの比較で、`True` が返される。  
  
     たとえば、次の例では、`Equals` は、`employee01` と `employee08` に対してのみ `True` を返します。  各行の前のコメントは、新しいインスタンスが `employee01` と一致しない理由を示します。  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` は、適切な一意の GetHashCode アルゴリズムを提供します。  このアルゴリズムは、主要なプロパティのみを使用してハッシュ コードを計算します。  
  
-   `ToString` は、次の例に示すように、連結されたプロパティ値の文字列を返します。  主要なプロパティとそれ以外のプロパティの両方を含みます。  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_3.vb)]  
  
 明示的に名前を付けられた匿名型のプロパティは、これらの生成されるメソッドと競合することはできません。  つまり、`.Equals`、`.GetHashCode`、または `.ToString` を使用してプロパティに名前を付けることはできません。  
  
 少なくとも 1 つの主要なプロパティを含む匿名型の定義は、<xref:System.IEquatable%601?displayProperty=fullName> インターフェイスも実装します \(`T` は匿名型の型です\)。  
  
> [!NOTE]
>  匿名型の宣言は、それらが同一のアセンブリの中にあり、プロパティの名前と推論された型が同じであり、それらのプロパティが同じ順序で宣言され、同じプロパティが主要なプロパティとマークされている場合のみ、同一の匿名型を作成します。  
  
## 参照  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)