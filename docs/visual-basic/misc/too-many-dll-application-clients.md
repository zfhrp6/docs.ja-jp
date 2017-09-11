---
title: "DLL アプリケーションのクライアントが多すぎる |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 18781161d1208e7e8d01f99eb9d655803d249e6e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="82e4c-102">DLL のクライアント アプリケーションの数が多すぎます</span><span class="sxs-lookup"><span data-stu-id="82e4c-102">Too many DLL application clients</span></span>
<span data-ttu-id="82e4c-103">ダイナミック リンク ライブラリ (DLL)[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]限られた数のホスト アプリケーションでのアクセスにのみ対応できます。</span><span class="sxs-lookup"><span data-stu-id="82e4c-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="82e4c-104">アプリケーションとその他のアプリケーションである[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)](アプリケーションでのアクセス可能性があります) のホストがすべてにアクセスしようとして、[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]同時 DLL です。</span><span class="sxs-lookup"><span data-stu-id="82e4c-104">Your application and other applications that are [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82e4c-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="82e4c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="82e4c-106">開いているアプリケーションへのアクセスの数を減らす[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="82e4c-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e4c-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="82e4c-107">See Also</span></span>  
 [<span data-ttu-id="82e4c-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="82e4c-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
