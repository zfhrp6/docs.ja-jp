---
title: バインドのマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 8fc860f52f8fde2aed3cae224c05bbcf08b864d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541886"
---
# <a name="binding-markup-extension"></a>バインドのマークアップ拡張機能
データ バインドされた値、中間式オブジェクトを作成して、要素と実行時にバインディングに適用されるデータ コンテキストを解釈するプロパティの値を延期します。  
  
## <a name="binding-expression-usage"></a>バインディング式の使用方法  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>構文のメモ  
 これらの構文、`[]`と`*`リテラルではありません。 示す表記の一部である 0 個以上*含む*`=`*値*のペアを使用すると、`,`それらと前の間の区切り記号*含む* `=`*値*ペア。  
  
 「バインド プロパティことができますされる設定と、バインド拡張機能」セクションに示すプロパティのいずれかの代わりに設定できるの属性を使用して、<xref:System.Windows.Data.Binding>オブジェクト要素。 ただし、外にある実際にマークアップ拡張機能の使用の<xref:System.Windows.Data.Binding>、一般的な CLR のプロパティを設定する属性の XAML 処理だけである<xref:System.Windows.Data.Binding>クラスです。 つまり、 `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*の値*`"]*/>`の属性と等価の構文は、<xref:System.Windows.Data.Binding>オブジェクトの要素の使用方法の代わりに、`Binding`式の使用。 特定のプロパティの XAML 属性の使用方法について学習する<xref:System.Windows.Data.Binding>の関連するプロパティの「XAML 属性の使用」を参照してください<xref:System.Windows.Data.Binding>.NET Framework クラス ライブラリです。  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|名前、<xref:System.Windows.Data.Binding>または<xref:System.Windows.Data.BindingBase>プロパティを設定します。 すべて<xref:System.Windows.Data.Binding>プロパティに設定することができます、`Binding`拡張機能、およびいくつかのプロパティは内で設定可能な`Binding`さらを使用してのみ式には、マークアップ拡張機能が入れ子になった。 参照してください「バインド プロパティことでく設定で、バインド拡張機能」セクションです。|  
|`value1, valueN`|プロパティを設定する値。 属性の値の処理は最終的には、型と、特定のロジックに固有<xref:System.Windows.Data.Binding>プロパティが設定されています。|  
|`path`|パスを設定する文字列、暗黙的な<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>プロパティです。 関連項目[PropertyPath XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)です。|  
  
## <a name="unqualified-binding"></a>非修飾 {バインディング}  
 `{Binding}` 「バインド式の使用」で表示される使用量を作成、<xref:System.Windows.Data.Binding>初期が含まれている既定値を持つオブジェクト<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>の`null`します。 これは、多くのシナリオにも便利ですので、作成した<xref:System.Windows.Data.Binding>など主要なデータ バインディングのプロパティに依存する可能性があります<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>と<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>実行時のデータ コンテキストに設定されています。 データ コンテキストの概念の詳細については、次を参照してください。[データ バインド](../../../../docs/framework/wpf/data/data-binding-wpf.md)です。  
  
