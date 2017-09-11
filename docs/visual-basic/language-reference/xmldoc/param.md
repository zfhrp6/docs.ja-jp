---
title: "&lt;param&gt; (Visual Basic) |Microsoft ドキュメント"
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
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: ddf5baf83816d757edf67cdf1c66dc24e4313b83
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017

---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="9f919-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f919-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="9f919-103">パラメーター名と説明を定義します。</span><span class="sxs-lookup"><span data-stu-id="9f919-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f919-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f919-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f919-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f919-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9f919-106">メソッドのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="9f919-106">The name of a method parameter.</span></span> <span data-ttu-id="9f919-107">名前は二重引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="9f919-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9f919-108">パラメーターの説明です。</span><span class="sxs-lookup"><span data-stu-id="9f919-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f919-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9f919-109">Remarks</span></span>  
 <span data-ttu-id="9f919-110">`<param>`メソッドのパラメーターのいずれかを説明するメソッドの宣言のコメントでタグを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f919-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="9f919-111">テキストを`<param>`タグは、次の場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f919-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="9f919-112">IntelliSense のパラメーター情報です。</span><span class="sxs-lookup"><span data-stu-id="9f919-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="9f919-113">詳細については、「[IntelliSense の使用](https://docs.microsoft.com/visualstudio/ide/using-intellisense)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f919-113">For more information, see [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="9f919-114">オブジェクト ブラウザー。</span><span class="sxs-lookup"><span data-stu-id="9f919-114">Object Browser.</span></span> <span data-ttu-id="9f919-115">詳細については、「[コードの構造の表示](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f919-115">For more information, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="9f919-116">使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。</span><span class="sxs-lookup"><span data-stu-id="9f919-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f919-117">例</span><span class="sxs-lookup"><span data-stu-id="9f919-117">Example</span></span>  
 <span data-ttu-id="9f919-118">この例では、`<param>`を記述するタグ、`id`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="9f919-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 <span data-ttu-id="9f919-119">[!code-vb[VbVbcnXmlDocComments&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9f919-119">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f919-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f919-120">See Also</span></span>  
 [<span data-ttu-id="9f919-121">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="9f919-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
