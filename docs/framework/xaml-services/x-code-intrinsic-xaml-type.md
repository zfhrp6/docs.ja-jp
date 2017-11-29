---
title: "x:Code 組み込み XAML 型 "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="34fa3-102">x:Code 組み込み XAML 型 </span><span class="sxs-lookup"><span data-stu-id="34fa3-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="34fa3-103">XAML の運用環境でコードの配置を許可します。</span><span class="sxs-lookup"><span data-stu-id="34fa3-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="34fa3-104">XAML、またはランタイムによって解釈など、後から使用の XAML の運用環境で左側をコンパイルする XAML プロセッサの実装でこのようなコードをコンパイルするか、できます。</span><span class="sxs-lookup"><span data-stu-id="34fa3-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="34fa3-105">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="34fa3-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="34fa3-106">コメント</span><span class="sxs-lookup"><span data-stu-id="34fa3-106">Remarks</span></span>  
 <span data-ttu-id="34fa3-107">内のコード、 `x:Code` XAML ディレクティブ要素が、一般的な XML 名前空間内の解釈のままと XAML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="34fa3-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="34fa3-108">そのため、必要がある通常を使用するコードを囲む`x:Code`内、`CDATA`セグメント。</span><span class="sxs-lookup"><span data-stu-id="34fa3-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="34fa3-109">`x:Code`次の XAML の運用環境のすべての可能な展開メカニズムは許可されません。</span><span class="sxs-lookup"><span data-stu-id="34fa3-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="34fa3-110">特定のフレームワーク (WPF など) でコードをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="34fa3-111">その他のフレームワーク`x:Code`使用状況を通常許可されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="34fa3-112">管理を許可するフレームワーク`x:Code`コンテンツを使用する適切な言語コンパイラ`x:Code`コンテンツは、アプリケーションのコンパイルに使用されるを含むプロジェクトの設定とターゲットによって決まります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="34fa3-113">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="34fa3-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="34fa3-114">内で宣言されているコード`x:Code`WPF には、いくつかの重要な制限。</span><span class="sxs-lookup"><span data-stu-id="34fa3-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="34fa3-115">`x:Code`ディレクティブ要素は XAML の運用環境のルート要素のすぐ下の子要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="34fa3-116">[X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)親ルート要素に提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-116">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="34fa3-117">コード内に配置`x:Code`は既にその XAML ページに対して作成される部分クラスのスコープ内にあるコンパイルによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="34fa3-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="34fa3-118">したがって、部分クラスのメンバーまたは変数を定義するすべてのコードがあります。</span><span class="sxs-lookup"><span data-stu-id="34fa3-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="34fa3-119">以外の場合、部分クラス内のクラスを入れ子にして、追加のクラスを定義することはできません (入れ子可能ですが、XAML で入れ子になったクラスは参照できないために、一般的ではありません)。</span><span class="sxs-lookup"><span data-stu-id="34fa3-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="34fa3-120">既存の部分クラスに使用される名前空間以外の CLR 名前空間を定義またはに追加できません。</span><span class="sxs-lookup"><span data-stu-id="34fa3-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="34fa3-121">部分クラスの CLR 名前空間の外部コードのエンティティへの参照する必要がありますすべて完全修飾します。</span><span class="sxs-lookup"><span data-stu-id="34fa3-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="34fa3-122">上書きを部分クラスのオーバーライド可能なメンバーにメンバーが宣言されている場合は、言語固有のオーバーライド キーワードを使用してこれを指定してください。</span><span class="sxs-lookup"><span data-stu-id="34fa3-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="34fa3-123">メンバーが宣言されている場合`x:Code`XAML から作成された部分クラスのメンバーと競合するスコープ、ように、コンパイラが、競合を報告していること、XAML ファイルことはできませんコンパイル、またはロードします。</span><span class="sxs-lookup"><span data-stu-id="34fa3-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fa3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="34fa3-124">See Also</span></span>  
 [<span data-ttu-id="34fa3-125">x:Class ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="34fa3-125">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="34fa3-126">WPF における分離コードと XAML</span><span class="sxs-lookup"><span data-stu-id="34fa3-126">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="34fa3-127">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="34fa3-127">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
