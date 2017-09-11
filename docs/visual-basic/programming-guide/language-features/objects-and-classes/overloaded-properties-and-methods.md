---
title: "オーバー ロードされたプロパティとメソッド (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0b0040f78fd8e091027e32efae3a0f26c2a08622
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="100fc-102">オーバーロードされたプロパティとメソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="100fc-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="100fc-103">オーバー ロードは、1 つ以上のプロシージャ、インスタンス コンス トラクターで異なる引数の型が同じ名前のクラスのプロパティの作成です。</span><span class="sxs-lookup"><span data-stu-id="100fc-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="100fc-104">使用率をオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="100fc-104">Overloading Usage</span></span>  
 <span data-ttu-id="100fc-105">オーバー ロードは、オブジェクト モデルで、別のデータ型を操作するプロシージャに同じ名前を使用しているときに便利です。</span><span class="sxs-lookup"><span data-stu-id="100fc-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="100fc-106">たとえば、複数のデータ型を表示できるクラスがある`Display`次のようにプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="100fc-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 <span data-ttu-id="100fc-107">[!code-vb[VbVbalrOOP #&64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="100fc-107">[!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="100fc-108">せず、オーバー ロードどおり、次に示すように、同じ場合でも各プロシージャの種類の名前を作成する必要は。</span><span class="sxs-lookup"><span data-stu-id="100fc-108">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 <span data-ttu-id="100fc-109">[!code-vb[VbVbalrOOP #&65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="100fc-109">[!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="100fc-110">オーバー ロードすると、使用できるデータ型の選択肢を提供するために、プロパティまたはメソッドを使用しやすきます。</span><span class="sxs-lookup"><span data-stu-id="100fc-110">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="100fc-111">たとえば、オーバー ロードされた`Display`説明以前メソッドで次のコード行のいずれか。</span><span class="sxs-lookup"><span data-stu-id="100fc-111">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 <span data-ttu-id="100fc-112">[!code-vb[VbVbalrOOP #&66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="100fc-112">[!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="100fc-113">実行時に[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]するパラメーターのデータ型に基づき適切なプロシージャの呼び出しを指定します。</span><span class="sxs-lookup"><span data-stu-id="100fc-113">At run time, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="100fc-114">オーバー ロードの規則</span><span class="sxs-lookup"><span data-stu-id="100fc-114">Overloading Rules</span></span>  
 <span data-ttu-id="100fc-115">クラスのオーバー ロードされたメンバーを作成するには、2 つ以上のプロパティまたは同じ名前を持つメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="100fc-115">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="100fc-116">オーバー ロードの派生メンバーを除く各オーバー ロードされたメンバーは、異なるパラメーター リストを持つ必要があり、次の項目は、プロパティまたはプロシージャをオーバー ロードとの差別化機能として使用できません。</span><span class="sxs-lookup"><span data-stu-id="100fc-116">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="100fc-117">修飾子など`ByVal`または`ByRef`メンバー、またはメンバーのパラメーターに適用されています。</span><span class="sxs-lookup"><span data-stu-id="100fc-117">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="100fc-118">パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="100fc-118">Names of parameters</span></span>  
  
-   <span data-ttu-id="100fc-119">プロシージャの戻り値の型</span><span class="sxs-lookup"><span data-stu-id="100fc-119">Return types of procedures</span></span>  
  
 <span data-ttu-id="100fc-120">`Overloads` 、オーバー ロードとは、キーワードは任意ですが、メンバーを使用していずれかのオーバー ロードされた場合、`Overloads`このキーワードはキーワード、その他のすべてのオーバー ロードされたメンバーと同じ名前で指定もする必要があります。</span><span class="sxs-lookup"><span data-stu-id="100fc-120">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="100fc-121">派生クラスで継承されたメンバーを同一パラメーターとパラメーターの型と呼ばれるプロセスを持つメンバーとオーバー ロードできます*名前とシグネチャによるシャドウ*します。</span><span class="sxs-lookup"><span data-stu-id="100fc-121">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="100fc-122">場合、`Overloads`名前とシグネチャによるシャドウ、メンバーの派生クラスの実装される基本クラスの実装ではなくとそのメンバーの他のすべてのオーバー ロードは、派生クラスのインスタンスに表示される場合に、キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="100fc-122">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="100fc-123">場合、`Overloads`キーワードを省略して、継承されたメンバーと同じパラメーターとパラメーターの型を持つメンバーを持つオーバー ロードし、オーバー ロードが呼び出されます*名前によるシャドウ*します。</span><span class="sxs-lookup"><span data-stu-id="100fc-123">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="100fc-124">継承されたメンバーの実装を置き換える名前によるシャドウおよびその他のすべてのオーバー ロードを置き換わります、派生クラスのインスタンスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="100fc-124">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="100fc-125">`Overloads`と`Shadows`修飾子両方では使用できません同じプロパティまたはメソッドです。</span><span class="sxs-lookup"><span data-stu-id="100fc-125">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="100fc-126">例</span><span class="sxs-lookup"><span data-stu-id="100fc-126">Example</span></span>  
 <span data-ttu-id="100fc-127">次の例では、いずれかを受け取るオーバー ロードされたメソッド、`String`または`Decimal`形式の金額と売上税が含まれている文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="100fc-127">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="100fc-128">この例を使用して、オーバー ロードされたメソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="100fc-128">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="100fc-129">新しいプロジェクトを開き、という名前のクラスを追加`TaxClass`します。</span><span class="sxs-lookup"><span data-stu-id="100fc-129">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="100fc-130">`TaxClass` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="100fc-130">Add the following code to the `TaxClass` class.</span></span>  
  
     <span data-ttu-id="100fc-131">[!code-vb[VbVbalrOOP #&67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="100fc-131">[!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span></span>  
  
3.  <span data-ttu-id="100fc-132">フォームに次の手順を追加します。</span><span class="sxs-lookup"><span data-stu-id="100fc-132">Add the following procedure to your form.</span></span>  
  
     <span data-ttu-id="100fc-133">[!code-vb[VbVbalrOOP #&68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="100fc-133">[!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span></span>  
  
4.  <span data-ttu-id="100fc-134">呼び出し、フォームにボタンを追加、`ShowTax`プロシージャから、`Button1_Click`ボタンのイベントです。</span><span class="sxs-lookup"><span data-stu-id="100fc-134">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="100fc-135">プロジェクトを実行し、オーバー ロードされたをテストするフォーム上のボタンをクリックして`ShowTax`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="100fc-135">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="100fc-136">実行時に、コンパイラは、使用されているパラメーターに一致する適切なオーバー ロードされた関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="100fc-136">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="100fc-137">ボタンをクリックすると、オーバー ロードされたメソッドが呼び出された最初、`Price`パラメーターを文字列と、メッセージは、"価格は、文字列です。</span><span class="sxs-lookup"><span data-stu-id="100fc-137">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="100fc-138">税金が $$5.12"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="100fc-138">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="100fc-139">`TaxAmount`呼び出された、`Decimal`値&2; 回目と、メッセージ、"価格は&10; 進数です。</span><span class="sxs-lookup"><span data-stu-id="100fc-139">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="100fc-140">税金が $$5.12"が表示されます。</span><span class="sxs-lookup"><span data-stu-id="100fc-140">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100fc-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="100fc-141">See Also</span></span>  
 <span data-ttu-id="100fc-142">[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-142">[Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="100fc-143"> [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-143"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="100fc-144"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-144"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="100fc-145"> [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-145"> [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="100fc-146"> [シャドウ](../../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-146"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="100fc-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span></span>  
<span data-ttu-id="100fc-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span></span>  
<span data-ttu-id="100fc-149"> [オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="100fc-149"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="100fc-150"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)</span><span class="sxs-lookup"><span data-stu-id="100fc-150"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)</span></span>
