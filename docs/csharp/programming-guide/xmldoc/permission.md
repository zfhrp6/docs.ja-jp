---
title: "&lt;permission&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
dev_langs:
- CSharp
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4b8f109d7e01f6e630f09939161b6a20c3a13f73
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="94b5f-102">&lt;permission&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="94b5f-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="94b5f-103">構文</span><span class="sxs-lookup"><span data-stu-id="94b5f-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94b5f-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94b5f-104">Parameters</span></span>  
 <span data-ttu-id="94b5f-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="94b5f-105">cref = " `member`"</span></span>  
 <span data-ttu-id="94b5f-106">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="94b5f-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="94b5f-107">コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="94b5f-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="94b5f-108">*member* は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="94b5f-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="94b5f-109">ジェネリック型への cref 参照を作成する方法については、「[\<see>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b5f-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="94b5f-110">メンバーへのアクセスの説明です。</span><span class="sxs-lookup"><span data-stu-id="94b5f-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94b5f-111">コメント</span><span class="sxs-lookup"><span data-stu-id="94b5f-111">Remarks</span></span>  
 <span data-ttu-id="94b5f-112">\<permission> タグを使用すると、メンバーのアクセスを文書化できます。</span><span class="sxs-lookup"><span data-stu-id="94b5f-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="94b5f-113"><xref:System.Security.PermissionSet> クラスを使用すると、メンバーへのアクセスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94b5f-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="94b5f-114">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="94b5f-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94b5f-115">例</span><span class="sxs-lookup"><span data-stu-id="94b5f-115">Example</span></span>  
 <span data-ttu-id="94b5f-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="94b5f-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b5f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="94b5f-117">See Also</span></span>  
 <span data-ttu-id="94b5f-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="94b5f-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="94b5f-119">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="94b5f-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

