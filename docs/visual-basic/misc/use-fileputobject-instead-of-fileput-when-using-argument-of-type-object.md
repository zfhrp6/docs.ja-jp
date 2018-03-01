---
title: "使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="d5a70-102">使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合</span><span class="sxs-lookup"><span data-stu-id="d5a70-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="d5a70-103">`FilePut`メソッドには、型の引数が含まれています。`Object`です。</span><span class="sxs-lookup"><span data-stu-id="d5a70-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="d5a70-104">あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5a70-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5a70-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d5a70-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d5a70-106">`FilePut` を `FilePutObject`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d5a70-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="d5a70-107">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="d5a70-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="d5a70-108">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5a70-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a70-109">参照</span><span class="sxs-lookup"><span data-stu-id="d5a70-109">See Also</span></span>  
   
 [<span data-ttu-id="d5a70-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="d5a70-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="d5a70-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="d5a70-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
