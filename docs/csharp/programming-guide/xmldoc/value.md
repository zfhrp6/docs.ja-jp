---
title: '&lt;value&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 22de15560d6db6e8a70cea744dd9d85359336306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="9c1fd-102">&lt;value&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9c1fd-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9c1fd-103">構文</span><span class="sxs-lookup"><span data-stu-id="9c1fd-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c1fd-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c1fd-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="9c1fd-105">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="9c1fd-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c1fd-106">コメント</span><span class="sxs-lookup"><span data-stu-id="9c1fd-106">Remarks</span></span>  
 <span data-ttu-id="9c1fd-107">\<value> タグを使用して、プロパティが表す値を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="9c1fd-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="9c1fd-108">Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) タグが追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9c1fd-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="9c1fd-109">その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c1fd-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="9c1fd-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="9c1fd-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1fd-111">例</span><span class="sxs-lookup"><span data-stu-id="9c1fd-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c1fd-112">参照</span><span class="sxs-lookup"><span data-stu-id="9c1fd-112">See Also</span></span>  
 [<span data-ttu-id="9c1fd-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9c1fd-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9c1fd-114">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="9c1fd-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
