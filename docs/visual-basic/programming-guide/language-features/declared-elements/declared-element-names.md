---
title: 宣言された要素の名前 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad883dd8e1de419c74b5bcdb8762994e762b4cf7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="ec2d0-102">宣言された要素の名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec2d0-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="ec2d0-103">すべての宣言された要素とも呼ばれる、名前が付いて、*識別子*、これは、コードを使用して、それを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ec2d0-104">ルール</span><span class="sxs-lookup"><span data-stu-id="ec2d0-104">Rules</span></span>  
 <span data-ttu-id="ec2d0-105">Visual Basic では、要素名は、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="ec2d0-106">文字は英字またはアンダー スコアで始める必要があります (`_`)。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="ec2d0-107">英字、十進数、およびアンダー スコアのみでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="ec2d0-108">アンダー スコアで始まる場合、少なくとも 1 つの文字が英字または 10 進数字でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="ec2d0-109">長さが 1023 文字はできません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="ec2d0-110">1023 文字の長さの制限にも適用されます、完全修飾名の文字列全体など`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`です。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="ec2d0-111">次の例では、有効な要素名を示します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="ec2d0-112">次の例では、無効な要素名を示します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="ec2d0-113">最初にアンダー スコアのみが含まれています、2 つ目が 10 進数の数字で始まるおよび 3 番目に無効な文字 ($) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="ec2d0-114">アンダー スコアで始まる要素名 (`_`) に含まれていませんが、[言語非依存および言語非依存コンポーネント](../../../../standard/language-independence-and-language-independent-components.md)(CLS) ため、CLS 準拠コードのような名前を定義するコンポーネントを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="ec2d0-115">ただし、要素名は、他の場所内でアンダー スコアは CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="ec2d0-116">名前の長さのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ec2d0-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="ec2d0-117">実際には、自分の名前する必要がありますをできるだけ短く中の要素の特性を明確にします。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="ec2d0-118">これにより、コードの読みやすさを向上させ、行の長さとソース ファイルのサイズを削減できます。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="ec2d0-119">その一方で、自分の名前を記述しません。 適切にどのような要素を表し、コードがそれを使用する方法長さである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="ec2d0-120">これは、コードの読みやすくするため重要です。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-120">This is important for the readability of your code.</span></span> <span data-ttu-id="ec2d0-121">理解しようとしている他の人が自分で見ることが、作成した後に長時間場合や、適切な要素名は、かなりの時間を保存できます。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="ec2d0-122">エスケープされた名前</span><span class="sxs-lookup"><span data-stu-id="ec2d0-122">Escaped Names</span></span>  
 <span data-ttu-id="ec2d0-123">一般に、要素名は、する必要がありますと一致しませんなどの Visual Basic で予約されているキーワードのいずれかの`Case`または`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="ec2d0-124">ただし、定義することができます、*エスケープ名前*、角かっこで囲まれている (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="ec2d0-125">エスケープされた名前は、角かっこは、任意のあいまいさをなくすために、Visual Basic のキーワードに一致することができます。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="ec2d0-126">また、後続のコードで、名前を参照するときに、角かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="ec2d0-127">一般に、エスケープされた名前を使用する必要がありますされる場合にのみ。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="ec2d0-128">コードは、名前として使用されているキーワードが確保されていない Visual Basic の以前のバージョンから移行しました。または</span><span class="sxs-lookup"><span data-stu-id="ec2d0-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="ec2d0-129">指定されたキーワードが予約されていない別の言語で記述されたコードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="ec2d0-130">それ以外の場合、キーワードを使用してその名前が競合する場合、要素名の変更を検討してください。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="ec2d0-131">統合開発環境 (IDE) では、これを行う簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="ec2d0-132">詳細については、次を参照してください。[リファクタリング](/visualstudio/vb-ide/refactoring-vb)です。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="ec2d0-133">名前で大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="ec2d0-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="ec2d0-134">Visual Basic での要素名は区別されません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="ec2d0-135">これは、コンパイラは、大文字と小文字のみが異なる 2 つの名前を比較し、ときを解釈するには同じ名前としてことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="ec2d0-136">たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="ec2d0-137">ただし、共通言語ランタイム (CLR) は、大文字小文字を区別バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="ec2d0-138">このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="ec2d0-139">たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="ec2d0-140">かどうか、その後、クラスを再コンパイルし、変更する要素の名前を`abc`クラスを使用して、他のアセンブリではその要素がアクセスできなく可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="ec2d0-141">したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="ec2d0-142">名前とロケール</span><span class="sxs-lookup"><span data-stu-id="ec2d0-142">Names and Locales</span></span>  
 <span data-ttu-id="ec2d0-143">名前の比較は、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="ec2d0-144">1 つのロケールで 2 つの名前が同じ場合は、すべてのロケールに一致するように保証されます。</span><span class="sxs-lookup"><span data-stu-id="ec2d0-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2d0-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec2d0-145">See Also</span></span>  
 [<span data-ttu-id="ec2d0-146">宣言された要素</span><span class="sxs-lookup"><span data-stu-id="ec2d0-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="ec2d0-147">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="ec2d0-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="ec2d0-148">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="ec2d0-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="ec2d0-149">ステートメント</span><span class="sxs-lookup"><span data-stu-id="ec2d0-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
