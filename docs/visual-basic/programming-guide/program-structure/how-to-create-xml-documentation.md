---
title: "方法: Visual Basic での XML ドキュメントの作成 |Microsoft ドキュメント"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3171877f4fa1913b5535d71d671cea97b5a22850
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="c5140-102">方法 : Visual Basic で XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="c5140-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="c5140-103">この例では、XML ドキュメントのコメントをコードに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c5140-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="c5140-104">型またはメンバーの XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="c5140-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="c5140-105">**コード エディター**ドキュメントを作成する型またはメンバー上の行にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="c5140-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="c5140-106">型`'''`(3 つの単一引用符付き)。</span><span class="sxs-lookup"><span data-stu-id="c5140-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="c5140-107">型またはメンバーの XML スケルトンが追加された、**コード エディター**します。</span><span class="sxs-lookup"><span data-stu-id="c5140-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="c5140-108">適切なタグの間のわかりやすい情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="c5140-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5140-109">各行を始める必要があります、XML ドキュメントのブロック内で行を追加する場合は、`'''`です。</span><span class="sxs-lookup"><span data-stu-id="c5140-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="c5140-110">新しい XML ドキュメント コメントを含む、型またはメンバーを使用する追加のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5140-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="c5140-111">IntelliSense のテキストを表示する、\<概要 > 型またはメンバーのタグ。</span><span class="sxs-lookup"><span data-stu-id="c5140-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="c5140-112">ドキュメント コメントを含む XML ファイルを生成するコードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c5140-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="c5140-113">詳細については、次を参照してください。 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)します。</span><span class="sxs-lookup"><span data-stu-id="c5140-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5140-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5140-114">See Also</span></span>  
 <span data-ttu-id="c5140-115">[XML を使用してコードを文書化します。](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c5140-115">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="c5140-116"> [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="c5140-116"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="c5140-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span><span class="sxs-lookup"><span data-stu-id="c5140-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span></span>
