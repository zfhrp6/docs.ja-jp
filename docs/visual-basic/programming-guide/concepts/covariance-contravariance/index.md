---
title: 共変性と反変性 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="de2d7-102">共変性と反変性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="de2d7-103">Visual Basic では、共変性と反変性により、配列型、デリゲート型、およびジェネリック型引数の暗黙の参照変換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="de2d7-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="de2d7-104">共変性は代入互換性を維持し、反変性はこれを反転させます。</span><span class="sxs-lookup"><span data-stu-id="de2d7-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="de2d7-105">次のコードでは、代入互換性、共変性、および反変性の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 <span data-ttu-id="de2d7-106">配列の共変性により、強い派生型の配列から弱い派生型の配列への暗黙の型変換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="de2d7-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="de2d7-107">ただし、次のコード例に示すように、この操作はタイプ セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="de2d7-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="de2d7-108">メソッド グループの共変性と反変性のサポートにより、メソッド シグネチャをデリゲート型と一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="de2d7-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="de2d7-109">これにより、一致するシグネチャを持つメソッドだけでなく、デリゲート型で指定された型よりも強い派生型 (共変性) を返すメソッドや、弱い派生型 (反変性) のパラメーターを受け取るメソッドを、デリゲートに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="de2d7-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="de2d7-110">詳細については、「[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」(デリゲートの分散 (Visual Basic)) および「[Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)」(デリゲートの分散の使用 (Visual Basic)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de2d7-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="de2d7-111">次のコード例は、メソッド グループでの共変性と反変性のサポートを示しています。</span><span class="sxs-lookup"><span data-stu-id="de2d7-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 <span data-ttu-id="de2d7-112">.NET Framework 4 以降では、Visual Basic でジェネリック インターフェイスと汎用デリゲートでの共変性と反変性がサポートされ、ジェネリック型パラメーターの暗黙の型変換が可能になっています。</span><span class="sxs-lookup"><span data-stu-id="de2d7-112">In .NET Framework 4 or later Visual Basic support covariance and contravariance in generic interfaces and delegates and allow for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="de2d7-113">詳細については、「[Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)」(ジェネリック インターフェイスの分散 (Visual Basic)) および「[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」(デリゲートの分散 (Visual Basic)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de2d7-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="de2d7-114">次のコード例は、ジェネリック インターフェイスの暗黙の参照変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="de2d7-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="de2d7-115">ジェネリック インターフェイスや汎用デリゲートは、そのジェネリック パラメーターが共変または反変として宣言されている場合、*バリアント*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="de2d7-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="de2d7-116">Visual Basic では、独自のバリアント インターフェイスおよびデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="de2d7-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="de2d7-117">詳細については、「[Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)」(バリアント ジェネリック インターフェイスの作成 (Visual Basic)) および「[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」(デリゲートの分散 (Visual Basic)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de2d7-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="de2d7-118">関連トピック</span><span class="sxs-lookup"><span data-stu-id="de2d7-118">Related Topics</span></span>  
  
|<span data-ttu-id="de2d7-119">タイトル</span><span class="sxs-lookup"><span data-stu-id="de2d7-119">Title</span></span>|<span data-ttu-id="de2d7-120">説明</span><span class="sxs-lookup"><span data-stu-id="de2d7-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="de2d7-121">ジェネリック インターフェイスの分散 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="de2d7-122">ジェネリック インターフェイスでの共変性と反変性について説明し、.NET Framework でのバリアント ジェネリック インターフェイスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="de2d7-123">バリアント ジェネリック インターフェイスの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="de2d7-124">カスタムのバリアント インターフェイスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="de2d7-125">ジェネリック コレクションに対するインターフェイスでの分散の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="de2d7-126"><xref:System.Collections.Generic.IEnumerable%601> および <xref:System.IComparable%601> インターフェイスでの共変性と反変性のサポートがコードの再利用にどのように役立つかを示します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="de2d7-127">デリゲートの分散 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="de2d7-128">汎用および非汎用デリゲートでの共変性と反変性について説明し、.NET Framework でのバリアント汎用デリゲートの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="de2d7-129">デリゲートの分散の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="de2d7-130">非汎用デリゲートでの共変性と反変性のサポートを使用して、メソッド シグネチャをデリゲート型に一致させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="de2d7-131">Func および Action 汎用デリゲートでの分散の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de2d7-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="de2d7-132">`Func` および `Action` デリゲートでの共変性と反変性のサポートがコードの再利用にどのように役立つかを示します。</span><span class="sxs-lookup"><span data-stu-id="de2d7-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
