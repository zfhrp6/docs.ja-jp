---
title: "RelativeSource のマークアップ拡張機能 | Microsoft Docs"
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
  - "RelativeSource"
helpviewer_keywords: 
  - "RelativeSource のマークアップ拡張機能"
  - "XAML, RelativeSource マークアップ拡張機能"
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# RelativeSource のマークアップ拡張機能
[バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)内で使用されるか、または XAML で設定された <xref:System.Windows.Data.Binding> 要素の <xref:System.Windows.Data.Binding.RelativeSource%2A> プロパティの設定時に使用される、<xref:System.Windows.Data.RelativeSource> バインディング ソースのプロパティを指定します。  
  
## XAML 属性の使用方法  
  
```  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## XAML 属性の使用方法 \(バインディング拡張内で入れ子にした場合\)  
  
```  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## XAML オブジェクト要素の使用方法  
  
```  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`modeEnumValue`|次のいずれかになります。<br /><br /> -   文字列トークン `Self`。<xref:System.Windows.Data.RelativeSource> に対応し、<xref:System.Windows.Data.RelativeSource.Mode%2A> プロパティは <xref:System.Windows.Data.RelativeSourceMode> に設定されます。<br />-   文字列トークン `TemplatedParent`。<xref:System.Windows.Data.RelativeSource> に対応し、<xref:System.Windows.Data.RelativeSource.Mode%2A> プロパティは <xref:System.Windows.Data.RelativeSourceMode> に設定されます。<br />-   文字列トークン `PreviousData`。<xref:System.Windows.Data.RelativeSource> に対応し、<xref:System.Windows.Data.RelativeSource.Mode%2A> プロパティは <xref:System.Windows.Data.RelativeSourceMode> に設定されます。<br />-   `FindAncestor` については、以下を参照してください。|  
|`FindAncestor`|文字列トークン `FindAncestor`。  このトークンを使用すると、`RelativeSource` によって先祖の型およびオプションで先祖レベルを指定するモードになります。  これは、<xref:System.Windows.Data.RelativeSource.Mode%2A> プロパティが <xref:System.Windows.Data.RelativeSourceMode> に設定された状態で作成された <xref:System.Windows.Data.RelativeSource> に対応します。|  
|`typeName`|`FindAncestor` モードで必要です。  <xref:System.Windows.Data.RelativeSource.AncestorType%2A> プロパティに指定する型の名前。|  
|`intLevel`|`FindAncestor` モードのオプションです。  論理ツリー内で親の方向に向けて数えた先祖レベル。|  
  
## 解説  
 `{RelativeSource TemplatedParent}` バインディングの用法は、コントロールの UI とロジックを分離するという、より大きな構想を解決するための鍵となる手法です。  これによって、テンプレートが適用される親 \(テンプレートが適用されるランタイム オブジェクト インスタンス\) へのバインディングをテンプレート定義内から行うことができます。  この場合、[TemplateBinding のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) は、実際には、`{Binding RelativeSource={RelativeSource TemplatedParent}}` というバインディング式を略したものです。  `TemplateBinding` と `{RelativeSource TemplatedParent}` の使用法はどちらも、テンプレートを定義する XAML 内でのみ意味を持ちます。  詳細については、「[TemplateBinding のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)」を参照してください。  
  
 `{RelativeSource FindAncestor}` の主な用途は、コントロール テンプレート内または予測可能な独立した UI 合成です。特定の先祖の型のビジュアル ツリー内にコントロールが常に存在することがわかっているケースで使用されます。  たとえば、項目コントロールの各項目は `FindAncestor` を使用して、その項目コントロールの親先祖のプロパティにバインドすることができます。  または、テンプレート内のコントロール合成に参加している要素は、同じ合成体系の親要素に対して `FindAncestor` バインディングを使用できます。  
  
 XAML 構文のセクションに示した `FindAncestor` モードのオブジェクト要素構文では、2 番目のオブジェクト要素構文は `FindAncestor` モード向けに使用されます。  `FindAncestor` モードでは、<xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値が必要です。  検索する先祖の型への [x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)参照を使用して、<xref:System.Windows.Data.RelativeSource.AncestorType%2A> を属性として設定する必要があります。  <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値は、実行時にバインディング要求を処理する際に使用されます。  
  
 `FindAncestor` モードでは、オプションの <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> プロパティは、要素ツリー内に型の先祖が複数存在する可能性がある場合に、先祖の検索のあいまいさを解消するのに役立ちます。  
  
 `FindAncestor` モードの使用方法の詳細については、「<xref:System.Windows.Data.RelativeSource>」を参照してください。  
  
 `{RelativeSource Self}` は、特定のインスタンスのプロパティが同じインスタンスの別のプロパティの値に依存しており、その 2 つのプロパティ間に通常の依存関係プロパティの関係 \(強制変換など\) が存在しない状況で活用できます。  まったく同じ値、まったく同じ型を持つ 2 つのプロパティが 1 つのオブジェクトに存在することはまれですが、`{RelativeSource Self}` を持つバインディングに `Converter` パラメーターを適用し、そのコンバーターを使用してソースとターゲットの型変換を行うこともできます。  `{RelativeSource Self}` は、<xref:System.Windows.MultiDataTrigger> の一部として活用することもできます。  
  
 たとえば、`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>` という XAML は、<xref:System.Windows.Shapes.Rectangle> 要素を定義します。<xref:System.Windows.FrameworkElement.Width%2A> にどのような値が入力されても、<xref:System.Windows.Shapes.Rectangle> は常に正方形となります。  
  
 `{RelativeSource PreviousData}` は、データ テンプレートで活用できるほか、バインディングにデータ ソースのコレクションを使用する場合にも役立ちます。  `{RelativeSource PreviousData}` を使用すると、コレクション内の隣接するデータ項目どうしの関係に注目することができます。  これと関連して、データ ソース内の現在の項目と直前の項目との間に <xref:System.Windows.Data.MultiBinding> を確立し、そのバインディング上のコンバーターを使用して、2 つの項目 \(およびそれらのプロパティ\) 間の相違を特定する手法もあります。  
  
 次の例の項目テンプレートに出現する 1 つ目の <xref:System.Windows.Controls.TextBlock> は、現在の数値を表示します。  2 つ目の <xref:System.Windows.Controls.TextBlock> バインディングは、<xref:System.Windows.Data.MultiBinding> で、通常 2 つの <xref:System.Windows.Data.Binding> 構成要素を持ちます \(現在のレコードと、`{RelativeSource PreviousData}` を使用して直前のデータ レコードを意図的に使用するバインディング\)。  <xref:System.Windows.Data.MultiBinding> 上のコンバーターが、両者の差を計算し、バインディングに返します。  
  
```  
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
  
 ここで説明されていないデータ バインディングの概念については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.Data.RelativeSource> クラスによって定義されます。  
  
 `RelativeSource` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  XAML のすべてのマークアップ拡張機能では、それぞれの属性構文で `{` と `}` の 2 つの記号を使用します。これは規約であり、これに従って XAML プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Data.Binding>   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [バインディング宣言の概要](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [x:Type マークアップ拡張機能](../../../../docs/framework/xaml-services/x-type-markup-extension.md)