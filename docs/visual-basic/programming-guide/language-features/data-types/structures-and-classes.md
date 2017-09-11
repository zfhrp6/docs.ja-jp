---
title: "構造体とクラス (Visual Basic) |Microsoft ドキュメント"
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
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
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
ms.openlocfilehash: c6874192a09db9ff5f247274247630d0bfa05ea3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="ceec9-102">構造体とクラス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceec9-102">Structures and Classes (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ceec9-103">構造体と結果の両方のエンティティに同じ機能のほとんどがサポートされると共に、クラスの構文を統一します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-103"> unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="ceec9-104">ただし、構造体とクラスの重要な違いもします。</span><span class="sxs-lookup"><span data-stu-id="ceec9-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="ceec9-105">クラスの参照型になるというメリットがある、参照を渡すことは、そのすべてのデータと構造体変数を渡すことよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="ceec9-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="ceec9-106">その一方で、構造体には、グローバル ヒープにメモリの割り当ては不要です。</span><span class="sxs-lookup"><span data-stu-id="ceec9-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="ceec9-107">構造体から継承することはできませんので構造体を拡張する必要のないオブジェクトに対してのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="ceec9-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="ceec9-108">作成するオブジェクト s インスタンスのサイズがあり、構造体とクラスのパフォーマンス特性を考慮に入れる場合は、構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="ceec9-109">類似点</span><span class="sxs-lookup"><span data-stu-id="ceec9-109">Similarities</span></span>  
 <span data-ttu-id="ceec9-110">構造体とクラスは、次の点で似ています。</span><span class="sxs-lookup"><span data-stu-id="ceec9-110">Structures and classes are similar in the following respects:</span></span>  
  
-   <span data-ttu-id="ceec9-111">どちらも*コンテナー*型、メンバーとして他の種類が含まれていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
-   <span data-ttu-id="ceec9-112">両方があるメンバーで、コンス トラクター、メソッド、プロパティ、フィールド、定数、列挙型、イベント、およびイベント ハンドラーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="ceec9-113">ただし、これらのメンバー宣言とを混同しないでください*要素*構造体の。</span><span class="sxs-lookup"><span data-stu-id="ceec9-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
-   <span data-ttu-id="ceec9-114">両方のメンバーも、個別のアクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="ceec9-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="ceec9-115">たとえば、1 つのメンバーを宣言できます`Public`別`Private`します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
-   <span data-ttu-id="ceec9-116">インターフェイスを両方実装できます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-116">Both can implement interfaces.</span></span>  
  
-   <span data-ttu-id="ceec9-117">両方が共有できますコンス トラクター、パラメーターの有無。</span><span class="sxs-lookup"><span data-stu-id="ceec9-117">Both can have shared constructors, with or without parameters.</span></span>  
  
-   <span data-ttu-id="ceec9-118">両方を公開できます、*既定プロパティ*、そのプロパティは、少なくとも&1; つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ceec9-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
-   <span data-ttu-id="ceec9-119">両方を宣言してイベントを発生させるし、デリゲートを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="ceec9-120">相違点</span><span class="sxs-lookup"><span data-stu-id="ceec9-120">Differences</span></span>  
 <span data-ttu-id="ceec9-121">構造体とクラスは、次のとおりで異なります。</span><span class="sxs-lookup"><span data-stu-id="ceec9-121">Structures and classes differ in the following particulars:</span></span>  
  
