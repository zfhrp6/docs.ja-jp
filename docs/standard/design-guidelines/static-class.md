---
title: "静的クラスのデザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c36bf5790d033eddb6bb7e0d910482143a9bcac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="static-class-design"></a><span data-ttu-id="61b79-102">静的クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="61b79-102">Static Class Design</span></span>
<span data-ttu-id="61b79-103">静的クラスが静的メンバーのみを格納するクラスとして定義されている (から継承されたインスタンス メンバーだけでなくもちろん<xref:System.Object?displayProperty=nameWithType>とコンス トラクターはプライベート可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="61b79-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="61b79-104">一部の言語では、静的クラスの組み込みサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="61b79-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="61b79-105">C# 2.0 以降では、静的クラスが宣言されると、sealed、abstract とインスタンス メンバーをオーバーライドまたは宣言されていることができます。</span><span class="sxs-lookup"><span data-stu-id="61b79-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="61b79-106">静的クラスは、純粋なオブジェクト指向デザインと単純さのバランスです。</span><span class="sxs-lookup"><span data-stu-id="61b79-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="61b79-107">その他の操作へのショートカットを提供によく使用されます (など<xref:System.IO.File?displayProperty=nameWithType>)、拡張メソッド、または完全なオブジェクト指向ラッパーが保証されているいない機能の保持者 (など<xref:System.Environment?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="61b79-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="61b79-108">**✓ しないで**静的クラスを慎重に使用します。</span><span class="sxs-lookup"><span data-stu-id="61b79-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="61b79-109">静的クラスは、オブジェクト指向のコア フレームワークのサポート クラスとしてのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61b79-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="61b79-110">**X しないで**静的クラスをその他のバケットとして扱います。</span><span class="sxs-lookup"><span data-stu-id="61b79-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="61b79-111">**X しないで**宣言または静的クラスでインスタンス メンバーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="61b79-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="61b79-112">**✓ しないで**として、シールされた抽象クラスで静的クラスを宣言し、使用するプログラミング言語には静的クラスの組み込みサポートがない場合は、プライベート インスタンス コンス トラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="61b79-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="61b79-113">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="61b79-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="61b79-114">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="61b79-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b79-115">参照</span><span class="sxs-lookup"><span data-stu-id="61b79-115">See Also</span></span>  
 [<span data-ttu-id="61b79-116">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="61b79-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="61b79-117">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="61b79-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
