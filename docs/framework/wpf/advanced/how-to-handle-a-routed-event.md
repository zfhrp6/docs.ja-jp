---
title: '方法 : ルーティング イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: 80b3be439498c0dc448322d1e7daf30202a470dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544318"
---
# <a name="how-to-handle-a-routed-event"></a>方法 : ルーティング イベントを処理する
バブル イベントの動作と、ルーティング イベント データを処理できるハンドラーを作成する方法を次の例に示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、要素は、要素ツリー構造体に配置されます。 親要素は、要素ツリー内で最初に子要素が発生させたイベントの処理に参加できます。 これは、イベント ルーティングにより可能です。  
  
 ルーティング イベントは通常、バブルまたはトンネルの 2 つのルーティング方法のいずれかに従います。 この例は、バブルのイベントについて説明し、使用、<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType>をどのようにルーティングのしくみを表示するイベントです。  
  
 次の例では、2 つ作成されます<xref:System.Windows.Controls.Button>を制御しを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性構文、一般的な親要素にあり、この例では、イベント ハンドラーをアタッチする<xref:System.Windows.Controls.StackPanel>です。 それぞれの個別のイベント ハンドラーをアタッチするのではなく<xref:System.Windows.Controls.Button>子要素、例を使用して属性の構文をイベント ハンドラーをアタッチする、<xref:System.Windows.Controls.StackPanel>親要素です。 このイベント処理パターンは、ハンドラーがアタッチされる要素の数を減らすための手法としてイベント ルーティングを使用する方法を示します。 すべてのバブル イベントごとに<xref:System.Windows.Controls.Button>親要素内のルートです。  
  
 親のことに注意して<xref:System.Windows.Controls.StackPanel>要素、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>属性を指定することによって部分的に限定として指定したイベントの名前、<xref:System.Windows.Controls.Button>クラスです。 <xref:System.Windows.Controls.Button>クラスは、<xref:System.Windows.Controls.Primitives.ButtonBase>派生クラスを持つ、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>でそのメンバーを一覧表示するイベントです。 イベント ハンドラーをアタッチするためのこの部分修飾手法が必要になるのは、ルーティング イベント ハンドラーがアタッチされる要素のメンバー一覧に、処理されているイベントが存在しない場合です。  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 次の例のハンドル、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  この例では、イベントを処理する要素とイベントを発生させる要素を報告します。 ユーザーがいずれかのボタンをクリックすると、イベント ハンドラーが実行されます。  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.RoutedEvent>  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
