---
title: "オーバーロードされたプロパティとメソッド (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="067a2-102">オーバーロードされたプロパティとメソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="067a2-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="067a2-103">オーバー ロードは、1 つ以上のプロシージャ、インスタンス コンス トラクター、またはで同じ名前が異なる引数の型クラスのプロパティの作成です。</span><span class="sxs-lookup"><span data-stu-id="067a2-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="067a2-104">使用率をオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="067a2-104">Overloading Usage</span></span>  
 <span data-ttu-id="067a2-105">オーバー ロードは、オブジェクト モデルで、別のデータ型を操作するプロシージャに同じ名前を使用しているときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="067a2-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="067a2-106">たとえば、いくつかの異なるデータ型を表示できるクラスがある`Display`次のような手順。</span><span class="sxs-lookup"><span data-stu-id="067a2-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 <span data-ttu-id="067a2-107">せず、オーバー ロードでもが同じで、次に示すよう各手順の種類の名前を作成する必要は。</span><span class="sxs-lookup"><span data-stu-id="067a2-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 <span data-ttu-id="067a2-108">オーバー ロードしやすくために使用できるデータ型の選択肢を提供するために、プロパティまたはメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="067a2-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="067a2-109">たとえば、オーバー ロードされた`Display`説明以前メソッドに次のコード行のいずれか。</span><span class="sxs-lookup"><span data-stu-id="067a2-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 <span data-ttu-id="067a2-110">実行時に、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]するパラメーターのデータ型に基づく適切なプロシージャの呼び出しを指定します。</span><span class="sxs-lookup"><span data-stu-id="067a2-110">At run time, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="067a2-111">オーバー ロードの規則</span><span class="sxs-lookup"><span data-stu-id="067a2-111">Overloading Rules</span></span>  
 <span data-ttu-id="067a2-112">クラスのオーバー ロードされたメンバーを作成するには、2 つ以上のプロパティまたは同じ名前のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="067a2-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="067a2-113">オーバー ロードされた派生メンバーを除く各オーバー ロードされたメンバーが異なるパラメーター リストを持つ必要があり、次の項目は、プロパティまたはプロシージャをオーバー ロードと区別する機能として使用できません。</span><span class="sxs-lookup"><span data-stu-id="067a2-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="067a2-114">修飾子をなど`ByVal`または`ByRef`メンバー、またはメンバーのパラメーターに適用されています。</span><span class="sxs-lookup"><span data-stu-id="067a2-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="067a2-115">パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="067a2-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="067a2-116">プロシージャの戻り値の型</span><span class="sxs-lookup"><span data-stu-id="067a2-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="067a2-117">`Overloads`キーワード省略可能な時に、オーバー ロードはメンバーを使用していずれかのオーバー ロードされた場合、`Overloads`このキーワードはキーワード、その他のすべてのオーバー ロードされたメンバーと同じ名前で指定も必要があります。</span><span class="sxs-lookup"><span data-stu-id="067a2-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="067a2-118">派生クラスで同じパラメーターおよびパラメーターの型と呼ばれるプロセスをしているメンバーを持つ継承されたメンバー オーバー ロードできます*名前とシグネチャによるシャドウ*です。</span><span class="sxs-lookup"><span data-stu-id="067a2-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="067a2-119">場合、`Overloads`シャドウ名前とシグネチャで、メンバーの派生クラスの実装が、基底クラスで実装ではなく使用され、そのメンバーの他のすべてのオーバー ロードできるようにするのインスタンスとキーワードを使用して、派生クラスです。</span><span class="sxs-lookup"><span data-stu-id="067a2-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="067a2-120">場合、`Overloads`同一パラメーターとパラメーターの型を持つメンバーを持つ継承されたメンバー オーバー ロード時にキーワードを省略すると、オーバー ロードが呼び出された*名前によるシャドウ*です。</span><span class="sxs-lookup"><span data-stu-id="067a2-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="067a2-121">継承されたメンバーの実装を置き換える名前によるシャドウと他のすべてのオーバー ロードを置き換わります、派生クラスのインスタンスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="067a2-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="067a2-122">`Overloads`と`Shadows`修飾子両方では使用できません、同じプロパティまたはメソッドです。</span><span class="sxs-lookup"><span data-stu-id="067a2-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="067a2-123">例</span><span class="sxs-lookup"><span data-stu-id="067a2-123">Example</span></span>  
 <span data-ttu-id="067a2-124">次の例は、いずれかを受け取るオーバー ロードされたメソッドを作成、`String`または`Decimal`形式の金額と sales 税を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="067a2-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="067a2-125">この例を使用して、オーバー ロードされたメソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="067a2-125">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="067a2-126">新しいプロジェクトを開き、という名前のクラスを追加`TaxClass`です。</span><span class="sxs-lookup"><span data-stu-id="067a2-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="067a2-127">`TaxClass` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="067a2-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  <span data-ttu-id="067a2-128">次の手順をフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="067a2-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  <span data-ttu-id="067a2-129">呼び出し、フォームにボタンを追加、`ShowTax`プロシージャから、`Button1_Click`ボタンのイベントです。</span><span class="sxs-lookup"><span data-stu-id="067a2-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="067a2-130">プロジェクトを実行し、オーバー ロードされたテストをフォーム上のボタンをクリックして`ShowTax`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="067a2-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="067a2-131">実行時に、コンパイラは、使用されているパラメーターに一致する適切なオーバー ロードされた関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="067a2-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="067a2-132">ボタンをクリックすると、オーバー ロードされたメソッドが呼び出された最初、`Price`パラメーターを文字列と、メッセージは、"価格は、文字列です。</span><span class="sxs-lookup"><span data-stu-id="067a2-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="067a2-133">税が $$5.12"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="067a2-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="067a2-134">`TaxAmount`使用が呼び出される、`Decimal`値を 2 番目の時間と、メッセージ、"価格は 10 進数です。</span><span class="sxs-lookup"><span data-stu-id="067a2-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="067a2-135">税が $$5.12"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="067a2-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067a2-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="067a2-136">See Also</span></span>  
 [<span data-ttu-id="067a2-137">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="067a2-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="067a2-138">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="067a2-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="067a2-139">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="067a2-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="067a2-140">継承の基本</span><span class="sxs-lookup"><span data-stu-id="067a2-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="067a2-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="067a2-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="067a2-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="067a2-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="067a2-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="067a2-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="067a2-144">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="067a2-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="067a2-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="067a2-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
