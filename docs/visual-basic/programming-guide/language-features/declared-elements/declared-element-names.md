---
title: "宣言された要素の名前 (Visual Basic) |Microsoft ドキュメント"
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
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
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
ms.openlocfilehash: 899bcb2ecc8f5c07fdf4592e15827ff67f55c136
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="7ff5f-102">宣言された要素の名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ff5f-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="7ff5f-103">どの宣言された要素にも、名前とも呼ばれます、*識別子*、これは、コードを使用してそれを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7ff5f-104">ルール</span><span class="sxs-lookup"><span data-stu-id="7ff5f-104">Rules</span></span>  
 <span data-ttu-id="7ff5f-105">内の要素名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-105">An element name in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must observe the following rules:</span></span>  
  
-   <span data-ttu-id="7ff5f-106">文字は英字またはアンダー スコアで始まる必要があります (`_`)。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="7ff5f-107">アルファベット文字、10 進数字およびアンダー スコアのみでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="7ff5f-108">アンダー スコアで始まる場合、少なくとも&1; つのアルファベット文字または&10; 進数字でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="7ff5f-109">1023 を超える文字はできません。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="7ff5f-110">1023 文字の長さの制限にも適用されます、完全修飾名の文字列全体など`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="7ff5f-111">次の例では、有効な要素名を示します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="7ff5f-112">次の例では、無効な要素名を示します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="7ff5f-113">最初には、アンダー スコアのみが含まれています。、2 つ目が&10; 進数字で始まるおよび&3; つ目には、無効な文字 ($) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="7ff5f-114">アンダー スコアで始まる要素名 (`_`) に含まれていませんが、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、CLS 準拠のコードはそのような名前を定義するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="7ff5f-115">ただし、要素名の他の任意の位置にアンダー スコアでは、CLS に準拠します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="7ff5f-116">名前の長さのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7ff5f-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="7ff5f-117">実際には、自分の名前は、できるだけ短く要素の特性を明確します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="7ff5f-118">これにより、コードの読みやすさを向上し、行の長さとソース ファイルのサイズを小さきます。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="7ff5f-119">これに対して、自分の名前は、いない適切に記述できる要素が表す意味を調べると、コードがこれを使用する方法長さである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="7ff5f-120">これは、コードの読みやすさにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-120">This is important for the readability of your code.</span></span> <span data-ttu-id="7ff5f-121">使い方も理解しようとする他の人がいる場合、または自分で検索する場合に作成した後、長い時間は、適切な要素名は、かなりの時間を保存できます。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="7ff5f-122">エスケープされた名前</span><span class="sxs-lookup"><span data-stu-id="7ff5f-122">Escaped Names</span></span>  
 <span data-ttu-id="7ff5f-123">一般に、要素名は、必要がありますと一致しませんによって予約されているキーワードのいずれかの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]など`Case`または`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-123">Generally, an element name must not match any of the keywords reserved by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], such as `Case` or `Friend`.</span></span> <span data-ttu-id="7ff5f-124">ただし、定義することができます、*エスケープ名前*、角かっこで囲まれている (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="7ff5f-125">エスケープされた名前がいずれかに一致[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]キーワード、角かっこは、任意のあいまいさを排除するためです。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-125">An escaped name can match any [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="7ff5f-126">後続のコードで名前を参照する場合は、角かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="7ff5f-127">一般に、エスケープされた名前を使用する必要がありますされる場合にのみ。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="7ff5f-128">以前のバージョンから移行済みのコードは[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は名として使用されているキーワードが予約されていないか、</span><span class="sxs-lookup"><span data-stu-id="7ff5f-128">Your code has migrated from a previous version of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="7ff5f-129">特定のキーワードは予約されていない別の言語で記述されたコードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="7ff5f-130">それ以外の場合、キーワードを使用してその名前が競合している場合、要素名の変更を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="7ff5f-131">統合開発環境 (IDE) では、これを行う簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="7ff5f-132">詳細については、次を参照してください。[リファクタリング](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb)します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-132">For more information, see [Refactoring](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="7ff5f-133">名前に大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="7ff5f-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="7ff5f-134">内の要素名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-134">Element names in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] are case-insensitive.</span></span> <span data-ttu-id="7ff5f-135">これは、コンパイラは、大文字と小文字だけが異なる&2; つの名前を比較し、ときと解釈するに同じ名前を意味します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="7ff5f-136">たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="7ff5f-137">ただし、共通言語ランタイム (CLR) は、大文字小文字を区別バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="7ff5f-138">このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="7ff5f-139">たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="7ff5f-140">かどうかは後で、クラスを再コンパイルし、要素の名前を変更する`abc`クラスを使用して、他のアセンブリがその要素にアクセスできなくします。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="7ff5f-141">したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="7ff5f-142">名前およびロケール</span><span class="sxs-lookup"><span data-stu-id="7ff5f-142">Names and Locales</span></span>  
 <span data-ttu-id="7ff5f-143">名前の比較ではロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="7ff5f-144">1 つのロケールで&2; つの名前が同じ場合は、すべてのロケールに一致するように、保証されます。</span><span class="sxs-lookup"><span data-stu-id="7ff5f-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff5f-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ff5f-145">See Also</span></span>  
 <span data-ttu-id="7ff5f-146">[宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ff5f-146">[Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span></span>  
<span data-ttu-id="7ff5f-147"> [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="7ff5f-147"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="7ff5f-148"> [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="7ff5f-148"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="7ff5f-149"> [ステートメント](../../../../visual-basic/language-reference/statements/index.md)</span><span class="sxs-lookup"><span data-stu-id="7ff5f-149"> [Statements](../../../../visual-basic/language-reference/statements/index.md)</span></span>
