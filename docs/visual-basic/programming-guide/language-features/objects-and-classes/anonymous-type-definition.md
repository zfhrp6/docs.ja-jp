---
title: 匿名型の定義 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="24aec-102">匿名型の定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24aec-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="24aec-103">匿名型のインスタンスの宣言に応答してでは、コンパイラは、型の指定したプロパティを格納する新しいクラス定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="24aec-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="24aec-104">コンパイラによって生成されたコード</span><span class="sxs-lookup"><span data-stu-id="24aec-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="24aec-105">定義については、次の`product`、コンパイラがプロパティを格納する新しいクラス定義を作成`Name`、 `Price`、および`OnHand`です。</span><span class="sxs-lookup"><span data-stu-id="24aec-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="24aec-106">クラス定義には、次のようなプロパティ定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="24aec-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="24aec-107">あることに注意してくださいありません`Set`キーのプロパティのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="24aec-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="24aec-108">キー プロパティの値とは、読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="24aec-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="24aec-109">さらに、匿名型の定義には、既定のコンス トラクターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="24aec-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="24aec-110">パラメーターが必要なコンス トラクターが許可されていません。</span><span class="sxs-lookup"><span data-stu-id="24aec-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="24aec-111">型定義がから継承した 3 つのメンバーをオーバーライドして匿名型の宣言には、少なくとも 1 つのキー プロパティが含まれている場合、 <xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。</span><span class="sxs-lookup"><span data-stu-id="24aec-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="24aec-112">キー プロパティが宣言されていない場合、のみ<xref:System.Object.ToString%2A>はオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="24aec-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="24aec-113">上書きは、次の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="24aec-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="24aec-114">`Equals`返します`True`匿名型の 2 つのインスタンスが、同じインスタンスである場合、または、次の条件を満たしている場合。</span><span class="sxs-lookup"><span data-stu-id="24aec-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="24aec-115">同じ数のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="24aec-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="24aec-116">プロパティが同じ名前を持つ、同じ順序で宣言されているし、推論された型が同じです。</span><span class="sxs-lookup"><span data-stu-id="24aec-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="24aec-117">名前の比較は区別されません。</span><span class="sxs-lookup"><span data-stu-id="24aec-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="24aec-118">キー プロパティでは、少なくとも 1 つのプロパティと`Key`キーワードは、同じプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="24aec-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="24aec-119">キー プロパティの対応する各ペアの比較を返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="24aec-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="24aec-120">たとえば、次の例についてで`Equals`を返します`True`のみ`employee01`と`employee08`です。</span><span class="sxs-lookup"><span data-stu-id="24aec-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="24aec-121">各行は、なぜ新しいインスタンスと一致しません理由を指定する前に、コメント`employee01`です。</span><span class="sxs-lookup"><span data-stu-id="24aec-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="24aec-122">`GetHashcode`適切に一意の GetHashCode アルゴリズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="24aec-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="24aec-123">アルゴリズムでは、キー プロパティだけを使って、ハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="24aec-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="24aec-124">`ToString`次の例のように連結されたプロパティの値の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="24aec-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="24aec-125">キーとキー以外のプロパティの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="24aec-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="24aec-126">匿名型のプロパティを明示的に指定されたこれらの生成されたメソッドと競合することはできません。</span><span class="sxs-lookup"><span data-stu-id="24aec-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="24aec-127">つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`プロパティの名前を付ける。</span><span class="sxs-lookup"><span data-stu-id="24aec-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="24aec-128">匿名型の定義には、少なくとも 1 つを含むキー プロパティも実装して、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の型です。</span><span class="sxs-lookup"><span data-stu-id="24aec-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24aec-129">匿名型の宣言は、同じアセンブリで発生した、それらのプロパティは、同じ名前を持つと推論された型が同じで、プロパティが同じ順序で宣言されているおよび同じプロパティがキー プロパティとしてマークされている場合にのみ、同じ匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="24aec-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24aec-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="24aec-130">See Also</span></span>  
 [<span data-ttu-id="24aec-131">匿名型</span><span class="sxs-lookup"><span data-stu-id="24aec-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="24aec-132">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="24aec-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
