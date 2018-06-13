---
title: バインディング宣言の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: a8652648e1ac9da96a027f9aa56f0eee40cbaf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557213"
---
# <a name="binding-declarations-overview"></a>バインディング宣言の概要
このトピックでは、バインディングを宣言するさまざまな方法について説明します。  
  
 
  
<a name="Prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを読む前に、マークアップ拡張機能の概念と使用方法について理解している必要があります。 マークアップ拡張機能の詳細については、 「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 このトピックでは、データ バインディングの概念については説明しません。 データ バインディングの概念の詳細については、「[Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>XAML でのバインディングの宣言  
 このセクションでは、XAML でバインディングを宣言する方法について説明します。  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>マークアップ拡張機能の使用方法  
 <xref:System.Windows.Data.Binding> はマークアップ拡張機能です。 バインディング拡張機能を使用してバインディングを宣言するとき、この宣言は、`Binding` キーワードに続く一連の句で構成され、コンマ (,) で区切られます。 バインディング宣言内の句の順序は任意で、多数の組み合わせが可能です。 句は*名前*=*値*場所のペアを*名前*の名前を指定、<xref:System.Windows.Data.Binding>プロパティおよび*値*はプロパティを設定する値。  
  
 マークアップでバインディング宣言文字列を作成する場合、この文字列はターゲット オブジェクトの特定の依存関係プロパティにアタッチする必要があります。 次の例は、バインドする方法を示しています、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>プロパティを指定することをバインド拡張機能を使用して、<xref:System.Windows.Data.Binding.Source%2A>と<xref:System.Windows.Data.Binding.Path%2A>プロパティです。  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 ほとんどのプロパティを指定することができます、<xref:System.Windows.Data.Binding>クラスのこのようにします。 バインディング拡張は、の一覧の場合と同様の詳細については<xref:System.Windows.Data.Binding>バインド拡張機能を使用して設定することはできませんのプロパティを参照してください、[バインディング マークアップ拡張](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)の概要です。  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>オブジェクト要素構文  
 オブジェクト要素構文は、バインディング宣言を作成する代替の方法です。 ほとんどの場合は、マークアップ拡張機能の使用とオブジェクト要素構文の使用のどちらにも特別な利点はありません。 ただし、マークアップ拡張機能がサポートしないシナリオでは (プロパティ値が文字列タイプではなく、このタイプの変換が存在しない場合)、オブジェクト要素構文を使用する必要があります。  
  
 オブジェクト要素構文とマークアップ拡張機能の使用の両方の例を次に示します。  
  
 [!code-xaml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 例では、バインド、<xref:System.Windows.Controls.TextBlock.Foreground%2A>拡張構文を使用してバインドを宣言するプロパティです。 バインディングの宣言、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティがオブジェクト要素の構文を使用します。  
  
 別の用語の詳細については、「[XAML Syntax の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding と PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> および<xref:System.Windows.Data.PriorityBinding>XAML 拡張構文をサポートしていません。 宣言する場合はオブジェクト要素の構文を使用する必要がありますそのため、<xref:System.Windows.Data.MultiBinding>または<xref:System.Windows.Data.PriorityBinding>XAML でします。  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>コードでバインディングを作成する方法  
 バインドを指定する別の方法は、プロパティを設定する上で直接、<xref:System.Windows.Data.Binding>コード内のオブジェクト。 次の例を作成する方法を示しています、<xref:System.Windows.Data.Binding>オブジェクトし、コードでプロパティを指定します。  この例では`TheConverter`を実装するオブジェクトには、<xref:System.Windows.Data.IValueConverter>インターフェイスです。  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 バインドするオブジェクトがある場合、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>呼び出すことができます、`SetBinding`メソッドを使用せずに直接オブジェクトを<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>です。 例については、「[Create a Binding in Code](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)」を参照してください。  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>バインディング パス構文  
 使用して、<xref:System.Windows.Data.Binding.Path%2A>プロパティにバインドするソースの値を指定します。  
  
-   最も簡単なケースで、<xref:System.Windows.Data.Binding.Path%2A>プロパティの値などを使用して、バインディングのソース オブジェクトのプロパティの名前は、`Path=PropertyName`です。  
  
-   プロパティのサブプロパティは、c# の場合と同様の構文で指定できます。 たとえば、句 `Path=ShoppingCart.Order` は、バインディングをオブジェクトのサブプロパティ `Order` またはプロパティ `ShoppingCart` に設定します。  
  
-   添付プロパティにバインドするには、添付プロパティをかっこで囲みます。 例については、添付プロパティをバインドする<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>、構文は`Path=(DockPanel.Dock)`します。  
  
-   プロパティのインデクサーは、インデクサーが適用されているプロパティ名の後ろの角かっこ内に指定できます。 たとえば、句 `Path=ShoppingCart[0]` は、プロパティの内部インデックスがリテラル文字列「0」を処理する方法に対応するインデックスへのバインディングを設定します。 入れ子になったインデクサーもサポートします。  
  
-   `Path` 句ではインデクサーとサブプロパティを混在させることができます。例: `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   インデクサーの内側には、コンマ (,) で区切られた複数のインデクサー パラメーターを設定できます。 各パラメーターの型は、かっこで指定できます。 たとえば、ことが`Path="[(sys:Int32)42,(sys:Int32)24]"`ここで、`sys`にマップされて、`System`名前空間。  
  
-   ソース コレクション ビューがある場合は、スラッシュ (/) を現在の項目を指定できます。 たとえば、この句`Path=/`ビューの現在のアイテムにバインディングを設定します。 ソースがコレクションである場合は、この構文は、既定のコレクション ビューの現在の項目を指定します。  
  
-   プロパティは、コレクションを走査するプロパティの名前とスラッシュを組み合わせることができます。 たとえば、`Path=/Offices/ManagerName`を含むソース コレクションの現在の項目を指定します、`Offices`コレクションであるプロパティ。 現在のアイテムが格納しているオブジェクト、`ManagerName`プロパティです。  
  
-   必要に応じて、現在のソースにバインドする、ピリオド (.) のパスを使用できます。 たとえば、`Text="{Binding}"` は、`Text="{Binding Path=.}"` と同じです。  
  
### <a name="escaping-mechanism"></a>エスケープのしくみ  
  
-   インデクサー ([ ]) 内では、キャレット文字 (^) は次の文字をエスケープします。  
  
-   設定した場合<xref:System.Windows.Data.Binding.Path%2A>XAML では、する必要があります XML 言語の定義には特定の文字エスケープ (XML エンティティを使用)。  
  
    -   文字 "&" をエスケープするには、`&` を使用します。  
  
    -   使用する`>`終了タグをエスケープする">"です。  
  
-   さらに、マークアップ拡張構文を使用して属性のバインディング全体を記述する場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マークアップ拡張機能パーサーで特別な意味を持つ文字を (円記号 \\ を使用して) エスケープする必要があります。  
  
    -   円記号 (\\) はエスケープ文字そのものです。  
  
    -   等号 (=) は、プロパティ名とプロパティの値を区切ります。  
  
    -   コンマ (,) はプロパティを区切ります。  
  
    -   右中かっこ (}) は、マークアップ拡張機能の終わりです。  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>既定の動作  
 既定の動作は、宣言で指定されていない場合には次のとおりです。  
  
-   バインディング ソースの値とバインディング ターゲットの値の型変換を実行しようとする既定のコンバーターが作成されます。 変換を実行できない場合、既定のコンバーターは `null` を返します。  
  
-   設定しない場合<xref:System.Windows.Data.Binding.ConverterCulture%2A>、バインド エンジンを使用して、`Language`バインディング ターゲット オブジェクトのプロパティです。 XAML では、既定で "en-US" になるか、または明示的に設定されている場合にはページのルート要素 (または任意の要素) から値を継承します。  
  
-   バインディングに既にデータ コンテキスト (たとえば、親要素から継承したデータ コンテキスト) があり、そのコンテキストによって返される項目またはコンテキストが何であれ、それがさらにパスを変更せずにバインディングすることについて適切である限り、バインディング宣言は句を持つことができません。`{Binding}`これは、多くの場合、データのスタイルに対してバインディングを指定する方法で、バインディングはコレクションに基づいて動作します。 詳細については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」の「バインディング ソースとして使用する全体オブジェクト」セクションを参照してください。  
  
-   既定値<xref:System.Windows.Data.Binding.Mode%2A>は一方向、バインドされている依存関係プロパティによっては双方向の間で変化します。 常にバインディング モードを明示的に宣言し、バインディングに目的の動作があることを確認できます。 一般に、ユーザーが編集できるコントロールのプロパティでなど<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>と<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>、双方向のバインディングでは、既定であり、その他のほとんどのプロパティは既定で一方向のバインド。  
  
-   既定値<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値によって異なります<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>と<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>も、バインドされた依存関係プロパティによって異なります。 ほとんどの依存関係プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> です。ただし、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> です。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [PropertyPath の XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)
