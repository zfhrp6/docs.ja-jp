---
title: プロテクト メンバー
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d4d334d9809f374442e19807d3b249a17a1d9df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="protected-members"></a><span data-ttu-id="47781-102">プロテクト メンバー</span><span class="sxs-lookup"><span data-stu-id="47781-102">Protected Members</span></span>
<span data-ttu-id="47781-103">単独で保護されたメンバーはすべての機能拡張を指定しないがサブクラス化によって拡張機能をより強力な行うことができます。</span><span class="sxs-lookup"><span data-stu-id="47781-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="47781-104">メインのパブリック インターフェイスを不必要に複雑化せず、高度なカスタマイズ オプションを公開に使用できます。</span><span class="sxs-lookup"><span data-stu-id="47781-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="47781-105">フレームワークの設計者は、「保護された」名前が false 安心感を与えることができますので、プロテクト メンバーには注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47781-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="47781-106">すべてのユーザーはサブクラス封印されていないクラスとメンバーへのアクセスが保護されているをできるパブリック メンバーに使用された守勢のコーディング方法が保護されたメンバーに適用するためすべて同じです。</span><span class="sxs-lookup"><span data-stu-id="47781-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="47781-107">**✓ を検討してください**高度なカスタマイズのメンバーを使用して保護されています。</span><span class="sxs-lookup"><span data-stu-id="47781-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="47781-108">**✓ しないで**セキュリティ、ドキュメント、および互換性分析するためにパブリックと封印されていないクラスにプロテクト メンバーを処理します。</span><span class="sxs-lookup"><span data-stu-id="47781-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="47781-109">クラスから継承するすべてのユーザーし、プロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="47781-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="47781-110">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="47781-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="47781-111">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="47781-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47781-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="47781-112">See Also</span></span>  
 [<span data-ttu-id="47781-113">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="47781-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="47781-114">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="47781-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
