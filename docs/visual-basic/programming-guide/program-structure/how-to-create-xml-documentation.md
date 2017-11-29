---
title: "方法 : Visual Basic で XML ドキュメントを作成する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="f71bc-102">方法 : Visual Basic で XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="f71bc-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="f71bc-103">この例では、XML ドキュメント コメントをコードに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f71bc-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="f71bc-104">型またはメンバーの XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="f71bc-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="f71bc-105">**コード エディター**ドキュメントを作成する型またはメンバー上の行にカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="f71bc-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="f71bc-106">型`'''`(3 つ単一引用符)。</span><span class="sxs-lookup"><span data-stu-id="f71bc-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="f71bc-107">XML スケルトンの型またはメンバーを追加、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f71bc-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="f71bc-108">適切なタグの間で情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="f71bc-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f71bc-109">それぞれの線が始まる必要があります、XML ドキュメントのブロック内で行を追加する場合`'''`です。</span><span class="sxs-lookup"><span data-stu-id="f71bc-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="f71bc-110">新しい XML ドキュメントのコメントに型またはメンバーを使用する追加のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f71bc-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="f71bc-111">IntelliSense のテキストを表示する、\<概要 > 型またはメンバーのタグ。</span><span class="sxs-lookup"><span data-stu-id="f71bc-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="f71bc-112">ドキュメント コメントを含む XML ファイルを生成するコードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f71bc-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="f71bc-113">詳細については、「[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f71bc-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71bc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f71bc-114">See Also</span></span>  
 [<span data-ttu-id="f71bc-115">XML の使用によるコードのドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="f71bc-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="f71bc-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="f71bc-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="f71bc-117">/doc</span><span class="sxs-lookup"><span data-stu-id="f71bc-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
