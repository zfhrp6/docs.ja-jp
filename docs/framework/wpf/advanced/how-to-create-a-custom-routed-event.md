---
title: '方法 : カスタム ルーティング イベントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a8aa038008ed93cedfe49fde4e0269712b4fb19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543707"
---
# <a name="how-to-create-a-custom-routed-event"></a>方法 : カスタム ルーティング イベントを作成する
イベントのルーティングをサポートするために、カスタム イベントを登録する必要があります、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッドです。 この例では、カスタム ルーティング イベント作成の基本を紹介します。  
  
## <a name="example"></a>例  
 次の例に示すように、最初に登録する、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッドです。 慣例により、<xref:System.Windows.RoutedEvent>静的フィールドの名前サフィックスを末尾***イベント***です。 この例では、イベントの名前は`Tap`イベントのルーティング方法で、<xref:System.Windows.RoutingStrategy.Bubble>です。 登録呼び出し後、イベントの add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベント アクセサーを提供できます。  
  
 この特別な例では `OnTap` 仮想メソッド経由でイベントが発生していますが、イベントの発生や変更に対するイベントの反応の仕方はニーズによって変わります。  
  
 この例は、の全体のサブクラスを基本的には実装にも注意してください<xref:System.Windows.Controls.Button>; そのサブクラスの個別のアセンブリとしてビルドし、は別にカスタム クラスとしてインスタンス化し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページ。 これはサブクラス化されたコントロールを他のコントロールで構成されたツリーに挿入できるという概念を示すものです。この状況では、このようなコントロールのカスタム イベントには、あらゆるネイティブ [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 要素とまったく同じイベント ルーティング機能が与えられます。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 トンネリング イベントが作成されて、同じ方法ですが、 <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> 'éý'<xref:System.Windows.RoutingStrategy.Tunnel>登録呼び出しで。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のトンネル イベントには接頭辞として "Preview" という単語が付く決まりになっています。  
  
 バブリング イベントの動作例については、「[ルーティング イベントを処理する](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
