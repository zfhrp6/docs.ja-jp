---
title: 使用して&#39;FilePutObject&#39;の代わりに&#39;FilePut&#39;型の引数を使用するときに&#39;オブジェクト&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641129"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="629b0-102">使用して&#39;FilePutObject&#39;の代わりに&#39;FilePut&#39;型の引数を使用するときに&#39;オブジェクト&#39;</span><span class="sxs-lookup"><span data-stu-id="629b0-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="629b0-103">`FilePut`メソッドには、型の引数が含まれています。`Object`です。</span><span class="sxs-lookup"><span data-stu-id="629b0-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="629b0-104">あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="629b0-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="629b0-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="629b0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="629b0-106">`FilePut` を `FilePutObject`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="629b0-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="629b0-107">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="629b0-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="629b0-108">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="629b0-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629b0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="629b0-109">See Also</span></span>  
   
 [<span data-ttu-id="629b0-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="629b0-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="629b0-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="629b0-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
