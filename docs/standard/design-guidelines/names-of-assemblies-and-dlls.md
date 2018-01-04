---
title: "アセンブリと DLL の名前"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76584e0d22b6e651dfd851675a72d1f0cb70feb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="37589-102">アセンブリと DLL の名前</span><span class="sxs-lookup"><span data-stu-id="37589-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="37589-103">アセンブリは、展開とマネージ コード アプリケーションの id の単位です。</span><span class="sxs-lookup"><span data-stu-id="37589-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="37589-104">アセンブリは、1 つまたは複数のファイルにまたがることができますが通常アセンブリは一対一、DLL にマップされます。</span><span class="sxs-lookup"><span data-stu-id="37589-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="37589-105">そのため、このセクションでは、のみ DLL の名前付け規則、アセンブリの名前付け規則にマップすることができますがについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37589-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="37589-106">**✓ しないで**アセンブリ System.Data などの機能の大きなチャンクを提案する Dll の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="37589-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="37589-107">アセンブリ名と DLL 名を名前空間の名前に対応する必要はありませんが、これはアセンブリの名前を付けるときは、名前空間の名前を次に適切です。</span><span class="sxs-lookup"><span data-stu-id="37589-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="37589-108">適切な経験則では、アセンブリに含まれるアセンブリの共通のプレフィックスに基づく DLL の名前です。</span><span class="sxs-lookup"><span data-stu-id="37589-108">A good rule of thumb is to name the DLL based on the common prefix of the assemblies contained in the assembly.</span></span> <span data-ttu-id="37589-109">たとえば、2 つの名前空間を持つアセンブリ`MyCompany.MyTechnology.FirstFeature`と`MyCompany.MyTechnology.SecondFeature`、呼び出すことが`MyCompany.MyTechnology.dll`です。</span><span class="sxs-lookup"><span data-stu-id="37589-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="37589-110">**✓ を検討してください**Dll を次のパターンに従って名前付け。</span><span class="sxs-lookup"><span data-stu-id="37589-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="37589-111">ここで`<Component>`ドットで区切られた 1 つ以上の句が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37589-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="37589-112">例:</span><span class="sxs-lookup"><span data-stu-id="37589-112">For example:</span></span>  
  
 <span data-ttu-id="37589-113">`Litware.Controls.dll`。</span><span class="sxs-lookup"><span data-stu-id="37589-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="37589-114">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="37589-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="37589-115">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="37589-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37589-116">参照</span><span class="sxs-lookup"><span data-stu-id="37589-116">See Also</span></span>  
 [<span data-ttu-id="37589-117">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="37589-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="37589-118">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="37589-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
