---
title: "Imports ステートメント (.NET Namespace よぶ型) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
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
ms.openlocfilehash: af177874c3278efd348b53a2b74b4d49d6628c61
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="84a0f-102">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="84a0f-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="84a0f-103">有効では、名前空間の修飾せずに参照する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="84a0f-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="84a0f-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="84a0f-105">Parts</span></span>  
  
|<span data-ttu-id="84a0f-106">用語</span><span class="sxs-lookup"><span data-stu-id="84a0f-106">Term</span></span>|<span data-ttu-id="84a0f-107">定義</span><span class="sxs-lookup"><span data-stu-id="84a0f-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="84a0f-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="84a0f-108">Optional.</span></span> <span data-ttu-id="84a0f-109">*インポート エイリアス*または名前ではコードから参照する`namespace`完全に修飾文字列の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="84a0f-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="84a0f-110">参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="84a0f-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="84a0f-111">Required.</span></span> <span data-ttu-id="84a0f-112">インポートされる名前空間の完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="84a0f-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="84a0f-113">名前空間の文字列はネストできます任意のレベルに。</span><span class="sxs-lookup"><span data-stu-id="84a0f-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="84a0f-114">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="84a0f-114">Optional.</span></span> <span data-ttu-id="84a0f-115">プログラミングの要素の名前は、名前空間で宣言します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="84a0f-116">任意のコンテナー要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a0f-117">コメント</span><span class="sxs-lookup"><span data-stu-id="84a0f-117">Remarks</span></span>  
 <span data-ttu-id="84a0f-118">`Imports`ステートメントにより、型を直接参照できる特定の名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="84a0f-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="84a0f-119">単一の名前空間名または入れ子になった名前空間の文字列を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="84a0f-120">入れ子になった各名前空間がピリオドで区切った次のより高いレベルの名前空間から (`.`) 次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="84a0f-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="84a0f-121">各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="84a0f-122">これらをたどるに任意のオプションを宣言など、`Option Strict`ステートメント、およびそれらの前に指定任意のプログラミング要素宣言など`Module`または`Class`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="84a0f-123">使用する`Imports`ファイル レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="84a0f-124">つまり、宣言コンテキストのインポートでソース ファイルである名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="84a0f-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="84a0f-125">`Imports`ステートメントは行いませんから他のプロジェクトおよびアセンブリの要素をプロジェクトで使用します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="84a0f-126">インポートは行われず、参照を設定します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="84a0f-127">既にプロジェクトに使用できる名前を修飾する必要性のみを削除します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="84a0f-128">詳細については、「を含む要素のインポート」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84a0f-129">暗黙の型を定義する`Imports`ステートメントを使用して、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="84a0f-130">詳細については、次を参照してください。[方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e)です。</span><span class="sxs-lookup"><span data-stu-id="84a0f-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="84a0f-131">インポート エイリアス</span><span class="sxs-lookup"><span data-stu-id="84a0f-131">Import Aliases</span></span>  
 <span data-ttu-id="84a0f-132">*インポート エイリアス*名前空間または型のエイリアスを定義します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="84a0f-133">インポート エイリアスは、1 つ以上の名前空間で宣言されているのと同じ名前を持つ項目を使用する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="84a0f-134">詳細および例に、「an 要素名を修飾する」を参照してください[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="84a0f-135">同じ名前のモジュール レベルでメンバーを宣言する必要があります`aliasname`します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="84a0f-136">Visual Basic コンパイラを使用した場合、`aliasname`宣言されたメンバーに対してのみとしません。 インポート エイリアスとして認識します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="84a0f-137">インポート エイリアスを宣言するために使用される構文は、XML 名前空間プレフィックスをインポートするため使用されることはそのようなが、結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="84a0f-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="84a0f-138">インポート エイリアスは、XML 名前空間プレフィックスとして使用できます XML リテラルと XML 軸プロパティだけで、プレフィックスで修飾された要素または属性の名前には、コードでは、式として使用できます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="84a0f-139">要素の名前</span><span class="sxs-lookup"><span data-stu-id="84a0f-139">Element Names</span></span>  
 <span data-ttu-id="84a0f-140">指定した場合`element`、表している必要があります、*コンテナー要素*、その他の要素を含めることができるプログラミング要素は、です。</span><span class="sxs-lookup"><span data-stu-id="84a0f-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="84a0f-141">コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙が含まれます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="84a0f-142">によって提供される要素のスコープ、`Imports`ステートメントは、指定するかどうかによって異なります`element`します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="84a0f-143">だけを指定する場合は、 `namespace`、すべて一意にその名前空間のメンバーとその名前空間内のコンテナー要素のメンバーの名前、修飾なしで利用されます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="84a0f-144">両方を指定する場合は、`namespace`と`element`、のみ、その要素のメンバーを修飾なしで使用します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a0f-145">例</span><span class="sxs-lookup"><span data-stu-id="84a0f-145">Example</span></span>  
 <span data-ttu-id="84a0f-146">次の例は、<xref:System.IO.DirectoryInfo>クラス</xref:System.IO.DirectoryInfo>を使用して、C:\ ディレクトリ内のすべてのフォルダーを返します</span><span class="sxs-lookup"><span data-stu-id="84a0f-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="84a0f-147">コードは いいえ`Imports`ステートメントをファイルの先頭にします。</span><span class="sxs-lookup"><span data-stu-id="84a0f-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="84a0f-148">したがって、 `DirectoryInfo`、 <xref:System.Text.StringBuilder>、および<xref:Microsoft.VisualBasic.ControlChars.CrLf>参照はすべて完全修飾名前空間にします</xref:Microsoft.VisualBasic.ControlChars.CrLf></xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="84a0f-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="84a0f-149">[!code-vb[VbVbalrStatements #&152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-149">[!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a0f-150">例</span><span class="sxs-lookup"><span data-stu-id="84a0f-150">Example</span></span>  
 <span data-ttu-id="84a0f-151">次の例が含まれます`Imports`参照先の名前空間ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="84a0f-152">そのため、型は、完全修飾名前空間にするのにはありません。</span><span class="sxs-lookup"><span data-stu-id="84a0f-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="84a0f-153">[!code-vb[VbVbalrStatements #&153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-153">[!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span></span>  
  
 <span data-ttu-id="84a0f-154">[!code-vb[VbVbalrStatements #&154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-154">[!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a0f-155">例</span><span class="sxs-lookup"><span data-stu-id="84a0f-155">Example</span></span>  
 <span data-ttu-id="84a0f-156">次の例が含まれます`Imports`参照先の名前空間の別名を作成するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-156">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="84a0f-157">種類は、エイリアスを持つ修飾されます。</span><span class="sxs-lookup"><span data-stu-id="84a0f-157">The types are qualified with the aliases.</span></span>  
  
 <span data-ttu-id="84a0f-158">[!code-vb[VbVbalrStatements #&155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-158">[!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span></span>  
  
 <span data-ttu-id="84a0f-159">[!code-vb[VbVbalrStatements #&156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-159">[!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a0f-160">例</span><span class="sxs-lookup"><span data-stu-id="84a0f-160">Example</span></span>  
 <span data-ttu-id="84a0f-161">次の例が含まれます`Imports`の参照先の型のエイリアスを作成するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84a0f-161">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="84a0f-162">エイリアスを使用して、種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="84a0f-162">Aliases are used to specify the types.</span></span>  
  
 <span data-ttu-id="84a0f-163">[!code-vb[VbVbalrStatements #&157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-163">[!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span></span>  
  
 <span data-ttu-id="84a0f-164">[!code-vb[VbVbalrStatements #&158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="84a0f-164">[!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a0f-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="84a0f-165">See Also</span></span>  
 <span data-ttu-id="84a0f-166">[Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="84a0f-166">[Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="84a0f-167"> [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="84a0f-167"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="84a0f-168"> [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="84a0f-168"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="84a0f-169"> [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="84a0f-169"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="84a0f-170"> [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="84a0f-170"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
