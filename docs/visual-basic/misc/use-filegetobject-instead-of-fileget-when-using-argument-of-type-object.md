---
title: "使用して &#39;FileGetObject &#39;代わりに &#39;です。FileGet &#39;型 &#39; オブジェクト &#39; の引数を使用する場合"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="7d120-102">使用して &#39;FileGetObject &#39;代わりに &#39;です。FileGet &#39;型 &#39; オブジェクト &#39; の引数を使用する場合</span><span class="sxs-lookup"><span data-stu-id="7d120-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="7d120-103">`FileGet` メソッドには、型 `Object`の引数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d120-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="7d120-104">あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d120-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="7d120-105">`My.Computer.Filesystem` によって提供される機能は、 `FileGet` または `FileGetObject`よりも使いやすく、パフォーマンスが優れています。</span><span class="sxs-lookup"><span data-stu-id="7d120-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d120-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7d120-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7d120-107">`FileGet` を `FileGetObject`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7d120-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="7d120-108">`Object` 引数をより具体的な種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="7d120-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d120-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d120-109">See Also</span></span>  
 [<span data-ttu-id="7d120-110">ビルド内にありません: FileGetObject 関数</span><span class="sxs-lookup"><span data-stu-id="7d120-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="7d120-111">My.Computer.FileSystem オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7d120-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
