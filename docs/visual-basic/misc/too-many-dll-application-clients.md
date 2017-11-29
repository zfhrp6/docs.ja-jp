---
title: "DLL のクライアント アプリケーションの数が多すぎます"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="82545-102">DLL のクライアント アプリケーションの数が多すぎます</span><span class="sxs-lookup"><span data-stu-id="82545-102">Too many DLL application clients</span></span>
<span data-ttu-id="82545-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のダイナミック リンク ライブラリ (DLL) にアクセスできるホスト アプリケーションの数は限られています。</span><span class="sxs-lookup"><span data-stu-id="82545-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="82545-104">使用しているアプリケーションと、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ホスト (その一部は使用しているアプリケーションによってアクセスされる可能性があります) であるその他のアプリケーションとがすべて同時に [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL にアクセスしようとしています。</span><span class="sxs-lookup"><span data-stu-id="82545-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82545-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="82545-105">To correct this error</span></span>  
  
-   <span data-ttu-id="82545-106">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]にアクセスする動作中のアプリケーションの数を減らします。</span><span class="sxs-lookup"><span data-stu-id="82545-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82545-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="82545-107">See Also</span></span>  
 [<span data-ttu-id="82545-108">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="82545-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
