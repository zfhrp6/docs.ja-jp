---
title: "名前付けのガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40da7449c88eaaba92e34374c002c7e175b2ef16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="naming-guidelines"></a><span data-ttu-id="eaed6-102">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="eaed6-102">Naming Guidelines</span></span>
<span data-ttu-id="eaed6-103">次のフレームワークの開発に名前付け規則の一貫性を確保すると、フレームワークの使いやすさに主要な金額があります。</span><span class="sxs-lookup"><span data-stu-id="eaed6-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="eaed6-104">これにより、広範囲に分散されたプロジェクトの多くの開発者によって使用されるフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="eaed6-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="eaed6-105">フォームの整合性を超えるフレームワーク要素の名前は簡単に理解する必要があり、各要素の機能を伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaed6-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="eaed6-106">この章の目標は、開発者に即時わかりやすい名前に一貫性のある名前付け規則のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="eaed6-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="eaed6-107">一般的なコード開発のガイドラインは、コード全体でより一貫性のある名前付けになると、これらの名前付け規則を採用することが必要があるだけは公開される Api に適用 (public または protected の型とメンバー、および明示的に実装されたインターフェイス)。</span><span class="sxs-lookup"><span data-stu-id="eaed6-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eaed6-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eaed6-108">In This Section</span></span>  
 [<span data-ttu-id="eaed6-109">大文字と小文字の表記規則</span><span class="sxs-lookup"><span data-stu-id="eaed6-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="eaed6-110">一般的な名前付け規則</span><span class="sxs-lookup"><span data-stu-id="eaed6-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="eaed6-111">アセンブリと Dll の名前</span><span class="sxs-lookup"><span data-stu-id="eaed6-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="eaed6-112">名前空間の名前</span><span class="sxs-lookup"><span data-stu-id="eaed6-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="eaed6-113">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="eaed6-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="eaed6-114">型のメンバーの名前</span><span class="sxs-lookup"><span data-stu-id="eaed6-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="eaed6-115">パラメーターの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="eaed6-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="eaed6-116">リソースの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="eaed6-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="eaed6-117">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="eaed6-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="eaed6-118">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="eaed6-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaed6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaed6-119">See Also</span></span>  
 [<span data-ttu-id="eaed6-120">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="eaed6-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
