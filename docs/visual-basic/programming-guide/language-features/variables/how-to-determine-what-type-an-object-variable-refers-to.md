---
title: '方法: オブジェクト変数で参照している型を確認する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="050aa-102">方法: オブジェクト変数で参照している型を確認する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="050aa-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="050aa-103">オブジェクト変数には、他の場所に格納されているデータへのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="050aa-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="050aa-104">実行時にそのデータの種類を変更できます。</span><span class="sxs-lookup"><span data-stu-id="050aa-104">The type of that data can change during run time.</span></span> <span data-ttu-id="050aa-105">時点で使用することができます、<xref:System.Type.GetTypeCode%2A>を現在の実行時の型を特定のメソッドまたは[TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)かどうかを現在の検索を実行時の型が、指定した型と互換性がします。</span><span class="sxs-lookup"><span data-stu-id="050aa-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="050aa-106">現在のオブジェクト変数を入力を正確なを確認するのを参照します。</span><span class="sxs-lookup"><span data-stu-id="050aa-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="050aa-107">オブジェクト変数を呼び出して、<xref:System.Object.GetType%2A>を取得する方法、<xref:System.Type?displayProperty=nameWithType>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="050aa-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="050aa-108"><xref:System.Type?displayProperty=nameWithType>クラス、共有メソッドを呼び出す<xref:System.Type.GetTypeCode%2A>を取得する、<xref:System.TypeCode>オブジェクトの種類の列挙値。</span><span class="sxs-lookup"><span data-stu-id="050aa-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="050aa-109">テストすることができます、<xref:System.TypeCode>などは、目的のどちらかの列挙体メンバーに対して列挙値`Double`です。</span><span class="sxs-lookup"><span data-stu-id="050aa-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="050aa-110">変数の型がを指定した型と互換性がオブジェクトかどうかを判断するには</span><span class="sxs-lookup"><span data-stu-id="050aa-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="050aa-111">使用して、`TypeOf`演算子と組み合わせて、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)でオブジェクトをテストする、`TypeOf`しています.`Is`式。</span><span class="sxs-lookup"><span data-stu-id="050aa-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="050aa-112">`TypeOf`しています.`Is`式を返します`True`オブジェクトのランタイム型が指定した型に互換性があります。</span><span class="sxs-lookup"><span data-stu-id="050aa-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="050aa-113">互換性のための基準は、指定した型がクラス、構造体、またはインターフェイスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="050aa-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="050aa-114">一般に、型は互換性のあるオブジェクトと同じ型の継承、または指定された型を実装する場合。</span><span class="sxs-lookup"><span data-stu-id="050aa-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="050aa-115">詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="050aa-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="050aa-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="050aa-116">Compiling the Code</span></span>  
 <span data-ttu-id="050aa-117">指定した型であることを変数または式に注意してください。</span><span class="sxs-lookup"><span data-stu-id="050aa-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="050aa-118">クラス、構造体、インターフェイスなど、定義された型の名前があります。</span><span class="sxs-lookup"><span data-stu-id="050aa-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="050aa-119">などの組み込みの型が含まれます`Integer`と`String`です。</span><span class="sxs-lookup"><span data-stu-id="050aa-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050aa-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="050aa-120">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [<span data-ttu-id="050aa-121">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="050aa-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="050aa-122">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="050aa-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="050aa-123">Object 型</span><span class="sxs-lookup"><span data-stu-id="050aa-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
