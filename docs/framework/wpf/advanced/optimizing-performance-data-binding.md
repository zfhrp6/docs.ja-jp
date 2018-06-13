---
title: 'パフォーマンスの最適化 : データ バインド'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: da870e9459ee2cbe0384c146546c378fb7247f03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548780"
---
# <a name="optimizing-performance-data-binding"></a>パフォーマンスの最適化 : データ バインド
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングは、アプリケーションがデータを提示し、データと対話するための簡単で一貫性のある方法を提供します。 要素は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトおよび [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] の形式のさまざまなデータ ソースのデータにバインドできます。  
  
 このトピックでは、データ バインディングのパフォーマンスに関する推奨事項について説明します。  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>データ バインディングの参照が解決されるしくみ  
 データ バインディングのパフォーマンスの問題に入る前に、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のデータ バインディング エンジンがバインディングのオブジェクト参照をどのように解決するのかを説明します。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のデータ バインディングでは、任意の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトをソースとして使用して、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトのプロパティ、サブプロパティ、インデクサーにバインドできます。 いずれかの Microsoft .NET Framework リフレクションを使用してバインドの参照が解決または<xref:System.ComponentModel.ICustomTypeDescriptor>です。 次に、バインディングのオブジェクト参照を解決するための 3 つの方法について説明します。  
  
 1 つ目は、リフレクションを使用する方法です。 ここで、<xref:System.Reflection.PropertyInfo>オブジェクトがプロパティの属性を検出するために使用し、プロパティのメタデータへのアクセスを提供します。 使用する場合、<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイス、データ バインディング エンジンには、このインターフェイスを使用してプロパティ値にアクセスします。 <xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスは、オブジェクトには静的なプロパティ セットにない場合に特に便利です。  
  
 実装することでいずれかのプロパティの変更通知を指定することができます、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスかに関連付けられている変更通知を使用して、<xref:System.ComponentModel.TypeDescriptor>です。 プロパティの変更通知を実装するための推奨の戦略が使用する<xref:System.ComponentModel.INotifyPropertyChanged>です。  
  
 ソース オブジェクトがある場合、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]オブジェクトと基になるプロパティは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティ、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]最初、ソース オブジェクトを取得するリフレクションを使用して、データ バインディング エンジンが、 <xref:System.ComponentModel.TypeDescriptor>、クエリを実行し、<xref:System.ComponentModel.PropertyDescriptor>です。 パフォーマンスの観点から見た場合、このリフレクション操作のシーケンスには非常に時間がかかる可能性があります。  
  
 オブジェクト参照を解決するための 2 つ目の方法では、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]を実装するソース オブジェクト、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス、およびソース プロパティが、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティです。 この場合、データ バインディング エンジンは、ソースの型に対してリフレクションを直接使用して必要なプロパティを取得します。 この方法も最適な方法とは言えませんが、最初の方法よりは作業セットの要件の負荷が小さくなります。  
  
 オブジェクト参照を解決する 3 番目の方法では、ソース オブジェクトである、<xref:System.Windows.DependencyObject>ソースのプロパティは、<xref:System.Windows.DependencyProperty>です。 この場合、データ バインディング エンジンはリフレクションを使用する必要はありません。 代わりに、プロパティ エンジンとデータ バインディング エンジンが連携してプロパティ参照を個別に解決します。 これが、データ バインディングに使用されているオブジェクト参照を解決するための最適な方法です。  
  
 次の表のデータ バインディングの速度を比較し、 <xref:System.Windows.Controls.TextBlock.Text%2A> 1,000 分の 1 つのプロパティ<xref:System.Windows.Controls.TextBlock>これら 3 つのメソッドを使用して要素。  
  
