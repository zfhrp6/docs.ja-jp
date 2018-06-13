---
title: ない&#39;Main&#39;で適切なシグネチャを持つメソッドが見つかりました&#39;&lt;名&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593221"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="3612d-102">ない&#39;Main&#39;で適切なシグネチャを持つメソッドが見つかりました&#39;&lt;名&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="3612d-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="3612d-103">コマンド ライン アプリケーションが必要な`Sub Main`定義します。</span><span class="sxs-lookup"><span data-stu-id="3612d-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="3612d-104">`Main` として宣言する必要があります`Public Shared`クラスでは、またはとして定義されている場合`Public`モジュールで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="3612d-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="3612d-105">**エラー ID:** BC30737</span><span class="sxs-lookup"><span data-stu-id="3612d-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3612d-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3612d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="3612d-107">定義、`Public Sub Main`プロジェクトのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3612d-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="3612d-108">として宣言`Shared`クラス内で定義する場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="3612d-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3612d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3612d-109">See Also</span></span>  
 [<span data-ttu-id="3612d-110">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="3612d-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="3612d-111">手順</span><span class="sxs-lookup"><span data-stu-id="3612d-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