-   <span data-ttu-id="ceec9-122">構造体は*値の型*; クラスは、*参照型*します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="ceec9-123">データとしてクラス型への参照を含むのではなく、構造体型の変数には、構造体のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ceec9-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
-   <span data-ttu-id="ceec9-124">スタックの割り当てを使用して構造クラスは、ヒープ割り当てを使用します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
-   <span data-ttu-id="ceec9-125">すべての構造体要素`Public`既定ではクラスの変数と定数は`Private`既定では、他のクラス メンバーは`Public`既定では。</span><span class="sxs-lookup"><span data-stu-id="ceec9-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="ceec9-126">クラス メンバーの場合は、この動作は、既定の Visual Basic 6.0 システムとの互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
-   <span data-ttu-id="ceec9-127">構造体の有効期限が必要に少なくとも&1; つの非共有変数または非共有の非カスタム イベントの要素です。クラスは、完全に空にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
-   <span data-ttu-id="ceec9-128">構造体の要素として宣言できません`Protected`; クラス メンバーにします。</span><span class="sxs-lookup"><span data-stu-id="ceec9-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
-   <span data-ttu-id="ceec9-129">構造体のプロシージャがである場合にのみイベントを処理、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャとのことでのみ、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md);、クラスのプロシージャは、いずれかを使用して、イベントを処理できます、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)キーワードまたは`AddHandler`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ceec9-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="ceec9-130">詳細については、次を参照してください。[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ceec9-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
-   <span data-ttu-id="ceec9-131">構造体の変数宣言は、初期化子、または配列の初期サイズを指定できません。クラスの変数宣言ことができます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
-   <span data-ttu-id="ceec9-132">構造体を暗黙的に継承、<xref:System.ValueType?displayProperty=fullName>クラスし、その他の型から継承できないクラスは、任意のクラスまたは<xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName>以外のクラスから継承できます</xref:System.ValueType?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ceec9-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=fullName> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="ceec9-133">構造体は、継承可能な; がないです。クラスです。</span><span class="sxs-lookup"><span data-stu-id="ceec9-133">Structures are not inheritable; classes are.</span></span>  
  
-   <span data-ttu-id="ceec9-134">構造体が決して終了して、共通言語ランタイム (CLR) を呼び出すことはありませんので、<xref:System.Object.Finalize%2A>メソッドすべての構造をクラスは、ガベージ コレクター (GC) を呼び出すで終了<xref:System.Object.Finalize%2A>アクティブな参照が残っていないを検出した場合にクラスにします</xref:System.Object.Finalize%2A></xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="ceec9-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
-   <span data-ttu-id="ceec9-135">構造体には、コンス トラクターは不要します。クラスでは。</span><span class="sxs-lookup"><span data-stu-id="ceec9-135">A structure does not require a constructor; a class does.</span></span>  
  
-   <span data-ttu-id="ceec9-136">構造体のパラメーターになる場合にのみ、非共有コンス トラクターパラメーターの有無は、クラスでを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="ceec9-137">すべての構造体には、パラメーターを指定しない暗黙の型のパブリック コンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="ceec9-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="ceec9-138">このコンス トラクターでは、既定値に構造体のすべてのデータ要素を初期化します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="ceec9-139">この動作を再定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="ceec9-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="ceec9-140">インスタンスと変数</span><span class="sxs-lookup"><span data-stu-id="ceec9-140">Instances and Variables</span></span>  
 <span data-ttu-id="ceec9-141">構造体は値型であるために、各構造体変数は永続的に個別の構造体のインスタンスにバインドします。</span><span class="sxs-lookup"><span data-stu-id="ceec9-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="ceec9-142">クラスは参照型、オブジェクト変数が異なる時間にさまざまなクラスのインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="ceec9-143">このような区別では、次の方法で構造体とクラスの使用に影響します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
-   <span data-ttu-id="ceec9-144">**初期化します。**</span><span class="sxs-lookup"><span data-stu-id="ceec9-144">**Initialization.**</span></span> <span data-ttu-id="ceec9-145">構造体変数には、暗黙的に、構造体のパラメーターなしのコンス トラクターを使用して要素の初期化が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="ceec9-146">したがって、`Dim s As struct1`は`Dim s As struct1 = New struct1()`です。</span><span class="sxs-lookup"><span data-stu-id="ceec9-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
-   <span data-ttu-id="ceec9-147">**変数の割り当てください。**</span><span class="sxs-lookup"><span data-stu-id="ceec9-147">**Assigning Variables.**</span></span> <span data-ttu-id="ceec9-148">1 つの構造体変数を別に代入するか、またはプロシージャの引数に構造体のインスタンスを渡すと、変数のすべての要素の現在の値は、新しい構造にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="ceec9-149">1 つのオブジェクト変数を別に代入するか、またはオブジェクト変数をプロシージャに渡すと、参照ポインターだけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
-   <span data-ttu-id="ceec9-150">**Nothing を代入します。**</span><span class="sxs-lookup"><span data-stu-id="ceec9-150">**Assigning Nothing.**</span></span> <span data-ttu-id="ceec9-151">値を割り当てることができます[Nothing](../../../../visual-basic/language-reference/nothing.md)構造体へのインスタンスでは、変数はまだ復旧して、変数に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="ceec9-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="ceec9-152">代入によって可変要素が再初期化がそのデータ要素にアクセスしたりメソッドを呼び出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="ceec9-153">これに対して、オブジェクト変数を設定した場合に`Nothing`、任意のクラス インスタンスの関連付けを解除し、別のインスタンスを割り当てるまで、変数を使ってメンバーにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ceec9-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
-   <span data-ttu-id="ceec9-154">**複数のインスタンス。**</span><span class="sxs-lookup"><span data-stu-id="ceec9-154">**Multiple Instances.**</span></span> <span data-ttu-id="ceec9-155">オブジェクト変数が、異なる時期に割り当てられた別のクラス インスタンスを持つことができ、複数のオブジェクト変数が、同時に、同じクラスのインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="ceec9-156">クラスのメンバーの値に加えた変更は、同じインスタンスを指す別の変数を使用してアクセスするときにそのメンバーに影響します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="ceec9-157">ただし、構造体の要素は、独自のインスタンス内で分離されます。</span><span class="sxs-lookup"><span data-stu-id="ceec9-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="ceec9-158">他の同じインスタンスであっても、別の構造体変数にその値への変更は反映されません`Structure`宣言します。</span><span class="sxs-lookup"><span data-stu-id="ceec9-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
-   <span data-ttu-id="ceec9-159">**等しいかどうか。**</span><span class="sxs-lookup"><span data-stu-id="ceec9-159">**Equality.**</span></span> <span data-ttu-id="ceec9-160">2 つの構造の等価テストは、要素でテストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceec9-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="ceec9-161">使用して&2; つのオブジェクト変数を比較することができます、<xref:System.Object.Equals%2A>メソッド</xref:System.Object.Equals%2A>。</span><span class="sxs-lookup"><span data-stu-id="ceec9-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="ceec9-162"><xref:System.Object.Equals%2A>2 つの変数が同じインスタンスを参照するかどうかを示します。</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="ceec9-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceec9-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceec9-163">See Also</span></span>  
 <span data-ttu-id="ceec9-164">[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-164">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="ceec9-165"> [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-165"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="ceec9-166"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-166"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="ceec9-167"> [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-167"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="ceec9-168"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-168"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="ceec9-169"> [構造体およびその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="ceec9-169"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="ceec9-170"> [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="ceec9-170"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
