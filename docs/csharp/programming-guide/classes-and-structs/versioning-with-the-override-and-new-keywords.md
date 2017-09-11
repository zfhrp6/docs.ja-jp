---
title: "Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 167262f7b2423fffec61b1e903f849d2ab387ed2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="77b04-102">Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="77b04-102">Versioning with the Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="77b04-103">C# 言語は、異なるライブラリ内の[基底](../../../csharp/language-reference/keywords/base.md)クラスと派生クラス間でのバージョン管理を進化させると同時に、下位互換性も維持されるよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="77b04-103">The C# language is designed so that versioning between [base](../../../csharp/language-reference/keywords/base.md) and derived classes in different libraries can evolve and maintain backward compatibility.</span></span> <span data-ttu-id="77b04-104">そのため、たとえば、派生クラスのメンバーと同じ名前を使用して基底[クラス](../../../csharp/language-reference/keywords/class.md)の新規メンバーが導入されても、C# では完全にサポートされ、予期しない動作は発生しません。</span><span class="sxs-lookup"><span data-stu-id="77b04-104">This means, for example, that the introduction of a new member in a base [class](../../../csharp/language-reference/keywords/class.md) with the same name as a member in a derived class is completely supported by C# and does not lead to unexpected behavior.</span></span> <span data-ttu-id="77b04-105">ただしこのことは、メソッドが派生メソッドをオーバーライドするためのものなのか、それとも同じ名前の派生メソッドを非表示にする新規メソッドなのかを、クラスで明示的に記述しなければならないということでもあります。</span><span class="sxs-lookup"><span data-stu-id="77b04-105">It also means that a class must explicitly state whether a method is intended to override an inherited method, or whether a method is a new method that hides a similarly named inherited method.</span></span>  
  
 <span data-ttu-id="77b04-106">C# では、派生クラスに基底クラスと同じ名前のメソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="77b04-106">In C#, derived classes can contain methods with the same name as base class methods.</span></span>  
  
-   <span data-ttu-id="77b04-107">基底クラスのメソッドは、[virtual](../../../csharp/language-reference/keywords/virtual.md) で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77b04-107">The base class method must be defined [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="77b04-108">派生クラスのメソッドの前に [new](../../../csharp/language-reference/keywords/new.md) または [override](../../../csharp/language-reference/keywords/override.md) キーワードがない場合、コンパイラは警告を発し、メソッドは `new` キーワードが存在する場合と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="77b04-108">If the method in the derived class is not preceded by [new](../../../csharp/language-reference/keywords/new.md) or [override](../../../csharp/language-reference/keywords/override.md) keywords, the compiler will issue a warning and the method will behave as if the `new` keyword were present.</span></span>  
  
-   <span data-ttu-id="77b04-109">派生クラスのメソッドの前に `new` キーワードがある場合、そのメソッドは基底クラスのメソッドに依存しないメソッドとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="77b04-109">If the method in the derived class is preceded with the `new` keyword, the method is defined as being independent of the method in the base class.</span></span>  
  
-   <span data-ttu-id="77b04-110">派生クラスのメソッドの前に `override` キーワードがある場合、派生クラスのオブジェクトは、基底クラスのメソッドの代わりにそのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="77b04-110">If the method in the derived class is preceded with the `override` keyword, objects of the derived class will call that method instead of the base class method.</span></span>  
  
-   <span data-ttu-id="77b04-111">基底クラスのメソッドは、`base` キーワードを使用して派生クラス内から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="77b04-111">The base class method can be called from within the derived class using the `base` keyword.</span></span>  
  
