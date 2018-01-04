---
title: "パラメーターに名前を付ける"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a10fa8835bfbcf826f8a3bb9318966e0dc603864
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="naming-parameters"></a><span data-ttu-id="27175-102">パラメーターに名前を付ける</span><span class="sxs-lookup"><span data-stu-id="27175-102">Naming Parameters</span></span>
<span data-ttu-id="27175-103">読みやすくするための明確な理由から、以外には、パラメーターは、ドキュメントでは、デザイナーで表示されるビジュアル デ ザイン ツール Intellisense および参照機能クラスを指定するときにためパラメーターの名前に関するガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="27175-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="27175-104">**✓ しないで**パラメーター名の camel 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="27175-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="27175-105">**✓ しないで**わかりやすいパラメーター名を使用します。</span><span class="sxs-lookup"><span data-stu-id="27175-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="27175-106">**✓ を検討してください**パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="27175-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="27175-107">演算子のオーバー ロードのパラメーターの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="27175-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="27175-108">**✓ は**使用`left`と`right`のパラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。</span><span class="sxs-lookup"><span data-stu-id="27175-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="27175-109">**✓ しないで**使用`value`で単項演算子のオーバー ロード パラメーター名はパラメーターに意味がない場合。</span><span class="sxs-lookup"><span data-stu-id="27175-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="27175-110">**✓ を検討してください**演算子にわかりやすい名前オーバー ロードのパラメーターの場合は重要な価値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="27175-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="27175-111">**X しないで**使用の省略形または数値の添字演算子のオーバー ロードのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="27175-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="27175-112">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="27175-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="27175-113">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="27175-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27175-114">参照</span><span class="sxs-lookup"><span data-stu-id="27175-114">See Also</span></span>  
 [<span data-ttu-id="27175-115">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="27175-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="27175-116">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="27175-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
