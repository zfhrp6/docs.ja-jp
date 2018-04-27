---
title: DLL のクライアント アプリケーションの数が多すぎます
ms.date: 07/20/2015
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
ms.openlocfilehash: 78b3291531c2097fb4124486f6fbac40e2d13b8e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="5a26c-102">DLL のクライアント アプリケーションの数が多すぎます</span><span class="sxs-lookup"><span data-stu-id="5a26c-102">Too many DLL application clients</span></span>
<span data-ttu-id="5a26c-103">Visual basic のダイナミック リンク ライブラリ (DLL) には、限られた数のアプリケーションをホストしてアクセスのみに対応します。</span><span class="sxs-lookup"><span data-stu-id="5a26c-103">The dynamic-link library (DLL) for Visual Basic can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="5a26c-104">アプリと Visual Basic のホスト (アプリケーションによって一部のアクセス可能性があります) は、他のアプリケーションすべてしようとしています、同時に、Visual Basic の DLL にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5a26c-104">Your application and other applications that are Visual Basic hosts (some of which may be accessed by your application) are all attempting to access the Visual Basic DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5a26c-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5a26c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5a26c-106">Visual Basic にアクセスするアプリケーションの数を削減します。</span><span class="sxs-lookup"><span data-stu-id="5a26c-106">Reduce the number of open applications accessing Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a26c-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a26c-107">See Also</span></span>  
 [<span data-ttu-id="5a26c-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="5a26c-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
