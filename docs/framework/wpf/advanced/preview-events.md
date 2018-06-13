---
title: プレビュー イベント
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 2d6c1ab32cb43730af2f935f4bd4405059994c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546137"
---
# <a name="preview-events"></a>プレビュー イベント
プレビュー イベントは、イベントのトンネリングとも呼ばれるは、イベントを発生し、イベント データのソースとして報告されている要素に対するアプリケーションのルートからのルートの方向の移動、ルーティングされたイベントです。 すべてのイベント シナリオがサポートまたはプレビュー イベント; が必要このトピックでは、プレビュー イベントが存在、アプリケーションやコンポーネントを処理する方法、それらの状況と、カスタム コンポーネントまたはクラスでプレビュー イベントを作成する場合があります適切なケースについて説明します。  
  
## <a name="preview-events-and-input"></a>プレビュー イベントと入力  
 イベントは一般には注意してプレビューを処理する場合、イベントをマーク処理イベントのデータ。 以外の任意の要素でプレビュー イベントの処理 (イベント データのソースとして報告されている要素) を発生させた要素は、要素外の発生するイベントを処理する機会が提供されていないのです。 場合によってコントロールの複合内のリレーションシップに問題の要素が存在しない場合に特に目的の結果を示します。  
  
 入力イベントの具体的には、プレビュー イベントもイベント データのインスタンスと共有と同じバブル イベント。 プレビュー イベントのクラスのハンドラーを使用して処理する入力イベントをマークする場合、バブルの入力イベント クラスのハンドラーは呼び出されません。 または、プレビュー イベントのインスタンス ハンドラーを使用してイベントを処理済みのマークする場合、バブルのイベントのハンドラーは通常呼び出されません。 クラス ハンドラーまたはインスタンス ハンドラーを登録またはアタッチする手法は通常使用されませんが、イベントが処理される、マークされている場合でも呼び出されるオプションです。  
  
 クラスの処理とプレビュー イベントに関連する方法の詳細については、次を参照してください。 [Handled、クラス処理とルーティング イベントをマーク](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)です。  
  
### <a name="working-around-event-suppression-by-controls"></a>コントロールによるイベント抑制の回避  
 プレビュー イベントは一般的に使用されている 1 つのシナリオでは、入力イベントの複合コントロールの処理です。 場合によっては、コントロールの作成者は、コンポーネント定義のイベント詳細についてを実行するかより具体的な動作を表すを置換するために、そのコントロールから送信されたから特定のイベントを抑制します。 インスタンス、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>抑制<xref:System.Windows.UIElement.MouseLeftButtonDown>と<xref:System.Windows.UIElement.MouseLeftButtonDown>によって生成されるバブルのイベント、<xref:System.Windows.Controls.Button>またはその複合要素にマウスをキャプチャして、発生を優先するため、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>によって常に発生するイベントを<xref:System.Windows.Controls.Button>自体です。 イベントとそのデータ、ルートで引き続きするので、 <xref:System.Windows.Controls.Button> 、イベント データをマーク<xref:System.Windows.RoutedEventArgs.Handled%2A>、のみ、イベントのハンドラーを示す具体的で動作する、`handledEventsToo`ケースが呼び出されます。  1 つの代替手段がコードでのハンドラーをアタッチするには、アプリケーションのルートに近い方には、その他の要素も必要がある場合、コントロールで抑制されたイベントを処理する、`handledEventsToo`として指定された`true`です。 入力イベントの プレビューと同等に処理するルーティングの方向を変更する簡単な手法は、多くの場合。 インスタンスの場合は、コントロールを抑制<xref:System.Windows.UIElement.MouseLeftButtonDown>のハンドラーを添付してみてください<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>代わりにします。 この手法だけが、基本要素の入力イベントなど<xref:System.Windows.UIElement.MouseLeftButtonDown>です。 これらの入力イベントは、トンネル/バブルのペアを使用して、両方のイベントを発生させるし、イベント データを共有します。  
  
 これらの手法のそれぞれは、副作用または制限事項のいずれかにあります。 プレビュー イベントの処理の有効であること、バブルのイベントを処理するハンドラーが無効にその時点でイベントを処理であるため、制限することは通常、Previ のままである間に処理されるイベントをマークすることをお勧めルートの新しい部分。 制限事項、`handledEventsToo`手法は指定できません、`handledEventsToo`ハンドラー[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を属性として登録する必要あります、イベント ハンドラー コードでハンドラーがアタッチするのには、要素へのオブジェクト参照を取得した後にします。  
  
## <a name="see-also"></a>関連項目  
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
