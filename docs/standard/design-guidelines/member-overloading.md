---
title: メンバーのオーバーロード
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 546db0540cf7852b40678476f732663369b15824
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="member-overloading"></a><span data-ttu-id="047e2-102">メンバーのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="047e2-102">Member Overloading</span></span>
<span data-ttu-id="047e2-103">メンバーのオーバー ロードでは、数または型のパラメーターでのみが異なる同じ名前を持っていて、同じ型に 2 つ以上のメンバーの作成を意味します。</span><span class="sxs-lookup"><span data-stu-id="047e2-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="047e2-104">たとえば、次のようにで、`WriteLine`メソッドはオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="047e2-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="047e2-105">メソッド、コンス トラクター、およびインデックス付きプロパティは、パラメーターを持つことができます、ためメンバーのみをオーバー ロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="047e2-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="047e2-106">オーバー ロードでは、使いやすさ、生産性、および再利用可能なライブラリの読みやすさを向上させるための最も重要な手法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="047e2-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="047e2-107">パラメーターの数のオーバー ロードできるようになりますコンス トラクターとメソッドの単純なバージョンを提供します。</span><span class="sxs-lookup"><span data-stu-id="047e2-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="047e2-108">パラメーターの型のオーバー ロードできるようになりますさまざまな種類の選択したセットに対して同じ操作を実行するメンバーに対して同じメンバー名を使用します。</span><span class="sxs-lookup"><span data-stu-id="047e2-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="047e2-109">**✓ しないで**短いオーバー ロードで使用される既定値を示すためにわかりやすいパラメーター名を使用しようとしています。</span><span class="sxs-lookup"><span data-stu-id="047e2-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="047e2-110">**避け x**オーバー ロードのパラメーター名は任意で変更します。</span><span class="sxs-lookup"><span data-stu-id="047e2-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="047e2-111">1 つのオーバー ロードのパラメーターは、別のオーバー ロードのパラメーターと同じ入力を表している場合、パラメーターは、同じ名前を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="047e2-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="047e2-112">**避け x**メンバーをオーバー ロードされているのパラメーターの順序で一貫していません。</span><span class="sxs-lookup"><span data-stu-id="047e2-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="047e2-113">同じ名前のパラメーターは、すべてのオーバー ロード内の同じ位置に表示されます。</span><span class="sxs-lookup"><span data-stu-id="047e2-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="047e2-114">**✓ は**(拡張機能が必要な場合)、最長のオーバー ロードだけの仮想を作成します。</span><span class="sxs-lookup"><span data-stu-id="047e2-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="047e2-115">短いオーバー ロードは、長いのオーバー ロードにを通じて単に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="047e2-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="047e2-116">**X しないで**使用`ref`または`out`メンバーをオーバー ロードする修飾子です。</span><span class="sxs-lookup"><span data-stu-id="047e2-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="047e2-117">一部の言語では、次のようにオーバー ロードへの呼び出しを解決できません。</span><span class="sxs-lookup"><span data-stu-id="047e2-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="047e2-118">さらに、このようなオーバー ロード通常完全に異なるセマンティクスを持つされずにおそらく必要がありますオーバー ロードが 2 つの異なるメソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="047e2-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="047e2-119">**X しないで**同じ位置と類似した種類のパラメーターを使用してまだセマンティクスが異なるオーバー ロードがあります。</span><span class="sxs-lookup"><span data-stu-id="047e2-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="047e2-120">**✓ しないで**許可`null`省略可能な引数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="047e2-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="047e2-121">**✓ しないで**メンバーの既定の引数を持つメンバーを定義するのではなく、オーバー ロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="047e2-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="047e2-122">既定の引数は、CLS 準拠ではありません。</span><span class="sxs-lookup"><span data-stu-id="047e2-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="047e2-123">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="047e2-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="047e2-124">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="047e2-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047e2-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="047e2-125">See Also</span></span>  
 [<span data-ttu-id="047e2-126">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="047e2-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="047e2-127">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="047e2-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