## <a name="implicit-path"></a>暗黙のパス  
 `Binding`マークアップ拡張機能の使用<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>、概念として「既定のプロパティ」ここで、`Path=`式に出現する必要はありません。 指定した場合、`Binding`暗黙的なパスを持つ式は、暗黙的なパスは、式では、前に、他の最初で表示する必要があります`bindProp` = `value`場所のペアを<xref:System.Windows.Data.Binding>プロパティは名前によって指定します。 例:`{Binding PathString}`ここで、`PathString`の値に評価される文字列は、<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>で、<xref:System.Windows.Data.Binding>マークアップ拡張機能を使用して作成します。 たとえば、コンマ区切り記号の後の他の名前付きプロパティの暗黙のパスを追加できます`{Binding LastName, Mode=TwoWay}`です。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>バインドのバインド拡張機能で設定できるプロパティ  
 このトピックで示す構文は、ジェネリックを使用して`bindProp` = `value`近似値の多数の読み取り/書き込みプロパティがあるため<xref:System.Windows.Data.BindingBase>または<xref:System.Windows.Data.Binding>を通じてに設定できる、`Binding`マークアップ拡張機能/式の構文。 暗黙的なを除き、任意の順序で設定できます<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>です。 (明示的に指定するオプションが`Path=`、任意の順序で設定する場合)。 基本的で設定できます 0 個以上のプロパティの下の一覧を使用して`bindProp` = `value`ペアはコンマで区切っています。  
  
 これらのプロパティ値のいくつかが、XAML では、テキスト構文からのネイティブな型変換をサポートしていないため、属性値として設定するためにマークアップ拡張機能を必要なオブジェクト タイプが必要です。 XAML 属性の使用方法についてのセクションです。 詳細については、各プロパティの .NET Framework クラス ライブラリのは、XAML 属性の構文を使用する文字列またはマークアップ拡張機能をさらにせず使用状況は、基本的にで指定した値と同じ、`Binding`式をそれぞれを囲む引用符を置かない例外`bindProp` =`value`で、`Binding`式。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: バインド可能なグループを識別する文字列。 これは、バインディングの比較的高度な概念です。リファレンス ページを参照してください<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>です。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: として設定できる、 `bindProp` = `value`文字列式では、これを行うには参照が必要です、オブジェクトの値として、など、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。 ここでは、値は、カスタムのコンバーター クラスのインスタンスです。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: は標準に準拠した識別子として式で設定可能参照トピックを参照して<xref:System.Windows.Data.Binding.ConverterCulture%2A>です。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: として設定できる、 `bindProp` = `value` 、式が、この文字列が渡されるパラメーターの型に依存します。 この使用法が、入れ子になったなどのオブジェクト参照を必要と値の参照型を渡す場合[StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: と相互に排他的な<xref:System.Windows.Data.Binding.RelativeSource%2A>と<xref:System.Windows.Data.Binding.Source%2A>; 各これらのバインドのプロパティを表す特定のバインディング方法です。 参照してください[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: として設定できる、 `bindProp` = `value` 、式が、この文字列が渡される値の型に依存します。 入れ子になったなどのオブジェクト参照の参照型を渡すことが必要な場合[StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>:*値*の定数名には、<xref:System.Windows.Data.BindingMode>列挙します。 たとえば、`{Binding Mode=OneWay}` のようにします。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: データ オブジェクト、または一般的なオブジェクト モデルへのパスを表す文字列。 形式は、このトピックでは適切に記述できないオブジェクト モデルを走査することをいくつかの異なる規則を提供します。 参照してください[PropertyPath XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)です。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: ではなく相互に排他的<xref:System.Windows.Data.Binding.ElementName%2A>と<xref:System.Windows.Data.Binding.Source%2A>; 各これらのバインドのプロパティを表す特定のバインディング方法です。 参照してください[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。 必要、入れ子になった[RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)使用状況の値を指定します。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: と相互に排他的な<xref:System.Windows.Data.Binding.RelativeSource%2A>と<xref:System.Windows.Data.Binding.ElementName%2A>; 各これらのバインドのプロパティを表す特定のバインディング方法です。 参照してください[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。 通常、入れ子になった拡張機能の使用が必要です、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)キーを持つリソース ディクショナリからオブジェクト データ ソースを参照します。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: バインドされたデータの文字列形式の規則を説明する文字列。 これは、バインディングの比較的高度な概念です。リファレンス ページを参照してください<xref:System.Windows.Data.BindingBase.StringFormat%2A>です。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: として設定できる、 `bindProp` = `value` 、式が、この文字列が渡されるパラメーターの型に依存します。 入れ子になったなどのオブジェクト参照の値として、参照型を渡すことが必要な場合[StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*値*の定数名には、<xref:System.Windows.Data.UpdateSourceTrigger>列挙します。 たとえば、`{Binding UpdateSourceTrigger=LostFocus}` のようにします。 特定のコントロールには、このバインドのプロパティの既定値がある可能性があります。 「<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。 「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: ブール値、いずれかになります`true`または`false`です。 既定値は、`false` です。 「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: XML データ ソースの XMLDOM にパスを説明する文字列。 参照してください[、XMLDataProvider および XPath クエリを使用して XML データにバインド](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)です。  
  
 プロパティは、次のとおり<xref:System.Windows.Data.Binding>を使用してを設定することはできません、`Binding`マークアップ拡張機能/`{Binding}`式のフォームです。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: このプロパティはコールバックの実装に対する参照が必要です。 以外のイベント ハンドラーのコールバック/メソッドは、XAML 構文で参照できません。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: プロパティは、のジェネリック コレクションを受け取って<xref:System.Windows.Controls.ValidationRule>オブジェクト。 これは、プロパティ要素として表現でした、<xref:System.Windows.Data.Binding>オブジェクトの要素で使用するためすぐに使用できる属性の解析方法がありません、`Binding`式。 参照トピックを参照して<xref:System.Windows.Data.Binding.ValidationRules%2A>です。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位の観点から、`Binding`式がローカルで設定すると同じ値です。 プロパティを持っていたのローカル値を設定したかどうか、`Binding`式、`Binding`が完全に削除します。 詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
 基本的なレベルでのデータ バインディングについては、このトピックでは説明しません。 参照してください[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> および<xref:System.Windows.Data.PriorityBinding>サポートしていない、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]拡張構文です。 代わりに、プロパティ要素を使用します。 参照トピックをご覧ください<xref:System.Windows.Data.MultiBinding>と<xref:System.Windows.Data.PriorityBinding>です。  
  
 XAML のブール値は、大文字小文字を区別します。 たとえばするを指定するか`{Binding NotifyOnValidationError=true}`または`{Binding NotifyOnValidationError=True}`です。  
  
 データの検証が関係するバインディングは、通常明示的な指定`Binding`要素ではなく同様、`{Binding ...}`式、および設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>または<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>式では通常ありません。 これは、コンパニオン プロパティ<xref:System.Windows.Data.Binding.ValidationRules%2A>形式の式で簡単に設定することはできません。 詳細については、次を参照してください。[実装バインド検証](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)です。  
  
 `Binding` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するは、属性の値名、リテラル値やハンドラー以外にエスケープする必要があるし、要件が特定の型やプロパティに起因する型コンバーターよりも多くのグローバル場合。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が文字列の内容を処理する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字です。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
 `Binding` 非定型のマークアップ拡張機能を<xref:System.Windows.Data.Binding>WPF の XAML 実装の拡張機能を実装するクラスは、他のいくつかのメソッドと XAML に関連していないプロパティにも実装します。 他のメンバーがさせるものでは<xref:System.Windows.Data.Binding>汎用性と自己完結型のクラスで、XAML マークアップ拡張機能として機能しているだけでなく多くのデータ バインディングのシナリオに対処できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.Binding>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