|**TextBlock の Text プロパティのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトのプロパティ|115|314|  
|プロパティに、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]を実装するオブジェクト <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|<xref:System.Windows.DependencyProperty>の<xref:System.Windows.DependencyObject>です。|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>大きな CLR オブジェクトへのバインディング  
 何千ものプロパティを持つ 1 つの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトへのデータ バインディングは、パフォーマンスに大きな影響を及ぼします。 この影響を最小限に抑えるには、その 1 つのオブジェクトを複数の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトに分割して、個々のオブジェクトのプロパティの数を減らします。 次の表は、1 つの大きな [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトへのデータ バインディングと複数の小さなオブジェクトへのデータ バインディングのバインディング時間とレンダリング時間を示しています。  
  
|**1000 個の TextBlock オブジェクトのデータ バインディングのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000 個のプロパティを持つ 1 つの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト|950|1200|  
|1 つのプロパティを持つ 1000 個の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>ItemsSource へのバインディング  
 考慮する必要があるシナリオ、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601>に表示する従業員の一覧を保持するオブジェクト、<xref:System.Windows.Controls.ListBox>です。 これら 2 つのオブジェクト間の対応を作成するには、従業員一覧にはバインド、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>です。 ここで、グループに新しい従業員が加わったとします。 この新しいユーザーをバインドに挿入するためにあると考えることがあります<xref:System.Windows.Controls.ListBox>値を単に従業員一覧にこのユーザーを追加し、データ バインディング エンジンによって自動的に認識されるには、この変更を想定しています。 想定性が証明 false です。実際には、変更は反映されませんで、<xref:System.Windows.Controls.ListBox>自動的にします。 これは、ため、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601>オブジェクトがコレクション変更イベントを自動的に発生しません。 取得するために、<xref:System.Windows.Controls.ListBox>の変更内容を選択するには、従業員のリストを再作成し、再アタッチする必要が、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>です。 この解決方法で問題は解決されますが、パフォーマンスへの影響はきわめて大きくなります。 再割り当てするたびに、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.ListBox>、新しいオブジェクトを<xref:System.Windows.Controls.ListBox>最初その前の項目でスロー除去し、そのリスト全体を再生成します。 場合、パフォーマンスに与える影響が拡大され、 <xref:System.Windows.Controls.ListBox> 、複雑なマップ<xref:System.Windows.DataTemplate>です。  
  
 この問題を非常に効率的なソリューションは、[従業員] ボックスの一覧を<xref:System.Collections.ObjectModel.ObservableCollection%601>です。 <xref:System.Collections.ObjectModel.ObservableCollection%601>オブジェクトがデータ バインディング エンジンが受信できる変更通知を発生させます。 イベントを追加またはから項目を削除、<xref:System.Windows.Controls.ItemsControl>リスト全体を再生成する必要はありません。  
  
 更新にかかる時間以下の表、 <xref:System.Windows.Controls.ListBox> (UI 仮想化が無効になっています) の 1 つの項目を追加するとします。 最初の行の数が経過時間を表すときに、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601>オブジェクトのバインド先<xref:System.Windows.Controls.ListBox>要素の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>します。 2 番目の行の数が経過時間を表すときに、<xref:System.Collections.ObjectModel.ObservableCollection%601>にバインドされて、<xref:System.Windows.Controls.ListBox>要素の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>します。 時間の大幅な削減効果を使用して、メモ、<xref:System.Collections.ObjectModel.ObservableCollection%601>データ バインディングの戦略です。  
  
|**ItemsSource のデータ バインディングのバインド先**|**1 項目の更新時間 (ミリ秒)**|  
|--------------------------------------|---------------------------------------|  
|[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601>オブジェクト|1656|  
|に、 <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IEnumerable ではなく IList を ItemsControl にバインドする  
 バインディングのいずれかを使用していれば、<xref:System.Collections.Generic.IList%601>または<xref:System.Collections.IEnumerable>を<xref:System.Windows.Controls.ItemsControl>オブジェクトを選択して、<xref:System.Collections.Generic.IList%601>オブジェクト。 バインド<xref:System.Collections.IEnumerable>を<xref:System.Windows.Controls.ItemsControl>強制的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ラッパーを作成する<xref:System.Collections.Generic.IList%601>オブジェクトで、2 番目のオブジェクトの不要なオーバーヘッドが、パフォーマンスに影響することを意味します。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>データ バインディングのためだけに CLR オブジェクトを XML に変換しない  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] コンテンツへのデータ バインディングが可能です。ただし、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] コンテンツへのデータ バインディングは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトへのデータ バインディングに比べて低速です。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトのデータをデータ バインディングのためだけに XML に変換しないでください。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
