---
title: "使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="cfaea-102">使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合</span><span class="sxs-lookup"><span data-stu-id="cfaea-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="cfaea-103">`FilePut`メソッドには、型の引数が含まれています。`Object`です。</span><span class="sxs-lookup"><span data-stu-id="cfaea-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="cfaea-104">あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfaea-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cfaea-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cfaea-105">To correct this error</span></span>  
  
-   <span data-ttu-id="cfaea-106">`FilePut` を `FilePutObject`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cfaea-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="cfaea-107">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="cfaea-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="cfaea-108">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="cfaea-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaea-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfaea-109">See Also</span></span>  
 [<span data-ttu-id="cfaea-110">ビルド内にありません: FilePutObject 関数</span><span class="sxs-lookup"><span data-stu-id="cfaea-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="cfaea-111">My.Computer.FileSystem オブジェクト</span><span class="sxs-lookup"><span data-stu-id="cfaea-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="cfaea-112">My.Computer.FileSystem.WriteAllBytes メソッド</span><span class="sxs-lookup"><span data-stu-id="cfaea-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
