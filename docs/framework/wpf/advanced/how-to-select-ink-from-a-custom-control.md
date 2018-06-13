---
title: '方法 : カスタム コントロールからインクを選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 6c85855cda4f74d557539ed7aea3f725550512e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548369"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>方法 : カスタム コントロールからインクを選択する
追加することによって、 <xref:System.Windows.Ink.IncrementalLassoHitTester> 、カスタム コントロールを有効にできますコントロールと同じように、選択ツールを使用してインクをユーザーが選択できるように、<xref:System.Windows.Controls.InkCanvas>なげなわを使用してインクを選択します。  
  
 この例では、インクが有効なカスタム コントロールの作成に慣れて前提としています。  インク入力を受け付けるカスタム コントロールを作成するを参照してください。[インク入力コントロールを作成する](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)です。  
  
## <a name="example"></a>例  
 ユーザーが、なげなわを描画するとき、<xref:System.Windows.Ink.IncrementalLassoHitTester>するストロークは、ユーザーがなげなわが完了したら、なげなわのパスの境界内を予測します。  なげなわのパスの境界内にあると判断したストロークは、選択されていると考えることができます。  選択されたストロークをオフになっていることができますもなります。  たとえば、ユーザー、描画中には方向が反転、<xref:System.Windows.Ink.IncrementalLassoHitTester>のストロークを選択解除できます。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>を生成、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントで、ユーザーは、描画中に応答する、カスタムの制御を有効にします。  たとえば、ユーザーを選択し、それらの選択を解除すると、ストロークの外観を変更できます。  
  
## <a name="managing-the-ink-mode"></a>インク モードの管理  
 なげなわがコントロール上のインクが異なって表示される場合、ユーザーに便利です。 これを実現するには、カスタム コントロールする必要がありますの追跡、ユーザーが記述またはインクを選択するかどうか。 これを行う最も簡単な方法は 2 つの値を持つ列挙体を宣言する: インクと、ユーザーがインクを選択することを示すために 1 つに、ユーザーを作成することを示すために 1 つです。  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 次に、2 つ追加<xref:System.Windows.Ink.DrawingAttributes>クラス: ユーザーがユーザーには、インクが選択したときに使用する 1 つのインクを書き込むときに使用する 1 つです。  コンス トラクターで初期化、<xref:System.Windows.Ink.DrawingAttributes>とアタッチ両方<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>同じイベント ハンドラーにイベント。 設定して、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インク<xref:System.Windows.Ink.DrawingAttributes>です。  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 選択モードを公開するプロパティを追加します。 選択モードを変更するときの設定、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を適切な<xref:System.Windows.Ink.DrawingAttributes>オブジェクトを再アタッチし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>プロパティを<xref:System.Windows.Controls.InkPresenter>です。  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 公開、<xref:System.Windows.Ink.DrawingAttributes>としてプロパティのアプリケーションは、インク ストロークと選択線の外観を特定できるようにします。  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 場合のプロパティ、<xref:System.Windows.Ink.DrawingAttributes>オブジェクトに対する変更を<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>にアタッチする必要があります、<xref:System.Windows.Controls.InkPresenter>です。  イベント ハンドラーで、<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>イベント、再接続、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>を<xref:System.Windows.Controls.InkPresenter>です。  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>使用して、IncrementalLassoHitTester  
 作成し、初期化、<xref:System.Windows.Ink.StrokeCollection>選択されたストロークを格納しています。  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 ユーザーがストロークを描画を開始、ときにインクまたはなげなわのいずれかの選択を解除、選択されたストロークです。 次に、ユーザーはなげなわを描画して場合に作成、<xref:System.Windows.Ink.IncrementalLassoHitTester>を呼び出して<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>にサブスクライブ、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベント、および呼び出し<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>です。 このコードを別のメソッドを指定できから呼び出される、<xref:System.Windows.UIElement.OnStylusDown%2A>と<xref:System.Windows.UIElement.OnMouseDown%2A>メソッドです。  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 スタイラスのポイントを追加、<xref:System.Windows.Ink.IncrementalLassoHitTester>ユーザーが、なげなわを描画中にします。  次のメソッドを呼び出して、 <xref:System.Windows.UIElement.OnStylusMove%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、 <xref:System.Windows.UIElement.OnMouseMove%2A>、および<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>メソッドです。  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 処理、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>イベント、ユーザーを選択し、ストロークの選択を解除するときに応答します。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs>クラスには、<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>と<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>ストロークを取得するプロパティがオンし、オフの場合、それぞれします。  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 ユーザーは、描画が完了すると、サブスクリプションの解除、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントと呼び出し<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>です。  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>すべてまとめて配置することです。  
 次の例は、カスタム コントロールをなげなわを使用してインクを選択するユーザーを有効にします。  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [インク入力コントロールの作成](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
