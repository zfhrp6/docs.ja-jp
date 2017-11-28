---
title: "&lt;value&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="173fa-102">&lt;value&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="173fa-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="173fa-103">構文</span><span class="sxs-lookup"><span data-stu-id="173fa-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="173fa-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="173fa-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="173fa-105">プロパティの説明。</span><span class="sxs-lookup"><span data-stu-id="173fa-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="173fa-106">コメント</span><span class="sxs-lookup"><span data-stu-id="173fa-106">Remarks</span></span>  
 <span data-ttu-id="173fa-107">\<value> タグを使用して、プロパティが表す値を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="173fa-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="173fa-108">Visual Studio .NET 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) タグが追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="173fa-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="173fa-109">その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="173fa-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="173fa-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="173fa-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="173fa-111">例</span><span class="sxs-lookup"><span data-stu-id="173fa-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="173fa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="173fa-112">See Also</span></span>  
 [<span data-ttu-id="173fa-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="173fa-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="173fa-114">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="173fa-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
