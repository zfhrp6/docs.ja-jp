---
title: 使用して&#39;FileGetObject&#39;の代わりに&#39;FileGet&#39;型の引数を使用するときに&#39;オブジェクト&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="baa95-102">使用して&#39;FileGetObject&#39;の代わりに&#39;FileGet&#39;型の引数を使用するときに&#39;オブジェクト&#39;</span><span class="sxs-lookup"><span data-stu-id="baa95-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="baa95-103">`FileGet` メソッドには、型 `Object`の引数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="baa95-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="baa95-104">あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baa95-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="baa95-105">`My.Computer.Filesystem` によって提供される機能は、 `FileGet` または `FileGetObject`よりも使いやすく、パフォーマンスが優れています。</span><span class="sxs-lookup"><span data-stu-id="baa95-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="baa95-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="baa95-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="baa95-107">`FileGet` を `FileGetObject`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="baa95-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="baa95-108">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="baa95-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa95-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="baa95-109">See Also</span></span>  
   
 [<span data-ttu-id="baa95-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="baa95-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
