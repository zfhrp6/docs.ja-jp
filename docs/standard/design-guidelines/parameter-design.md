---
title: パラメーターのデザイン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e39b38fd72f9f3b9ce76aa6f7e96e44841daabb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578275"
---
# <a name="parameter-design"></a><span data-ttu-id="cb4d6-102">パラメーターのデザイン</span><span class="sxs-lookup"><span data-stu-id="cb4d6-102">Parameter Design</span></span>
<span data-ttu-id="cb4d6-103">このセクションでは、引数をチェックするためのガイドラインにセクションを含むパラメーターのデザインの大まかなガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="cb4d6-104">さらを参照してくださいで解説するガイドライン[パラメーターの名前付け](../../../docs/standard/design-guidelines/naming-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-104">In addition, you should refer to the guidelines described in [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).</span></span>  
  
 <span data-ttu-id="cb4d6-105">**✓ しないで**メンバーで必要な機能を提供する少なくとも派生パラメーター型を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-105">**✓ DO** use the least derived parameter type that provides the functionality required by the member.</span></span>  
  
 <span data-ttu-id="cb4d6-106">たとえば、コレクションを列挙し、各項目をコンソールに出力するメソッドをデザインするとします。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="cb4d6-107">このようなメソッドを実行する必要があります<xref:System.Collections.IEnumerable>、パラメーターとしてされません<xref:System.Collections.ArrayList>または<xref:System.Collections.IList>、例を示します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>  
  
 <span data-ttu-id="cb4d6-108">**X しないで**予約済みのパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-108">**X DO NOT** use reserved parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-109">さらに、メンバーへの入力は、将来のバージョンで必要な場合は、新しいオーバー ロードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>  
  
 <span data-ttu-id="cb4d6-110">**X しないで**ポインター、ポインターの配列または多次元配列をパラメーターとして受け取るメソッドがパブリックに公開します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-110">**X DO NOT** have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-111">ポインターと多次元配列は、比較的を適切に使用するが困難です。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="cb4d6-112">ほとんどの場合に、Api はパラメーターとしてのこれらの型を防ぐために再設計することができます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-113">**✓ しないで**すべて配置`out`で値をすべてのパラメーターと`ref`パラメーター (除外パラメーター配列) のパラメーターの順序のオーバー ロード間の不整合が発生する場合でも (を参照してください[メンバーオーバー ロード](../../../docs/standard/design-guidelines/member-overloading.md))。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-113">**✓ DO** place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](../../../docs/standard/design-guidelines/member-overloading.md)).</span></span>  
  
 <span data-ttu-id="cb4d6-114">`out`パラメーターは、余分な戻り値として見なすことができ、理解しやすいメソッドのシグネチャは、それらをまとめてグループ化します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>  
  
 <span data-ttu-id="cb4d6-115">**✓ しないで**メンバーをオーバーライドするときに名前のパラメーターまたはインターフェイス メンバーの実装で一貫しています。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-115">**✓ DO** be consistent in naming parameters when overriding members or implementing interface members.</span></span>  
  
 <span data-ttu-id="cb4d6-116">これよりメソッド間の関係を通信します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-116">This better communicates the relationship between the methods.</span></span>  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="cb4d6-117">列挙型とブール型のパラメーターの選択</span><span class="sxs-lookup"><span data-stu-id="cb4d6-117">Choosing Between Enum and Boolean Parameters</span></span>  
 <span data-ttu-id="cb4d6-118">**✓ しないで**メンバーが 2 つ以上のブール型パラメーターを持っている場合は、列挙型を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-118">**✓ DO** use enums if a member would otherwise have two or more Boolean parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-119">**X しないで**ブール値を使用してない場合は、絶対に 3 つ以上の値が必要な表示できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-119">**X DO NOT** use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>  
  
 <span data-ttu-id="cb4d6-120">列挙型は、値の将来の追加のためにスペースを割り当てる一方でので説明される列挙型に値を追加するすべての問題に注意する必要があります[Enum デザイン](../../../docs/standard/design-guidelines/enum.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](../../../docs/standard/design-guidelines/enum.md).</span></span>  
  
 <span data-ttu-id="cb4d6-121">**✓ を検討してください**は本当に 2 つの状態の値であり、のみを使用してブール型プロパティを初期化するコンス トラクターのパラメーターのブール値を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-121">**✓ CONSIDER** using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>  
  
