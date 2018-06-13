---
title: カスタム コントロールへのメソッドの実装
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 9df2bc9257c3f697f30cbe8c679ffc88ec34517b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538114"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="38ca3-102">カスタム コントロールへのメソッドの実装</span><span class="sxs-lookup"><span data-stu-id="38ca3-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="38ca3-103">コントロールにメソッドを実装する方法は、他のコンポーネントにメソッドを実装する場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="38ca3-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="38ca3-104">Visual Basic では、値を返す必要のあるメソッドは `Public Function` として実装されます。</span><span class="sxs-lookup"><span data-stu-id="38ca3-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="38ca3-105">値が返されない場合は、`Public Sub` として実装されます。</span><span class="sxs-lookup"><span data-stu-id="38ca3-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="38ca3-106">メソッドは次の構文で宣言します。</span><span class="sxs-lookup"><span data-stu-id="38ca3-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="38ca3-107">関数は値を返すため、整数、文字列、オブジェクトなど、戻り値の型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38ca3-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="38ca3-108">`Function` プロシージャや `Sub` プロシージャが引数をとる場合は、引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38ca3-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="38ca3-109">Visual Basic とは異なり、C# では関数とプロシージャが区別されません。</span><span class="sxs-lookup"><span data-stu-id="38ca3-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="38ca3-110">メソッドは値を返すか、または `void` を返します。</span><span class="sxs-lookup"><span data-stu-id="38ca3-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="38ca3-111">C# のパブリック メソッドを宣言する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="38ca3-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="38ca3-112">メソッドを宣言する際、可能な限り、メソッドのすべての引数を明示的なデータ型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="38ca3-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="38ca3-113">オブジェクト参照を使用する引数は、特定のクラス型として宣言される必要があります (例: `As Widget` ではなく、`As Object`)。</span><span class="sxs-lookup"><span data-stu-id="38ca3-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="38ca3-114">Visual Basic では、既定の設定 `Option Strict` によって自動的にこの規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="38ca3-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="38ca3-115">型付き引数を使用することにより、開発者によるエラーの多くを、実行時ではなく、コンパイラによって検出できます。</span><span class="sxs-lookup"><span data-stu-id="38ca3-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="38ca3-116">コンパイラは常に多くのエラーを検出するのに対し、ランタイム テストは、テスト スイートと同程度の精度しかありません。</span><span class="sxs-lookup"><span data-stu-id="38ca3-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="38ca3-117">オーバーロードされたメソッド</span><span class="sxs-lookup"><span data-stu-id="38ca3-117">Overloaded Methods</span></span>  
 <span data-ttu-id="38ca3-118">コントロールのユーザーが、メソッドにさまざまなパラメーターの組み合わせを指定できるようにするには、明示的なデータ型を使用して、メソッドのオーバーロードを複数提供します。</span><span class="sxs-lookup"><span data-stu-id="38ca3-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="38ca3-119">テスト時にエラーが検出されない場合があるため、任意のデータ型を含めることのできる `As Object` として宣言するパラメーターは作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="38ca3-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38ca3-120">共通言語ランタイムの汎用データ型は、`Object` ではなく、`Variant` です。</span><span class="sxs-lookup"><span data-stu-id="38ca3-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="38ca3-121">`Variant` は、言語から削除されました。</span><span class="sxs-lookup"><span data-stu-id="38ca3-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="38ca3-122">たとえば、`Spin` という仮想のコントロールに `Widget` メソッドがあり、スピンの方向と速度を直接指定するか、角運動量を吸収する他の `Widget` オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="38ca3-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="38ca3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="38ca3-123">See Also</span></span>  
 [<span data-ttu-id="38ca3-124">イベント</span><span class="sxs-lookup"><span data-stu-id="38ca3-124">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="38ca3-125">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="38ca3-125">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
