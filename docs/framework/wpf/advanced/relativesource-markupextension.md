---
title: "RelativeSource のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="3514e-102">RelativeSource のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="3514e-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="3514e-103">プロパティを指定します、<xref:System.Windows.Data.RelativeSource>内で使用する、バインド データ ソース、[バインディング マークアップ拡張](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)を設定する場合や、<xref:System.Windows.Data.Binding.RelativeSource%2A>のプロパティ、 <xref:System.Windows.Data.Binding> XAML で確立されている要素です。</span><span class="sxs-lookup"><span data-stu-id="3514e-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3514e-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="3514e-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="3514e-105">XAML 属性の使用方法 (バインディング拡張内で入れ子にした場合)</span><span class="sxs-lookup"><span data-stu-id="3514e-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="3514e-106">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="3514e-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3514e-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="3514e-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="3514e-108">次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="3514e-108">One of the following:</span></span><br /><br /> <span data-ttu-id="3514e-109">-文字列トークン`Self`; に対応する、<xref:System.Windows.Data.RelativeSource>で作成されると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.Self>です。</span><span class="sxs-lookup"><span data-stu-id="3514e-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="3514e-110">-文字列トークン`TemplatedParent`; に対応する、<xref:System.Windows.Data.RelativeSource>で作成されると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>です。</span><span class="sxs-lookup"><span data-stu-id="3514e-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="3514e-111">-文字列トークン`PreviousData`; に対応する、<xref:System.Windows.Data.RelativeSource>で作成されると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.PreviousData>です。</span><span class="sxs-lookup"><span data-stu-id="3514e-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="3514e-112">-は後述情報で`FindAncestor`モード。</span><span class="sxs-lookup"><span data-stu-id="3514e-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="3514e-113">文字列トークン `FindAncestor`。</span><span class="sxs-lookup"><span data-stu-id="3514e-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="3514e-114">このトークンを使用すると、`RelativeSource` によって先祖の型およびオプションで先祖レベルを指定するモードになります。</span><span class="sxs-lookup"><span data-stu-id="3514e-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="3514e-115">これは、<xref:System.Windows.Data.RelativeSource> プロパティが <xref:System.Windows.Data.RelativeSource.Mode%2A> に設定された状態で作成された <xref:System.Windows.Data.RelativeSourceMode.FindAncestor> に対応します。</span><span class="sxs-lookup"><span data-stu-id="3514e-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="3514e-116">`FindAncestor` モードで必要です。</span><span class="sxs-lookup"><span data-stu-id="3514e-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="3514e-117"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> プロパティに指定する型の名前。</span><span class="sxs-lookup"><span data-stu-id="3514e-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="3514e-118">`FindAncestor` モードのオプションです。</span><span class="sxs-lookup"><span data-stu-id="3514e-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="3514e-119">論理ツリー内で親の方向に向けて数えた先祖レベル。</span><span class="sxs-lookup"><span data-stu-id="3514e-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3514e-120">コメント</span><span class="sxs-lookup"><span data-stu-id="3514e-120">Remarks</span></span>  
 <span data-ttu-id="3514e-121">`{RelativeSource TemplatedParent}`バインディングでの使用は、コントロールの UI とコントロールのロジックの分離のより大きな概念に対応するキーの手法です。</span><span class="sxs-lookup"><span data-stu-id="3514e-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="3514e-122">これによって、テンプレートが適用される親 (テンプレートが適用されるランタイム オブジェクト インスタンス) へのバインディングをテンプレート定義内から行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3514e-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="3514e-123">この場合の[TemplateBinding マークアップ拡張機能](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)が実際には、次のバインド式の短縮形:`{Binding RelativeSource={RelativeSource TemplatedParent}}`です。</span><span class="sxs-lookup"><span data-stu-id="3514e-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="3514e-124">`TemplateBinding`または`{RelativeSource TemplatedParent}`の使用法が両方のテンプレートを定義する XAML 内でのみ関連します。</span><span class="sxs-lookup"><span data-stu-id="3514e-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="3514e-125">詳細については、次を参照してください[TemplateBinding マークアップ拡張機能。](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="3514e-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="3514e-126">`{RelativeSource FindAncestor}`場合、特定の先祖の種類のビジュアル ツリー内にあるコントロールが常に必要な場所でコントロール テンプレートまたは予測可能な自己完結型の UI コンポジション、主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3514e-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="3514e-127">たとえば、項目コントロールの各項目は `FindAncestor` を使用して、その項目コントロールの親先祖のプロパティにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="3514e-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="3514e-128">または、テンプレート内のコントロール合成に参加している要素は、同じ合成体系の親要素に対して `FindAncestor` バインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3514e-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="3514e-129">XAML 構文のセクションに示した `FindAncestor` モードのオブジェクト要素構文では、2 番目のオブジェクト要素構文は `FindAncestor` モード向けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="3514e-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="3514e-130">`FindAncestor` モードでは、<xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値が必要です。</span><span class="sxs-lookup"><span data-stu-id="3514e-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="3514e-131">設定する必要があります<xref:System.Windows.Data.RelativeSource.AncestorType%2A>を使用して、属性として、 [X:type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)検索する先祖の型への参照。</span><span class="sxs-lookup"><span data-stu-id="3514e-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="3514e-132"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値は、実行時にバインディング要求を処理する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3514e-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="3514e-133">`FindAncestor` モードでは、オプションの <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> プロパティは、要素ツリー内に型の先祖が複数存在する可能性がある場合に、先祖の検索のあいまいさを解消するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3514e-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="3514e-134">`FindAncestor` モードの使用方法の詳細については、「<xref:System.Windows.Data.RelativeSource>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3514e-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="3514e-135">`{RelativeSource Self}`シナリオに便利ですが、インスタンスの 1 つのプロパティは必要があります、同じインスタンスと一般的な依存関係プロパティ関係がない (強制型変換) などの別のプロパティの値に依存既にこれら 2 つのプロパティの間が存在します。</span><span class="sxs-lookup"><span data-stu-id="3514e-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="3514e-136">リテラルと同じです (と同じように型指定された) の値になるようオブジェクトに対して 2 つのプロパティが存在し、適用することもことはまれですが、`Converter`パラメーターになっているバインディングを`{RelativeSource Self}`ソースの間で変換するコンバーターを使用して、対象の種類。</span><span class="sxs-lookup"><span data-stu-id="3514e-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="3514e-137">別のシナリオとして`{RelativeSource Self}`の一部として、<xref:System.Windows.MultiDataTrigger>です。</span><span class="sxs-lookup"><span data-stu-id="3514e-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="3514e-138">たとえば、<xref:System.Windows.Shapes.Rectangle> という XAML は、<xref:System.Windows.FrameworkElement.Width%2A> 要素を定義します。<xref:System.Windows.Shapes.Rectangle> にどのような値が入力されても、`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>` は常に正方形となります。</span><span class="sxs-lookup"><span data-stu-id="3514e-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="3514e-139">`{RelativeSource PreviousData}`データ テンプレート、またはバインディングを使用しているコレクションのデータ ソースとしての場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3514e-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="3514e-140">使用することができます`{RelativeSource PreviousData}`をコレクション内の連続するデータ項目間のリレーションシップを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3514e-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="3514e-141">これと関連して、データ ソース内の現在の項目と直前の項目との間に <xref:System.Windows.Data.MultiBinding> を確立し、そのバインディング上のコンバーターを使用して、2 つの項目 (およびそれらのプロパティ) 間の相違を特定する手法もあります。</span><span class="sxs-lookup"><span data-stu-id="3514e-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="3514e-142">次の例の項目テンプレートに出現する 1 つ目の <xref:System.Windows.Controls.TextBlock> は、現在の数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="3514e-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="3514e-143">2 番目<xref:System.Windows.Controls.TextBlock>バインディングは、<xref:System.Windows.Data.MultiBinding>名目上のある 2 つ<xref:System.Windows.Data.Binding>consistuents: 現在のレコードと前のデータ レコードを使用して、意図的に使用するバインディング`{RelativeSource PreviousData}`です。</span><span class="sxs-lookup"><span data-stu-id="3514e-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="3514e-144"><xref:System.Windows.Data.MultiBinding> 上のコンバーターが、両者の差を計算し、バインディングに返します。</span><span class="sxs-lookup"><span data-stu-id="3514e-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 <span data-ttu-id="3514e-145">ここでは、概念が未カバーとしてデータ バインディングを記述するを参照してください[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="3514e-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="3514e-146">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.Data.RelativeSource>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3514e-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="3514e-147">`RelativeSource` はマークアップ拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="3514e-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="3514e-148">一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。</span><span class="sxs-lookup"><span data-stu-id="3514e-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="3514e-149">XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が、属性を処理する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字です。</span><span class="sxs-lookup"><span data-stu-id="3514e-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="3514e-150">詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。</span><span class="sxs-lookup"><span data-stu-id="3514e-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3514e-151">参照</span><span class="sxs-lookup"><span data-stu-id="3514e-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="3514e-152">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="3514e-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3514e-153">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3514e-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="3514e-154">マークアップ拡張機能と WPF XAML</span><span class="sxs-lookup"><span data-stu-id="3514e-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="3514e-155">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="3514e-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3514e-156">バインディング宣言の概要</span><span class="sxs-lookup"><span data-stu-id="3514e-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="3514e-157">x:Type マークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="3514e-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
