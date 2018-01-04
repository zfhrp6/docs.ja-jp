---
title: "コレクション型依存関係プロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e572bf7d404d0d824d3127789190ce81d4c98998
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="collection-type-dependency-properties"></a><span data-ttu-id="325ab-102">コレクション型依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="325ab-102">Collection-Type Dependency Properties</span></span>
<span data-ttu-id="325ab-103">ここでは、プロパティの型がコレクション型である場合に依存関係プロパティを実装する方法についての、ガイダンスと推奨されるパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="325ab-103">This topic provides guidance and suggested patterns for how to implement a dependency property where the type of the property is a collection type.</span></span>  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a><span data-ttu-id="325ab-104">コレクション型依存関係プロパティの実装</span><span class="sxs-lookup"><span data-stu-id="325ab-104">Implementing a Collection-Type Dependency Property</span></span>  
 <span data-ttu-id="325ab-105">依存関係プロパティの一般に、実装されるパターンに従う必要ですを定義すること、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティのラッパーをそのプロパティが支えられた、<xref:System.Windows.DependencyProperty>識別子ではなく、フィールドまたは別のコンストラクト。</span><span class="sxs-lookup"><span data-stu-id="325ab-105">For a dependency property in general, the implementation pattern that you follow is that you define a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrapper, where that property is backed by a <xref:System.Windows.DependencyProperty> identifier rather than a field or other construct.</span></span> <span data-ttu-id="325ab-106">コレクション型プロパティを実装するときは、これと同じパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="325ab-106">You follow this same pattern when you implement a collection-type property.</span></span> <span data-ttu-id="325ab-107">ただし、コレクション型のプロパティ複雑にいくつかのパターンに、コレクション内に含まれる型自体がされるたびに、<xref:System.Windows.DependencyObject>または<xref:System.Windows.Freezable>クラスを派生します。</span><span class="sxs-lookup"><span data-stu-id="325ab-107">However, a collection-type property introduces some complexity to the pattern whenever the type that is contained within the collection is itself a <xref:System.Windows.DependencyObject> or <xref:System.Windows.Freezable> derived class.</span></span>  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a><span data-ttu-id="325ab-108">既定値を上回るコレクションの初期化</span><span class="sxs-lookup"><span data-stu-id="325ab-108">Initializing the Collection Beyond the Default Value</span></span>  
 <span data-ttu-id="325ab-109">依存関係プロパティを作成するときは、初期フィールド値としてプロパティの既定値を指定しません。</span><span class="sxs-lookup"><span data-stu-id="325ab-109">When you create a dependency property, you do not specify the property default value as the initial field value.</span></span> <span data-ttu-id="325ab-110">代わりに、依存関係プロパティのメタデータを使用して既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="325ab-110">Instead, you specify the default value through the dependency property metadata.</span></span> <span data-ttu-id="325ab-111">プロパティが参照型の場合、依存関係プロパティのメタデータで指定する既定値はインスタンスごとの既定値ではありません。その型のすべてのインスタンスに適用される既定値です。</span><span class="sxs-lookup"><span data-stu-id="325ab-111">If your property is a reference type, the default value specified in dependency property metadata is not a default value per instance; instead it is a default value that applies to all instances of the type.</span></span> <span data-ttu-id="325ab-112">したがって、コレクション プロパティ メタデータによって定義される単一の静的コレクションを、その型の新しく作成されるインスタンスの作業既定値として使用しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="325ab-112">Therefore you must be careful to not use the singular static collection defined by the collection property metadata as the working default value for newly created instances of your type.</span></span> <span data-ttu-id="325ab-113">代わりに、クラス コンストラクターのロジックの一部として、コレクションの値に一意 (インスタンス) のコレクションを意図的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="325ab-113">Instead, you must make sure that you deliberately set the collection value to a unique (instance) collection as part of your class constructor logic.</span></span> <span data-ttu-id="325ab-114">それ以外の場合は、意図しないシングルトン クラスを作成することになります。</span><span class="sxs-lookup"><span data-stu-id="325ab-114">Otherwise you will have created an unintentional singleton class.</span></span>  
  
 <span data-ttu-id="325ab-115">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="325ab-115">Consider the following example.</span></span> <span data-ttu-id="325ab-116">この例は、`Aquarium` クラスの定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="325ab-116">The following section of the example shows the definition for a class `Aquarium`.</span></span> <span data-ttu-id="325ab-117">クラスは、コレクション型の依存関係プロパティを定義`AquariumObjects`、ジェネリックを使用する<xref:System.Collections.Generic.List%601>を持つ型、<xref:System.Windows.FrameworkElement>制約を入力します。</span><span class="sxs-lookup"><span data-stu-id="325ab-117">The class defines the collection type dependency property `AquariumObjects`, which uses the generic <xref:System.Collections.Generic.List%601> type with a <xref:System.Windows.FrameworkElement> type constraint.</span></span> <span data-ttu-id="325ab-118"><xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>メタデータに、依存関係プロパティの呼び出しによって確立、既定値を新しいジェネリック<xref:System.Collections.Generic.List%601>です。</span><span class="sxs-lookup"><span data-stu-id="325ab-118">In the <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> call for the dependency property, the metadata establishes the default value to be a new generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 <span data-ttu-id="325ab-119">ただし、コードをこのままにすると、単一のリストの既定値が `Aquarium` のすべてのインスタンスで共有されます。</span><span class="sxs-lookup"><span data-stu-id="325ab-119">However, if you just left the code as shown, that single list default value is shared for all instances of `Aquarium`.</span></span> <span data-ttu-id="325ab-120">次のテスト コードは、2 つの異なる `Aquarium` インスタンスをインスタンス化し、それぞれに単一の異なる `Fish` を追加する方法を示していますが、これを実行すると、想定外の結果になります。</span><span class="sxs-lookup"><span data-stu-id="325ab-120">If you ran the following test code, which is intended to show how you would instantiate two separate `Aquarium` instances and add a single different `Fish` to each of them, you would see a surprising result:</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 <span data-ttu-id="325ab-121">各コレクションのカウントが 1 になるのではなく、いずれのコレクションもカウントが 2 になります。</span><span class="sxs-lookup"><span data-stu-id="325ab-121">Instead of each collection having a count of one, each collection has a count of two!</span></span> <span data-ttu-id="325ab-122">これは、各 `Aquarium` で `Fish` が既定値のコレクションに追加されますが、その起因となっているのがメタデータでの単一のコンストラクター呼び出しであり、したがって、すべてのインスタンス間で共有されるためです。</span><span class="sxs-lookup"><span data-stu-id="325ab-122">This is because each `Aquarium` added its `Fish` to the default value collection, which resulted from a single constructor call in the metadata and is therefore shared between all instances.</span></span> <span data-ttu-id="325ab-123">これは望ましい状況ではありません。</span><span class="sxs-lookup"><span data-stu-id="325ab-123">This situation is almost never what you want.</span></span>  
  
 <span data-ttu-id="325ab-124">この問題を解決するには、クラス コンストラクターの呼び出しの一部として、コレクションの依存関係プロパティの値を一意のインスタンスにリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="325ab-124">To correct this problem, you must reset the collection dependency property value to a unique instance, as part of the class constructor call.</span></span> <span data-ttu-id="325ab-125">プロパティが読み取り専用の依存関係プロパティを使用する、<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>メソッドを使用して、設定を<xref:System.Windows.DependencyPropertyKey>ことのみがアクセスできる、クラス内で。</span><span class="sxs-lookup"><span data-stu-id="325ab-125">Because the property is a read-only dependency property, you use the <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> method to set it, using the <xref:System.Windows.DependencyPropertyKey> that is only accessible within the class.</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 <span data-ttu-id="325ab-126">再びテスト コードを実行すると、結果は期待したものに近くなり、各 `Aquarium` が独自の一意のコレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="325ab-126">Now, if you ran that same test code again, you could see more expected results, where each `Aquarium` supported its own unique collection.</span></span>  
  
 <span data-ttu-id="325ab-127">コレクション プロパティを読み取り/書き込みにすると、このパターンには若干のバリエーションが発生します。</span><span class="sxs-lookup"><span data-stu-id="325ab-127">There would be a slight variation on this pattern if you chose to have your collection property be read-write.</span></span> <span data-ttu-id="325ab-128">その場合が非キーの署名を呼び出すことも、初期化を行うには、コンス トラクターからパブリック set アクセサーを呼び出すことが<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>、セットのラッパー内でパブリックを使用して<xref:System.Windows.DependencyProperty>識別子。</span><span class="sxs-lookup"><span data-stu-id="325ab-128">In that case, you could call the public set accessor from the constructor to do the initialization, which would still be calling the nonkey signature of <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> within your set wrapper, using a public <xref:System.Windows.DependencyProperty> identifier.</span></span>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a><span data-ttu-id="325ab-129">コレクション プロパティからのバインディング値変更の報告</span><span class="sxs-lookup"><span data-stu-id="325ab-129">Reporting Binding Value Changes from Collection Properties</span></span>  
 <span data-ttu-id="325ab-130">それ自体が依存関係プロパティであるコレクション プロパティは、変更をサブプロパティに自動的には報告しません。</span><span class="sxs-lookup"><span data-stu-id="325ab-130">A collection property that is itself a dependency property does not automatically report changes to its subproperties.</span></span> <span data-ttu-id="325ab-131">コレクションにバインディングを作成している場合は、これによってバインディングが変更を報告しないことがあり、一部のデータ バインディング シナリオが無効になります。</span><span class="sxs-lookup"><span data-stu-id="325ab-131">If you are creating bindings into a collection, this can prevent the binding from reporting changes, thus invalidating some data binding scenarios.</span></span> <span data-ttu-id="325ab-132">ただし、コレクション型を使用する場合<xref:System.Windows.FreezableCollection%601>コレクションの種類として、コレクション内に含まれる要素のサブプロパティ変更正しくが報告され、バインドが期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="325ab-132">However, if you use the collection type <xref:System.Windows.FreezableCollection%601> as your collection type, then subproperty changes to contained elements in the collection are properly reported, and binding works as expected.</span></span>  
  
 <span data-ttu-id="325ab-133">依存関係オブジェクトのコレクション内のサブプロパティのバインディングを有効にするプロパティの作成、コレクション型として<xref:System.Windows.FreezableCollection%601>、いずれかにそのコレクションの型制約が設定された<xref:System.Windows.DependencyObject>クラスを派生します。</span><span class="sxs-lookup"><span data-stu-id="325ab-133">To enable subproperty binding in a dependency object collection, create the collection property as type <xref:System.Windows.FreezableCollection%601>, with a type constraint for that collection to any <xref:System.Windows.DependencyObject> derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325ab-134">参照</span><span class="sxs-lookup"><span data-stu-id="325ab-134">See Also</span></span>  
 <xref:System.Windows.FreezableCollection%601>  
 [<span data-ttu-id="325ab-135">WPF における XAML とカスタム クラス</span><span class="sxs-lookup"><span data-stu-id="325ab-135">XAML and Custom Classes for WPF</span></span>](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [<span data-ttu-id="325ab-136">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="325ab-136">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="325ab-137">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="325ab-137">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="325ab-138">カスタム依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="325ab-138">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="325ab-139">依存関係プロパティのメタデータ</span><span class="sxs-lookup"><span data-stu-id="325ab-139">Dependency Property Metadata</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
