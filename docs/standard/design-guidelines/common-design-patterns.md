---
title: 共通デザイン パターン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8ce4a80501868bde2082d0ea65ffd033d8783935
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="common-design-patterns"></a><span data-ttu-id="e21bd-102">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="e21bd-102">Common Design Patterns</span></span>
<span data-ttu-id="e21bd-103">ソフトウェア パターン、パターン言語、およびアドレスのパターンの非常に幅広いサブジェクト antipatterns で多くの書籍があります。</span><span class="sxs-lookup"><span data-stu-id="e21bd-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="e21bd-104">したがって、ガイドラインと非常に限定された一連の .NET Framework Api の設計で頻繁に使用するパターンに関連付けられているディスカッションについても説明します。</span><span class="sxs-lookup"><span data-stu-id="e21bd-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e21bd-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e21bd-105">In This Section</span></span>  
 [<span data-ttu-id="e21bd-106">依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="e21bd-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="e21bd-107">Dispose パターン</span><span class="sxs-lookup"><span data-stu-id="e21bd-107">Dispose Pattern</span></span>](../../../docs/standard/design-guidelines/dispose-pattern.md)  
 <span data-ttu-id="e21bd-108">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e21bd-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e21bd-109">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="e21bd-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21bd-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e21bd-110">See Also</span></span>  
 [<span data-ttu-id="e21bd-111">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e21bd-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
