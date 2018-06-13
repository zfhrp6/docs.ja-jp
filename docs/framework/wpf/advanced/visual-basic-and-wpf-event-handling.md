---
title: Visual Basic と WPF のイベント処理
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 321b4547bffbbae3c16ef8dd046bdff65ebe0bf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547824"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic と WPF のイベント処理
Microsoft Visual Basic .NET 言語具体的には、使用できます、言語固有`Handles`にイベント ハンドラーを関連付けるインスタンスの属性を持つイベント ハンドラーのアタッチまたはを使用する代わりに、キーワード、<xref:System.Windows.UIElement.AddHandler%2A>メソッドです。 ただし、`Handles`ために、ハンドラーのインスタンスにアタッチする方法はいくつかの制限には、`Handles`構文は、の特定のルーティング イベント機能の一部をサポートできない、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システムです。  
  
## <a name="using-handles-in-a-wpf-application"></a>WPF アプリケーションで「ハンドル」の使用  
 インスタンスでとイベントに接続されているイベント ハンドラー`Handles`すべては、必須の要素の属性値を割り当てられているイベント ハンドラーのインスタンスの部分クラス宣言内で定義する必要があります。 のみを指定できます`Handles`を持つページ上の要素の<xref:System.Windows.FrameworkContentElement.Name%2A>プロパティの値 (または[X:name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)宣言されている)。 これは、ため、<xref:System.Windows.FrameworkContentElement.Name%2A>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]をサポートするために必要なインスタンスの参照を作成、 *Instance.Event*で必要な参照形式、`Handles`構文です。 要素でのみ使用できるを`Handles`せず、<xref:System.Windows.FrameworkContentElement.Name%2A>参照は、部分クラスを定義するルート要素のインスタンス。  
  
 分離することにより、複数の要素に同じハンドラーを割り当てることができます*Instance.Event*後参照`Handles`をコンマでします。  
  
 使用することができます`Handles`に複数のハンドラーを同じに割り当てる*Instance.Event*参照します。 ハンドラーがで指定された順序に任意の重要度が割り当てられない、`Handles`参照; 任意の順序で、同じイベントを処理するハンドラーを起動できることを想定する必要があります。  
  
 追加されたハンドラーを削除する`Handles`宣言を呼び出すことができます<xref:System.Windows.UIElement.RemoveHandler%2A>です。  
  
 使用することができます`Handles`にそれらのメンバー テーブルで処理されるイベントを定義するインスタンスにハンドラーをアタッチするように、ルーティングされたイベントのハンドラーをアタッチします。 ルーティング イベントにアタッチされているハンドラーの`Handles`としてアタッチされているハンドラーと同じルーティング規則に従う[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性、またはの一般的なシグネチャを持つ<xref:System.Windows.UIElement.AddHandler%2A>します。 つまり、このイベントは既に設定されて処理される場合 (、<xref:System.Windows.RoutedEventArgs.Handled%2A>イベント データのプロパティは`True`) のハンドラーをアタッチし、`Handles`イベント インスタンスをへの応答は呼び出されません。 イベントは、またはクラスには、現在の要素またはルート上の以前の要素を処理して、ルート内の別の要素のインスタンス ハンドラーによって処理されるマークでした。 ペア トンネル/バブル イベントをサポートする入力イベントのトンネリングのルートを処理イベントのペア マークいる可能性があります。 ルーティング イベントの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>ハンドラーの追加「ハンドル」の制限事項  
 `Handles` 添付イベントのハンドラーを参照することはできません。 使用する必要があります、`add`その添付イベントのアクセサー メソッドまたは*typename.eventname*イベント属性で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
 ルーティング イベントの場合のみ使用できます`Handles`ハンドラーを割り当てるインスタンスのメンバー テーブルのイベントが存在するインスタンス。 ただし、ルーティングされたイベントで一般に、親要素できますから子要素、イベントのリスナー場合でも、親要素では、そのメンバー テーブルでは、そのイベントはありません。 属性の構文ではこれを指定できます、 *typename.membername*修飾どの型が実際に処理するイベントを定義するフォームの属性です。 インスタンスの親`Page`(のない`Click`イベントが定義されている) 形式で、属性のハンドラーを割り当てることでボタン クリック イベントのリッスンできる`Button.Click`です。 `Handles`はサポートしていません、 *typename.membername*フォームで、競合しているをサポートする必要がありますので*Instance.Event*フォーム。 詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
 `Handles` 既に処理済みとしてマークされるイベントに対して呼び出されるハンドラーをアタッチできません。 代わりに、コードと呼び出しを使用する必要があります、`handledEventsToo`のオーバー ロード<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>です。  
  
> [!NOTE]
>  使用しないで、 `Handles` XAML で、同じイベントのイベント ハンドラーを指定すると、Visual Basic コードの構文。 この場合、イベント ハンドラーが 2 回呼び出されます。  
  
## <a name="how-wpf-implements-handles-functionality"></a>どの WPF 実装「機能を処理」  
 ときに、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページがコンパイルされた中間ファイルは、宣言`Friend``WithEvents`を持つページ上のすべての要素への参照、<xref:System.Windows.FrameworkContentElement.Name%2A>プロパティ セット (または[X:name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)宣言されている)。 各名前付きインスタンスが使用してハンドラーに割り当てることのできる要素である可能性のある`Handles`です。  
  
> [!NOTE]
>  内で[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、[!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)]要素が使用できる入力候補を表示できます、`Handles`ページ内の参照。 ただし、これがかかるコンパイル パスの 1 つの中間ファイルがすべてに設定できるように、`Friends`参照します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
