---
title: "x:Subclass ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xsubclass-directive"></a><span data-ttu-id="130f9-102">x:Subclass ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="130f9-102">x:Subclass Directive</span></span>
<span data-ttu-id="130f9-103">XAML マークアップのコンパイルの動作を変更してとき`x:Class`も用意されています。</span><span class="sxs-lookup"><span data-stu-id="130f9-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="130f9-104">基になっている部分クラスを作成する代わりに`x:Class`、提供されている`x:Class`、中間クラスとして作成された基になる、指定された派生クラスを想定し、`x:Class`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="130f9-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="130f9-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="130f9-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="130f9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="130f9-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="130f9-107">Optional.</span></span> <span data-ttu-id="130f9-108">含む CLR 名前空間が指定`classname`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="130f9-109">場合`namespace`を指定すると、ドット (.) で区切られます`namespace`と`classname`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="130f9-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="130f9-110">Required.</span></span> <span data-ttu-id="130f9-111">読み込まれた XAML およびその XAML の分離コードで接続する部分クラスの CLR 名を指定します。</span><span class="sxs-lookup"><span data-stu-id="130f9-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="130f9-112">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="130f9-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="130f9-113">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="130f9-113">Optional.</span></span> <span data-ttu-id="130f9-114">異なっていてもかまいません`namespace`他の各名前空間を解決できない場合。</span><span class="sxs-lookup"><span data-stu-id="130f9-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="130f9-115">含む CLR 名前空間が指定`subclassName`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="130f9-116">場合`subclassName`を指定すると、ドット (.) で区切られます`subclassNamespace`と`subclassName`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="130f9-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="130f9-117">Required.</span></span> <span data-ttu-id="130f9-118">サブクラスの CLR 名を指定します。</span><span class="sxs-lookup"><span data-stu-id="130f9-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="130f9-119">依存関係</span><span class="sxs-lookup"><span data-stu-id="130f9-119">Dependencies</span></span>  
 <span data-ttu-id="130f9-120">[X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)も、同じオブジェクトに提供される必要があり、そのオブジェクトは XAML の運用環境のルート要素である必要があります。</span><span class="sxs-lookup"><span data-stu-id="130f9-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="130f9-121">コメント</span><span class="sxs-lookup"><span data-stu-id="130f9-121">Remarks</span></span>  
 <span data-ttu-id="130f9-122">`x:Subclass`使用状況は、主に、部分クラス宣言をサポートしない言語のものです。</span><span class="sxs-lookup"><span data-stu-id="130f9-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="130f9-123">として使用されるクラス、`x:Subclass`入れ子になったクラスにすることはできませんと`x:Subclass`「の依存関係」セクションで説明したように、ルート オブジェクトを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="130f9-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="130f9-124">それ以外の場合の概念の意味`x:Subclass`.NET Framework XAML サービス実装では未定義です。</span><span class="sxs-lookup"><span data-stu-id="130f9-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="130f9-125">これは、.NET Framework XAML サービスの動作にどの XAML マークアップおよびコードのバックアップを接続、全体的なプログラミング モデルが指定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="130f9-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="130f9-126">さらに概念の実装に関連する`x:Class`と`x:Subclass`プログラミング モデルまたはアプリケーションのモデルを使用して、XAML マークアップ、コンパイルされたマークアップ、および CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="130f9-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="130f9-127">各フレームワークには、いくつかの動作、またはビルド環境に含める必要がある特定のコンポーネントを有効にする、独自のビルド アクションがあります。</span><span class="sxs-lookup"><span data-stu-id="130f9-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="130f9-128">フレームワーク内でビルド アクションも異なります分離コードに使用される特定の CLR 言語。</span><span class="sxs-lookup"><span data-stu-id="130f9-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="130f9-129">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="130f9-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="130f9-130">`x:Subclass`ページのルートでまたはを指定できます、<xref:System.Windows.Application>を既に持っているアプリケーション定義のルート`x:Class`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="130f9-131">宣言`x:Subclass`ページまたはアプリケーションのルート、または、no を指定する以外の任意の要素で`x:Class`が存在し、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="130f9-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="130f9-132">その作業を正しく派生を作成するクラス、`x:Subclass`シナリオは非常に複雑です。</span><span class="sxs-lookup"><span data-stu-id="130f9-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="130f9-133">中間ファイル (プロジェクトの obj フォルダーの名前には、.xaml ファイル名と、マークアップ コンパイルによって生成される .g ファイル) を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="130f9-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="130f9-134">これらの中間ファイルは、コンパイルされたアプリケーションに参加している、部分クラスで特定のプログラミング構成要素の起点を特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="130f9-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="130f9-135">派生クラスでイベント ハンドラーがある必要があります`internal override`(`Friend Overrides`で[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) コンパイル時に中間クラスで作成されると、ハンドラーのスタブをオーバーライドするためにします。</span><span class="sxs-lookup"><span data-stu-id="130f9-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="130f9-136">それ以外の場合、派生クラスの実装には、(シャドウ)、中間クラスの実装が非表示にし、中間クラスのハンドラーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="130f9-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="130f9-137">両方を定義するときに`x:Class`と`x:Subclass`、によって参照されているクラスのすべての実装を提供する必要はありません`x:Class`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="130f9-138">のみを使用して名前を指定する必要があります、`x:Class`属性のコンパイラに中間ファイル (コンパイラ選択しません、既定の名前でも) で作成するクラスについてガイダンスを持つようにします。</span><span class="sxs-lookup"><span data-stu-id="130f9-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="130f9-139">付与できる、`x:Class`クラスの実装です。 ただし、これは、典型的なシナリオの両方を使用して`x:Class`と`x:Subclass`です。</span><span class="sxs-lookup"><span data-stu-id="130f9-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130f9-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="130f9-140">See Also</span></span>  
 [<span data-ttu-id="130f9-141">x:Class ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="130f9-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="130f9-142">WPF における XAML とカスタム クラス</span><span class="sxs-lookup"><span data-stu-id="130f9-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
