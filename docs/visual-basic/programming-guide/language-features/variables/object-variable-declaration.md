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
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="8a051-102">オブジェクト変数の宣言 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a051-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="8a051-103">オブジェクト変数を宣言するのにには、通常の宣言ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a051-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="8a051-104">どちらか、データ型を指定する`Object`(つまり、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)) または元のオブジェクトを作成する具体的なクラスです。</span><span class="sxs-lookup"><span data-stu-id="8a051-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="8a051-105">として変数を宣言する`Object`として宣言することと同じ<xref:System.Object?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="8a051-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8a051-106">特定のオブジェクト クラスを持つ変数を宣言する場合は、すべてのメソッドとそのクラスと継承クラスによって公開されるプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8a051-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="8a051-107">持つ変数を宣言する場合<xref:System.Object>のメンバーのみにアクセスできる、<xref:System.Object>クラスを有効にする場合を除き、`Option Strict Off`遅延バインドできるようにします。</span><span class="sxs-lookup"><span data-stu-id="8a051-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="8a051-108">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="8a051-108">Declaration Syntax</span></span>  
 <span data-ttu-id="8a051-109">オブジェクト変数を宣言するのにには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a051-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="8a051-110">指定することも[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、 `Protected Friend`、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)、または[静的](../../../../visual-basic/language-reference/modifiers/static.md)宣言します。</span><span class="sxs-lookup"><span data-stu-id="8a051-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="8a051-111">次の例の宣言は有効です。</span><span class="sxs-lookup"><span data-stu-id="8a051-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="8a051-112">遅延バインディングと、事前バインディング</span><span class="sxs-lookup"><span data-stu-id="8a051-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="8a051-113">場合がありますの特定のクラスが、コードが実行されるまで不明です。</span><span class="sxs-lookup"><span data-stu-id="8a051-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="8a051-114">この例でオブジェクト変数を宣言する必要があります、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="8a051-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="8a051-115">任意の型のオブジェクトへの参照を一般的なが作成され、実行時に特定のクラスが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8a051-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="8a051-116">これと呼ばれる*遅延バインディング*です。</span><span class="sxs-lookup"><span data-stu-id="8a051-116">This is called *late binding*.</span></span> <span data-ttu-id="8a051-117">遅延バインディングには、その他の実行時間が必要です。</span><span class="sxs-lookup"><span data-stu-id="8a051-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="8a051-118">メソッドとそれに割り当てる最も最近クラスのプロパティに、コードも制限されます。</span><span class="sxs-lookup"><span data-stu-id="8a051-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="8a051-119">これにより、コードが別のクラスのメンバーにアクセスを試みると実行時エラーが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="8a051-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="8a051-120">コンパイル時に特定のクラスをわかっている場合に、そのクラスを指定するオブジェクト変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a051-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="8a051-121">これは、*事前バインディング*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8a051-121">This is called *early binding*.</span></span> <span data-ttu-id="8a051-122">事前バインディングは、パフォーマンスが向上し、コードのすべてのメソッドと、特定のクラスのプロパティへのアクセスを保証します。</span><span class="sxs-lookup"><span data-stu-id="8a051-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="8a051-123">変数の場合は前の例宣言で`objA`クラスのオブジェクトのみを使用して<xref:System.Windows.Forms.Label?displayProperty=nameWithType>を指定する必要があります`As System.Windows.Forms.Label`その宣言でします。</span><span class="sxs-lookup"><span data-stu-id="8a051-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="8a051-124">事前バインディングの利点</span><span class="sxs-lookup"><span data-stu-id="8a051-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="8a051-125">特定のクラスとしてオブジェクト変数を宣言すると、いくつかの利点を示します。</span><span class="sxs-lookup"><span data-stu-id="8a051-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
-   <span data-ttu-id="8a051-126">自動的な型チェック</span><span class="sxs-lookup"><span data-stu-id="8a051-126">Automatic type checking</span></span>  
  
-   <span data-ttu-id="8a051-127">特定のクラスのすべてのメンバーに対するアクセスの保証</span><span class="sxs-lookup"><span data-stu-id="8a051-127">Guaranteed access to all members of the specific class</span></span>  
  
