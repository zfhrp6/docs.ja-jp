---
title: "DrawingVisual オブジェクトの使用"
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
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a33e56b69a357694a1d1a23d5cd3c887c88cea37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual オブジェクトの使用
このトピックの使用方法の概要を説明する<xref:System.Windows.Media.DrawingVisual>内のオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ビジュアル層です。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual>は、軽量な図形、画像、またはテキストを表示するために使用されるクラスを描画します。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual ホスト コンテナー  
 使用するために<xref:System.Windows.Media.DrawingVisual>オブジェクト、オブジェクトのホストのコンテナーを作成する必要があります。 ホストのコンテナー オブジェクトがから派生する必要があります、<xref:System.Windows.FrameworkElement>レイアウトやイベント処理のサポートを提供するクラス、<xref:System.Windows.Media.DrawingVisual>クラスがありません。 ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトでは可視プロパティは表示されません。 ただし、<xref:System.Windows.UIElement.Visibility%2A>にコンテナー ホストのプロパティを設定する必要があります<xref:System.Windows.Visibility.Visible>以外の場合、その子要素の [なし] が表示されます。  
  
 ビジュアル オブジェクトのホストのコンテナー オブジェクトを作成するときのビジュアル オブジェクトの参照を保存する必要があります、<xref:System.Windows.Media.VisualCollection>です。 使用して、<xref:System.Windows.Media.VisualCollection.Add%2A>ホスト コンテナーにビジュアル オブジェクトを追加します。 次の例では、ホストのコンテナー オブジェクトが作成、および 3 つのビジュアル オブジェクトに追加されます、<xref:System.Windows.Media.VisualCollection>です。  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Creating DrawingVisual オブジェクトの作成  
 作成するときに、<xref:System.Windows.Media.DrawingVisual>オブジェクトの描画コンテンツがありません。 テキスト、グラフィック、またはイメージのコンテンツを追加するには、オブジェクトを取得することによって<xref:System.Windows.Media.DrawingContext>とそこに描画します。 A<xref:System.Windows.Media.DrawingContext>呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッド、<xref:System.Windows.Media.DrawingVisual>オブジェクト。  
  
 四角形を描く、<xref:System.Windows.Media.DrawingContext>を使用して、<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。 他の種類のコンテンツを描画するための同様のメソッドもあります。 描画の内容を完了すると、 <xref:System.Windows.Media.DrawingContext>、呼び出し、<xref:System.Windows.Media.DrawingContext.Close%2A>を終了するメソッド、<xref:System.Windows.Media.DrawingContext>内容を保持するとします。  
  
 次の例で、<xref:System.Windows.Media.DrawingVisual>オブジェクトが作成され、四角形の描画にその<xref:System.Windows.Media.DrawingContext>です。  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement メンバーのオーバーライドの作成  
 ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。 これは、ホスト コンテナーが派生クラスのメンバーのオーバーライドを実装する必要があります<xref:System.Windows.FrameworkElement>クラスです。  
  
 オーバーライドする必要がある 2 つのメンバーを次に示します。  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: 子要素のコレクションから指定したインデックス位置の子を返します。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: この要素内でビジュアル子要素の数を取得します。  
  
 次の例では、2 つのオーバーライド<xref:System.Windows.FrameworkElement>メンバーが実装されます。  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>ヒット テストのサポート  
 イベント処理の表示プロパティが表示されない場合でも、そのホストのコンテナー オブジェクトを提供できます: ただし、その<xref:System.Windows.UIElement.Visibility%2A>プロパティに設定する必要があります<xref:System.Windows.Visibility.Visible>です。 これにより、マウス イベント (マウスの左ボタンのリリースなど) をトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。 イベントの処理ルーチンを呼び出すことによって、ヒット テスト実装できます、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドです。 メソッドの<xref:System.Windows.Media.HitTestResultCallback>パラメーターは、ヒット テストの結果として得られるアクションを決定するのに使用できるユーザー定義のプロシージャを表します。  
  
 次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装しています。  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
