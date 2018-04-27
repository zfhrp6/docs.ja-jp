---
title: 構造体とクラス (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf72fb0a7a34d45774cb9a58c037ebcb1c05288f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="79002-102">構造体とクラス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79002-102">Structures and Classes (Visual Basic)</span></span>
<span data-ttu-id="79002-103">Visual Basic では、構造体とクラスは、両方のエンティティに同じ機能のほとんどがサポートされる結果の構文を統一します。</span><span class="sxs-lookup"><span data-stu-id="79002-103">Visual Basic unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="79002-104">ただし、構造体とクラスの重要な違いもできます。</span><span class="sxs-lookup"><span data-stu-id="79002-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="79002-105">クラスが参照型になるというメリットがある、参照を渡すことが、そのすべてのデータと構造体変数を渡すより効率的です。</span><span class="sxs-lookup"><span data-stu-id="79002-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="79002-106">その一方で、構造体には、グローバル ヒープにメモリの割り当ては不要です。</span><span class="sxs-lookup"><span data-stu-id="79002-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="79002-107">構造体から継承することはできませんので構造体を拡張する必要がないオブジェクトに対してのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="79002-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="79002-108">構造体を使用すると、オブジェクトを作成する小さいインスタンス サイズの場合は、構造体とクラスのパフォーマンス特性を考慮します。</span><span class="sxs-lookup"><span data-stu-id="79002-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="79002-109">類似点</span><span class="sxs-lookup"><span data-stu-id="79002-109">Similarities</span></span>  
 <span data-ttu-id="79002-110">構造体とクラスは、次の点で似ています。</span><span class="sxs-lookup"><span data-stu-id="79002-110">Structures and classes are similar in the following respects:</span></span>  
  
-   <span data-ttu-id="79002-111">これらはいずれも*コンテナー*型、メンバーとして他の型が含まれていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="79002-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
-   <span data-ttu-id="79002-112">両方があるメンバーで、コンス トラクター、メソッド、プロパティ、フィールド、定数、列挙型、イベント、およびイベント ハンドラーに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="79002-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="79002-113">ただし、これらのメンバーの宣言とを混同しないでください*要素*構造体の。</span><span class="sxs-lookup"><span data-stu-id="79002-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
-   <span data-ttu-id="79002-114">両方のメンバーも、個別のアクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="79002-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="79002-115">たとえば、1 つのメンバーを宣言できます`Public`別および`Private`です。</span><span class="sxs-lookup"><span data-stu-id="79002-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
-   <span data-ttu-id="79002-116">インターフェイスを実装両方できます。</span><span class="sxs-lookup"><span data-stu-id="79002-116">Both can implement interfaces.</span></span>  
  
-   <span data-ttu-id="79002-117">両方が共有できますコンス トラクター、またはパラメーターなし。</span><span class="sxs-lookup"><span data-stu-id="79002-117">Both can have shared constructors, with or without parameters.</span></span>  
  
-   <span data-ttu-id="79002-118">両方を公開できます、*既定プロパティ*プロパティは、少なくとも 1 つのパラメーターを受け取りますが、します。</span><span class="sxs-lookup"><span data-stu-id="79002-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
-   <span data-ttu-id="79002-119">両方を宣言でき、イベントを発生させるし、デリゲートを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="79002-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="79002-120">相違点</span><span class="sxs-lookup"><span data-stu-id="79002-120">Differences</span></span>  
 <span data-ttu-id="79002-121">構造体とクラスは、次のとおりで異なります。</span><span class="sxs-lookup"><span data-stu-id="79002-121">Structures and classes differ in the following particulars:</span></span>  
  
-   <span data-ttu-id="79002-122">構造体は*値の型*; クラスは、*型参照*です。</span><span class="sxs-lookup"><span data-stu-id="79002-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="79002-123">クラス型としてのデータへの参照を含むのではなく、構造体の型の変数には、構造体のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79002-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
-   <span data-ttu-id="79002-124">使用して構造はスタック割り当てです。クラスは、ヒープの割り当てを使用します。</span><span class="sxs-lookup"><span data-stu-id="79002-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
-   <span data-ttu-id="79002-125">構造体のすべての要素は`Public`クラス変数の既定では、定数は、`Private`既定では、他のクラス メンバーは`Public`既定です。</span><span class="sxs-lookup"><span data-stu-id="79002-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="79002-126">クラスのメンバーには、この動作は、既定の Visual Basic 6.0 のシステムとの互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="79002-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
-   <span data-ttu-id="79002-127">構造体の有効期限がありますには、少なくとも 1 つの非共有変数または非共有、カスタム イベントの要素です。クラスは、完全に空にすることができます。</span><span class="sxs-lookup"><span data-stu-id="79002-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
-   <span data-ttu-id="79002-128">構造体の要素として宣言することはできません`Protected`; クラスのメンバーのことができます。</span><span class="sxs-lookup"><span data-stu-id="79002-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
-   <span data-ttu-id="79002-129">構造体のプロシージャはイベントを処理できる場合にのみ、[共有](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`プロシージャ、およびだけでは、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 任意のクラスのプロシージャは、いずれかのを使用して、イベントを処理できます[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)キーワードまたは`AddHandler`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="79002-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="79002-130">詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79002-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
-   <span data-ttu-id="79002-131">構造体の変数宣言には、初期化子または配列の初期サイズを指定できません。クラスの変数宣言できます。</span><span class="sxs-lookup"><span data-stu-id="79002-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
-   <span data-ttu-id="79002-132">構造体を暗黙的に継承、<xref:System.ValueType?displayProperty=nameWithType>クラスし、その他の型から継承できませんクラスが以外の任意のクラスまたはクラスから継承できます<xref:System.ValueType?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="79002-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=nameWithType> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="79002-133">構造体が継承可能な; できません。クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="79002-133">Structures are not inheritable; classes are.</span></span>  
  
-   <span data-ttu-id="79002-134">構造体は決して終了しているため、共通言語ランタイム (CLR) を呼び出すことはありません、<xref:System.Object.Finalize%2A>メソッドすべての構造をクラスが、ガベージ コレクター (GC) を呼び出すによって終了<xref:System.Object.Finalize%2A>アクティブな参照がないを検出した場合にクラス残りの。</span><span class="sxs-lookup"><span data-stu-id="79002-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
-   <span data-ttu-id="79002-135">構造体には、コンス トラクターは不要します。クラスでは。</span><span class="sxs-lookup"><span data-stu-id="79002-135">A structure does not require a constructor; a class does.</span></span>  
  
-   <span data-ttu-id="79002-136">構造体を持つことができますパラメーターを取る場合にのみ、非共有コンス トラクター。パラメーターの有無は、クラスでそれらを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="79002-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="79002-137">すべての構造体には、パラメーターなし暗黙的なパブリック コンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="79002-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="79002-138">このコンス トラクターでは、構造体のすべてのデータ要素が既定値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="79002-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="79002-139">この動作を再定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="79002-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="79002-140">インスタンスと変数</span><span class="sxs-lookup"><span data-stu-id="79002-140">Instances and Variables</span></span>  
 <span data-ttu-id="79002-141">構造体は値型であるために、各構造体変数は永続的に個別の構造体のインスタンスにバインドします。</span><span class="sxs-lookup"><span data-stu-id="79002-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="79002-142">クラスは参照型、オブジェクト変数は、異なる時刻でさまざまなクラスのインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="79002-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="79002-143">この違いでは、次の方法で構造体とクラスの使用に影響します。</span><span class="sxs-lookup"><span data-stu-id="79002-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
-   <span data-ttu-id="79002-144">**初期化します。**</span><span class="sxs-lookup"><span data-stu-id="79002-144">**Initialization.**</span></span> <span data-ttu-id="79002-145">構造体変数には、構造体のパラメーターなしのコンス トラクターを使用して要素の初期化で、暗黙的に含まれています。</span><span class="sxs-lookup"><span data-stu-id="79002-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="79002-146">したがって、`Dim s As struct1`は等価`Dim s As struct1 = New struct1()`です。</span><span class="sxs-lookup"><span data-stu-id="79002-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
-   <span data-ttu-id="79002-147">**変数を代入しています。**</span><span class="sxs-lookup"><span data-stu-id="79002-147">**Assigning Variables.**</span></span> <span data-ttu-id="79002-148">間、1 つの構造体変数を割り当てるか、プロシージャの引数に構造体のインスタンスを渡すときに、変数のすべての要素の現在の値は、新しい構造にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="79002-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="79002-149">間、1 つのオブジェクト変数を割り当てるか、プロシージャをオブジェクト変数を渡すときに参照ポインターだけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="79002-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
-   <span data-ttu-id="79002-150">**何を割り当てます。**</span><span class="sxs-lookup"><span data-stu-id="79002-150">**Assigning Nothing.**</span></span> <span data-ttu-id="79002-151">値を割り当てることができます[Nothing](../../../../visual-basic/language-reference/nothing.md)構造体を変数が、インスタンスは引き続き、変数に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="79002-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="79002-152">そのメソッドを呼び出すして変数の要素が、割り当てで再初期化されますが、そのデータ要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="79002-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="79002-153">オブジェクト変数を設定する場合とは異なり、 `Nothing`、すべてのクラスのインスタンスから関連付けを解除し、別のインスタンスを割り当てるまで、変数をメンバーにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="79002-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
-   <span data-ttu-id="79002-154">**複数のインスタンス。**</span><span class="sxs-lookup"><span data-stu-id="79002-154">**Multiple Instances.**</span></span> <span data-ttu-id="79002-155">オブジェクト変数が異なるタイミングでそれに割り当てられている別のクラスのインスタンスを持つことができ、いくつかのオブジェクト変数が、同時に、同じクラスのインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="79002-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="79002-156">クラス メンバーの値に加えた変更は、同じインスタンスを指す別の変数を使用してアクセスするときにそのメンバーに影響します。</span><span class="sxs-lookup"><span data-stu-id="79002-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="79002-157">ただし、構造体の要素は、独自のインスタンス内で分離されます。</span><span class="sxs-lookup"><span data-stu-id="79002-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="79002-158">他のインスタンスが同じであっても、別の構造体変数にその値への変更は反映されません`Structure`宣言します。</span><span class="sxs-lookup"><span data-stu-id="79002-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
-   <span data-ttu-id="79002-159">**等しいかどうか。**</span><span class="sxs-lookup"><span data-stu-id="79002-159">**Equality.**</span></span> <span data-ttu-id="79002-160">2 つの構造の等価テストは、要素でテストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79002-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="79002-161">使用して 2 つのオブジェクト変数を比較することができます、<xref:System.Object.Equals%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="79002-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="79002-162"><xref:System.Object.Equals%2A> 2 つの変数が同じインスタンスをポイントするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="79002-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79002-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="79002-163">See Also</span></span>  
 [<span data-ttu-id="79002-164">データの種類</span><span class="sxs-lookup"><span data-stu-id="79002-164">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="79002-165">複合データ型</span><span class="sxs-lookup"><span data-stu-id="79002-165">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="79002-166">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="79002-166">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="79002-167">構造体</span><span class="sxs-lookup"><span data-stu-id="79002-167">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="79002-168">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="79002-168">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="79002-169">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="79002-169">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="79002-170">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="79002-170">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
