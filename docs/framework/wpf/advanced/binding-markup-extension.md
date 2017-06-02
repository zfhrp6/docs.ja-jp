---
title: "バインドのマークアップ拡張機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Binding"
helpviewer_keywords: 
  - "バインディングのマークアップ拡張機能"
  - "XAML, バインディングのマークアップ拡張機能"
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# バインドのマークアップ拡張機能
プロパティ値を、データ バインドされた値として指定できるようにします。中間の式オブジェクトを作成し、実行時に要素とそのバインディングに適用されるデータ コンテキストを解釈します。  
  
## Binding 式の使用方法  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## 構文についてのメモ  
 これらの構文の `[]` と `*` は、リテラルではありません。  0 個以上の *bindProp*`=`*value* ペアを使用できることを示す表記法の一部です。先行する *bindProp*`=`*value* ペアとの区切り記号には `,` が使用されます。  
  
 「バインディング拡張で設定できるバインディング プロパティ」に示すプロパティはいずれも、<xref:System.Windows.Data.Binding> オブジェクト要素の属性を使用して設定することもできます。  ただしそれは、実際には <xref:System.Windows.Data.Binding> のマークアップ拡張機能の使用方法ではなく、CLR <xref:System.Windows.Data.Binding> クラスのプロパティを設定する属性の一般的な XAML 処理にすぎません。  つまり、`<Binding` *bindProp1*`="`*value1*`"[` *bindPropN*`="`*valueN*`"]*/>` は、`Binding` 式の使用方法ではなく、<xref:System.Windows.Data.Binding> オブジェクト要素の属性を使用した同等の構文です。  <xref:System.Windows.Data.Binding> の特定のプロパティの XAML 属性の使用方法の詳細については、.NET Framework クラス ライブラリで、<xref:System.Windows.Data.Binding> の該当するプロパティの「XAML 属性の使用方法」を参照してください。  
  
## XAML 値  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|設定対象の <xref:System.Windows.Data.Binding> プロパティまたは <xref:System.Windows.Data.BindingBase> プロパティの名前。  <xref:System.Windows.Data.Binding> のすべてのプロパティを `Binding` 拡張を使用して設定できるとは限りません。また、プロパティによっては、マークアップ拡張機能をさらに入れ子にしなければ `Binding` 式の中では設定できません。  「バインディング拡張で設定できるバインディング プロパティ」を参照してください。|  
|`value1, valueN`|プロパティに設定する値。  属性値の処理は、最終的には、設定される特定の <xref:System.Windows.Data.Binding> プロパティの型とロジックによって決まります。|  
|`path`|暗黙的な <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> プロパティを設定するパス文字列。  [PropertyPath の XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md) も参照してください。|  
  
## 非修飾の {Binding}  
 「Binding 式の使用方法」に示した `{Binding}` という使用方法では、既定値 \(`null` の初期値 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> など\) を使用して <xref:System.Windows.Data.Binding> オブジェクトが作成されます。  それでも、さまざまなシナリオで役に立ちます。作成される <xref:System.Windows.Data.Binding> は、実行時のデータ コンテキストで設定される主要なデータ バインディング プロパティ \(<xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> や <xref:System.Windows.Data.Binding.Source%2A?displayProperty=fullName> など\) に依存する可能性があるためです。  データ コンテキストの概念の詳細については、「[データ バインディング](../../../../docs/framework/wpf/data/data-binding-wpf.md)」を参照してください。  
  
## 暗黙のパス  
 `Binding` マークアップ拡張機能では、<xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> を概念的な "既定のプロパティ" として使用します。そのため、`Path=` を式で指定する必要はありません。  暗黙的なパスを含む `Binding` 式を指定する場合は、その暗黙的なパスを式で最初に \(<xref:System.Windows.Data.Binding> プロパティを名前で指定する他の `bindProp`\=`value` ペアより先に\) 指定する必要があります   \(例: `{Binding PathString}` \(`PathString` は、マークアップ拡張機能の使用方法によって作成される <xref:System.Windows.Data.Binding> の <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> の値に評価される文字列\)\)。  暗黙のパスの後に、他の名前付きプロパティをコンマで区切って追加することもできます。たとえば、`{Binding LastName, Mode=TwoWay}` のように指定します。  
  
