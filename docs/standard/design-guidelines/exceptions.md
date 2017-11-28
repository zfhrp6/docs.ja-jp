---
title: "例外のデザインのガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="7282a-102">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7282a-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="7282a-103">例外処理では、エラーの戻り値ベースのレポートに比べて多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="7282a-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="7282a-104">適切なフレームワークの設計では、例外のメリットを実現アプリケーション開発者は、ことができます。</span><span class="sxs-lookup"><span data-stu-id="7282a-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="7282a-105">このセクションでは、例外の利点を説明し、それらを効果的に使用するためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="7282a-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7282a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7282a-106">In This Section</span></span>  
 [<span data-ttu-id="7282a-107">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="7282a-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="7282a-108">標準の例外型を使用します。</span><span class="sxs-lookup"><span data-stu-id="7282a-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="7282a-109">例外とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="7282a-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="7282a-110">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7282a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7282a-111">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="7282a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7282a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7282a-112">See Also</span></span>  
 [<span data-ttu-id="7282a-113">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7282a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