### <a name="validating-arguments"></a><span data-ttu-id="cb4d6-122">引数の検証</span><span class="sxs-lookup"><span data-stu-id="cb4d6-122">Validating Arguments</span></span>  
 <span data-ttu-id="cb4d6-123">**✓ しないで**パブリック、プロテクト、または明示的に実装されたメンバーに渡される引数を検証します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-123">**✓ DO** validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="cb4d6-124">スロー <xref:System.ArgumentException?displayProperty=nameWithType>、または検証に失敗した場合、そのサブクラスのいずれか。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>  
  
 <span data-ttu-id="cb4d6-125">実際の検証とは限りませんが、パブリックまたはプロテクト メンバー自体で発生することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="cb4d6-126">プライベートまたは内部ルーチン内の下位レベルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="cb4d6-127">主要なポイントでは、エンドユーザーに公開されている領域全体が引数をチェックします。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>  
  
 <span data-ttu-id="cb4d6-128">**✓ しないで**スロー <xref:System.ArgumentNullException> null 引数が渡され、メンバーが null の引数をサポートしていない場合。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-128">**✓ DO** throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>  
  
 <span data-ttu-id="cb4d6-129">**✓ しないで**列挙型のパラメーターを検証します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-129">**✓ DO** validate enum parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-130">列挙型の引数は列挙型で定義されている範囲であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="cb4d6-131">CLR は、値が列挙型で定義されていない場合でも、任意の整数値を列挙の値にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>  
  
 <span data-ttu-id="cb4d6-132">**X しないで**使用<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>enum の範囲を確認します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-132">**X DO NOT** use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>  
  
 <span data-ttu-id="cb4d6-133">**✓ しないで**変更可能な引数がありますが変更されている検証後に注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-133">**✓ DO** be aware that mutable arguments might have changed after they were validated.</span></span>  
  
 <span data-ttu-id="cb4d6-134">メンバーが高度なセキュリティの場合は、コピーを作成および検証し、引数を処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>  
  
### <a name="parameter-passing"></a><span data-ttu-id="cb4d6-135">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="cb4d6-135">Parameter Passing</span></span>  
 <span data-ttu-id="cb4d6-136">Framework デザイナーの観点からは、パラメーターの 3 つの主要なグループ: 値渡しのパラメーター、`ref`パラメーター、および`out`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-137">引数が値渡しでパラメーターを通じて渡されると、メンバーは、実際に渡された引数のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="cb4d6-138">引数が値型の場合、引数のコピーは、スタックに配置します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="cb4d6-139">引数の参照型では、参照のコピーは、スタックに配置されます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="cb4d6-140">パラメーターの値渡しを c#、VB.NET、および C++ での既定値などの最も一般的な CLR 言語。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>  
  
 <span data-ttu-id="cb4d6-141">を介して、引数が渡されたときに、`ref`パラメーター、メンバーがで渡される実際の引数への参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="cb4d6-142">引数が値型の場合は、引数への参照は、スタックに配置します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="cb4d6-143">引数の参照型では、参照への参照はスタックに配置されます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="cb4d6-144">`Ref` パラメーターは、呼び出し元によって渡された引数の変更をメンバーに許可を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>  
  
 <span data-ttu-id="cb4d6-145">`Out` パラメーターはのような`ref`小さな違いがいくつかのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="cb4d6-146">割り当てられていないため、読み取れませんメンバー本体でいくつかの値が割り当ては、前に、パラメーターが最初と見なされます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="cb4d6-147">また、パラメーターは、メンバーを返す前に、いくつかの値を割り当てられるにします。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-147">Also, the parameter has to be assigned some value before the member returns.</span></span>  
  
 <span data-ttu-id="cb4d6-148">**避け x**を使用して`out`または`ref`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-148">**X AVOID** using `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-149">使用して`out`または`ref`パラメーターには、ポインター、値型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理の使用経験が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="cb4d6-150">また、違い`out`と`ref`パラメーターはあまり理解されていません。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="cb4d6-151">一般向けの設計 framework 設計者が扱い方を習得するユーザーを待たない`out`または`ref`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="cb4d6-152">**X しないで**参照型を参照渡しされます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-152">**X DO NOT** pass reference types by reference.</span></span>  
  
 <span data-ttu-id="cb4d6-153">参照を交換に使用できるメソッドなど、ルールをいくつかの例外があります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>  
  
### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="cb4d6-154">可変個のパラメーターを持つメンバー</span><span class="sxs-lookup"><span data-stu-id="cb4d6-154">Members with Variable Number of Parameters</span></span>  
 <span data-ttu-id="cb4d6-155">メンバーを可変個の引数を受け取ることができますが、配列パラメーターを提供することによって表されます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="cb4d6-156">たとえば、<xref:System.String>次のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-156">For example, <xref:System.String> provides the following method:</span></span>  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 <span data-ttu-id="cb4d6-157">ユーザーが呼び出すことができますし、<xref:System.String.Format%2A?displayProperty=nameWithType>メソッドは、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 <span data-ttu-id="cb4d6-158">配列パラメーターに、c# params キーワードを追加すると、いわゆる params 配列パラメーターにパラメーターを変更し、一時的な配列の作成へのショートカットを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 <span data-ttu-id="cb4d6-159">メソッドを呼び出して、引数リスト内で直接、配列の要素を渡すことによって、ユーザーは、これを行います。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 <span data-ttu-id="cb4d6-160">パラメーター リストの最後のパラメーターにのみ、params キーワードを追加できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="cb4d6-161">**✓ を検討してください**要素の数が少ない配列を渡すエンドユーザーが予想される場合、配列パラメーターに、params キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-161">**✓ CONSIDER** adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="cb4d6-162">多数の要素が渡されることに共通のシナリオと予測される場合は、ユーザーが、これらの要素のインラインを渡す可能性がありますし、ので、params キーワードは必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-162">If it’s expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>  
  
 <span data-ttu-id="cb4d6-163">**避け x**があれば、呼び出し元はほとんどの場合、入力既に配列内に params 配列を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-163">**X AVOID** using params arrays if the caller would almost always have the input already in an array.</span></span>  
  
 <span data-ttu-id="cb4d6-164">たとえば、バイト配列パラメーターを持つメンバーがほとんどありません呼び出されます個々 のバイトを渡すことによってです。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="cb4d6-165">このため、.NET Framework でのバイト配列パラメーターは、params キーワードを使わないでください。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>  
  
 <span data-ttu-id="cb4d6-166">**X しないで**params 配列パラメーターを受け取るメンバーによって、配列が変更された場合、params 配列を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-166">**X DO NOT** use params arrays if the array is modified by the member taking the params array parameter.</span></span>  
  
 <span data-ttu-id="cb4d6-167">多数のコンパイラが、呼び出しサイトで一時配列に、メンバーの引数を有効にするため、配列を一時オブジェクトにすることがあります、したがって配列へのすべての変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>  
  
 <span data-ttu-id="cb4d6-168">**✓ を検討してください**単純なオーバー ロードで、params キーワードを使用する場合でもより複雑なオーバー ロードでは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-168">**✓ CONSIDER** using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>  
  
 <span data-ttu-id="cb4d6-169">すべてのオーバー ロードである場合でも、1 つのオーバー ロードで params 配列を持つユーザーが値のかどうかはどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-169">Ask yourself if users would value having the params array in one overload even if it wasn’t in all overloads.</span></span>  
  
 <span data-ttu-id="cb4d6-170">**✓ しないで**パラメーターを params キーワードを使用できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-170">**✓ DO** try to order parameters to make it possible to use the params keyword.</span></span>  
  
 <span data-ttu-id="cb4d6-171">**✓ を検討してください**非常にパフォーマンスが重視される Api の引数の数が少ない呼び出しに対して特別なオーバー ロードとコード パスを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-171">**✓ CONSIDER** providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="cb4d6-172">これにより、引数の数が少ない、API が呼び出されたときに、配列オブジェクトを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="cb4d6-173">配列パラメーターの単数形を取得、数値のサフィックスを追加することによって、パラメーターの名前を形成します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>  
  
 <span data-ttu-id="cb4d6-174">コード パス全体を特別なケースに配列を作成するだけでなくより一般的なメソッドを呼び出す場合、これを行うのみ必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>  
  
 <span data-ttu-id="cb4d6-175">**✓ しないで**params 配列引数として null を渡すことがあります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-175">**✓ DO** be aware that null could be passed as a params array argument.</span></span>  
  
 <span data-ttu-id="cb4d6-176">配列が処理する前に null でないことを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-176">You should validate that the array is not null before processing.</span></span>  
  
 <span data-ttu-id="cb4d6-177">**X しないで**を使用して、`varargs`メソッド、それ以外の場合、省略記号と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-177">**X DO NOT** use the `varargs` methods, otherwise known as the ellipsis.</span></span>  
  
 <span data-ttu-id="cb4d6-178">C などのいくつかの CLR 言語変数パラメーター リストと呼ばれるを渡すための別の規則のサポート`varargs`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="cb4d6-179">規則は CLS 準拠ではないため、フレームワークで使用できません。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>  
  
### <a name="pointer-parameters"></a><span data-ttu-id="cb4d6-180">ポインター パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb4d6-180">Pointer Parameters</span></span>  
 <span data-ttu-id="cb4d6-181">一般に、ポインター、適切に設計されたマネージ コード フレームワークのパブリック サーフェス領域に表示されません。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="cb4d6-182">ほとんどの場合、ポインターをカプセル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="cb4d6-183">ただし、場合によってはポインターは、相互運用性の理由から、必要な適切なポインターを使用して、このような場合は。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>  
  
 <span data-ttu-id="cb4d6-184">**✓ しないで**ポインターが CLS 準拠ではないために、ポインター引数を受け取り、メンバーの代替を提供します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-184">**✓ DO** provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>  
  
 <span data-ttu-id="cb4d6-185">**避け x**高い引数のポインター引数のチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-185">**X AVOID** doing expensive argument checking of pointer arguments.</span></span>  
  
 <span data-ttu-id="cb4d6-186">**✓ しないで**共通ポインターに関連する規則を伴うメンバーをデザインするときに従う必要です。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-186">**✓ DO** follow common pointer-related conventions when designing members with pointers.</span></span>  
  
 <span data-ttu-id="cb4d6-187">たとえば、必要はありません開始インデックスを渡すに同じ結果を得るには単純なポインターの算術演算を使用できるためです。</span><span class="sxs-lookup"><span data-stu-id="cb4d6-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>  
  
 <span data-ttu-id="cb4d6-188">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="cb4d6-188">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="cb4d6-189">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="cb4d6-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4d6-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb4d6-190">See Also</span></span>  
 [<span data-ttu-id="cb4d6-191">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="cb4d6-191">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="cb4d6-192">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="cb4d6-192">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