-   <span data-ttu-id="77b04-112">`override`、 `virtual`、および `new` キーワードは、プロパティ、インデクサー、およびイベントにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="77b04-112">The `override`, `virtual`, and `new` keywords can also be applied to properties, indexers, and events.</span></span>  
  
 <span data-ttu-id="77b04-113">既定では、C# のメソッドは仮想ではありません。</span><span class="sxs-lookup"><span data-stu-id="77b04-113">By default, C# methods are not virtual.</span></span> <span data-ttu-id="77b04-114">メソッドが仮想として宣言されている場合、そのメソッドを継承しているすべてのクラスは、独自のバージョンを実装できます。</span><span class="sxs-lookup"><span data-stu-id="77b04-114">If a method is declared as virtual, any class inheriting the method can implement its own version.</span></span> <span data-ttu-id="77b04-115">仮想メソッドを仮想にするには、基底クラスのメソッド宣言で `virtual` 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="77b04-115">To make a method virtual, the `virtual` modifier is used in the method declaration of the base class.</span></span> <span data-ttu-id="77b04-116">その後、派生クラスは `override` キーワードを使用して基底の仮想メソッドをオーバーライドするか、または `new` キーワードを使用して基底クラスの仮想メソッドを非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="77b04-116">The derived class can then override the base virtual method by using the `override` keyword or hide the virtual method in the base class by using the `new` keyword.</span></span> <span data-ttu-id="77b04-117">`override` と `new` のいずれのキーワードも指定されていない場合、コンパイラは警告を発し、派生クラスのメソッドは基底クラスのメソッドを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="77b04-117">If neither the `override` keyword nor the `new` keyword is specified, the compiler will issue a warning and the method in the derived class will hide the method in the base class.</span></span>  
  
 <span data-ttu-id="77b04-118">実演的な例として、会社 A が `GraphicsClass` というクラスを作成し、プログラムで使用する場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="77b04-118">To demonstrate this in practice, assume for a moment that Company A has created a class named `GraphicsClass`, which your program uses.</span></span> <span data-ttu-id="77b04-119">次のコードは `GraphicsClass` です。</span><span class="sxs-lookup"><span data-stu-id="77b04-119">The following is `GraphicsClass`:</span></span>  
  
 <span data-ttu-id="77b04-120">[!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-120">[!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]</span></span>  
  
 <span data-ttu-id="77b04-121">この会社では、このクラスを使用して独自のクラスを派生させ、新しいメソッドを追加しました。</span><span class="sxs-lookup"><span data-stu-id="77b04-121">Your company uses this class, and you use it to derive your own class, adding a new method:</span></span>  
  
 <span data-ttu-id="77b04-122">[!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-122">[!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]</span></span>  
  
 <span data-ttu-id="77b04-123">このアプリケーションは、会社 A が `GraphicsClass` の新しいバージョン (次のようなコード) をリリースするまでは、問題なく使用できていました。</span><span class="sxs-lookup"><span data-stu-id="77b04-123">Your application is used without problems, until Company A releases a new version of `GraphicsClass`, which resembles the following code:</span></span>  
  
 <span data-ttu-id="77b04-124">[!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-124">[!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]</span></span>  
  
 <span data-ttu-id="77b04-125">`GraphicsClass` の新バージョンに、`DrawRectangle` というメソッドが含まれていますが、</span><span class="sxs-lookup"><span data-stu-id="77b04-125">The new version of `GraphicsClass` now contains a method named `DrawRectangle`.</span></span> <span data-ttu-id="77b04-126">当初は何も起こりませんでした。</span><span class="sxs-lookup"><span data-stu-id="77b04-126">Initially, nothing occurs.</span></span> <span data-ttu-id="77b04-127">新バージョンでは、旧バージョンとのバイナリ互換性が維持されています。</span><span class="sxs-lookup"><span data-stu-id="77b04-127">The new version is still binary compatible with the old version.</span></span> <span data-ttu-id="77b04-128">配置したソフトウェアは、それらのコンピューター システムに新しいクラスがインストールされても、機能し続けます。</span><span class="sxs-lookup"><span data-stu-id="77b04-128">Any software that you have deployed will continue to work, even if the new class is installed on those computer systems.</span></span> <span data-ttu-id="77b04-129">`DrawRectangle` メソッドへの既存の呼び出しは、派生クラス内のバージョンを引き続き参照します。</span><span class="sxs-lookup"><span data-stu-id="77b04-129">Any existing calls to the method `DrawRectangle` will continue to reference your version, in your derived class.</span></span>  
  
 <span data-ttu-id="77b04-130">しかし、`GraphicsClass` の新バージョンを使用してアプリケーションを再コンパイルした途端、コンパイラから警告 (CS0108) が発せられます。</span><span class="sxs-lookup"><span data-stu-id="77b04-130">However, as soon as you recompile your application by using the new version of `GraphicsClass`, you will receive a warning from the compiler, CS0108.</span></span> <span data-ttu-id="77b04-131">この警告は、アプリケーション内での `DrawRectangle` メソッドの動作方法を検討する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="77b04-131">This warning informs you that you have to consider how you want your `DrawRectangle` method to behave in your application.</span></span>  
  
 <span data-ttu-id="77b04-132">このメソッドで新しい基底クラスをオーバーライドする場合は、`override` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="77b04-132">If you want your method to override the new base class method, use the `override` keyword:</span></span>  
  
 <span data-ttu-id="77b04-133">[!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-133">[!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]</span></span>  
  
 <span data-ttu-id="77b04-134">`override` キーワードを使用すると、`YourDerivedGraphicsClass` から派生したすべてのオブジェクトは、派生クラス バージョンの `DrawRectangle` を使用するようになります。</span><span class="sxs-lookup"><span data-stu-id="77b04-134">The `override` keyword makes sure that any objects derived from `YourDerivedGraphicsClass` will use the derived class version of `DrawRectangle`.</span></span> <span data-ttu-id="77b04-135">`YourDerivedGraphicsClass` から派生したオブジェクトは、base キーワードを使用することで基底クラス バージョンの `DrawRectangle` にもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="77b04-135">Objects derived from `YourDerivedGraphicsClass` can still access the base class version of `DrawRectangle` by using the base keyword:</span></span>  
  
 <span data-ttu-id="77b04-136">[!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-136">[!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]</span></span>  
  
 <span data-ttu-id="77b04-137">このメソッドで新しい基底クラス メソッドをオーバーライドしない場合には、次の考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="77b04-137">If you do not want your method to override the new base class method, the following considerations apply.</span></span> <span data-ttu-id="77b04-138">2 つのメソッド間の混乱を避けるために、メソッドの名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="77b04-138">To avoid confusion between the two methods, you can rename your method.</span></span> <span data-ttu-id="77b04-139">これは時間がかかるうえにエラーが起こりやすいため、場合によっては実用的でない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77b04-139">This can be time-consuming and error-prone, and just not practical in some cases.</span></span> <span data-ttu-id="77b04-140">ただし、プロジェクトが比較的小さい場合は、Visual Studio のリファクタリング オプションを使用して、メソッドの名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="77b04-140">However, if your project is relatively small, you can use Visual Studio's Refactoring options to rename the method.</span></span> <span data-ttu-id="77b04-141">詳しくは、「[クラスおよび型のリファクタリング (クラス デザイナー)](/visualstudio/ide/refactoring-classes-and-types-class-designer)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77b04-141">For more information, see [Refactoring Classes and Types (Class Designer)](/visualstudio/ide/refactoring-classes-and-types-class-designer).</span></span>  
  
 <span data-ttu-id="77b04-142">なお、派生クラスの定義内で `new` キーワードを使用することで、警告を回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="77b04-142">Alternatively, you can prevent the warning by using the keyword `new` in your derived class definition:</span></span>  
  
 <span data-ttu-id="77b04-143">[!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-143">[!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]</span></span>  
  
 <span data-ttu-id="77b04-144">`new` キーワードを使用すると、その定義によって基底クラス内の定義が非表示にされることがコンパイラに伝えられます。</span><span class="sxs-lookup"><span data-stu-id="77b04-144">Using the `new` keyword tells the compiler that your definition hides the definition that is contained in the base class.</span></span> <span data-ttu-id="77b04-145">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="77b04-145">This is the default behavior.</span></span>  
  
## <a name="override-and-method-selection"></a><span data-ttu-id="77b04-146">オーバーライドとメソッド選択</span><span class="sxs-lookup"><span data-stu-id="77b04-146">Override and Method Selection</span></span>  
 <span data-ttu-id="77b04-147">クラスでメソッドを指定したときに、その呼び出しと互換性のあるメソッドが 2 つ以上ある場合、C# コンパイラはどのメソッドを呼び出すのが最適かを選択します (たとえば、同じ名前のメソッドが 2 つあり、そのパラメーターと、渡されたパラメーターとの間に互換性がある場合)。</span><span class="sxs-lookup"><span data-stu-id="77b04-147">When a method is named on a class, the C# compiler selects the best method to call if more than one method is compatible with the call, such as when there are two methods with the same name, and parameters that are compatible with the parameter passed.</span></span> <span data-ttu-id="77b04-148">たとえば、次の各メソッドには互換性があります。</span><span class="sxs-lookup"><span data-stu-id="77b04-148">The following methods would be compatible:</span></span>  
  
 <span data-ttu-id="77b04-149">[!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-149">[!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]</span></span>  
  
 <span data-ttu-id="77b04-150">`Derived` のインスタンスで `DoWork` が呼び出されると、C# コンパイラはまず、`Derived` で最初に宣言された `DoWork` のバージョンと互換性がある呼び出しを実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="77b04-150">When `DoWork` is called on an instance of `Derived`, the C# compiler will first try to make the call compatible with the versions of `DoWork` declared originally on `Derived`.</span></span> <span data-ttu-id="77b04-151">オーバーライド メソッドは、クラスで宣言されたものとは見なされません。これらは、基底クラスで宣言されたメソッドの新しい実装です。</span><span class="sxs-lookup"><span data-stu-id="77b04-151">Override methods are not considered as declared on a class, they are new implementations of a method declared on a base class.</span></span> <span data-ttu-id="77b04-152">C# コンパイラは、メソッドの呼び出しを `Derived` にある元のメソッドと対応付けできない場合にのみ、その呼び出しを、同じ名前と互換パラメーターを持つオーバーライド メソッドに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="77b04-152">Only if the C# compiler cannot match the method call to an original method on `Derived` will it try to match the call to an overridden method with the same name and compatible parameters.</span></span> <span data-ttu-id="77b04-153">例:</span><span class="sxs-lookup"><span data-stu-id="77b04-153">For example:</span></span>  
  
 <span data-ttu-id="77b04-154">[!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-154">[!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]</span></span>  
  
 <span data-ttu-id="77b04-155">変数 `val` は double 型に暗黙的に変換できるので、C# コンパイラは `DoWork(int)` の代わりに `DoWork(double)` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="77b04-155">Because the variable `val` can be converted to a double implicitly, the C# compiler calls `DoWork(double)` instead of `DoWork(int)`.</span></span> <span data-ttu-id="77b04-156">この問題を回避する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="77b04-156">There are two ways to avoid this.</span></span> <span data-ttu-id="77b04-157">1 つ目は、仮想メソッドと同じ名前の新しいメソッドを宣言しないようにすることです。</span><span class="sxs-lookup"><span data-stu-id="77b04-157">First, avoid declaring new methods with the same name as virtual methods.</span></span> <span data-ttu-id="77b04-158">2 つ目は、`Derived` のインスタンスを `Base` にキャストすることで、C# コンパイラに基底クラス メソッドのリストを検索させ、仮想メソッドを呼び出すようにすることです。</span><span class="sxs-lookup"><span data-stu-id="77b04-158">Second, you can instruct the C# compiler to call the virtual method by making it search the base class method list by casting the instance of `Derived` to `Base`.</span></span> <span data-ttu-id="77b04-159">メソッドが仮想なので、`Derived` にある `DoWork(int)` の実装が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="77b04-159">Because the method is virtual, the implementation of `DoWork(int)` on `Derived` will be called.</span></span> <span data-ttu-id="77b04-160">例:</span><span class="sxs-lookup"><span data-stu-id="77b04-160">For example:</span></span>  
  
 <span data-ttu-id="77b04-161">[!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="77b04-161">[!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]</span></span>  
  
 <span data-ttu-id="77b04-162">`new` と `override` の例について詳しくは、「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="77b04-162">For more examples of `new` and `override`, see [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b04-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="77b04-163">See Also</span></span>  
 <span data-ttu-id="77b04-164">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="77b04-164">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="77b04-165">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="77b04-165">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="77b04-166">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="77b04-166">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 [<span data-ttu-id="77b04-167">継承</span><span class="sxs-lookup"><span data-stu-id="77b04-167">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

