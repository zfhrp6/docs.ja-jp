---
title: "&lt;value&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
dev_langs:
- CSharp
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
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
ms.openlocfilehash: 71c8d5ab2e99291f05ef362960b0eeac969e9de1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="0f4d0-102">&lt;value&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0f4d0-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="0f4d0-103">構文</span><span class="sxs-lookup"><span data-stu-id="0f4d0-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f4d0-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f4d0-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="0f4d0-105">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="0f4d0-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f4d0-106">コメント</span><span class="sxs-lookup"><span data-stu-id="0f4d0-106">Remarks</span></span>  
 <span data-ttu-id="0f4d0-107">\<value> タグを使用して、プロパティが表す値を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="0f4d0-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="0f4d0-108">Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) タグが追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0f4d0-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="0f4d0-109">その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f4d0-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="0f4d0-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="0f4d0-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f4d0-111">例</span><span class="sxs-lookup"><span data-stu-id="0f4d0-111">Example</span></span>  
 <span data-ttu-id="0f4d0-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0f4d0-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4d0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f4d0-113">See Also</span></span>  
 <span data-ttu-id="0f4d0-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0f4d0-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="0f4d0-115">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="0f4d0-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

