---
title: パラメーターに名前を付ける
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6b96bb05c52de4bfd8b6ad6b972c9d22ca66da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="naming-parameters"></a><span data-ttu-id="6d052-102">パラメーターに名前を付ける</span><span class="sxs-lookup"><span data-stu-id="6d052-102">Naming Parameters</span></span>
<span data-ttu-id="6d052-103">読みやすくするための明確な理由から、以外には、パラメーターは、ドキュメントでは、デザイナーで表示されるビジュアル デ ザイン ツール Intellisense および参照機能クラスを指定するときにためパラメーターの名前に関するガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d052-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="6d052-104">**✓ しないで**パラメーター名の camel 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="6d052-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="6d052-105">**✓ しないで**わかりやすいパラメーター名を使用します。</span><span class="sxs-lookup"><span data-stu-id="6d052-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="6d052-106">**✓ を検討してください**パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="6d052-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="6d052-107">演算子のオーバー ロードのパラメーターの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="6d052-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="6d052-108">**✓ は**使用`left`と`right`のパラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。</span><span class="sxs-lookup"><span data-stu-id="6d052-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="6d052-109">**✓ しないで**使用`value`で単項演算子のオーバー ロード パラメーター名はパラメーターに意味がない場合。</span><span class="sxs-lookup"><span data-stu-id="6d052-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="6d052-110">**✓ を検討してください**演算子にわかりやすい名前オーバー ロードのパラメーターの場合は重要な価値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6d052-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="6d052-111">**X しないで**使用の省略形または数値の添字演算子のオーバー ロードのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="6d052-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="6d052-112">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="6d052-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6d052-113">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="6d052-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d052-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d052-114">See Also</span></span>  
 [<span data-ttu-id="6d052-115">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="6d052-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="6d052-116">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="6d052-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
