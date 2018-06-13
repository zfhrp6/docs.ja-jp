---
title: 属性リスト (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604075"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="1f65f-102">属性リスト (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f65f-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="1f65f-103">宣言されたプログラミング要素に適用される属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="1f65f-104">複数の属性を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="1f65f-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="1f65f-105">1 つの属性の構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f65f-106">構文</span><span class="sxs-lookup"><span data-stu-id="1f65f-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1f65f-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="1f65f-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="1f65f-108">ソース ファイルの先頭に適用される属性に必須です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="1f65f-109">指定できます[アセンブリ](../../../visual-basic/language-reference/modifiers/assembly.md)または[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="1f65f-110">必須。</span><span class="sxs-lookup"><span data-stu-id="1f65f-110">Required.</span></span> <span data-ttu-id="1f65f-111">属性の名前。</span><span class="sxs-lookup"><span data-stu-id="1f65f-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="1f65f-112">任意。</span><span class="sxs-lookup"><span data-stu-id="1f65f-112">Optional.</span></span> <span data-ttu-id="1f65f-113">この属性の位置指定引数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="1f65f-114">複数の引数は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="1f65f-115">任意。</span><span class="sxs-lookup"><span data-stu-id="1f65f-115">Optional.</span></span> <span data-ttu-id="1f65f-116">この属性の変数またはプロパティの初期化子の一覧です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="1f65f-117">複数の初期化子は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f65f-118">コメント</span><span class="sxs-lookup"><span data-stu-id="1f65f-118">Remarks</span></span>  
 <span data-ttu-id="1f65f-119">(型、プロシージャ、プロパティ、およびなど)、ほぼすべてのプログラミング要素には、1 つまたは複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="1f65f-120">属性がアセンブリのメタデータに表示され、コードに注釈を付けるか、特定のプログラミング要素を使用する方法を指定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="1f65f-121">Visual Basic と .NET Framework によって定義された属性を適用して、独自の属性を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="1f65f-122">属性を使用する場合の詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="1f65f-123">詳細については、属性名は、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1f65f-124">ルール</span><span class="sxs-lookup"><span data-stu-id="1f65f-124">Rules</span></span>  
  
-   <span data-ttu-id="1f65f-125">**配置します。**</span><span class="sxs-lookup"><span data-stu-id="1f65f-125">**Placement.**</span></span> <span data-ttu-id="1f65f-126">最も宣言されたプログラミング要素に属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="1f65f-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="1f65f-127">配置する 1 つまたは複数の属性を適用する、*属性ブロック*要素宣言の先頭にします。</span><span class="sxs-lookup"><span data-stu-id="1f65f-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="1f65f-128">属性の一覧内の各エントリには、適用する属性および修飾子と属性のこの呼び出しを使用している引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="1f65f-129">**山かっこです。**</span><span class="sxs-lookup"><span data-stu-id="1f65f-129">**Angle Brackets.**</span></span> <span data-ttu-id="1f65f-130">属性リストを指定する場合は、山かっこで囲む必要があります ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="1f65f-131">**宣言の一部です。**</span><span class="sxs-lookup"><span data-stu-id="1f65f-131">**Part of the Declaration.**</span></span> <span data-ttu-id="1f65f-132">属性は、個別のステートメントではなく、要素の宣言の一部である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f65f-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="1f65f-133">行連結シーケンスを使用することができます (" `_`") を複数のソース コード行に、宣言ステートメントを拡張します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="1f65f-134">**修飾子です。**</span><span class="sxs-lookup"><span data-stu-id="1f65f-134">**Modifiers.**</span></span> <span data-ttu-id="1f65f-135">属性の修飾子 (`Assembly`または`Module`)、ソース ファイルの先頭のプログラミング要素に適用されるすべての属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f65f-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="1f65f-136">属性の修飾子は、ソース ファイルの先頭には存在しない要素に適用される属性では許可されません。</span><span class="sxs-lookup"><span data-stu-id="1f65f-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="1f65f-137">**引数。**</span><span class="sxs-lookup"><span data-stu-id="1f65f-137">**Arguments.**</span></span> <span data-ttu-id="1f65f-138">属性のすべての位置指定引数には、任意の変数またはプロパティの初期化子が前に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f65f-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f65f-139">例</span><span class="sxs-lookup"><span data-stu-id="1f65f-139">Example</span></span>  
 <span data-ttu-id="1f65f-140">次の例に適用されます、<xref:System.Runtime.InteropServices.DllImportAttribute>属性のスケルトン定義を`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1f65f-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <span data-ttu-id="1f65f-141"><xref:System.Runtime.InteropServices.DllImportAttribute> 属性付きの手順がアンマネージ ダイナミック リンク ライブラリ (DLL) のエントリ ポイントを表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="1f65f-142">属性は、位置指定引数として DLL 名と変数の初期化子とその他の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1f65f-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f65f-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f65f-143">See Also</span></span>  
 [<span data-ttu-id="1f65f-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="1f65f-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [<span data-ttu-id="1f65f-145">Module \<キーワード></span><span class="sxs-lookup"><span data-stu-id="1f65f-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="1f65f-146">属性の概要</span><span class="sxs-lookup"><span data-stu-id="1f65f-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="1f65f-147">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="1f65f-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