## バインディング拡張で設定できるバインディング プロパティ  
 ここに示す構文では、`bindProp`\=`value` という一般的な形式を使用します。`Binding` マークアップ拡張機能\/式の構文を使用して設定可能な、<xref:System.Windows.Data.BindingBase> や <xref:System.Windows.Data.Binding> の読み書き可能なプロパティは多数あるためです。  暗黙的な <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> 以外は、設定する順序は自由です   \(`Path=` を明示的に指定することもできます。その場合は、このプロパティを自由な順序で設定できます\)。  基本的に、下の一覧に示したプロパティのうち 0 個以上を、`bindProp`\=`value` ペアの形式で、コンマで区切って設定します。  
  
 これらのプロパティ値のいくつかは、要求しているオブジェクト型が XAML のテキスト構文からのネイティブ型変換をサポートしていないので、さらに属性値として設定するためにマークアップ拡張機能が必要です。  詳細については、.NET Framework クラス ライブラリで各プロパティの「XAML 属性の使用方法」を参照してください。さらなるマークアップ拡張機能の使用を含む場合も含まない場合も、XAML 属性構文で使用する文字列は、`Binding` 式で指定する値と基本的に同じです。違いは、`Binding` 式では各 `bindProp`\=`value` を引用符で囲まないことだけです。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: バインディング グループの候補を示す文字列。  これは比較的高度なバインディング概念です。詳細については、<xref:System.Windows.Data.BindingBase.BindingGroupName%2A> のリファレンス ページを参照してください。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: ブール値。`true` と `false` のいずれかです。  既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: `bindProp`\=`value` の文字列として式で設定できますが、そのためには値のオブジェクト参照 \([StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)など\) が必要です。  この場合の値は、カスタム コンバーター クラスのインスタンスです。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: 標準ベースの識別子として式で設定できます。<xref:System.Windows.Data.Binding.ConverterCulture%2A> のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: `bindProp`\=`value` の文字列として式で設定できますが、渡されるパラメーターの型に依存します。  値に参照型を渡す場合、この使用方法では入れ子になった [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: このプロパティと <xref:System.Windows.Data.Binding.RelativeSource%2A> および <xref:System.Windows.Data.Binding.Source%2A> は同時に使用できません。これらの各バインディング プロパティは特定のバインディング方法を表します。  「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: `bindProp`\=`value` の文字列として式で設定できますが、渡される値の型に依存します。  参照型を渡す場合は、入れ子になった [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: ブール値。`true` と `false` のいずれかです。  既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *value* は <xref:System.Windows.Data.BindingMode> 列挙体の定数名です。  たとえば、`{Binding Mode=OneWay}` のようにします。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: ブール値。`true` または `false` のいずれかです。  既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: ブール値。`true` と `false` のいずれかです。  既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: ブール値。`true` または `false` のいずれかです。  既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: データ オブジェクトまたは汎用オブジェクト モデルへのパスを表す文字列。  ここで詳しく説明することはできませんが、この形式は、オブジェクト モデルを走査するための複数の異なる規約に対応しています。  「[PropertyPath の XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: このプロパティと <xref:System.Windows.Data.Binding.ElementName%2A> および <xref:System.Windows.Data.Binding.Source%2A> は同時に使用できません。これらの各バインディング プロパティは特定のバインディング方法を表します。  「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  値を指定するには、入れ子になった [RelativeSource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)の使用が必要です。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: このプロパティと <xref:System.Windows.Data.Binding.RelativeSource%2A> および <xref:System.Windows.Data.Binding.ElementName%2A> は同時に使用できません。これらの各バインディング プロパティは特定のバインディング方法を表します。  「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  入れ子になった拡張機能の使用 \(通常は、キーを持つリソース ディクショナリのオブジェクト データ ソースを参照する [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)\) が必要です。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: バインドされたデータの文字列書式指定規則を表す文字列。  これは比較的高度なバインディング概念です。詳細については、<xref:System.Windows.Data.BindingBase.StringFormat%2A> のリファレンス ページを参照してください。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: `bindProp`\=`value` の文字列として式で設定できますが、渡されるパラメーターの型に依存します。  値に参照型を渡す場合は、入れ子になった [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *value* は <xref:System.Windows.Data.UpdateSourceTrigger> 列挙体の定数名です。  たとえば、`{Binding UpdateSourceTrigger=LostFocus}` のようにします。  特定のコントロールには、このバインディング プロパティに対して別の既定値がある可能性があります。  「<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: ブール値。`true` と `false` のいずれかです。  既定値は、`false` です。  「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: ブール値。`true` と `false` のいずれかです。  既定値は、`false` です。  「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: XML データ ソースの XMLDOM へのパスを表す文字列。  「[XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。  
  
 次に示す <xref:System.Windows.Data.Binding> のプロパティは、`Binding` マークアップ拡張機能\/`{Binding}` 式の形式を使用して設定することはできません。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: このプロパティには、コールバック実装への参照が必要です。  コールバック\/イベント ハンドラー以外のメソッドは、XAML 構文で参照できません。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: このプロパティは、<xref:System.Windows.Controls.ValidationRule> オブジェクトのジェネリック コレクションを受け取ります。  <xref:System.Windows.Data.Binding> オブジェクト要素のプロパティ要素として表現することもできますが、`Binding` 式ですぐに使用できる属性解析方法がありません。  <xref:System.Windows.Data.Binding.ValidationRules%2A> のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## 解説  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位という点では、`Binding` 式はローカルで設定される値と同等です。  `Binding` 式を持っているプロパティに対してローカル値を設定すると、`Binding` は完全に削除されます。  詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
 ここでは、基本レベルでのデータ バインディングについては説明しません。  「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> および <xref:System.Windows.Data.PriorityBinding> は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 拡張構文をサポートしません。代わりに、プロパティ要素を使用します。  <xref:System.Windows.Data.MultiBinding> および <xref:System.Windows.Data.PriorityBinding> のリファレンス トピックを参照してください。  
  
 XAML のブール値は、大文字と小文字を区別しません。  たとえば、`{Binding NotifyOnValidationError=true}` または `{Binding NotifyOnValidationError=True}` のように指定できます。  
  
 通常、データ検証を伴うバインディングは、`{Binding ...}` 式としてではなく、明示的な `Binding` 要素で指定され、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> または <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> を式で設定することは一般的ではありません。  これは、コンパニオン プロパティである <xref:System.Windows.Data.Binding.ValidationRules%2A> を式の形式で容易に設定できないためです。  詳細については、「[バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)」を参照してください。  
  
 `Binding` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに属性が追加される型コンバーターにとどまらない場合です。  XAML のすべてのマークアップ拡張機能では、それぞれの属性構文で `{` と `}` の 2 つの記号を使用します。これは規約であり、これに従って XAML プロセッサは、マークアップ拡張機能で文字列の内容を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 `Binding` が他のマークアップ拡張機能と異なる点は、WPF の XAML 実装のこの拡張機能を実装する <xref:System.Windows.Data.Binding> クラスが、XAML に関連しないその他のいくつかのメソッドやプロパティも実装することです。  他のメンバーの目的は、<xref:System.Windows.Data.Binding> を汎用性の高い、自己完結型のクラスにすることです。これによって、XAML マークアップ拡張機能としての機能に加え、さまざまなデータ バインディング シナリオに対応できるようになります。  
  
## 参照  
 <xref:System.Windows.Data.Binding>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)