-   <span data-ttu-id="8a051-128">コード エディターで Microsoft IntelliSense サポート</span><span class="sxs-lookup"><span data-stu-id="8a051-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
-   <span data-ttu-id="8a051-129">コードの読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="8a051-129">Improved readability of your code</span></span>  
  
-   <span data-ttu-id="8a051-130">コードの少ないエラー</span><span class="sxs-lookup"><span data-stu-id="8a051-130">Fewer errors in your code</span></span>  
  
-   <span data-ttu-id="8a051-131">エラーが検出は、コンパイル時ではなく実行時</span><span class="sxs-lookup"><span data-stu-id="8a051-131">Errors caught at compile time rather than run time</span></span>  
  
-   <span data-ttu-id="8a051-132">コードの実行を高速化</span><span class="sxs-lookup"><span data-stu-id="8a051-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="8a051-133">オブジェクト変数のメンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8a051-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="8a051-134">ときに`Option Strict`なって`On`、オブジェクト変数が宣言するクラスのプロパティとメソッドのみにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8a051-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="8a051-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8a051-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="8a051-136">この例の場合、 `p` で使用できるのは <xref:System.Object> クラス自体のメンバーのみです。 `Left` プロパティは含まれません。</span><span class="sxs-lookup"><span data-stu-id="8a051-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="8a051-137">一方、 `q` は、 <xref:System.Windows.Forms.Label>型として宣言されているため、 <xref:System.Windows.Forms.Label> 名前空間の <xref:System.Windows.Forms> クラスのすべてのメソッドとプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a051-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="8a051-138">オブジェクト変数の柔軟性</span><span class="sxs-lookup"><span data-stu-id="8a051-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="8a051-139">継承階層内のオブジェクトを使用する場合がある、オブジェクト変数を宣言するのに使用するどのクラスです。</span><span class="sxs-lookup"><span data-stu-id="8a051-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="8a051-140">クラスを選択するときに、クラスのメンバーへのアクセスに対してオブジェクトの代入の柔軟性のバランスを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a051-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="8a051-141">たとえば、継承階層につながる、<xref:System.Windows.Forms.Form?displayProperty=nameWithType>クラス。</span><span class="sxs-lookup"><span data-stu-id="8a051-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="8a051-142">アプリケーションと呼ばれるフォーム クラスを定義すると仮定`specialForm`、クラスから継承される<xref:System.Windows.Forms.Form>です。</span><span class="sxs-lookup"><span data-stu-id="8a051-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8a051-143">具体的を参照するオブジェクト変数を宣言する`specialForm`次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="8a051-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="8a051-144">前の例で、宣言の制限、変数`nextForm`クラスのオブジェクトに`specialForm`、すべてのメソッドとプロパティのこともできますしかし、`specialForm`に利用可能な`nextForm`元となるすべてのクラスのすべてのメンバーと、。`specialForm`を継承します。</span><span class="sxs-lookup"><span data-stu-id="8a051-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="8a051-145">一般的なオブジェクト変数を設定するには、宣言する型にすることを<xref:System.Windows.Forms.Form>次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="8a051-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="8a051-146">前の例で、宣言には、任意のフォームをアプリケーションを割り当てることができます`anyForm`です。</span><span class="sxs-lookup"><span data-stu-id="8a051-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="8a051-147">ただしが`anyForm`クラスのすべてのメンバーにアクセスできる<xref:System.Windows.Forms.Form>、追加のメソッドやプロパティなどの特定のフォーム定義のいずれかを使用できません`specialForm`です。</span><span class="sxs-lookup"><span data-stu-id="8a051-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="8a051-148">基底クラスのすべてのメンバーが派生クラスで使用できますが、派生クラスで追加されたメンバーが、基底クラスにご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="8a051-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a051-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a051-149">See Also</span></span>  
 [<span data-ttu-id="8a051-150">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="8a051-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="8a051-151">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="8a051-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="8a051-152">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="8a051-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="8a051-153">方法: オブジェクト変数を宣言し、Visual Basic でオブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="8a051-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="8a051-154">方法: オブジェクトのメンバーにアクセスする</span><span class="sxs-lookup"><span data-stu-id="8a051-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [<span data-ttu-id="8a051-155">New 演算子</span><span class="sxs-lookup"><span data-stu-id="8a051-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="8a051-156">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="8a051-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="8a051-157">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="8a051-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
